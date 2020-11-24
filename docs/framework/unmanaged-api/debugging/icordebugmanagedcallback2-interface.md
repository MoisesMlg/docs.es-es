---
title: ICorDebugManagedCallback2 (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 937a2fb322eb63461d90e215635e1b10ab6afd09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689789"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 (Interfaz)

Proporciona métodos para admitir el control de excepciones del depurador y asistentes para depuración administrada (MDA). `ICorDebugManagedCallback2` es una extensión lógica de la interfaz [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md)|Notifica al depurador que ha cambiado el conjunto de tareas asociado a la conexión especificada.|  
|[Método CreateConnection](icordebugmanagedcallback2-createconnection-method.md)|Notifica al depurador que se ha creado una nueva conexión.|  
|[Método DestroyConnection](icordebugmanagedcallback2-destroyconnection-method.md)|Notifica al depurador que se ha terminado la conexión especificada.|  
|[Método Exception](icordebugmanagedcallback2-exception-method.md)|Notifica al depurador que se ha iniciado una búsqueda de un controlador de excepciones.|  
|[Método ExceptionUnwind](icordebugmanagedcallback2-exceptionunwind-method.md)|Proporciona una notificación de estado durante el proceso de desenredo de excepciones.|  
|[Método FunctionRemapComplete](icordebugmanagedcallback2-functionremapcomplete-method.md)|Notifica al depurador que la ejecución del código ha cambiado a una nueva versión de una función editada.|  
|[Método FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md)|Notifica al depurador que la ejecución del código ha alcanzado un punto de secuencia en una versión anterior de una función editada.|  
|[Método MDANotification](icordebugmanagedcallback2-mdanotification-method.md)|Proporciona una notificación de que la ejecución del código ha encontrado un mensaje del Asistente para la depuración administrada (MDA).|  
  
## <a name="remarks"></a>Comentarios  

 La `ICorDebugManagedCallback2` interfaz extiende la `ICorDebugManagedCallback` interfaz para controlar los nuevos eventos de depuración introducidos en la .NET Framework versión 2,0.  
  
 Un depurador debe implementar `ICorDebugManagedCallback2` si está depurando .NET Framework aplicaciones 2,0. Una instancia de `ICorDebugManagedCallback` o `ICorDebugManagedCallback2` se pasa como el objeto de devolución de llamada a [ICorDebug:: SetManagedHandler (](icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
> Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Diagnóstico de errores con asistentes de depuraciones administradas](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interfaces para depuración](debugging-interfaces.md)
- [ICorDebugManagedCallback (Interfaz)](icordebugmanagedcallback-interface.md)
