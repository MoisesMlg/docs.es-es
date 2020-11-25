---
title: ICorDebugValue::GetAddress (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728373"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="641ae-102">ICorDebugValue::GetAddress (Método)</span><span class="sxs-lookup"><span data-stu-id="641ae-102">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="641ae-103">Obtiene la dirección de este objeto "ICorDebugValue", que está en proceso de depuración.</span><span class="sxs-lookup"><span data-stu-id="641ae-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641ae-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="641ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="641ae-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="641ae-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="641ae-106">enuncia Puntero a un `CORDB_ADDRESS` objeto que especifica la dirección de este objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="641ae-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="641ae-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="641ae-107">Remarks</span></span>  

 <span data-ttu-id="641ae-108">Si el valor no está disponible, se devuelve 0 (cero).</span><span class="sxs-lookup"><span data-stu-id="641ae-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="641ae-109">Esto puede ocurrir si el valor es, al menos, parcialmente en registros o almacenados en un identificador de recolector de elementos no utilizados ( `GCHandle` ).</span><span class="sxs-lookup"><span data-stu-id="641ae-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="641ae-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="641ae-110">Requirements</span></span>  

 <span data-ttu-id="641ae-111">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="641ae-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="641ae-112">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="641ae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="641ae-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="641ae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="641ae-114">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="641ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="641ae-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="641ae-115">See also</span></span>
