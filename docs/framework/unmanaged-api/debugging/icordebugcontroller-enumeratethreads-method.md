---
title: ICorDebugController::EnumerateThreads (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: f98118f9206d9ccd7dc9dc9a943500c7b4cd676a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732663"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="1c78a-102">ICorDebugController::EnumerateThreads (Método)</span><span class="sxs-lookup"><span data-stu-id="1c78a-102">ICorDebugController::EnumerateThreads Method</span></span>

<span data-ttu-id="1c78a-103">Obtiene un enumerador para los subprocesos administrados activos en el proceso.</span><span class="sxs-lookup"><span data-stu-id="1c78a-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c78a-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1c78a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c78a-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1c78a-105">Parameters</span></span>  

 `ppThreads`  
 <span data-ttu-id="1c78a-106">enuncia Puntero a la dirección de un objeto "ICorDebugThreadEnum (" que representa un enumerador para todos los subprocesos administrados que están activos en el proceso.</span><span class="sxs-lookup"><span data-stu-id="1c78a-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c78a-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="1c78a-107">Remarks</span></span>  

 <span data-ttu-id="1c78a-108">Un subproceso se considera activo después de que se haya enviado la devolución de llamada [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) y antes de que se haya enviado la devolución de llamada [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1c78a-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="1c78a-109">Es posible que un subproceso administrado no tenga necesariamente ningún marco administrado en la pila.</span><span class="sxs-lookup"><span data-stu-id="1c78a-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="1c78a-110">Los subprocesos se pueden enumerar incluso antes de la devolución de llamada [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1c78a-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="1c78a-111">La enumeración estará vacía naturalmente.</span><span class="sxs-lookup"><span data-stu-id="1c78a-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c78a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c78a-112">Requirements</span></span>  

 <span data-ttu-id="1c78a-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c78a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c78a-114">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c78a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c78a-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c78a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c78a-116">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c78a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c78a-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1c78a-117">See also</span></span>
