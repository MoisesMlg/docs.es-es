---
title: EmbedResource (Método)
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 34439b7c01dee7d7789d989b58e8944c6282b71b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676392"
---
# <a name="embedresource-method"></a><span data-ttu-id="3c859-102">EmbedResource (Método)</span><span class="sxs-lookup"><span data-stu-id="3c859-102">EmbedResource Method</span></span>

<span data-ttu-id="3c859-103">Declara un recurso incrustado.</span><span class="sxs-lookup"><span data-stu-id="3c859-103">Declares an embedded resource.</span></span> <span data-ttu-id="3c859-104">Este método no inserta realmente el recurso.</span><span class="sxs-lookup"><span data-stu-id="3c859-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c859-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3c859-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c859-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3c859-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="3c859-107">IDENTIFICADOR del ensamblado.</span><span class="sxs-lookup"><span data-stu-id="3c859-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3c859-108">Token de archivo o ID. de ensamblado del archivo que contiene el recurso.</span><span class="sxs-lookup"><span data-stu-id="3c859-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="3c859-109">Nombre del recurso.</span><span class="sxs-lookup"><span data-stu-id="3c859-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="3c859-110">Desplazamiento del recurso desde RVA.</span><span class="sxs-lookup"><span data-stu-id="3c859-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3c859-111">Marcas de accesibilidad como `mrPublic` y `mrPrivate` .</span><span class="sxs-lookup"><span data-stu-id="3c859-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="3c859-112">Estas marcas se pueden pasar al [método DefineExportedType (](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c859-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c859-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3c859-113">Return Value</span></span>  

 <span data-ttu-id="3c859-114">Devuelve S_OK si el método se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="3c859-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c859-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c859-115">Requirements</span></span>  

 <span data-ttu-id="3c859-116">Requiere ALink. h.</span><span class="sxs-lookup"><span data-stu-id="3c859-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c859-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3c859-117">See also</span></span>

- [<span data-ttu-id="3c859-118">IALink (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="3c859-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3c859-119">IALink2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="3c859-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3c859-120">API de ALink</span><span class="sxs-lookup"><span data-stu-id="3c859-120">ALink API</span></span>](index.md)
