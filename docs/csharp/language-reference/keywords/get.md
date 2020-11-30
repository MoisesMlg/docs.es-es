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
# <a name="get-c-reference"></a><span data-ttu-id="158b8-103">get (Referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="158b8-103">get (C# Reference)</span></span>

<span data-ttu-id="158b8-104">La palabra clave `get` define un método de *descriptor de acceso* en una propiedad o un indizador que devuelve el valor de la propiedad o el elemento del indizador.</span><span class="sxs-lookup"><span data-stu-id="158b8-104">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="158b8-105">Para obtener más información, consulte [Propiedades](../../programming-guide/classes-and-structs/properties.md), [Propiedades autoimplementadas](../../programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indexers Indizadores](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="158b8-105">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="158b8-106">En el ejemplo siguiente se definen unos descriptores de acceso `get` y `set` para una propiedad denominada `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="158b8-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="158b8-107">Usa un campo privado denominado `_seconds` para respaldar el valor de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="158b8-107">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="158b8-108">A menudo, el descriptor de acceso `get` consta de una única instrucción que devuelve un valor, como en el ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="158b8-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="158b8-109">A partir de C# 7.0, se puede implementar el descriptor de acceso `get` como un miembro con forma de expresión.</span><span class="sxs-lookup"><span data-stu-id="158b8-109">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="158b8-110">En el ejemplo siguiente se implementan los descriptores de acceso `get` y `set` como miembros con forma de expresión.</span><span class="sxs-lookup"><span data-stu-id="158b8-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="158b8-111">En los casos sencillos en los que los descriptores de acceso `get` y `set` de una propiedad no realizan ninguna operación aparte de establecer o recuperar un valor en un campo de respaldo privado, puede aprovechar la compatibilidad del compilador de C# con las propiedades implementadas automáticamente.</span><span class="sxs-lookup"><span data-stu-id="158b8-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="158b8-112">En el ejemplo siguiente se implementa `Hours` como una propiedad implementada automáticamente.</span><span class="sxs-lookup"><span data-stu-id="158b8-112">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="158b8-113">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="158b8-113">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="158b8-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="158b8-114">See also</span></span>

- [<span data-ttu-id="158b8-115">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="158b8-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="158b8-116">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="158b8-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="158b8-117">Palabras clave de C#</span><span class="sxs-lookup"><span data-stu-id="158b8-117">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="158b8-118">Propiedades</span><span class="sxs-lookup"><span data-stu-id="158b8-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
