---
title: ICorDebugILCode2 (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: b9289b5afc88c926ce585a4e620364cf2dc979d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703335"
---
# <a name="icordebugilcode2-interface"></a>ICorDebugILCode2 (Interfaz)

[Compatible con .NET Framework 4.5.2 y versiones posteriores]  
  
 Extiende lógicamente la interfaz [ICorDebugILCode](icordebugilcode-interface.md) para proporcionar métodos que devuelven el token de la firma de variable local de una función y que asignan los desplazamientos del lenguaje intermedio INSTRUMENTADO (IL) del generador de perfiles a los desplazamientos de Il del método original.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método GetInstrumentedILMap](icordebugilcode2-getinstrumentedilmap-method.md)|Devuelve la correspondencia entre los desplazamientos del IL instrumentado del generador de perfiles y los desplazamientos del IL del método original para esta instancia.|  
|[GetLocalVarSigToken (Método)](icordebugilcode2-getlocalvarsigtoken-method.md)|Obtiene el token de metadatos de la firma de variable local para la función que esta instancia representa.|  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [ICorDebugILCode (Interfaz)](icordebugilcode-interface.md)
- [Interfaces para depuración](debugging-interfaces.md)
- [Depuración](index.md)
