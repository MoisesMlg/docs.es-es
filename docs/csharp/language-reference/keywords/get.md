---
description: 'get: Referencia de C#'
title: 'get: Referencia de C#'
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "89139741"
---
# <a name="get-c-reference"></a>get (Referencia de C#)

La palabra clave `get` define un método de *descriptor de acceso* en una propiedad o un indizador que devuelve el valor de la propiedad o el elemento del indizador. Para obtener más información, consulte [Propiedades](../../programming-guide/classes-and-structs/properties.md), [Propiedades autoimplementadas](../../programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexers Indizadores](../../programming-guide/indexers/index.md).  
  
En el ejemplo siguiente se definen unos descriptores de acceso `get` y `set` para una propiedad denominada `Seconds`. Usa un campo privado denominado `_seconds` para respaldar el valor de la propiedad.  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
A menudo, el descriptor de acceso `get` consta de una única instrucción que devuelve un valor, como en el ejemplo anterior. A partir de C# 7.0, se puede implementar el descriptor de acceso `get` como un miembro con forma de expresión. En el ejemplo siguiente se implementan los descriptores de acceso `get` y `set` como miembros con forma de expresión.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

En los casos sencillos en los que los descriptores de acceso `get` y `set` de una propiedad no realizan ninguna operación aparte de establecer o recuperar un valor en un campo de respaldo privado, puede aprovechar la compatibilidad del compilador de C# con las propiedades implementadas automáticamente. En el ejemplo siguiente se implementa `Hours` como una propiedad implementada automáticamente.
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Especificación del lenguaje C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [Palabras clave de C#](./index.md)
- [Propiedades](../../programming-guide/classes-and-structs/properties.md)
