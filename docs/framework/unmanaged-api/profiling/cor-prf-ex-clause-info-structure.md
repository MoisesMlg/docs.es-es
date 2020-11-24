---
title: COR_PRF_EX_CLAUSE_INFO (Estructura)
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: e8dd9f21803021975f4651ba3e6e5f4d3da0ea82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675001"
---
# <a name="cor_prf_ex_clause_info-structure"></a>COR_PRF_EX_CLAUSE_INFO (Estructura)

Almacena información sobre una instancia específica de cláusula de excepción y su marco asociado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`clauseType`|Un valor de la enumeración [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) que especifica el tipo de cláusula de excepción que el código acaba de escribir o a la izquierda.|  
|`programCounter`|El punto de entrada nativo del controlador de la cláusula, por ejemplo, el contenido del registro de la EIP x86.|  
|`framePointer`|El puntero al marco lógico para el controlador de la cláusula, por ejemplo, el contenido del registro del EBP x86.|  
|`shadowStackPointer`|Puntero a la pila de la sombra. Este valor es el contenido del registro de BSP y se aplica solo a IA64.|  
  
## <a name="remarks"></a>Comentarios  

 Cuando se recibe una notificación de excepción, se puede usar [ICorProfilerInfo2:: getnotifiedexceptionclauseinfo (](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) para obtener la información de la dirección nativa y el marco de la cláusula de excepción ( `catch` / `finally` /Filter) que está a punto de ejecutarse o que se acaba de ejecutar.  
  
 La ejecución de una cláusula de excepción implica estas devoluciones de llamada de Common Language Runtime (CLR):  
  
- [ICorProfilerCallback:: Exceptioncatcherenter (](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback:: Exceptionunwindfinallyenter (](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback:: Exceptionsearchfilterenter (](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback:: Exceptioncatcherleave (](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionUnwindFinallyLeave (](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback:: Exceptionsearchfilterleave (](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Estructuras para generación de perfiles](profiling-structures.md)
