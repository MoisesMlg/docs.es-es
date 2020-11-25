---
title: IMetaDataImport::GetParamForMethodIndex (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: d4d3ba5713398876b55c072f0cda7eb5d599c4d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729294"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="776af-102">IMetaDataImport::GetParamForMethodIndex (Método)</span><span class="sxs-lookup"><span data-stu-id="776af-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="776af-103">Obtiene el token que representa un parámetro especificado del método representado por el token de MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="776af-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="776af-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="776af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="776af-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="776af-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="776af-106">de Token que representa el método para el que se va a devolver el token de parámetro.</span><span class="sxs-lookup"><span data-stu-id="776af-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="776af-107">de Posición ordinal en la lista de parámetros donde se produce el parámetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="776af-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="776af-108">Los parámetros se numeran a partir de uno, con el valor devuelto del método en la posición cero.</span><span class="sxs-lookup"><span data-stu-id="776af-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="776af-109">enuncia Un puntero a un token ParamDef que representa el parámetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="776af-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="776af-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="776af-110">Requirements</span></span>  

 <span data-ttu-id="776af-111">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="776af-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="776af-112">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="776af-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="776af-113">**Biblioteca:** Se incluye como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="776af-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="776af-114">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="776af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776af-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="776af-115">See also</span></span>

- [<span data-ttu-id="776af-116">IMetaDataImport (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="776af-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="776af-117">IMetaDataImport2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="776af-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
