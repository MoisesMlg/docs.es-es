---
title: ICorProfilerFunctionControl (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
ms.openlocfilehash: 733a8f0bc7e8c19823827297a50f9c6906614ca7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698395"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="6e564-102">ICorProfilerFunctionControl (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="6e564-102">ICorProfilerFunctionControl Interface</span></span>

<span data-ttu-id="6e564-103">Proporciona métodos que permiten a un generador de perfiles de código comunicarse con Common Language Runtime (CLR) para controlar cómo debe generar el código el compilador JIT cuando vuelva a compilar un método específico.</span><span class="sxs-lookup"><span data-stu-id="6e564-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e564-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6e564-104">Methods</span></span>  
  
|<span data-ttu-id="6e564-105">Método</span><span class="sxs-lookup"><span data-stu-id="6e564-105">Method</span></span>|<span data-ttu-id="6e564-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="6e564-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e564-107">Método SetCodegenFlags</span><span class="sxs-lookup"><span data-stu-id="6e564-107">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="6e564-108">Establece una o varias marcas de la enumeración [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) para controlar la generación de código para una función recompilada Just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="6e564-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="6e564-109">SetILFunctionBody (Método)</span><span class="sxs-lookup"><span data-stu-id="6e564-109">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="6e564-110">Reemplaza el cuerpo del Lenguaje intermedio común (CIL) del método.</span><span class="sxs-lookup"><span data-stu-id="6e564-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="6e564-111">SetILInstrumentedCodeMap (Método)</span><span class="sxs-lookup"><span data-stu-id="6e564-111">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="6e564-112">Establece un mapa de código para la función especificada usando las entradas del mapa de Common Intermediate Language (CIL) especificadas.</span><span class="sxs-lookup"><span data-stu-id="6e564-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e564-113">Comentarios</span><span class="sxs-lookup"><span data-stu-id="6e564-113">Remarks</span></span>  

 <span data-ttu-id="6e564-114">La interfaz `ICorProfilerFunctionControl` proporciona métodos para controlar la generación de código para una única función que se ha vuelto a compilar.</span><span class="sxs-lookup"><span data-stu-id="6e564-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="6e564-115">El generador de perfiles obtiene una instancia de esta interfaz a través de la devolución de llamada [ICorProfilerCallback4:: getrejitparameters (](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6e564-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="6e564-116">Cada instancia de `ICorProfilerFunctionControl` controla todas las instancias de una función.</span><span class="sxs-lookup"><span data-stu-id="6e564-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e564-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e564-117">Requirements</span></span>  

 <span data-ttu-id="6e564-118">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e564-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e564-119">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e564-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e564-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e564-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e564-121">**.NET Framework versiones:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e564-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e564-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="6e564-122">See also</span></span>

- [<span data-ttu-id="6e564-123">ICorProfilerInfo4 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="6e564-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="6e564-124">Interfaces para generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="6e564-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6e564-125">Método EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="6e564-125">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
