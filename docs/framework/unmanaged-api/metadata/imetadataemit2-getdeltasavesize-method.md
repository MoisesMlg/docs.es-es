---
title: IMetaDataEmit2::GetDeltaSaveSize (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
ms.openlocfilehash: 36021333c1efb61e23c16782d8ad721de62c2643
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674347"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="4f6cb-102">IMetaDataEmit2::GetDeltaSaveSize (Método)</span><span class="sxs-lookup"><span data-stu-id="4f6cb-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>

<span data-ttu-id="4f6cb-103">Obtiene un valor que indica cualquier cambio en el tamaño de los metadatos que es el resultado de la sesión de edición y continuación actual.</span><span class="sxs-lookup"><span data-stu-id="4f6cb-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6cb-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4f6cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f6cb-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4f6cb-105">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="4f6cb-106">de Uno de los valores de [CorSaveSize (](corsavesize-enumeration.md) , que indica el nivel de precisión que se desea.</span><span class="sxs-lookup"><span data-stu-id="4f6cb-106">[in] One of the [CorSaveSize](corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="4f6cb-107">En el .NET Framework versión 2,0, este parámetro se omite.</span><span class="sxs-lookup"><span data-stu-id="4f6cb-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="4f6cb-108">enuncia Cambio en el tamaño de los metadatos.</span><span class="sxs-lookup"><span data-stu-id="4f6cb-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f6cb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f6cb-109">Requirements</span></span>  

 <span data-ttu-id="4f6cb-110">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f6cb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f6cb-111">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f6cb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f6cb-112">**Biblioteca:** Se usa como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f6cb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f6cb-113">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f6cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f6cb-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4f6cb-114">See also</span></span>

- [<span data-ttu-id="4f6cb-115">IMetaDataEmit2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="4f6cb-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="4f6cb-116">IMetaDataEmit (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="4f6cb-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
