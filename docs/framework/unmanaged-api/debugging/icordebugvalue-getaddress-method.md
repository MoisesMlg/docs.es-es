---
title: ICorDebugValue::GetAddress (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728373"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress (Método)

Obtiene la dirección de este objeto "ICorDebugValue", que está en proceso de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `pAddress`  
 enuncia Puntero a un `CORDB_ADDRESS` objeto que especifica la dirección de este objeto de valor.  
  
## <a name="remarks"></a>Comentarios  

 Si el valor no está disponible, se devuelve 0 (cero). Esto puede ocurrir si el valor es, al menos, parcialmente en registros o almacenados en un identificador de recolector de elementos no utilizados ( `GCHandle` ).  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también
