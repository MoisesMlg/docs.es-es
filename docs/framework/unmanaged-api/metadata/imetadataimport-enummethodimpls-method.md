---
title: IMetaDataImport::EnumMethodImpls (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: 40ab610110e96018b1c598d04b24a762ecb50717
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690524"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="ab4d2-102">IMetaDataImport::EnumMethodImpls (Método)</span><span class="sxs-lookup"><span data-stu-id="ab4d2-102">IMetaDataImport::EnumMethodImpls Method</span></span>

<span data-ttu-id="ab4d2-103">Enumera los tokens MethodBody y MethodDeclaration que representan métodos del tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab4d2-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ab4d2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab4d2-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ab4d2-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="ab4d2-106">[in, out] Puntero al enumerador.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ab4d2-107">Debe ser NULL para la primera llamada de este método.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="ab4d2-108">de Un token de TypeDef para el tipo cuyas implementaciones de método se van a enumerar.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="ab4d2-109">enuncia Matriz en la que se van a almacenar los tokens de MethodBody.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="ab4d2-110">enuncia Matriz en la que se van a almacenar los tokens MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ab4d2-111">de Tamaño máximo de las `rMethodBody` matrices y `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="ab4d2-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ab4d2-112">de Número real de métodos devueltos en `rMethodBody` y `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="ab4d2-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab4d2-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ab4d2-113">Return Value</span></span>  
  
|<span data-ttu-id="ab4d2-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab4d2-114">HRESULT</span></span>|<span data-ttu-id="ab4d2-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="ab4d2-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ab4d2-116">`EnumMethodImpls` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ab4d2-117">No hay tokens de método para enumerar.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="ab4d2-118">En ese caso, `pcTokens` es cero.</span><span class="sxs-lookup"><span data-stu-id="ab4d2-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab4d2-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab4d2-119">Requirements</span></span>  

 <span data-ttu-id="ab4d2-120">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab4d2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab4d2-121">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ab4d2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab4d2-122">**Biblioteca:** Se incluye como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab4d2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab4d2-123">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab4d2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4d2-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ab4d2-124">See also</span></span>

- [<span data-ttu-id="ab4d2-125">IMetaDataImport (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ab4d2-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ab4d2-126">IMetaDataImport2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ab4d2-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
