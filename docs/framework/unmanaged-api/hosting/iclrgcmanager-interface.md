---
title: ICLRGCManager (Interfaz)
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: dbe3df6bb20e5ad8f9eb534a366405eb9c33984f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678251"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager (Interfaz)

Proporciona métodos que permiten a un host interactuar con el sistema de recolección de elementos no utilizados del Common Language Runtime.  
  
> [!NOTE]
> A partir del .NET Framework 4,5, puede usar el método [iclrgcmanager2 (:: setgcstartuplimitsex (](iclrgcmanager2-setgcstartuplimitsex-method.md) para establecer el tamaño de un segmento de recolección de elementos no utilizados y el tamaño máximo de la generación 0 del sistema de recolección de elementos no utilizados en valores mayores que el `DWORD` límite impuesto por el método [setgcstartuplimits (](iclrgcmanager-setgcstartuplimits-method.md) .  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método Collect](iclrgcmanager-collect-method.md)|Fuerza una recolección de elementos no utilizados para la generación especificada.|  
|[GetStats (Método)](iclrgcmanager-getstats-method.md)|Obtiene un conjunto de estadísticas actuales sobre el sistema de recolección de elementos no utilizados.|  
|[Método SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md)|Establece el tamaño de un segmento de recolección de elementos no utilizados y el tamaño máximo de la generación 0 del sistema de recolección de elementos no utilizados.|  
  
## <a name="remarks"></a>Comentarios  

 El Common Language Runtime (CLR) implementa su mecanismo de recolección de elementos no utilizados con el <xref:System.GC> tipo administrado. Para obtener más información sobre el sistema de recolección de elementos no utilizados, consulte recolección de [elementos no utilizados](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE. h  
  
 **Biblioteca:** Se incluye como un recurso en MSCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Administración automática de la memoria](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS (Estructura)](cor-gc-stats-structure.md)
- [ICLRControl (Interfaz)](iclrcontrol-interface.md)
- [Interfaces de hospedaje de CLR](clr-hosting-interfaces.md)
- [Interfaces de hospedaje](hosting-interfaces.md)
- [Hospedar aplicaciones de WPF](index.md)
