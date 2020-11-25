---
title: ICorDebugProcess::IsOSSuspended (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: fffa61d8e406162251b0934a9846e5a813422798
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724590"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended (Método)

Obtiene un valor que indica si el subproceso especificado se ha suspendido como resultado de que el depurador detenga este proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parámetros  

 `threadID`  
 de IDENTIFICADOR del subproceso en cuestión.  
  
 `pbSuspended`  
 enuncia Un puntero a un valor booleano que es `true` si se ha suspendido el subproceso especificado; de lo contrario, * `pbSuspended` es `false` .  
  
## <a name="remarks"></a>Comentarios  

 Cuando el subproceso especificado se ha suspendido como resultado de que el depurador detenga este proceso, el recuento de suspensión de Win32 del subproceso especificado se incrementa en uno. Es posible que la interfaz de usuario (UI) del depurador desee tener en cuenta esta información si muestra el recuento de suspensiones del sistema operativo (SO) del subproceso al usuario.  
  
 El `IsOSSuspended` método tiene sentido solo en el contexto de la depuración no administrada. Durante la depuración administrada, los subprocesos se suspenden de forma cooperativa en lugar de suspender el sistema operativo.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
