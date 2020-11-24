---
title: ICorDebugController::Terminate (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 460aeeca9d62ce91a11a24d774c8e681ed4f00ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679811"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="81dd7-102">ICorDebugController::Terminate (Método)</span><span class="sxs-lookup"><span data-stu-id="81dd7-102">ICorDebugController::Terminate Method</span></span>

<span data-ttu-id="81dd7-103">Finaliza el proceso con el código de salida especificado.</span><span class="sxs-lookup"><span data-stu-id="81dd7-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81dd7-104">Este método es un contenedor para la función de Win32 `TerminateProcess` .</span><span class="sxs-lookup"><span data-stu-id="81dd7-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="81dd7-105">Por lo tanto, `Terminate` utiliza el código de salida del mismo modo que la función de Win32 `TerminateProcess` lo utiliza.</span><span class="sxs-lookup"><span data-stu-id="81dd7-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dd7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="81dd7-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81dd7-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="81dd7-107">Parameters</span></span>  

 `exitCode`  
 <span data-ttu-id="81dd7-108">de Un valor numérico que es el código de salida.</span><span class="sxs-lookup"><span data-stu-id="81dd7-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="81dd7-109">Los valores numéricos válidos se definen en Winbase. h.</span><span class="sxs-lookup"><span data-stu-id="81dd7-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81dd7-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="81dd7-110">Remarks</span></span>  

 <span data-ttu-id="81dd7-111">Si el proceso se detiene cuando `Terminate` se llama a, el proceso debe continuar usando el método [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) para que el depurador reciba la confirmación de la finalización a través de la devolución de llamada [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) o [ICorDebugManagedCallback:: exitappdomain (](icordebugmanagedcallback-exitappdomain-method.md) .</span><span class="sxs-lookup"><span data-stu-id="81dd7-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81dd7-112">Este método no está implementado por un dominio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="81dd7-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="81dd7-113">Es decir, no se implementa en el <xref:System.AppDomain> nivel.</span><span class="sxs-lookup"><span data-stu-id="81dd7-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81dd7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81dd7-114">Requirements</span></span>  

 <span data-ttu-id="81dd7-115">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81dd7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81dd7-116">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81dd7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81dd7-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81dd7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81dd7-118">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81dd7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81dd7-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="81dd7-119">See also</span></span>
