---
title: Interfaz ICorDebugStepper
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: 8b5bbb65034e5b715532397c9ecc650da9aee912
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718298"
---
# <a name="icordebugstepper-interface"></a>Interfaz ICorDebugStepper

Representa un paso en la ejecución del código realizado por un depurador, actúa como identificador entre la emisión y la finalización de un comando, y proporciona un modo de cancelar un paso.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método Deactivate](icordebugstepper-deactivate-method.md)|Hace que se `ICorDebugStepper` cancele el último comando de paso que se ha recibido.|  
|[IsActive (Método)](icordebugstepper-isactive-method.md)|Obtiene un valor que indica si este `ICorDebugStepper` está ejecutando actualmente un paso.|  
|[Método SetInterceptMask](icordebugstepper-setinterceptmask-method.md)|Establece un valor Cordebugintercept (que especifica los tipos de código a los que se van a recorrer.|  
|[Método SetRangeIL](icordebugstepper-setrangeil-method.md)|Establece un valor que indica si las llamadas a [ICorDebugStepper:: steprange (](icordebugstepper-steprange-method.md) pasan valores de argumento en relación con el código nativo o con el código del lenguaje intermedio de Microsoft (MSIL) del método que se va a recorrer.|  
|[Método SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)|Establece un valor de Cordebugunmappedstop (que especifica el tipo de código no asignado en el que se detendrá la ejecución.|  
|[Método Step](icordebugstepper-step-method.md)|Hace que esto pase `ICorDebugStepper` de un solo paso a través de su subproceso contenedor y, opcionalmente, para continuar con la ejecución paso a paso de las funciones a las que se llama en el subproceso.|  
|[Método StepOut](icordebugstepper-stepout-method.md)|Hace que esto `ICorDebugStepper` se lleve a cabo de un solo paso a través de su subproceso contenedor y que se complete cuando el fotograma actual devuelva el control al marco que realiza la llamada.|  
|[Método StepRange](icordebugstepper-steprange-method.md)|Hace que esto `ICorDebugStepper` pase de un solo paso a través de su subproceso contenedor y que devuelva cuando llegue al código más allá del último de los intervalos especificados.|  
  
## <a name="remarks"></a>Comentarios  

 La `ICorDebugStepper` interfaz sirve para los siguientes fines:  
  
- Actúa como un identificador entre un comando Step que se emite y la finalización de ese comando.  
  
- Proporciona una interfaz central para encapsular todo el paso que se puede realizar.  
  
- Proporciona una manera de cancelar prematuramente una operación de ejecución paso a paso.  
  
 Puede haber más de un stepper por subproceso. Por ejemplo, se puede tener acceso a un punto de interrupción mientras se realiza la ejecución paso a paso por procedimientos y el usuario puede iniciar una nueva operación de ejecución paso a paso dentro de esa función. Depende del depurador determinar cómo tratar esta situación. Es posible que el depurador desee cancelar la operación de ejecución paso a paso original o anidar las dos operaciones. La `ICorDebugStepper` interfaz admite ambas opciones.  
  
 Un stepper se puede migrar entre subprocesos si el Common Language Runtime (CLR) realiza una llamada entre subprocesos y con referencias calculadas.  
  
> [!NOTE]
> Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Interfaces para depuración](debugging-interfaces.md)
