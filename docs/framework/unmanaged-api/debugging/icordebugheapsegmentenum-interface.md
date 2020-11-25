---
title: ICorDebugHeapSegmentEnum (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: 42126d15c64175f35bba89a1ab6abacc64128012
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704635"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum (Interfaz)

Proporciona un enumerador para las regiones de memoria del montón administrado. Esta interfaz es una subclase de la interfaz ICorDebugEnum.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Next (Método)](icordebugheapsegmentenum-next-method.md)|Obtiene el número especificado de instancias de [COR_SEGMENT](cor-segment-structure.md) que contienen información sobre las regiones del montón administrado.|  
  
## <a name="remarks"></a>Comentarios  

 La `ICorDebugHeapSegmentEnum` interfaz implementa la interfaz ICorDebugEnum.  
  
 Una `ICorDebugHeapSegmentEnum` instancia se rellena con [COR_SEGMENT](cor-segment-structure.md) instancias llamando al método [ICorDebugProcess5:: enumerateheapregions (](icordebugprocess5-enumerateheapregions-method.md) . Los objetos [COR_SEGMENT](cor-segment-structure.md) de la colección se pueden enumerar llamando al método [Icordebugheapsegmentenum (:: Next](icordebugheapsegmentenum-next-method.md) .  
  
 Un `ICorDebugHeapSegmentEnum` objeto de colección enumera todas las regiones de memoria que pueden contener objetos administrados, pero no garantiza que los objetos administrados residan realmente en esas regiones. Puede incluir información sobre las regiones de memoria vacía o reservada.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Interfaces para depuración](debugging-interfaces.md)
