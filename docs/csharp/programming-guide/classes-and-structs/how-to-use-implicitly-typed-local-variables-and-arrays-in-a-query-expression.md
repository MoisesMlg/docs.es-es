---
title: Procedimiento para usar matrices y variables locales con tipo implícito en expresiones de consulta - Guía de programación de C#
description: Use variables locales con tipo implícito en C# para hacer que el compilador determine el tipo de una variable local. Tendrá que usarlas para almacenar tipos anónimos.
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: 0379cf7a172b989a9c686fd2da20ca8bf8da4997
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098870"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="75a82-104">Procedimiento para usar matrices y variables locales con tipo implícito en expresiones de consulta (Guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="75a82-104">How to use implicitly typed local variables and arrays in a query expression (C# Programming Guide)</span></span>

<span data-ttu-id="75a82-105">Puede usar variables locales con tipo implícito siempre que quiera que el compilador determine el tipo de una variable local.</span><span class="sxs-lookup"><span data-stu-id="75a82-105">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="75a82-106">Debe usar variables locales con tipo implícito para almacenar tipos anónimos, que a menudo se usan en las expresiones de consulta.</span><span class="sxs-lookup"><span data-stu-id="75a82-106">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="75a82-107">En los ejemplos siguientes, se muestran los usos obligatorios y opcionales de las variables locales con tipo implícito en las consultas.</span><span class="sxs-lookup"><span data-stu-id="75a82-107">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="75a82-108">Las variables locales con tipo implícito se declaran mediante la palabra clave contextual [var](../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="75a82-108">Implicitly typed local variables are declared by using the [var](../../language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="75a82-109">Para obtener más información, vea [Variables locales con asignación implícita de tipos](./implicitly-typed-local-variables.md) y [Matrices con asignación implícita de tipos](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="75a82-109">For more information, see [Implicitly Typed Local Variables](./implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a82-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="75a82-110">Example</span></span>  

 <span data-ttu-id="75a82-111">En el ejemplo siguiente, se muestra un escenario común en el que la palabra clave `var` es necesaria: una expresión de consulta que genera una secuencia de tipos anónimos.</span><span class="sxs-lookup"><span data-stu-id="75a82-111">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="75a82-112">En este escenario, la variable de consulta y la variable de iteración en la instrucción `foreach` deben escribirse de forma implícita mediante el uso de `var` porque no se tiene acceso a un nombre de tipo para el tipo anónimo.</span><span class="sxs-lookup"><span data-stu-id="75a82-112">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="75a82-113">Para obtener más información sobre los tipos anónimos, vea [Tipos anónimos](./anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="75a82-113">For more information about anonymous types, see [Anonymous Types](./anonymous-types.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="75a82-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="75a82-114">Example</span></span>  

 <span data-ttu-id="75a82-115">En el ejemplo siguiente, se usa la palabra clave `var` en una situación similar, pero en la que el uso de `var` es opcional.</span><span class="sxs-lookup"><span data-stu-id="75a82-115">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="75a82-116">Dado que `student.LastName` es una cadena, la ejecución de la consulta devuelve una secuencia de cadenas.</span><span class="sxs-lookup"><span data-stu-id="75a82-116">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="75a82-117">Por tanto, el tipo de `queryID` podría declararse como `System.Collections.Generic.IEnumerable<string>` en lugar de `var`.</span><span class="sxs-lookup"><span data-stu-id="75a82-117">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="75a82-118">La palabra clave `var` se usa por comodidad.</span><span class="sxs-lookup"><span data-stu-id="75a82-118">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="75a82-119">En el ejemplo, la variable de iteración en la instrucción `foreach` se escribe de forma explícita como una cadena, pero se podría declarar mediante `var`.</span><span class="sxs-lookup"><span data-stu-id="75a82-119">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="75a82-120">Dado que el tipo de la variable de iteración no es un tipo anónimo, el uso de `var` es opcional, no es obligatorio.</span><span class="sxs-lookup"><span data-stu-id="75a82-120">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="75a82-121">Recuerde que `var` no es un tipo, sino una instrucción para que el compilador deduzca y asigne el tipo.</span><span class="sxs-lookup"><span data-stu-id="75a82-121">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a><span data-ttu-id="75a82-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="75a82-122">See also</span></span>

- [<span data-ttu-id="75a82-123">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="75a82-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="75a82-124">Métodos de extensión</span><span class="sxs-lookup"><span data-stu-id="75a82-124">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="75a82-125">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="75a82-125">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="75a82-126">var</span><span class="sxs-lookup"><span data-stu-id="75a82-126">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="75a82-127">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="75a82-127">LINQ in C#</span></span>](../../linq/index.md)
