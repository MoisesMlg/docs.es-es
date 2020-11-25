---
title: IHostThreadPoolManager::SetMaxThreads (Método)
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 68e806daa63d13ad6c1f3b5de634c20ca02e8eb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730726"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="267e4-102">IHostThreadPoolManager::SetMaxThreads (Método)</span><span class="sxs-lookup"><span data-stu-id="267e4-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>

<span data-ttu-id="267e4-103">Establece el número máximo de subprocesos que el host puede mantener en el grupo de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="267e4-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267e4-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="267e4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="267e4-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="267e4-105">Parameters</span></span>  

 `MaxThreads`  
 <span data-ttu-id="267e4-106">Número máximo de subprocesos de trabajo en el grupo de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="267e4-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="267e4-107">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="267e4-107">Return Value</span></span>  
  
|<span data-ttu-id="267e4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="267e4-108">HRESULT</span></span>|<span data-ttu-id="267e4-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="267e4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="267e4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="267e4-110">S_OK</span></span>|<span data-ttu-id="267e4-111">`SetMaxThreads` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="267e4-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="267e4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="267e4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="267e4-113">El Common Language Runtime (CLR) no se ha cargado en un proceso o el CLR se encuentra en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="267e4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="267e4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="267e4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="267e4-115">Se agotó el tiempo de espera de la llamada.</span><span class="sxs-lookup"><span data-stu-id="267e4-115">The call timed out.</span></span>|  
|<span data-ttu-id="267e4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="267e4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="267e4-117">El autor de la llamada no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="267e4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="267e4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="267e4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="267e4-119">Se canceló un evento mientras un subproceso o fibra bloqueados estaba esperando en él.</span><span class="sxs-lookup"><span data-stu-id="267e4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="267e4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="267e4-120">E_FAIL</span></span>|<span data-ttu-id="267e4-121">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="267e4-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="267e4-122">Cuando un método devuelve E_FAIL, CLR ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="267e4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="267e4-123">Las llamadas subsiguientes a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="267e4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="267e4-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="267e4-124">E_NOTIMPL</span></span>|<span data-ttu-id="267e4-125">El host no proporciona una implementación de `SetMaxThreads` .</span><span class="sxs-lookup"><span data-stu-id="267e4-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="267e4-126">Comentarios</span><span class="sxs-lookup"><span data-stu-id="267e4-126">Remarks</span></span>  

 <span data-ttu-id="267e4-127">No se necesita un host para permitir que CLR configure el tamaño del grupo de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="267e4-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="267e4-128">Es posible que algunos hosts quieran un control exclusivo sobre el grupo de subprocesos, por motivos como la implementación, el rendimiento o la escalabilidad.</span><span class="sxs-lookup"><span data-stu-id="267e4-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="267e4-129">En este caso, un host debe devolver un valor HRESULT de E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="267e4-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="267e4-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="267e4-130">Requirements</span></span>  

 <span data-ttu-id="267e4-131">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="267e4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="267e4-132">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="267e4-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="267e4-133">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="267e4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="267e4-134">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="267e4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267e4-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="267e4-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="267e4-136">Método GetMaxThreads</span><span class="sxs-lookup"><span data-stu-id="267e4-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="267e4-137">Método SetMinThreads</span><span class="sxs-lookup"><span data-stu-id="267e4-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="267e4-138">IHostThreadPoolManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="267e4-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
