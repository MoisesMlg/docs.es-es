---
title: 'Cómo: Crear tareas precalculadas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: e83b467e23013b5690db7cc63d061cab4d5d0e31
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734509"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="68df7-102">Cómo: Crear tareas precalculadas</span><span class="sxs-lookup"><span data-stu-id="68df7-102">How to: Create Pre-Computed Tasks</span></span>

<span data-ttu-id="68df7-103">En este documento se describe cómo utilizar el método <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> para recuperar los resultados de las operaciones asincrónicas de descarga que se retienen en una memoria caché.</span><span class="sxs-lookup"><span data-stu-id="68df7-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="68df7-104">El método <xref:System.Threading.Tasks.Task.FromResult%2A> devuelve un objeto <xref:System.Threading.Tasks.Task%601> terminado que contiene el valor proporcionado como su propiedad <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="68df7-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="68df7-105">Este método es útil cuando se realiza una operación asincrónica que devuelve un objeto <xref:System.Threading.Tasks.Task%601> y el resultado de ese objeto <xref:System.Threading.Tasks.Task%601> ya se ha calculado.</span><span class="sxs-lookup"><span data-stu-id="68df7-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68df7-106">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="68df7-106">Example</span></span>  

 <span data-ttu-id="68df7-107">En el ejemplo siguiente se descargan cadenas desde la Web.</span><span class="sxs-lookup"><span data-stu-id="68df7-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="68df7-108">Define el método `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="68df7-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="68df7-109">Este método descarga cadenas de la Web de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="68df7-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="68df7-110">En este ejemplo también se usa un objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> para almacenar en caché los resultados de las operaciones anteriores.</span><span class="sxs-lookup"><span data-stu-id="68df7-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="68df7-111">Si la dirección de entrada se mantiene en esta memoria caché, `DownloadStringAsync` utiliza el método <xref:System.Threading.Tasks.Task.FromResult%2A> para generar un objeto <xref:System.Threading.Tasks.Task%601> que incluye el contenido en esa dirección.</span><span class="sxs-lookup"><span data-stu-id="68df7-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="68df7-112">En caso contrario, `DownloadStringAsync` descarga el archivo desde la Web y agrega el resultado a la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="68df7-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="68df7-113">Este ejemplo calcula el tiempo necesario para descargar varias cadenas dos veces.</span><span class="sxs-lookup"><span data-stu-id="68df7-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="68df7-114">El segundo conjunto de operaciones de descarga debe tardar menos tiempo que el primer conjunto porque los resultados se mantienen en la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="68df7-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="68df7-115">El método <xref:System.Threading.Tasks.Task.FromResult%2A> habilita el método `DownloadStringAsync` para crear objetos <xref:System.Threading.Tasks.Task%601> que contienen estos resultados precalculados.</span><span class="sxs-lookup"><span data-stu-id="68df7-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68df7-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="68df7-116">See also</span></span>

- [<span data-ttu-id="68df7-117">Programación asincrónica basada en tareas</span><span class="sxs-lookup"><span data-stu-id="68df7-117">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
