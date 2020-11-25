---
title: ICorDebugStepper::StepRange (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: d9698afa2723a5d772ecf5a055f09c5ee3bc13f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727658"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="b72aa-102">ICorDebugStepper::StepRange (Método)</span><span class="sxs-lookup"><span data-stu-id="b72aa-102">ICorDebugStepper::StepRange Method</span></span>

<span data-ttu-id="b72aa-103">Hace que este objeto ICorDebugStepper tenga un solo paso a través de su subproceso contenedor y que devuelva cuando llegue al código que se encuentra más allá del último de los intervalos especificados.</span><span class="sxs-lookup"><span data-stu-id="b72aa-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72aa-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b72aa-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b72aa-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b72aa-105">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="b72aa-106">de Establezca en `true` para entrar en una función a la que se llama en el subproceso.</span><span class="sxs-lookup"><span data-stu-id="b72aa-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="b72aa-107">Establezca en `false` para recorrer la función.</span><span class="sxs-lookup"><span data-stu-id="b72aa-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="b72aa-108">de Matriz de estructuras de COR_DEBUG_STEP_RANGE, cada una de las cuales especifica un intervalo.</span><span class="sxs-lookup"><span data-stu-id="b72aa-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="b72aa-109">[in] Tamaño de la matriz `ranges`.</span><span class="sxs-lookup"><span data-stu-id="b72aa-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b72aa-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="b72aa-110">Remarks</span></span>  

 <span data-ttu-id="b72aa-111">El `StepRange` método funciona como el método [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , con la salvedad de que no se completa hasta que se alcanza el código fuera del intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="b72aa-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="b72aa-112">Esto puede ser más eficaz que ejecutar una instrucción cada vez.</span><span class="sxs-lookup"><span data-stu-id="b72aa-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="b72aa-113">Los intervalos se especifican como una lista de pares de desplazamiento desde el inicio del marco del stepper.</span><span class="sxs-lookup"><span data-stu-id="b72aa-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="b72aa-114">Los intervalos son relativos al código del lenguaje intermedio de Microsoft (MSIL) de un método.</span><span class="sxs-lookup"><span data-stu-id="b72aa-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="b72aa-115">Llame a [ICorDebugStepper:: SetRangeIL (](icordebugstepper-setrangeil-method.md) con `false` para que los intervalos sean relativos al código nativo de un método.</span><span class="sxs-lookup"><span data-stu-id="b72aa-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b72aa-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b72aa-116">Requirements</span></span>  

 <span data-ttu-id="b72aa-117">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b72aa-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b72aa-118">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b72aa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b72aa-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b72aa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b72aa-120">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b72aa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
