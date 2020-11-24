---
title: Procedimiento para controlar excepciones en bucles paralelos
description: Aprenda a controlar excepciones en bucles paralelos en .NET. Vea un ejemplo de cómo ajustar todas las excepciones del bucle en System.AggregateException.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: e8478f27b21b9b9dbf85d68f766c24aa5b9cf600
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825759"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Procedimiento para controlar excepciones en bucles paralelos
Las sobrecargas <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> no tienen ningún mecanismo especial para controlar las excepciones que puedan iniciarse. En este sentido, se asemejan a bucles `for` y `foreach` normales (`For` y `For Each` en Visual Basic). Una excepción no controlada hace que el bucle termine en cuanto finalicen todas las iteraciones que se estén ejecutando.
  
 Cuando agregue su propia lógica de control de excepciones a los bucles paralelos, tenga en cuenta la posibilidad de que se inicien excepciones similares en varios subprocesos al mismo tiempo y la opción de que una excepción iniciada en un subproceso puede hacer que se inicie otra excepción en otro subproceso. Puede controlar ambos casos ajustando todas las excepciones del bucle en <xref:System.AggregateException?displayProperty=nameWithType>. En el ejemplo siguiente, se muestra un posible enfoque.  
  
> [!NOTE]
> Cuando está habilitada la opción "Solo mi código", en algunos casos, Visual Studio se interrumpe en la línea que produce la excepción y muestra el mensaje de error "Excepción no controlada por el código de usuario". Este error es benigno. Puede presionar F5 para continuar y ver el comportamiento de control de excepciones que se muestra en el siguiente ejemplo. Para evitar que Visual Studio se interrumpa con el primer error, desactive la casilla "Solo mi código" en **Herramientas, Opciones, Depurar, General**.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se detectan todas las excepciones y, a continuación, se ajusta en un <xref:System.AggregateException?displayProperty=nameWithType> que se produce. El llamador puede decidir qué excepciones se deben administrar.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Vea también

- [Paralelismo de datos](data-parallelism-task-parallel-library.md)
- [Expresiones lambda en PLINQ y TPL](lambda-expressions-in-plinq-and-tpl.md)
