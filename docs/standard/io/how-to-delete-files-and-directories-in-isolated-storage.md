---
title: 'Cómo: Eliminar archivos y directorios en almacenamiento aislado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: ea1d7a460a8867f069aa4b4d915e03d6948e23b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688515"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="c500c-102">Cómo: Eliminar archivos y directorios en almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="c500c-102">How to: Delete Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="c500c-103">Puede eliminar directorios y archivos en un archivo de almacenamiento aislado.</span><span class="sxs-lookup"><span data-stu-id="c500c-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="c500c-104">Dentro de un almacén, los nombres de archivos y directorios dependen del sistema operativo y se especifican con respecto a la raíz del sistema de archivos virtual.</span><span class="sxs-lookup"><span data-stu-id="c500c-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="c500c-105">No distinguen mayúsculas de minúsculas en sistemas operativos Windows.</span><span class="sxs-lookup"><span data-stu-id="c500c-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="c500c-106">La clase <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> proporciona dos métodos para eliminar directorios y archivos: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> y <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="c500c-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="c500c-107">Se genera una excepción <xref:System.IO.IsolatedStorage.IsolatedStorageException> si trata de eliminar un archivo o directorio que no existe.</span><span class="sxs-lookup"><span data-stu-id="c500c-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="c500c-108">Si incluye un carácter comodín en el nombre, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> produce una excepción <xref:System.IO.IsolatedStorage.IsolatedStorageException> y <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> produce una excepción <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c500c-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="c500c-109">El método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> produce un error si el directorio contiene archivos o subdirectorios.</span><span class="sxs-lookup"><span data-stu-id="c500c-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="c500c-110">Puede usar los métodos <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> y <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> para recuperar los archivos y directorios existentes.</span><span class="sxs-lookup"><span data-stu-id="c500c-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="c500c-111">Para obtener información sobre cómo buscar en el sistema de archivos virtual de un almacén, vea [Cómo: Buscar archivos y directorios existentes en almacenamiento aislado](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="c500c-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c500c-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c500c-112">Example</span></span>  

 <span data-ttu-id="c500c-113">En el ejemplo de código siguiente se crean y luego se eliminan varios directorios y archivos.</span><span class="sxs-lookup"><span data-stu-id="c500c-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c500c-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="c500c-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="c500c-115">Almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="c500c-115">Isolated Storage</span></span>](isolated-storage.md)
