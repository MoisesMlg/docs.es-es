---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 18aed5c5314fc1057767b599c538952a1d4d6b57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722237"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="7c52a-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks (Método)</span><span class="sxs-lookup"><span data-stu-id="7c52a-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>

<span data-ttu-id="7c52a-103">Especifica las funciones implementadas por el generador de perfiles a las que se llamará en los enlaces "Enter", "Leave" y "llamada" de las funciones administradas.</span><span class="sxs-lookup"><span data-stu-id="7c52a-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c52a-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7c52a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c52a-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7c52a-105">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="7c52a-106">de Puntero a la implementación de que se va a usar como devolución de llamada de [FunctionEnter (](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7c52a-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="7c52a-107">de Puntero a la implementación de que se va a usar como devolución de llamada de [FunctionLeave (](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7c52a-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="7c52a-108">de Puntero a la implementación de que se va a usar como devolución de llamada de [FunctionTailcall (](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7c52a-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c52a-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="7c52a-109">Remarks</span></span>  

 <span data-ttu-id="7c52a-110">En la versión .NET Framework 1,0, cada puntero de función puede ser null para deshabilitar la devolución de llamada correspondiente.</span><span class="sxs-lookup"><span data-stu-id="7c52a-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="7c52a-111">Solo un conjunto de devoluciones de llamada puede estar activo a la vez.</span><span class="sxs-lookup"><span data-stu-id="7c52a-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="7c52a-112">Por lo tanto, si un generador de perfiles llama a `SetEnterLeaveFunctionHooks` y a [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 (](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` tiene prioridad.</span><span class="sxs-lookup"><span data-stu-id="7c52a-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="7c52a-113">`SetEnterLeaveFunctionHooks`Solo se puede llamar al método desde la devolución de llamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) del generador de perfiles.</span><span class="sxs-lookup"><span data-stu-id="7c52a-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c52a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c52a-114">Requirements</span></span>  

 <span data-ttu-id="7c52a-115">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c52a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c52a-116">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c52a-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c52a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c52a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c52a-118">**.NET Framework versiones:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c52a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c52a-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7c52a-119">See also</span></span>

- [<span data-ttu-id="7c52a-120">ICorProfilerInfo (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="7c52a-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
