---
title: Interacción de la directiva de caché, antigüedad máxima y obsolencia máxima
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: bdfa608b5169755b2b4daaaa26e562308ae2be01
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250611"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="43311-102">Interacción de la directiva de caché, antigüedad máxima y obsolencia máxima</span><span class="sxs-lookup"><span data-stu-id="43311-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>

<span data-ttu-id="43311-103">Para garantizar que se devuelva a la aplicación cliente el contenido más actualizado, la interacción de la directiva de caché de cliente y los requisitos de revalidación de servidor siempre da como resultado la directiva de caché más conservadora.</span><span class="sxs-lookup"><span data-stu-id="43311-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="43311-104">Todos los ejemplos de este tema muestran la directiva de caché de un recurso que se ha almacenado en caché el 1 de enero y expira el 4 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="43311-105">En los ejemplos siguientes se usa el valor de obsolescencia máximo (`maxStale`) junto con una antigüedad máxima (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="43311-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="43311-106">Si la directiva de caché establece `maxAge` = 5 días y no especifica un valor `maxStale`, según el valor `maxAge`, el contenido se puede usar hasta el 6 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="43311-107">Pero según los requisitos de revalidación de servidor, el contenido expira el 4 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="43311-108">Dado que la fecha de expiración del contenido es más conservadora (anterior), tiene prioridad sobre la directiva `maxAge`.</span><span class="sxs-lookup"><span data-stu-id="43311-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="43311-109">Por lo tanto, el contenido expira el 4 de enero y se debe volver a validar aunque no se haya alcanzado su antigüedad máxima.</span><span class="sxs-lookup"><span data-stu-id="43311-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="43311-110">Si la directiva de caché establece `maxAge` = 5 días y `maxStale` = 3 días, según el valor `maxAge`, el contenido se puede usar hasta el 6 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="43311-111">Según el valor `maxStale`, el contenido se puede usar hasta el 7 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="43311-112">Por lo tanto, el contenido se vuelve a validar el 6 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="43311-113">Si la directiva de caché establece `maxAge` = 5 días y `maxStale` = 1 día, según el valor `maxAge`, el contenido se puede usar hasta el 6 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="43311-114">Según el valor `maxStale`, el contenido se puede usar hasta el 5 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="43311-115">Por lo tanto, el contenido se vuelve a validar el 5 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="43311-116">Cuando la antigüedad máxima es menor que la fecha de expiración del contenido, el comportamiento de almacenamiento en caché más conservador siempre prevalece y el valor de obsolescencia máximo no tiene ningún efecto.</span><span class="sxs-lookup"><span data-stu-id="43311-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="43311-117">Los ejemplos siguientes muestran el efecto de establecer un valor de obsolescencia máximo (`maxStale`) cuando se alcanza la antigüedad máxima (`maxAge`) antes de que expire el contenido:</span><span class="sxs-lookup"><span data-stu-id="43311-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="43311-118">Si la directiva de caché establece `maxAge` = 1 día y no especifica un valor para `maxStale`, el contenido se vuelve a validar el 2 de enero aunque no haya expirado.</span><span class="sxs-lookup"><span data-stu-id="43311-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="43311-119">Si la directiva de caché establece `maxAge` = 1 día y `maxStale` = 3 días, el contenido se vuelve a validar el 2 de enero para aplicar el valor de directiva más conservador.</span><span class="sxs-lookup"><span data-stu-id="43311-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="43311-120">Si la directiva de caché establece `maxAge` = 1 día y `maxStale` = 1 día, el contenido se vuelve a validar el 2 de enero.</span><span class="sxs-lookup"><span data-stu-id="43311-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43311-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="43311-121">See also</span></span>

- [<span data-ttu-id="43311-122">Administración de la memoria caché para aplicaciones de red</span><span class="sxs-lookup"><span data-stu-id="43311-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="43311-123">Directiva de caché</span><span class="sxs-lookup"><span data-stu-id="43311-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="43311-124">Location-Based Cache Policies (Directivas de caché basadas en la ubicación)</span><span class="sxs-lookup"><span data-stu-id="43311-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- <span data-ttu-id="43311-125">[Time-Based Cache Policies](time-based-cache-policies.md) (Directivas de caché de duración definida)</span><span class="sxs-lookup"><span data-stu-id="43311-125">[Time-Based Cache Policies](time-based-cache-policies.md)</span></span>
- [<span data-ttu-id="43311-126">Configurar el almacenamiento en caché de las aplicaciones de red</span><span class="sxs-lookup"><span data-stu-id="43311-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="43311-127">Interacción de la directiva de caché, antigüedad máxima y actualización mínima</span><span class="sxs-lookup"><span data-stu-id="43311-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
