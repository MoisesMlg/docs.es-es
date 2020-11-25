---
title: IGCHost (Interfaz)
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 8965797321e68443c01d05f97d147f2320a76739
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724304"
---
# <a name="igchost-interface"></a><span data-ttu-id="38f96-102">IGCHost (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="38f96-102">IGCHost Interface</span></span>

<span data-ttu-id="38f96-103">Proporciona métodos para obtener información sobre el sistema de recolección de elementos no utilizados y para controlar algunos aspectos de la recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="38f96-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38f96-104">A partir del .NET Framework 4,5, puede usar el método [igchost2 (:: setgcstartuplimitsex (](igchost2-setgcstartuplimitsex-method.md) para establecer el tamaño de un segmento de recolección de elementos no utilizados y el tamaño máximo de la generación 0 del sistema de recolección de elementos no utilizados en valores mayores que el `DWORD` límite impuesto por el método [setgcstartuplimits (](igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="38f96-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38f96-105">Esta interfaz solo es para uso experto.</span><span class="sxs-lookup"><span data-stu-id="38f96-105">This interface is for expert usage only.</span></span> <span data-ttu-id="38f96-106">Puede afectar al rendimiento de una aplicación si se usa de forma incorrecta.</span><span class="sxs-lookup"><span data-stu-id="38f96-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38f96-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="38f96-107">Methods</span></span>  
  
|<span data-ttu-id="38f96-108">Método</span><span class="sxs-lookup"><span data-stu-id="38f96-108">Method</span></span>|<span data-ttu-id="38f96-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="38f96-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38f96-110">Método Collect</span><span class="sxs-lookup"><span data-stu-id="38f96-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="38f96-111">Obliga a que se produzca una colección para la generación dada, independientemente del estado de la recolección de elementos no utilizados actual.</span><span class="sxs-lookup"><span data-stu-id="38f96-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="38f96-112">GetStats (Método)</span><span class="sxs-lookup"><span data-stu-id="38f96-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="38f96-113">Obtiene las estadísticas para el estado actual del sistema de recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="38f96-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="38f96-114">Método GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="38f96-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="38f96-115">Obtiene las estadísticas por subproceso para la recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="38f96-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="38f96-116">Método SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="38f96-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="38f96-117">Establece el tamaño del segmento y el tamaño máximo de la generación 0.</span><span class="sxs-lookup"><span data-stu-id="38f96-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="38f96-118">Método SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="38f96-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="38f96-119">Establece el tamaño máximo de la memoria virtual del tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="38f96-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38f96-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38f96-120">Requirements</span></span>  

 <span data-ttu-id="38f96-121">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f96-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f96-122">**Encabezado:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="38f96-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="38f96-123">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38f96-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38f96-124">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f96-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f96-125">Consulte también</span><span class="sxs-lookup"><span data-stu-id="38f96-125">See also</span></span>

- [<span data-ttu-id="38f96-126">Interfaces de hospedaje</span><span class="sxs-lookup"><span data-stu-id="38f96-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="38f96-127">CorRuntimeHost (Coclase)</span><span class="sxs-lookup"><span data-stu-id="38f96-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
