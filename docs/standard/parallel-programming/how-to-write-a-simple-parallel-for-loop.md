---
title: Procedimiento para escribir un bucle Parallel.For simple
description: Aprenda a escribir bucles Parallel.For en .NET en los que no tiene que cancelar el bucle, interrumpir las iteraciones del bucle ni mantener ningún estado local del subproceso.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Parallel.For, How to Write
- for loop, parallel construction in .NET
- parallel for loops, how to use
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
ms.openlocfilehash: 506d6dd725f5d42c6c445a14c5f450c815bfdde1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826639"
---
# <a name="how-to-write-a-simple-parallelfor-loop"></a>Procedimiento para escribir un bucle Parallel.For simple

Este tema contiene dos ejemplos que ilustran el método <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. El primer ejemplo usa la sobrecarga del método <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=nameWithType> y el segundo usa la sobrecarga <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=nameWithType>, las dos sobrecargas más simples del método <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. Puede usar estas dos sobrecargas del método <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> cuando no sea necesario cancelar el bucle, interrumpir las iteraciones del bucle o mantener cualquier estado local de subproceso.

> [!NOTE]
> En esta documentación, se utilizan expresiones lambda para definir delegados en la TPL. Si no está familiarizado con las expresiones lambda de C# o Visual Basic, consulte [Expresiones lambda en PLINQ y TPL](lambda-expressions-in-plinq-and-tpl.md).

El primer ejemplo calcula el tamaño de los archivos de un solo directorio. El segundo calcula el producto de dos matrices.

## <a name="directory-size-example"></a>Ejemplo de tamaño de directorio

Este ejemplo es una utilidad de línea de comandos simple que calcula el tamaño total de los archivos de un directorio. Espera una ruta de directorio única como argumento e informa del número y el tamaño total de los archivos del directorio. Después de comprobar que el directorio existe, usa el método <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> para enumerar los archivos del directorio y determinar su tamaño. A continuación, el tamaño de los archivos se agrega a la variable `totalSize`. Tenga en cuenta que la adición se realiza llamando a <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> para que se lleve a cabo como una operación atómica. De lo contrario, varias tareas podrían tratar de actualizar la variable `totalSize` simultáneamente.

[!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
[!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]

## <a name="matrix-and-stopwatch-example"></a>Ejemplo de matriz y cronómetro

Este ejemplo usa el método <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> para calcular el producto de dos matrices. También muestra cómo usar la clase <xref:System.Diagnostics.Stopwatch?displayProperty=nameWithType> para comparar el rendimiento de un bucle paralelo con un bucle no paralelo. Tenga en cuenta que, como puede generar un gran volumen de salida, el ejemplo permite redirigir la salida a un archivo.

[!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
[!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]

Al paralelizar código, incluidos los bucles, un objetivo importante consiste en usar los procesadores tanto como sea posible, sin paralelizar en exceso hasta el punto de que la sobrecarga del procesamiento en paralelo niegue cualquier mejora en el rendimiento. En este ejemplo concreto solo se paraleliza el bucle externo, ya que el bucle interno no realiza mucho trabajo. La combinación de una pequeña cantidad de trabajo y efectos no deseados en la caché puede producir una degradación del rendimiento en los bucles paralelos anidados. Por consiguiente, paralelizar el bucle exterior solo es la mejor manera de maximizar las ventajas de simultaneidad en la mayoría de los sistemas.

## <a name="the-delegate"></a>Delegado

El tercer parámetro de esta sobrecarga de <xref:System.Threading.Tasks.Parallel.For%2A> es un delegado de tipo `Action<int>` en C# o `Action(Of Integer)` en Visual Basic. Un delegado `Action`, tanto si tiene uno, dieciséis o ningún parámetro de tipo, siempre devuelve void. En Visual Basic, el comportamiento de `Action` se define con `Sub`. El ejemplo usa una expresión lambda para crear el delegado, pero puede crear el delegado de otras maneras. Para obtener más información, consulte [Expresiones lambda en PLINQ y TPL](lambda-expressions-in-plinq-and-tpl.md).

## <a name="the-iteration-value"></a>Valor de iteración

El delegado toma un solo parámetro de entrada cuyo valor es la iteración actual. Este valor de iteración lo suministra el tiempo de ejecución y su valor inicial es el índice del primer elemento del segmento (partición) del origen que se está procesando en el subproceso actual.

Si necesita más control sobre el nivel de simultaneidad, use una de las sobrecargas que toma un parámetro de entrada <xref:System.Threading.Tasks.ParallelOptions?displayProperty=nameWithType>, como <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=nameWithType>.

## <a name="return-value-and-exception-handling"></a>Valor devuelto y control de excepciones

<xref:System.Threading.Tasks.Parallel.For%2A> devuelve un objeto <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=nameWithType> cuando se completen todos los subprocesos. Este valor devuelto es útil cuando se desea detener o interrumpir la iteración de bucle manualmente, ya que <xref:System.Threading.Tasks.ParallelLoopResult> almacena información, como la última iteración que se ejecutó hasta completarse. Si se producen una o más excepciones en uno de los subprocesos, se inicia <xref:System.AggregateException?displayProperty=nameWithType>.

En el código de este ejemplo, no se usa el valor devuelto de <xref:System.Threading.Tasks.Parallel.For%2A>.

## <a name="analysis-and-performance"></a>Análisis y rendimiento

Puede usar el Asistente de rendimiento para ver el uso de CPU en el equipo. Como experimento, aumente el número de columnas y filas de las matrices. Cuanto mayores sean las matrices, mayor será la diferencia de rendimiento entre las versiones paralelas y secuenciales del cálculo. Si la matriz es pequeña, la versión secuencial se ejecutará más rápido debido a la sobrecarga de la configuración del bucle paralelo.

Las llamadas sincrónicas a los recursos compartidos, como la consola o el sistema de archivos, reducirán considerablemente el rendimiento de un bucle paralelo. Al medir el rendimiento, intente evitar las llamadas como <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dentro del bucle.

## <a name="compile-the-code"></a>Compilar el código

Copie y pegue este código en un proyecto de Visual Studio.

## <a name="see-also"></a>Vea también

- <xref:System.Threading.Tasks.Parallel.For%2A>
- <xref:System.Threading.Tasks.Parallel.ForEach%2A>
- [Paralelismo de datos](data-parallelism-task-parallel-library.md)
- [Programación en paralelo](index.md)
