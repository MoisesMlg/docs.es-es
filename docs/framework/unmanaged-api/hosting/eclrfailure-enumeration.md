---
title: EClrFailure (Enumeración)
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: d2794b53ed17640413928b3af0d1ed3656e25f22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675768"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure (Enumeración)

Describe el conjunto de errores para los que un host puede establecer acciones de directiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Se produjo un error al intentar asignar un recurso (por ejemplo, un subproceso, un bloque de memoria o un bloqueo) en una región de código que no es crítica.|  
|`FAIL_CriticalResource`|Se produjo un error al intentar asignar un recurso (por ejemplo, un subproceso, un bloque de memoria o un bloqueo) en una región crítica de código.|  
|`FAIL_FatalRuntime`|El Common Language Runtime (CLR) ya no puede ejecutar código administrado en el proceso. En adelante, las llamadas a las funciones de hospedaje devuelven un valor HRESULT de HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Un subproceso no pudo liberar un bloqueo al devolver un <xref:System.AppDomain> objeto. El host no puede establecer este error para hacer que un subproceso se anule.|  
|`FAIL_StackOverflow`|Se ha producido un desbordamiento de pila.|  
|`FAIL_AccessViolation`|Se intentó leer o escribir en la memoria protegida. No se admite en el .NET Framework 4.|  
|`FAIL_CodeContract`|Error de contrato de código. Vea [contratos de código](../../debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Comentarios  

 Vea el método [ICLRPolicyManager:: setactiononfailure (](iclrpolicymanager-setactiononfailure-method.md) para obtener una lista de los valores de [EPolicyAction](epolicyaction-enumeration.md) que el host puede usar para especificar las acciones de directiva para las condiciones de error. Para obtener más información sobre las regiones críticas y no críticas de código, vea [EClrOperation](eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [ICLRPolicyManager (Interfaz)](iclrpolicymanager-interface.md)
- [Método SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager (Interfaz)](ihostpolicymanager-interface.md)
- [Enumeraciones para hosts](hosting-enumerations.md)
