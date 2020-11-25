---
title: ICorProfilerCallback::JITFunctionPitched (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 51fec26837b3c7f0a0328a7b64ff4a02148283da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725520"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="081b1-102">ICorProfilerCallback::JITFunctionPitched (Método)</span><span class="sxs-lookup"><span data-stu-id="081b1-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="081b1-103">Notifica al generador de perfiles que se ha quitado de la memoria una función que se ha compilado Just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="081b1-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="081b1-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="081b1-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="081b1-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="081b1-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="081b1-106">de IDENTIFICADOR de la función que se ha quitado.</span><span class="sxs-lookup"><span data-stu-id="081b1-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="081b1-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="081b1-107">Remarks</span></span>  

 <span data-ttu-id="081b1-108">Si se llama a la función que se quita, el generador de perfiles recibirá nuevos eventos de compilación JIT cuando se vuelva a compilar la función.</span><span class="sxs-lookup"><span data-stu-id="081b1-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="081b1-109">Actualmente, el compilador JIT de Common Language Runtime (CLR) no quita funciones de la memoria, por lo que esta devolución de llamada no se utiliza actualmente y el generador de perfiles no las recibirá.</span><span class="sxs-lookup"><span data-stu-id="081b1-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="081b1-110">El valor de `functionId` no es válido hasta que se vuelva a compilar la función.</span><span class="sxs-lookup"><span data-stu-id="081b1-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="081b1-111">Cuando se vuelva a compilar la función, se usará el mismo `functionId` valor.</span><span class="sxs-lookup"><span data-stu-id="081b1-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="081b1-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="081b1-112">Requirements</span></span>  

 <span data-ttu-id="081b1-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="081b1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="081b1-114">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="081b1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="081b1-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="081b1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="081b1-116">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="081b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081b1-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="081b1-117">See also</span></span>

- [<span data-ttu-id="081b1-118">ICorProfilerCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="081b1-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
