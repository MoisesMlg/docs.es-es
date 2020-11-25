---
title: ICorDebugHandleValue::GetHandleType (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.GetHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type:
- apiref
ms.openlocfilehash: 72ef9a0fe4cd08ce67594600375953c249243d4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734158"
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="0ffba-102">ICorDebugHandleValue::GetHandleType (Método)</span><span class="sxs-lookup"><span data-stu-id="0ffba-102">ICorDebugHandleValue::GetHandleType Method</span></span>

<span data-ttu-id="0ffba-103">Obtiene un valor que indica el tipo de identificador al que hace referencia este objeto ICorDebugHandleValue.</span><span class="sxs-lookup"><span data-stu-id="0ffba-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ffba-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0ffba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ffba-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0ffba-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="0ffba-106">enuncia Un puntero a un valor de la enumeración CorDebugHandleType (que indica el tipo de este identificador.</span><span class="sxs-lookup"><span data-stu-id="0ffba-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ffba-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0ffba-107">Requirements</span></span>  

 <span data-ttu-id="0ffba-108">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ffba-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ffba-109">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ffba-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ffba-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ffba-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ffba-111">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ffba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
