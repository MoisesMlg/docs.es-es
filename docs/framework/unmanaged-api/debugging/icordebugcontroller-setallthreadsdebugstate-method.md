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
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState (Método)

Establece el estado de depuración de todos los subprocesos administrados en el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `state`  
 de Un valor de la enumeración "CorDebugThreadState (" que especifica el estado del subproceso para la depuración.  
  
 `pExceptThisThread`  
 de Un puntero a un objeto "ICorDebugThread" que representa un subproceso que se va a excluir de la configuración del estado de depuración. Si este valor es null, no hay ningún subproceso exento.  
  
## <a name="remarks"></a>Comentarios  

 El `SetAllThreadsDebugState` método puede afectar a los subprocesos que no son visibles a través del [método enumeratethreads (](icordebugcontroller-enumeratethreads-method.md), por lo que los subprocesos que se suspendieron con el `SetAllThreadsDebugState` método deberán reanudarse con el `SetAllThreadsDebugState` método.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también
