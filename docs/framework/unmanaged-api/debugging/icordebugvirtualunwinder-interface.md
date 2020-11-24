---
title: Interfaz de ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 67f2234d37165e421874815bdc2ef34f8f50749a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679382"
---
# <a name="icordebugvirtualunwinder-interface"></a>Interfaz de ICorDebugVirtualUnwinder

Proporciona métodos que ayudan al desenredo de la pila.  
  
## <a name="methods"></a>Métodos  
  
|Método|Nombre|  
|------------|----------|  
|[Método GetContext](icordebugvirtualunwinder-getcontext-method.md)|Obtiene el contexto actual de este responsable del desenredado.|  
|[Next (Método)](icordebugvirtualunwinder-next-method.md)|Avanza hasta el contexto del llamador.|  
  
## <a name="remarks"></a>Comentarios  

 Los miembros de la interfaz `ICorDebugVirtualUnwinder` se implementan mediante el depurador para ayudar al desenredo de pila.  
  
> [!NOTE]
> Esta interfaz solo está disponible con .NET Native. Si implementa esta interfaz para escenarios de ICorDebug fuera de .NET Native, Common Language Runtime ignorará esta interfaz.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Interfaces para depuración](debugging-interfaces.md)
- [Depuración](index.md)
