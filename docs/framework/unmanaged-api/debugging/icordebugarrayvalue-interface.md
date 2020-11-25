---
title: Interfaz ICorDebugArrayValue
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 90688132b98f8316a4b08988c08b2f7cc7ce0fd8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725058"
---
# <a name="icordebugarrayvalue-interface"></a>Interfaz ICorDebugArrayValue

Subclase de ICorDebugHeapValue que representa una matriz unidimensional o multidimensional.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método GetBaseIndicies](icordebugarrayvalue-getbaseindicies-method.md)|Obtiene el índice base de cada dimensión de la matriz.|  
|[GetCount (Método)](icordebugarrayvalue-getcount-method.md)|Obtiene el número total de elementos de la matriz.|  
|[Método GetDimensions](icordebugarrayvalue-getdimensions-method.md)|Obtiene las dimensiones de la matriz.|  
|[Método GetElement](icordebugarrayvalue-getelement-method.md)|Obtiene un valor que representa el elemento especificado en la matriz.|  
|[Método GetElementAtPosition](icordebugarrayvalue-getelementatposition-method.md)|Obtiene el elemento en la posición especificada y trata la matriz como una matriz unidimensional de base cero.|  
|[Método GetElementType](icordebugarrayvalue-getelementtype-method.md)|Obtiene el tipo simple de los elementos de la matriz.|  
|[Método GetRank](icordebugarrayvalue-getrank-method.md)|Obtiene el número de dimensiones de la matriz.|  
|[Método HasBaseIndicies](icordebugarrayvalue-hasbaseindicies-method.md)|Determina si la matriz tiene índices base.|  
  
## <a name="remarks"></a>Comentarios  

 `ICorDebugArrayValue` admite Matrices unidimensionales y multidimensionales.  
  
> [!NOTE]
> Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Interfaces para depuración](debugging-interfaces.md)
