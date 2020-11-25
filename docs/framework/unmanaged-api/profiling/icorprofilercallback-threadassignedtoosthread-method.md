---
title: ICorProfilerCallback::ThreadAssignedToOSThread (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 2d6f34d88dd79fe350f1c018e3afa55e5b180c46
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732013"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="9b7ed-102">ICorProfilerCallback::ThreadAssignedToOSThread (Método)</span><span class="sxs-lookup"><span data-stu-id="9b7ed-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>

<span data-ttu-id="9b7ed-103">Notifica al generador de perfiles que un subproceso administrado se está implementando utilizando un subproceso del sistema operativo determinado.</span><span class="sxs-lookup"><span data-stu-id="9b7ed-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7ed-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9b7ed-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b7ed-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9b7ed-105">Parameters</span></span>  

 `managedThreadId`  
 <span data-ttu-id="9b7ed-106">de Identificador del subproceso administrado.</span><span class="sxs-lookup"><span data-stu-id="9b7ed-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="9b7ed-107">de Identificador del subproceso del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="9b7ed-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b7ed-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="9b7ed-108">Remarks</span></span>  

 <span data-ttu-id="9b7ed-109">La `ThreadAssignedToOSThread` devolución de llamada existe para que el generador de perfiles pueda mantener una asignación precisa entre fibras de subprocesos del sistema operativo y subprocesos administrados.</span><span class="sxs-lookup"><span data-stu-id="9b7ed-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b7ed-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b7ed-110">Requirements</span></span>  

 <span data-ttu-id="9b7ed-111">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b7ed-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b7ed-112">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b7ed-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b7ed-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b7ed-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b7ed-114">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b7ed-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7ed-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9b7ed-115">See also</span></span>

- [<span data-ttu-id="9b7ed-116">ICorProfilerCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="9b7ed-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
