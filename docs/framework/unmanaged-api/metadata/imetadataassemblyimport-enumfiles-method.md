---
title: IMetaDataAssemblyImport::EnumFiles (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: f9af770f3bdca98f6b3d06d8b0fe6c92745f73e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731634"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="92627-102">IMetaDataAssemblyImport::EnumFiles (Método)</span><span class="sxs-lookup"><span data-stu-id="92627-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="92627-103">Enumera los archivos a los que se hace referencia en el manifiesto del ensamblado actual.</span><span class="sxs-lookup"><span data-stu-id="92627-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92627-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="92627-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92627-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="92627-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="92627-106">[in, out] Puntero al enumerador.</span><span class="sxs-lookup"><span data-stu-id="92627-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="92627-107">Debe ser un valor null para la primera llamada de este método.</span><span class="sxs-lookup"><span data-stu-id="92627-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="92627-108">enuncia Matriz utilizada para almacenar los `mdFile` tokens de metadatos.</span><span class="sxs-lookup"><span data-stu-id="92627-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="92627-109">de Número máximo de `mdFile` tokens que se pueden colocar en `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="92627-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="92627-110">enuncia Número de `mdFile` tokens realmente colocados en `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="92627-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92627-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="92627-111">Return Value</span></span>  
  
|<span data-ttu-id="92627-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92627-112">HRESULT</span></span>|<span data-ttu-id="92627-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="92627-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="92627-114">`EnumFiles` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="92627-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="92627-115">No hay tokens que enumerar.</span><span class="sxs-lookup"><span data-stu-id="92627-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="92627-116">En este caso, `pcTokens` se establece en cero.</span><span class="sxs-lookup"><span data-stu-id="92627-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92627-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92627-117">Requirements</span></span>  

 <span data-ttu-id="92627-118">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92627-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92627-119">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="92627-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92627-120">**Biblioteca:** Se usa como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92627-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92627-121">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92627-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92627-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="92627-122">See also</span></span>

- [<span data-ttu-id="92627-123">IMetaDataAssemblyImport (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="92627-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
