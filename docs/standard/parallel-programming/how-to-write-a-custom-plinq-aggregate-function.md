---
title: 'Cómo: Escribir una función de agregado personalizada de PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: dc03802c960c0926380d7b7fa44fdf436b8fea89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734262"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="69b83-102">Cómo: Escribir una función de agregado personalizada de PLINQ</span><span class="sxs-lookup"><span data-stu-id="69b83-102">How to: Write a Custom PLINQ Aggregate Function</span></span>

<span data-ttu-id="69b83-103">En este ejemplo se muestra cómo utilizar el método <xref:System.Linq.ParallelEnumerable.Aggregate%2A> para aplicar una función de agregación personalizada a una secuencia de origen.</span><span class="sxs-lookup"><span data-stu-id="69b83-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="69b83-104">La finalidad de este ejemplo es mostrar el uso, y puede que su ejecución no sea tan rápida como la de la consulta LINQ to Objects secuencial equivalente.</span><span class="sxs-lookup"><span data-stu-id="69b83-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="69b83-105">Para más información sobre la velocidad, vea [Introducción a la velocidad en PLINQ](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="69b83-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69b83-106">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="69b83-106">Example</span></span>  

 <span data-ttu-id="69b83-107">En el ejemplo siguiente se calcula la desviación estándar de una secuencia de enteros.</span><span class="sxs-lookup"><span data-stu-id="69b83-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="69b83-108">Este ejemplo utiliza una sobrecarga del operador de consulta estándar agregado que sea único en PLINQ.</span><span class="sxs-lookup"><span data-stu-id="69b83-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="69b83-109">Esta sobrecarga adopta un delegado adicional <xref:System.Func%603?displayProperty=nameWithType> como tercer parámetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="69b83-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="69b83-110">Este delegado combina los resultados de todos los subprocesos antes de realizar el cálculo final de los resultados agregados.</span><span class="sxs-lookup"><span data-stu-id="69b83-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="69b83-111">En este ejemplo se agregan las sumas de todos los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="69b83-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="69b83-112">Tenga en cuenta que, cuando un cuerpo de expresiones lambda consta de una única expresión, el valor devuelto del delegado <xref:System.Func%602?displayProperty=nameWithType> es el valor de la expresión.</span><span class="sxs-lookup"><span data-stu-id="69b83-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b83-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="69b83-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="69b83-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="69b83-114">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
