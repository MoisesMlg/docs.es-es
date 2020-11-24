---
title: ICorDebugThread2::InterceptCurrentException (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 96e3a90bcb7700915bfd3618d7bae40c0ff64a75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678602"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="56d49-102">ICorDebugThread2::InterceptCurrentException (Método)</span><span class="sxs-lookup"><span data-stu-id="56d49-102">ICorDebugThread2::InterceptCurrentException Method</span></span>

<span data-ttu-id="56d49-103">Permite a un depurador interceptar la excepción actual en este subproceso.</span><span class="sxs-lookup"><span data-stu-id="56d49-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d49-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="56d49-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56d49-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="56d49-105">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="56d49-106">de Puntero a un ICorDebugFrame que representa el marco de pila activo.</span><span class="sxs-lookup"><span data-stu-id="56d49-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56d49-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="56d49-107">Remarks</span></span>  

 <span data-ttu-id="56d49-108">`InterceptCurrentException`Se puede llamar al método entre una devolución de llamada de excepción ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) o [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) y la llamada asociada a [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="56d49-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d49-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56d49-109">Requirements</span></span>  

 <span data-ttu-id="56d49-110">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56d49-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56d49-111">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56d49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56d49-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56d49-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56d49-113">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
