---
title: Procedimiento Uso del bloque Try/Catch para detectar excepciones
description: Utilice el bloque Try para incluir instrucciones que puedan generar o producir una excepción. Coloque las instrucciones para controlar las excepciones en uno o varios bloques Catch.
ms.date: 02/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
ms.openlocfilehash: cfe5b2b304cdb9efe7f0d91059fe1c279b4fa2dd
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828015"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Cómo usar el bloque Try/Catch para detectar excepciones

Coloque las instrucciones de código que podrían elevar o producir una excepción en un bloque `try`, y las que se usan para controlar la excepción o excepciones en uno o varios bloques `catch` debajo del bloque `try`. Cada bloque `catch` incluye el tipo de excepción y puede contener instrucciones adicionales necesarias para controlar ese tipo de excepción.

En el ejemplo siguiente, un elemento <xref:System.IO.StreamReader> abre un archivo denominado *data.txt* y recupera una línea del archivo. Como es posible que el código genere cualquiera de las tres excepciones, se coloca en un bloque `try`. Tres bloques `catch` detectan las excepciones y las controlan mostrando los resultados en la consola.

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

Common Language Runtime (CLR) detecta las excepciones no controladas por los bloques `catch`. Si CLR detecta una excepción, puede producirse uno de los resultados siguientes, en función de la configuración de CLR:

- Aparece un cuadro de diálogo **Depurar**.
- El programa detiene la ejecución y aparece un cuadro de diálogo con información de la excepción.
- Se imprime un error en el [flujo de salida de error estándar](xref:System.Console.Error).

> [!NOTE]
> La mayoría del código puede producir una excepción y algunas excepciones, como <xref:System.OutOfMemoryException>, las puede generar el propio CLR en cualquier momento. Aunque no es obligatorio que las aplicaciones controlen estas excepciones, tenga en cuenta esta posibilidad al escribir bibliotecas que puedan usar otros usuarios. Para obtener sugerencias sobre cuándo establecer el código en un bloque `try`, vea [Procedimientos recomendados para excepciones](best-practices-for-exceptions.md).

## <a name="see-also"></a>Vea también

- [Excepciones](index.md)
- [Control de errores de E/S en .NET](../io/handling-io-errors.md)
