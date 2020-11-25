---
title: Interfaz ICorDebugFrame
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: bdc17e2c6c63deae1420fe738eac51153f6b368e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726345"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="1aab9-102">Interfaz ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="1aab9-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="1aab9-103">Representa un marco en la pila actual.</span><span class="sxs-lookup"><span data-stu-id="1aab9-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1aab9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1aab9-104">Methods</span></span>  
  
|<span data-ttu-id="1aab9-105">Método</span><span class="sxs-lookup"><span data-stu-id="1aab9-105">Method</span></span>|<span data-ttu-id="1aab9-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="1aab9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1aab9-107">CreateStepper (Método)</span><span class="sxs-lookup"><span data-stu-id="1aab9-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="1aab9-108">Obtiene un ICorDebugStepper para realizar operaciones de ejecución paso a paso con respecto a este `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="1aab9-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="1aab9-109">Método GetCallee</span><span class="sxs-lookup"><span data-stu-id="1aab9-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="1aab9-110">Obtiene un puntero al `ICorDebugFrame` en la cadena actual a la que este marco llamó, o devuelve NULL si se trata del marco más interno de la cadena.</span><span class="sxs-lookup"><span data-stu-id="1aab9-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="1aab9-111">Método GetCaller</span><span class="sxs-lookup"><span data-stu-id="1aab9-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="1aab9-112">Obtiene un puntero al `ICorDebugFrame` en la cadena actual que llamó a este marco, o devuelve NULL si se trata del marco más externo de la cadena.</span><span class="sxs-lookup"><span data-stu-id="1aab9-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="1aab9-113">Método GetChain</span><span class="sxs-lookup"><span data-stu-id="1aab9-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="1aab9-114">Obtiene un puntero al `ICorDebugFrame` elemento ICorDebugChain del que forma parte.</span><span class="sxs-lookup"><span data-stu-id="1aab9-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="1aab9-115">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="1aab9-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="1aab9-116">Obtiene un puntero a la clase ICorDebugCode asociada a este marco de pila.</span><span class="sxs-lookup"><span data-stu-id="1aab9-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="1aab9-117">Método GetFunction</span><span class="sxs-lookup"><span data-stu-id="1aab9-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="1aab9-118">Obtiene un puntero a la clase ICorDebugFunction que contiene el código asociado a este marco de pila.</span><span class="sxs-lookup"><span data-stu-id="1aab9-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="1aab9-119">Método GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="1aab9-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="1aab9-120">Obtiene el símbolo (token) de metadatos para la función que contiene el código asociado a este marco de pila.</span><span class="sxs-lookup"><span data-stu-id="1aab9-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="1aab9-121">GetStackRange (Método)</span><span class="sxs-lookup"><span data-stu-id="1aab9-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="1aab9-122">Obtiene el intervalo de direcciones absolutas del marco de pila representado por este `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="1aab9-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aab9-123">Comentarios</span><span class="sxs-lookup"><span data-stu-id="1aab9-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1aab9-124">Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.</span><span class="sxs-lookup"><span data-stu-id="1aab9-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aab9-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1aab9-125">Requirements</span></span>  

 <span data-ttu-id="1aab9-126">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aab9-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aab9-127">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aab9-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aab9-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aab9-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aab9-129">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aab9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aab9-130">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1aab9-130">See also</span></span>

- [<span data-ttu-id="1aab9-131">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="1aab9-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
