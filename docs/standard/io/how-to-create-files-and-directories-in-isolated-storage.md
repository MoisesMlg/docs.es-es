---
title: Procedimiento para crear archivos y directorios en almacenamiento aislado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: 1f6e8e1a048fcf7f8fd278eaac4988fa0e35791d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684998"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="dc7fe-102">Procedimiento para crear archivos y directorios en almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="dc7fe-102">How to: Create Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="dc7fe-103">Después de haber obtenido un almacén aislado, puede crear directorios y archivos para almacenar los datos.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-103">After you've obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="dc7fe-104">Dentro de un almacén, los nombres de archivos y directorios se especifican con respecto a la raíz del sistema de archivos virtual.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="dc7fe-105">Para crear un directorio, use el método de instancia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="dc7fe-106">Si especifica un subdirectorio de un directorio que no existe, se crearán ambos directorios.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-106">If you specify a subdirectory of a directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="dc7fe-107">Si especifica un directorio que ya existe, el método realiza la devolución sin crear un directorio y no se genera ninguna excepción.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="dc7fe-108">Sin embargo, si especifica un nombre de directorio que contiene caracteres no válidos, se produce la excepción <xref:System.IO.IsolatedStorage.IsolatedStorageException>.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="dc7fe-109">Para crear un archivo, use el método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dc7fe-110">En el sistema operativo Windows, los nombres de archivos y directorios del almacenamiento aislado distinguen mayúsculas y minúsculas.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="dc7fe-111">Es decir, si crea un archivo denominado `ThisFile.txt` y luego crea otro archivo llamado `THISFILE.TXT`, solo se crea un archivo.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="dc7fe-112">El nombre de archivo mantiene las mayúsculas y minúsculas originales para la presentación.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-112">The file name keeps its original casing for display purposes.</span></span>  

 <span data-ttu-id="dc7fe-113">La creación de un archivo de almacenamiento aislado producirá una excepción del tipo <xref:System.IO.IsolatedStorage.IsolatedStorageException> si la ruta de acceso contiene un directorio que no existe.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-113">Isolated storage file creation will throw an <xref:System.IO.IsolatedStorage.IsolatedStorageException> if the path contains a directory that does not exist.</span></span>
  
## <a name="example"></a><span data-ttu-id="dc7fe-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="dc7fe-114">Example</span></span>  

 <span data-ttu-id="dc7fe-115">En el ejemplo de código siguiente se muestra cómo crear archivos y directorios en un almacén aislado.</span><span class="sxs-lookup"><span data-stu-id="dc7fe-115">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dc7fe-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="dc7fe-116">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="dc7fe-117">Almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="dc7fe-117">Isolated Storage</span></span>](isolated-storage.md)
