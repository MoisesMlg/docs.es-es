---
title: CorDebugIntercept (Enumeración)
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 3d3d4af8e9ee073c0aefec418a3b53c4589adf0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729114"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="cc4c2-102">CorDebugIntercept (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="cc4c2-102">CorDebugIntercept Enumeration</span></span>

<span data-ttu-id="cc4c2-103">Indica los tipos de código que se pueden interceptar, es decir, ejecutar paso a paso.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4c2-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cc4c2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="cc4c2-105">Miembros</span><span class="sxs-lookup"><span data-stu-id="cc4c2-105">Members</span></span>  
  
|<span data-ttu-id="cc4c2-106">Miembro</span><span class="sxs-lookup"><span data-stu-id="cc4c2-106">Member</span></span>|<span data-ttu-id="cc4c2-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="cc4c2-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="cc4c2-108">No se puede interceptar ningún código.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="cc4c2-109">Se puede interceptar un constructor.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="cc4c2-110">Se puede interceptar un filtro de excepción.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="cc4c2-111">Se puede interceptar código que exija seguridad.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="cc4c2-112">Se puede interceptar una directiva de contexto.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="cc4c2-113">No se usa.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="cc4c2-114">Se puede interceptar todo el código.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc4c2-115">Comentarios</span><span class="sxs-lookup"><span data-stu-id="cc4c2-115">Remarks</span></span>  

 <span data-ttu-id="cc4c2-116">Use el método [ICorDebugStepper:: setinterceptmask (](icordebugstepper-setinterceptmask-method.md) para establecer los tipos de código que se pueden interceptar.</span><span class="sxs-lookup"><span data-stu-id="cc4c2-116">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc4c2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc4c2-117">Requirements</span></span>  

 <span data-ttu-id="cc4c2-118">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc4c2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4c2-119">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc4c2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc4c2-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc4c2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc4c2-121">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc4c2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4c2-122">Consulte también</span><span class="sxs-lookup"><span data-stu-id="cc4c2-122">See also</span></span>

- [<span data-ttu-id="cc4c2-123">Enumeraciones de depuración</span><span class="sxs-lookup"><span data-stu-id="cc4c2-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
