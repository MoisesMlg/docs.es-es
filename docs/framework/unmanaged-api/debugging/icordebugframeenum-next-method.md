---
title: ICorDebugFrameEnum::Next (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 76b96dfd9d22c7e770671dcc01cb421430df729f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728191"
---
# <a name="icordebugframeenumnext-method"></a>ICorDebugFrameEnum::Next (Método)

Obtiene el número especificado de instancias de ICorDebugFrame, comenzando en la posición actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `celt`  
 de El número de `ICorDebugFrame` instancias que se van a recuperar.  
  
 `frames`  
 enuncia Matriz de punteros, cada uno de los cuales señala a un `ICorDebugFrame` objeto.  
  
 `pceltFetched`  
 enuncia Puntero al número de `ICorDebugFrame` instancias devueltas realmente. Este valor puede ser null si `celt` es uno.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
