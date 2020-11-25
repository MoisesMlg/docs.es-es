---
title: IHostTask::Alert (Método)
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 5a4870a4472081a78cd1fade51f441c22aa5eb48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720482"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="ff268-102">IHostTask::Alert (Método)</span><span class="sxs-lookup"><span data-stu-id="ff268-102">IHostTask::Alert Method</span></span>

<span data-ttu-id="ff268-103">Solicita que el host reactive la tarea representada por la instancia actual de [IHostTask](ihosttask-interface.md) , por lo que se puede anular la tarea.</span><span class="sxs-lookup"><span data-stu-id="ff268-103">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff268-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ff268-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ff268-105">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ff268-105">Return Value</span></span>  
  
|<span data-ttu-id="ff268-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff268-106">HRESULT</span></span>|<span data-ttu-id="ff268-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="ff268-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff268-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff268-108">S_OK</span></span>|<span data-ttu-id="ff268-109">El método se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="ff268-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="ff268-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff268-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff268-111">El Common Language Runtime (CLR) no se ha cargado en un proceso o el CLR se encuentra en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="ff268-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ff268-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff268-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff268-113">Se agotó el tiempo de espera de la llamada.</span><span class="sxs-lookup"><span data-stu-id="ff268-113">The call timed out.</span></span>|  
|<span data-ttu-id="ff268-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff268-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff268-115">El autor de la llamada no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="ff268-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff268-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff268-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff268-117">Se canceló un evento mientras un subproceso o fibra bloqueados estaba esperando en él.</span><span class="sxs-lookup"><span data-stu-id="ff268-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff268-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff268-118">E_FAIL</span></span>|<span data-ttu-id="ff268-119">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="ff268-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ff268-120">Cuando un método devuelve E_FAIL, CLR ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="ff268-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff268-121">Las llamadas subsiguientes a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ff268-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff268-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="ff268-122">Remarks</span></span>  

 <span data-ttu-id="ff268-123">CLR llama al `Alert` método cuando <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> se llama desde el código de usuario, o cuando se <xref:System.AppDomain> cierra el asociado a la actual <xref:System.Threading.Thread> .</span><span class="sxs-lookup"><span data-stu-id="ff268-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="ff268-124">El host debe volver inmediatamente, porque la llamada se realiza de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="ff268-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="ff268-125">Si el host no puede avisar inmediatamente de la tarea, se debe reactivar la próxima vez que entre en un estado en el que se pueda avisar.</span><span class="sxs-lookup"><span data-stu-id="ff268-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff268-126">`Alert` afecta solo a las tareas a las que el tiempo de ejecución ha pasado un valor [WAIT_OPTION](wait-option-enumeration.md) de WAIT_ALERTABLE a métodos como [join](ihosttask-join-method.md).</span><span class="sxs-lookup"><span data-stu-id="ff268-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff268-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff268-127">Requirements</span></span>  

 <span data-ttu-id="ff268-128">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff268-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff268-129">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff268-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff268-130">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff268-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff268-131">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff268-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff268-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ff268-132">See also</span></span>

- [<span data-ttu-id="ff268-133">ICLRTask (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ff268-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ff268-134">ICLRTaskManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ff268-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ff268-135">IHostTask (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ff268-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ff268-136">IHostTaskManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ff268-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
