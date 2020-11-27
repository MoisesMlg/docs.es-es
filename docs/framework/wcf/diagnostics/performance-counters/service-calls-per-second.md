---
title: 'Servicio: Llamadas por segundo'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 7e702d402909c4a85a2cb42c837e0813c4d9f841
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252886"
---
# <a name="service-calls-per-second"></a>Servicio: Llamadas por segundo

Nombre del contador: llamadas por segundo.  
  
## <a name="description"></a>Descripción  

 El número de llamadas por segundo a este servicio.  
  
 Este contador es de tipo de contador de rendimiento [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cuyo valor se calcula mediante la siguiente fórmula.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F), donde el numerador (N) representa el número de operaciones realizadas durante el último intervalo de muestra, el denominador (D) representa el número de pasos transcurridos desde el último intervalo de muestra y F representa la frecuencia de los pasos.
