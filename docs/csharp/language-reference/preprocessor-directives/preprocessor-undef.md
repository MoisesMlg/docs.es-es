---
description: '#undef: Referencia de C#'
title: '#undef: Referencia de C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "91150562"
---
# <a name="undef-c-reference"></a><span data-ttu-id="cecc7-103">#undef (Referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="cecc7-103">#undef (C# Reference)</span></span>

<span data-ttu-id="cecc7-104">`#undef` le permite anular la definición de un símbolo, de tal forma que, si se usa como la expresión en una directiva [#if](./preprocessor-if.md), la expresión se evaluará como `false`.</span><span class="sxs-lookup"><span data-stu-id="cecc7-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="cecc7-105">Un símbolo se puede definir con la directiva [#define](./preprocessor-define.md) o la opción del compilador [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="cecc7-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="cecc7-106">La directiva `#undef` debe aparecer en el archivo antes de que use cualquier instrucción que tampoco sea una directiva.</span><span class="sxs-lookup"><span data-stu-id="cecc7-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecc7-107">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="cecc7-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="cecc7-108">**DEBUG está sin definirse**</span><span class="sxs-lookup"><span data-stu-id="cecc7-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="cecc7-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="cecc7-109">See also</span></span>

- [<span data-ttu-id="cecc7-110">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="cecc7-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cecc7-111">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="cecc7-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cecc7-112">Directivas de preprocesador de C#</span><span class="sxs-lookup"><span data-stu-id="cecc7-112">C# Preprocessor Directives</span></span>](./index.md)
