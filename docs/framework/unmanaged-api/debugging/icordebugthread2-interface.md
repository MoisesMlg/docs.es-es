---
title: Interfaz ICorDebugThread2
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: fd4ad536d7d3df2b8f91f206459122cf083c8b9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691141"
---
# <a name="icordebugthread2-interface"></a>Interfaz ICorDebugThread2

Actúa como una extensión lógica de la interfaz ICorDebugThread.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método GetActiveFunctions](icordebugthread2-getactivefunctions-method.md)|Obtiene una matriz de instancias de COR_ACTIVE_FUNCTION que contienen datos sobre las funciones activas de los marcos de un subproceso.|  
|[Método GetConnectionID](icordebugthread2-getconnectionid-method.md)|Obtiene un identificador de conexión para este `ICorDebugThread2` .|  
|[Método GetTaskID](icordebugthread2-gettaskid-method.md)|Obtiene un identificador de tarea para este `ICorDebugThread2` .|  
|[Método GetVolatileOSThreadID](icordebugthread2-getvolatileosthreadid-method.md)|Obtiene el identificador del subproceso del sistema operativo para este `ICorDebugThread2` .|  
|[Método InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md)|Permite a un depurador interceptar la excepción actual en un subproceso.|  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
> Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Interfaces para depuración](debugging-interfaces.md)
