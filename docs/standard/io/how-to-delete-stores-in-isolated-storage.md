---
title: 'Cómo: Eliminar almacenes de almacenamiento aislado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
ms.openlocfilehash: 47421b4ab223a0c68a7449ba58fd010ef6f7ccab
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830784"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="ae708-102">Cómo: Eliminar almacenes de almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="ae708-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="ae708-103">La clase <xref:System.IO.IsolatedStorage.IsolatedStorageFile> proporciona dos métodos para eliminar archivos de almacenamiento aislado:</span><span class="sxs-lookup"><span data-stu-id="ae708-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="ae708-104">El método de instancia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> no toma ningún argumento y elimina el almacén que lo llama.</span><span class="sxs-lookup"><span data-stu-id="ae708-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="ae708-105">No se requieren permisos para realizar esta operación.</span><span class="sxs-lookup"><span data-stu-id="ae708-105">No permissions are required for this operation.</span></span> <span data-ttu-id="ae708-106">Cualquier código que pueda acceder al almacén puede eliminar alguno o todos los datos que contenga.</span><span class="sxs-lookup"><span data-stu-id="ae708-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="ae708-107">El método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> toma el valor de enumeración <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> y elimina todos los almacenes del usuario que está ejecutando el código.</span><span class="sxs-lookup"><span data-stu-id="ae708-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="ae708-108">Esta operación requiere permiso <xref:System.Security.Permissions.IsolatedStorageFilePermission> para el valor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .</span><span class="sxs-lookup"><span data-stu-id="ae708-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae708-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ae708-109">Example</span></span>  
 <span data-ttu-id="ae708-110">En el ejemplo de código siguiente se muestra el uso de los métodos <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> estático y de instancia.</span><span class="sxs-lookup"><span data-stu-id="ae708-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="ae708-111">La clase obtiene dos almacenes; uno está aislado de usuario y ensamblado, y el otro está aislado de usuario, dominio y ensamblado.</span><span class="sxs-lookup"><span data-stu-id="ae708-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="ae708-112">El almacén de usuario, dominio y ensamblado se elimina con una llamada al método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> del archivo de almacenamiento aislado  `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="ae708-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="ae708-113">A continuación, se eliminan todos los demás almacenes del usuario con una llamada al método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="ae708-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ae708-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="ae708-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="ae708-115">Almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="ae708-115">Isolated Storage</span></span>](isolated-storage.md)
