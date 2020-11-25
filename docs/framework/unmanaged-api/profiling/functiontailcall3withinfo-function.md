---
title: FunctionTailcall3WithInfo (Función)
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: c23c791197c9925038f71e70409e4ca3ebabb23e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722873"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="4202c-102">FunctionTailcall3WithInfo (Función)</span><span class="sxs-lookup"><span data-stu-id="4202c-102">FunctionTailcall3WithInfo Function</span></span>

<span data-ttu-id="4202c-103">Notifica al generador de perfiles que la función que se está ejecutando actualmente está a punto de realizar una llamada de cola a otra función y proporciona un identificador que se puede pasar al [método ICorProfilerInfo3:: GetFunctionTailcall3Info (](icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar el marco de pila.</span><span class="sxs-lookup"><span data-stu-id="4202c-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4202c-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4202c-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4202c-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4202c-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="4202c-106">\[in] el identificador de la función que se ejecuta actualmente y que está a punto de realizar una llamada de cola.</span><span class="sxs-lookup"><span data-stu-id="4202c-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="4202c-107">\[in] un identificador opaco que representa información sobre un marco de pila determinado.</span><span class="sxs-lookup"><span data-stu-id="4202c-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="4202c-108">Este identificador es válido solo durante la devolución de llamada a la que se pasa.</span><span class="sxs-lookup"><span data-stu-id="4202c-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="4202c-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="4202c-109">Remarks</span></span>  

 <span data-ttu-id="4202c-110">El `FunctionTailcall3WithInfo` método de devolución de llamada notifica al generador de perfiles cuando se llama a las funciones y permite que el generador de perfiles use el [método ICorProfilerInfo3:: GetFunctionTailcall3Info (](icorprofilerinfo3-getfunctiontailcall3info-method.md) para inspeccionar el marco de pila.</span><span class="sxs-lookup"><span data-stu-id="4202c-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="4202c-111">Para obtener acceso a la información del marco de pila, se debe `COR_PRF_ENABLE_FRAME_INFO` establecer la marca.</span><span class="sxs-lookup"><span data-stu-id="4202c-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="4202c-112">El generador de perfiles puede utilizar el [método ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para establecer las marcas de evento y, a continuación, usar el [método ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo (](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) para registrar la implementación de esta función.</span><span class="sxs-lookup"><span data-stu-id="4202c-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4202c-113">La `FunctionTailcall3WithInfo` función es una devolución de llamada; debe implementarla.</span><span class="sxs-lookup"><span data-stu-id="4202c-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="4202c-114">La implementación debe usar el `__declspec(naked)` atributo de clase de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4202c-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="4202c-115">El motor de ejecución no guarda ningún registro antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="4202c-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="4202c-116">En la entrada, debe guardar todos los registros que use, incluidos los de la unidad de punto flotante (FPU).</span><span class="sxs-lookup"><span data-stu-id="4202c-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="4202c-117">Al salir, debe restaurar la pila desactivando todos los parámetros insertados por el autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="4202c-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="4202c-118">La implementación de `FunctionTailcall3WithInfo` no debe bloquearse porque retrasará la recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="4202c-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="4202c-119">La implementación no debe intentar una recolección de elementos no utilizados, porque es posible que la pila no esté en un estado reconocible para la recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="4202c-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="4202c-120">Si se intenta realizar una recolección de elementos no utilizados, el tiempo de ejecución se bloqueará hasta que se `FunctionTailcall3WithInfo` devuelva.</span><span class="sxs-lookup"><span data-stu-id="4202c-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="4202c-121">Además, la función FunctionTailcall3WithInfo no debe llamar a código administrado ni producir una asignación de memoria administrada de ninguna manera.</span><span class="sxs-lookup"><span data-stu-id="4202c-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4202c-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4202c-122">Requirements</span></span>  

 <span data-ttu-id="4202c-123">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4202c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4202c-124">**Encabezado:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="4202c-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4202c-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4202c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4202c-126">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4202c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4202c-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4202c-127">See also</span></span>

- [<span data-ttu-id="4202c-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4202c-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="4202c-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="4202c-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="4202c-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="4202c-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4202c-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4202c-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4202c-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4202c-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="4202c-133">Setenterleavefunctionhooks3 (</span><span class="sxs-lookup"><span data-stu-id="4202c-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="4202c-134">Setenterleavefunctionhooks3withinfo (</span><span class="sxs-lookup"><span data-stu-id="4202c-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="4202c-135">Setfunctionidmapper (</span><span class="sxs-lookup"><span data-stu-id="4202c-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="4202c-136">Setfunctionidmapper2 (</span><span class="sxs-lookup"><span data-stu-id="4202c-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="4202c-137">Funciones estáticas globales para generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="4202c-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
