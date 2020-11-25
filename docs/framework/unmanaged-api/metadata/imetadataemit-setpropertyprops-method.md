---
title: IMetaDataEmit::SetPropertyProps (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: 553a82475f241fac3a56c1fb009e3ed56b2c14f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704258"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="65cec-102">IMetaDataEmit::SetPropertyProps (Método)</span><span class="sxs-lookup"><span data-stu-id="65cec-102">IMetaDataEmit::SetPropertyProps Method</span></span>

<span data-ttu-id="65cec-103">Establece las características almacenadas en los metadatos de una propiedad definida por una llamada anterior al [método DefineProperty](imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="65cec-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65cec-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="65cec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65cec-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="65cec-105">Parameters</span></span>  

 `pr`  
 <span data-ttu-id="65cec-106">de Token para la propiedad que se va a cambiar.</span><span class="sxs-lookup"><span data-stu-id="65cec-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="65cec-107">de Marcas de propiedad.</span><span class="sxs-lookup"><span data-stu-id="65cec-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="65cec-108">de Tipo del valor predeterminado de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="65cec-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="65cec-109">de Valor predeterminado de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="65cec-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="65cec-110">de Recuento de caracteres (Unicode) en `pValue` .</span><span class="sxs-lookup"><span data-stu-id="65cec-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="65cec-111">de El método que establece el valor de propiedad.</span><span class="sxs-lookup"><span data-stu-id="65cec-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="65cec-112">de Método que obtiene el valor de propiedad.</span><span class="sxs-lookup"><span data-stu-id="65cec-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="65cec-113">de Matriz de otros métodos asociados a la propiedad.</span><span class="sxs-lookup"><span data-stu-id="65cec-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="65cec-114">Termine esta matriz con un `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="65cec-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65cec-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65cec-115">Requirements</span></span>  

 <span data-ttu-id="65cec-116">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65cec-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65cec-117">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="65cec-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65cec-118">**Biblioteca:** Se usa como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65cec-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65cec-119">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65cec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65cec-120">Consulte también</span><span class="sxs-lookup"><span data-stu-id="65cec-120">See also</span></span>

- [<span data-ttu-id="65cec-121">IMetaDataEmit (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="65cec-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="65cec-122">IMetaDataEmit2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="65cec-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
