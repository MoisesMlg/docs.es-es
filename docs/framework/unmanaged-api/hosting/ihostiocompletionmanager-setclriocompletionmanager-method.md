---
title: IHostIoCompletionManager::SetCLRIoCompletionManager (Método)
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: d370cc81942269bd79e06e0fa57fe5d79832b3c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724850"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="57d44-102">IHostIoCompletionManager::SetCLRIoCompletionManager (Método)</span><span class="sxs-lookup"><span data-stu-id="57d44-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="57d44-103">Proporciona al host un puntero de interfaz a la instancia de [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) implementada por el Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="57d44-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57d44-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="57d44-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57d44-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="57d44-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="57d44-106">de Puntero de interfaz a una `ICLRIoCompletionManager` instancia de proporcionada por el CLR.</span><span class="sxs-lookup"><span data-stu-id="57d44-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57d44-107">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="57d44-107">Return Value</span></span>  
  
|<span data-ttu-id="57d44-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57d44-108">HRESULT</span></span>|<span data-ttu-id="57d44-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="57d44-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57d44-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57d44-110">S_OK</span></span>|<span data-ttu-id="57d44-111">`SetCLRIoCompletionManager` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="57d44-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="57d44-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57d44-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57d44-113">CLR no se ha cargado en un proceso o CLR está en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="57d44-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57d44-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57d44-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57d44-115">Se agotó el tiempo de espera de la llamada.</span><span class="sxs-lookup"><span data-stu-id="57d44-115">The call timed out.</span></span>|  
|<span data-ttu-id="57d44-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57d44-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57d44-117">El autor de la llamada no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="57d44-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57d44-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57d44-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57d44-119">Se canceló un evento mientras un subproceso o fibra bloqueados estaba esperando en él.</span><span class="sxs-lookup"><span data-stu-id="57d44-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57d44-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57d44-120">E_FAIL</span></span>|<span data-ttu-id="57d44-121">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="57d44-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57d44-122">Cuando un método devuelve E_FAIL, CLR ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="57d44-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57d44-123">Las llamadas subsiguientes a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57d44-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57d44-124">Comentarios</span><span class="sxs-lookup"><span data-stu-id="57d44-124">Remarks</span></span>  

 <span data-ttu-id="57d44-125">Después de llamar a CLR `SetCLRIoCompletionManager` , el host debe llamar a [ICLRIoCompletionManager:: alcomplete](iclriocompletionmanager-oncomplete-method.md) para notificar a CLR cuando se ha completado una solicitud de e/s.</span><span class="sxs-lookup"><span data-stu-id="57d44-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57d44-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57d44-126">Requirements</span></span>  

 <span data-ttu-id="57d44-127">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57d44-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57d44-128">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57d44-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57d44-129">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57d44-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57d44-130">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57d44-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d44-131">Consulte también</span><span class="sxs-lookup"><span data-stu-id="57d44-131">See also</span></span>

- [<span data-ttu-id="57d44-132">ICLRIoCompletionManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="57d44-132">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="57d44-133">IHostIoCompletionManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="57d44-133">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
