---
title: IMetaDataImport::EnumUserStrings (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: c7dcc740dcf9b228713693a57dc8ef96d215ebad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716569"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="777c5-102">IMetaDataImport::EnumUserStrings (Método)</span><span class="sxs-lookup"><span data-stu-id="777c5-102">IMetaDataImport::EnumUserStrings Method</span></span>

<span data-ttu-id="777c5-103">Enumera los tokens de String que representan las cadenas codificadas de forma rígida en el ámbito de metadatos actual.</span><span class="sxs-lookup"><span data-stu-id="777c5-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777c5-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="777c5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="777c5-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="777c5-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="777c5-106">[in, out] Puntero al enumerador.</span><span class="sxs-lookup"><span data-stu-id="777c5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="777c5-107">Debe ser NULL para la primera llamada de este método.</span><span class="sxs-lookup"><span data-stu-id="777c5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="777c5-108">enuncia Matriz que se usa para almacenar los tokens de cadena.</span><span class="sxs-lookup"><span data-stu-id="777c5-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="777c5-109">[in] Tamaño máximo de la matriz `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="777c5-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="777c5-110">enuncia El número de tokens de cadena devueltos en `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="777c5-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="777c5-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="777c5-111">Return Value</span></span>  
  
|<span data-ttu-id="777c5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="777c5-112">HRESULT</span></span>|<span data-ttu-id="777c5-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="777c5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="777c5-114">`EnumUserStrings` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="777c5-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="777c5-115">No hay tokens que enumerar.</span><span class="sxs-lookup"><span data-stu-id="777c5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="777c5-116">En ese caso, `pcStrings` es cero.</span><span class="sxs-lookup"><span data-stu-id="777c5-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="777c5-117">Comentarios</span><span class="sxs-lookup"><span data-stu-id="777c5-117">Remarks</span></span>  

 <span data-ttu-id="777c5-118">Los tokens de cadena se crean mediante el método [IMetaDataEmit::D efineuserstring](imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="777c5-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="777c5-119">Este método está diseñado para que lo use un explorador de metadatos en lugar de un compilador.</span><span class="sxs-lookup"><span data-stu-id="777c5-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777c5-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="777c5-120">Requirements</span></span>  

 <span data-ttu-id="777c5-121">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="777c5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777c5-122">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="777c5-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="777c5-123">**Biblioteca:** Se incluye como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="777c5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="777c5-124">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="777c5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777c5-125">Consulte también</span><span class="sxs-lookup"><span data-stu-id="777c5-125">See also</span></span>

- [<span data-ttu-id="777c5-126">IMetaDataImport (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="777c5-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="777c5-127">IMetaDataImport2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="777c5-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
