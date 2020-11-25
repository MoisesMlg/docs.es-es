---
title: IMetaDataEmit2::SaveDeltaToStream (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: dad916d74c4e754d8fd3ffb62024e49617f5de05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702027"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="29d48-102">IMetaDataEmit2::SaveDeltaToStream (Método)</span><span class="sxs-lookup"><span data-stu-id="29d48-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>

<span data-ttu-id="29d48-103">Guarda los cambios de la sesión de edición y continuación actual en la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="29d48-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d48-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="29d48-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29d48-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="29d48-105">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="29d48-106">de Puntero de interfaz a la secuencia de escritura en la que se van a guardar los cambios.</span><span class="sxs-lookup"><span data-stu-id="29d48-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="29d48-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="29d48-107">[in] Reserved.</span></span> <span data-ttu-id="29d48-108">Este valor debe ser cero.</span><span class="sxs-lookup"><span data-stu-id="29d48-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d48-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29d48-109">Requirements</span></span>  

 <span data-ttu-id="29d48-110">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29d48-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d48-111">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="29d48-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29d48-112">**Biblioteca:** Se usa como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29d48-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29d48-113">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d48-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d48-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="29d48-114">See also</span></span>

- [<span data-ttu-id="29d48-115">IMetaDataEmit2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="29d48-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="29d48-116">IMetaDataEmit (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="29d48-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
