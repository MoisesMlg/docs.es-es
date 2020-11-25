---
title: ICLRPolicyManager::SetActionOnFailure (Método)
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 8f44247ca7904a40f5ebc092d95c2e08b6048438
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725578"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="f1c25-102">ICLRPolicyManager::SetActionOnFailure (Método)</span><span class="sxs-lookup"><span data-stu-id="f1c25-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="f1c25-103">Especifica la acción de la Directiva que debe realizar el Common Language Runtime (CLR) cuando se produce el error especificado.</span><span class="sxs-lookup"><span data-stu-id="f1c25-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1c25-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f1c25-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1c25-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f1c25-105">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="f1c25-106">de Uno de los valores de [eclrfailure (](eclrfailure-enumeration.md) , que indica el tipo de error para el que se realizará la acción.</span><span class="sxs-lookup"><span data-stu-id="f1c25-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="f1c25-107">de Uno de los valores de [EPolicyAction](epolicyaction-enumeration.md) , que indica la acción que se debe realizar cuando se produce un error.</span><span class="sxs-lookup"><span data-stu-id="f1c25-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="f1c25-108">Para obtener una lista de valores admitidos, vea la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="f1c25-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1c25-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="f1c25-109">Return Value</span></span>  
  
|<span data-ttu-id="f1c25-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1c25-110">HRESULT</span></span>|<span data-ttu-id="f1c25-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="f1c25-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1c25-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1c25-112">S_OK</span></span>|<span data-ttu-id="f1c25-113">`SetActionOnFailure` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1c25-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="f1c25-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1c25-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1c25-115">CLR no se ha cargado en un proceso o CLR está en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="f1c25-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f1c25-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f1c25-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f1c25-117">Se agotó el tiempo de espera de la llamada.</span><span class="sxs-lookup"><span data-stu-id="f1c25-117">The call timed out.</span></span>|  
|<span data-ttu-id="f1c25-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1c25-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f1c25-119">El autor de la llamada no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="f1c25-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f1c25-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f1c25-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f1c25-121">Se canceló un evento mientras un subproceso o fibra bloqueados estaba esperando en él.</span><span class="sxs-lookup"><span data-stu-id="f1c25-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f1c25-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1c25-122">E_FAIL</span></span>|<span data-ttu-id="f1c25-123">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="f1c25-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1c25-124">Después de que un método devuelve E_FAIL, CLR ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="f1c25-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f1c25-125">Las llamadas subsiguientes a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f1c25-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f1c25-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f1c25-126">E_INVALIDARG</span></span>|<span data-ttu-id="f1c25-127">No se puede establecer una acción de directiva para la operación especificada o se especificó una acción de Directiva no válida para la operación.</span><span class="sxs-lookup"><span data-stu-id="f1c25-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1c25-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="f1c25-128">Remarks</span></span>  

 <span data-ttu-id="f1c25-129">De forma predeterminada, CLR produce una excepción cuando no puede asignar un recurso como memoria.</span><span class="sxs-lookup"><span data-stu-id="f1c25-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="f1c25-130">`SetActionOnFailure` permite que el host Invalide este comportamiento especificando la acción de la Directiva que se realizará en caso de error.</span><span class="sxs-lookup"><span data-stu-id="f1c25-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="f1c25-131">En la tabla siguiente se muestran las combinaciones de los valores [eclrfailure (](eclrfailure-enumeration.md) y [EPolicyAction](epolicyaction-enumeration.md) que se admiten.</span><span class="sxs-lookup"><span data-stu-id="f1c25-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="f1c25-132">(El prefijo FAIL_ se omite de los valores de [eclrfailure (](eclrfailure-enumeration.md) ).</span><span class="sxs-lookup"><span data-stu-id="f1c25-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="f1c25-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="f1c25-133">NonCriticalResource</span></span>|<span data-ttu-id="f1c25-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="f1c25-134">CriticalResource</span></span>|<span data-ttu-id="f1c25-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="f1c25-135">FatalRuntime</span></span>|<span data-ttu-id="f1c25-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="f1c25-136">OrphanedLock</span></span>|<span data-ttu-id="f1c25-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="f1c25-137">StackOverflow</span></span>|<span data-ttu-id="f1c25-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="f1c25-138">AccessViolation</span></span>|<span data-ttu-id="f1c25-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="f1c25-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="f1c25-140">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-140">X</span></span>|<span data-ttu-id="f1c25-141">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-141">X</span></span>||||<span data-ttu-id="f1c25-142">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-142">N/A</span></span>||  
|<span data-ttu-id="f1c25-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="f1c25-143">eThrowException</span></span>|<span data-ttu-id="f1c25-144">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-144">X</span></span>|<span data-ttu-id="f1c25-145">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-145">X</span></span>||||<span data-ttu-id="f1c25-146">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="f1c25-147">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-147">X</span></span>|<span data-ttu-id="f1c25-148">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-148">X</span></span>||||<span data-ttu-id="f1c25-149">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-149">N/A</span></span>|<span data-ttu-id="f1c25-150">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="f1c25-151">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-151">X</span></span>|<span data-ttu-id="f1c25-152">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-152">X</span></span>||||<span data-ttu-id="f1c25-153">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-153">N/A</span></span>|<span data-ttu-id="f1c25-154">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="f1c25-155">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-155">X</span></span>|<span data-ttu-id="f1c25-156">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-156">X</span></span>||<span data-ttu-id="f1c25-157">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-157">X</span></span>||<span data-ttu-id="f1c25-158">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-158">N/A</span></span>|<span data-ttu-id="f1c25-159">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="f1c25-160">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-160">X</span></span>|<span data-ttu-id="f1c25-161">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-161">X</span></span>||<span data-ttu-id="f1c25-162">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-162">X</span></span>|<span data-ttu-id="f1c25-163">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-163">X</span></span>|<span data-ttu-id="f1c25-164">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-164">N/A</span></span>|<span data-ttu-id="f1c25-165">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="f1c25-166">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-166">X</span></span>|<span data-ttu-id="f1c25-167">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-167">X</span></span>||<span data-ttu-id="f1c25-168">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-168">X</span></span>|<span data-ttu-id="f1c25-169">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-169">X</span></span>|<span data-ttu-id="f1c25-170">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-170">N/A</span></span>|<span data-ttu-id="f1c25-171">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-171">X</span></span>|  
|<span data-ttu-id="f1c25-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="f1c25-172">eFastExitProcess</span></span>|<span data-ttu-id="f1c25-173">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-173">X</span></span>|<span data-ttu-id="f1c25-174">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-174">X</span></span>||<span data-ttu-id="f1c25-175">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-175">X</span></span>|<span data-ttu-id="f1c25-176">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-176">X</span></span>|<span data-ttu-id="f1c25-177">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="f1c25-178">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-178">X</span></span>|<span data-ttu-id="f1c25-179">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-179">X</span></span>|<span data-ttu-id="f1c25-180">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-180">X</span></span>|<span data-ttu-id="f1c25-181">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-181">X</span></span>|<span data-ttu-id="f1c25-182">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-182">X</span></span>|<span data-ttu-id="f1c25-183">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="f1c25-184">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-184">X</span></span>|<span data-ttu-id="f1c25-185">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-185">X</span></span>|<span data-ttu-id="f1c25-186">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-186">X</span></span>|<span data-ttu-id="f1c25-187">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-187">X</span></span>|<span data-ttu-id="f1c25-188">X</span><span class="sxs-lookup"><span data-stu-id="f1c25-188">X</span></span>|<span data-ttu-id="f1c25-189">N/D</span><span class="sxs-lookup"><span data-stu-id="f1c25-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="f1c25-190">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1c25-190">Requirements</span></span>  

 <span data-ttu-id="f1c25-191">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c25-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c25-192">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f1c25-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1c25-193">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1c25-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1c25-194">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c25-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c25-195">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f1c25-195">See also</span></span>

- [<span data-ttu-id="f1c25-196">EClrFailure (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="f1c25-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="f1c25-197">EPolicyAction (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="f1c25-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="f1c25-198">ICLRControl (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="f1c25-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f1c25-199">ICLRPolicyManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="f1c25-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
