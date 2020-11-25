---
title: ICorDebugEval2::CreateValueForType (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 0b17bd729733665fbc4645aecd2e588b7eba14bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729699"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType (Método)

Obtiene un puntero a una nueva ICorDebugValue del tipo especificado, con un valor inicial de cero o null.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `pType`  
 de Puntero a un objeto ICorDebugType que representa el tipo.  
  
 `ppValue`  
 enuncia Puntero a la dirección de un `ICorDebugValue` objeto que representa el valor.  
  
## <a name="remarks"></a>Comentarios  

 `CreateValueForType` generaliza [ICorDebugEval:: CreateValue (](icordebugeval-createvalue-method.md) permitiéndole especificar un tipo de objeto arbitrario, incluidos los tipos construidos como `List<int>` . El único propósito de este método es generar un valor que se pueda pasar a una evaluación de función.  
  
 El tipo debe ser una clase o un tipo de valor. No se puede usar este método para crear valores de matriz o valores de cadena.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
