---
title: ICorDebugThread4::GetBlockingObjects (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: eb8692aebe7b702b5778b3f13e496d81dcd45784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678552"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects (Método)

Proporciona una enumeración ordenada de las estructuras [CorDebugBlockingObject](cordebugblockingobject-structure.md) que proporcionan información de bloqueo de subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a>Parámetros  

 `ppBlockingObjectEnum`  
 enuncia Puntero a una enumeración ordenada de estructuras [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
## <a name="remarks"></a>Comentarios  

 El primer elemento de la enumeración devuelta corresponde a la primera estructura que está bloqueando el subproceso. El segundo elemento corresponde a un elemento de bloqueo que se encuentra mientras se ejecuta una llamada a procedimiento asincrónico (APC) cuando se bloquea en el primero, y así sucesivamente.  
  
 La enumeración solo es válida para la duración del estado sincronizado actual.  
  
 Se debe llamar a este método mientras el código depurado esté en un estado sincronizado.  
  
 Si `ppBlockingObjectEnum` no es un puntero válido, el resultado es indefinido.  
  
 Si un subproceso está bloqueado y no se puede determinar el error, el método devuelve un valor HRESULT que indica un error. de lo contrario, Devuelve S_OK.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [ICorDebugThread4 (Interfaz)](icordebugthread4-interface.md)
- [Interfaces para depuración](debugging-interfaces.md)
- [Depuración](index.md)
