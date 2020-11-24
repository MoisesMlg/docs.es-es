---
title: ICorDebugController::SetAllThreadsDebugState (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: d8375948be5820aaf6e879b82bcfde6471cccf3f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679902"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="0d125-102">ICorDebugController::SetAllThreadsDebugState (Método)</span><span class="sxs-lookup"><span data-stu-id="0d125-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>

<span data-ttu-id="0d125-103">Establece el estado de depuración de todos los subprocesos administrados en el proceso.</span><span class="sxs-lookup"><span data-stu-id="0d125-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d125-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0d125-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d125-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d125-105">Parameters</span></span>  

 `state`  
 <span data-ttu-id="0d125-106">de Un valor de la enumeración "CorDebugThreadState (" que especifica el estado del subproceso para la depuración.</span><span class="sxs-lookup"><span data-stu-id="0d125-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="0d125-107">de Un puntero a un objeto "ICorDebugThread" que representa un subproceso que se va a excluir de la configuración del estado de depuración.</span><span class="sxs-lookup"><span data-stu-id="0d125-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="0d125-108">Si este valor es null, no hay ningún subproceso exento.</span><span class="sxs-lookup"><span data-stu-id="0d125-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d125-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="0d125-109">Remarks</span></span>  

 <span data-ttu-id="0d125-110">El `SetAllThreadsDebugState` método puede afectar a los subprocesos que no son visibles a través del [método enumeratethreads (](icordebugcontroller-enumeratethreads-method.md), por lo que los subprocesos que se suspendieron con el `SetAllThreadsDebugState` método deberán reanudarse con el `SetAllThreadsDebugState` método.</span><span class="sxs-lookup"><span data-stu-id="0d125-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d125-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d125-111">Requirements</span></span>  

 <span data-ttu-id="0d125-112">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d125-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d125-113">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d125-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d125-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d125-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d125-115">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d125-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d125-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0d125-116">See also</span></span>
