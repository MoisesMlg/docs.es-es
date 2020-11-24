---
title: Procedimiento para copiar directorios
description: Vea cómo usar clases de E/S que copian de forma sincrónica el contenido de un directorio en otra ubicación.
ms.date: 12/27/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: b81723b9ed7067826692e8383bf64058d4295f0c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830836"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="d2f0b-103">Procedimiento para copiar directorios</span><span class="sxs-lookup"><span data-stu-id="d2f0b-103">How to: Copy directories</span></span>

<span data-ttu-id="d2f0b-104">En este artículo se muestra cómo usar las clases de E/S para copiar de forma sincrónica el contenido de un directorio en otra ubicación.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-104">This article demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="d2f0b-105">Para obtener un ejemplo de la copia asincrónica de archivos, vea [E/S de archivos asincrónica](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="d2f0b-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="d2f0b-106">En este ejemplo, para copiar los subdirectorios se establece el elemento `copySubDirs` del método `DirectoryCopy` en `true`.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="d2f0b-107">Para copiar de forma recursiva los subdirectorios, el método `DirectoryCopy` se llama a si mismo en cada subdirectorio hasta que no haya ninguno más para copiar.</span><span class="sxs-lookup"><span data-stu-id="d2f0b-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2f0b-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d2f0b-108">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="d2f0b-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="d2f0b-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="d2f0b-110">E/S de archivos y secuencias</span><span class="sxs-lookup"><span data-stu-id="d2f0b-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="d2f0b-111">Tareas de E/S comunes</span><span class="sxs-lookup"><span data-stu-id="d2f0b-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="d2f0b-112">E/S de archivos asincrónica</span><span class="sxs-lookup"><span data-stu-id="d2f0b-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
