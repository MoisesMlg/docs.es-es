---
title: Mensajes en cola rechazados por segundo
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 2b7686ee94ab051bc255bdb71681c8d1c473094c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276209"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="58cd8-102">Mensajes en cola rechazados por segundo</span><span class="sxs-lookup"><span data-stu-id="58cd8-102">Queued Rejected Messages Per Second</span></span>

<span data-ttu-id="58cd8-103">Nombre de contador: mensajes en cola rechazados por segundo.</span><span class="sxs-lookup"><span data-stu-id="58cd8-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="58cd8-104">Descripción</span><span class="sxs-lookup"><span data-stu-id="58cd8-104">Description</span></span>  

 <span data-ttu-id="58cd8-105">Número de mensajes rechazados cada segundo por el transporte en cola en este servicio.</span><span class="sxs-lookup"><span data-stu-id="58cd8-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="58cd8-106">Este contador es de tipo de contador de rendimiento [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), cuyo valor se calcula mediante la siguiente fórmula.</span><span class="sxs-lookup"><span data-stu-id="58cd8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="58cd8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="58cd8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
