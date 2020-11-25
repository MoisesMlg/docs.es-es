---
title: ICorDebugRegisterSet (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 940810288b72be0d4dfc5366176663c22c369ebb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712384"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="95996-102">ICorDebugRegisterSet (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="95996-102">ICorDebugRegisterSet Interface</span></span>

<span data-ttu-id="95996-103">Representa el conjunto de registros disponibles en el equipo que está ejecutando código actualmente.</span><span class="sxs-lookup"><span data-stu-id="95996-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95996-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="95996-104">Methods</span></span>  
  
|<span data-ttu-id="95996-105">Método</span><span class="sxs-lookup"><span data-stu-id="95996-105">Method</span></span>|<span data-ttu-id="95996-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="95996-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95996-107">GetRegisters (Método)</span><span class="sxs-lookup"><span data-stu-id="95996-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="95996-108">Obtiene el valor de cada registro (en el equipo que está ejecutando código actualmente) especificado por la máscara de bits.</span><span class="sxs-lookup"><span data-stu-id="95996-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="95996-109">GetRegistersAvailable (Método)</span><span class="sxs-lookup"><span data-stu-id="95996-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="95996-110">Obtiene una máscara de bits que indica qué registros de `ICorDebugRegisterSet` están disponibles actualmente.</span><span class="sxs-lookup"><span data-stu-id="95996-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="95996-111">GetThreadContext (Método)</span><span class="sxs-lookup"><span data-stu-id="95996-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="95996-112">Obtiene el contexto del subproceso actual.</span><span class="sxs-lookup"><span data-stu-id="95996-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="95996-113">Método SetRegisters</span><span class="sxs-lookup"><span data-stu-id="95996-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="95996-114">No se ha implementado para la versión .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="95996-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="95996-115">Método SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="95996-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="95996-116">No se ha implementado para el .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="95996-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95996-117">Comentarios</span><span class="sxs-lookup"><span data-stu-id="95996-117">Remarks</span></span>  

 <span data-ttu-id="95996-118">La `ICorDebugRegisterSet` interfaz solo admite registros de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="95996-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="95996-119">Use la interfaz [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) en plataformas como IA-64 que requieran registros adicionales.</span><span class="sxs-lookup"><span data-stu-id="95996-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95996-120">Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.</span><span class="sxs-lookup"><span data-stu-id="95996-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95996-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95996-121">Requirements</span></span>  

 <span data-ttu-id="95996-122">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95996-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95996-123">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95996-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95996-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95996-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95996-125">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95996-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95996-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="95996-126">See also</span></span>

- [<span data-ttu-id="95996-127">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="95996-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="95996-128">ICorDebugRegisterSet2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="95996-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
