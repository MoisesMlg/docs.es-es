---
title: COR_DEBUG_STEP_RANGE (Estructura)
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
ms.openlocfilehash: cd85ba2e6a907ff9546614e02b4da5f45e74b924
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726644"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="5736a-102">COR_DEBUG_STEP_RANGE (Estructura)</span><span class="sxs-lookup"><span data-stu-id="5736a-102">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="5736a-103">Contiene información de desplazamiento para un intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="5736a-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="5736a-104">Esta estructura la usa el método [ICorDebugStepper:: steprange (](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5736a-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5736a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5736a-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="5736a-106">Miembros</span><span class="sxs-lookup"><span data-stu-id="5736a-106">Members</span></span>  
  
|<span data-ttu-id="5736a-107">Miembro</span><span class="sxs-lookup"><span data-stu-id="5736a-107">Member</span></span>|<span data-ttu-id="5736a-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="5736a-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="5736a-109">Desplazamiento del principio del intervalo.</span><span class="sxs-lookup"><span data-stu-id="5736a-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="5736a-110">Desplazamiento del final del intervalo.</span><span class="sxs-lookup"><span data-stu-id="5736a-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5736a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5736a-111">Requirements</span></span>  

 <span data-ttu-id="5736a-112">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5736a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5736a-113">**Encabezado:** Cordebug. idl</span><span class="sxs-lookup"><span data-stu-id="5736a-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="5736a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5736a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5736a-115">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5736a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5736a-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5736a-116">See also</span></span>

- [<span data-ttu-id="5736a-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="5736a-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="5736a-118">Estructuras de depuración</span><span class="sxs-lookup"><span data-stu-id="5736a-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5736a-119">Depuración</span><span class="sxs-lookup"><span data-stu-id="5736a-119">Debugging</span></span>](index.md)
