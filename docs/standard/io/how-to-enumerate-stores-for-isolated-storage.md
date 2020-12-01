---
title: 'Cómo: Enumerar los almacenes de almacenamiento aislado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: f01ca70b3fd5b778274ef5bd7fcb63e26d9916a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734652"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="f99bb-102">Cómo: Enumerar los almacenes de almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="f99bb-102">How to: Enumerate Stores for Isolated Storage</span></span>

<span data-ttu-id="f99bb-103">Puede enumerar todos los almacenes aislados para el usuario actual con el uso del método estático <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f99bb-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="f99bb-104">Este método adopta un valor <xref:System.IO.IsolatedStorage.IsolatedStorageScope> y devuelve un enumerador <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.</span><span class="sxs-lookup"><span data-stu-id="f99bb-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="f99bb-105">Para enumerar los almacenes, debe tener el permiso <xref:System.Security.Permissions.IsolatedStorageFilePermission> que especifica el valor <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="f99bb-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="f99bb-106">Si se llama al método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> con el valor <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, devuelve una matriz de objetos <xref:System.IO.IsolatedStorage.IsolatedStorageFile> definidos para el usuario actual.</span><span class="sxs-lookup"><span data-stu-id="f99bb-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f99bb-107">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f99bb-107">Example</span></span>  

 <span data-ttu-id="f99bb-108">En el ejemplo de código siguiente se obtiene un almacén aislado por usuario y ensamblado, se crean unos cuantos archivos y se recuperan los archivos mediante el método <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="f99bb-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f99bb-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="f99bb-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="f99bb-110">Almacenamiento aislado</span><span class="sxs-lookup"><span data-stu-id="f99bb-110">Isolated Storage</span></span>](isolated-storage.md)
