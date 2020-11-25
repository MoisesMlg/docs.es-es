---
title: ICorDebugManagedCallback3 (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: e04f5be6d2612b26bf7d71807753d170e6a5a7a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723303"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="3a435-102">ICorDebugManagedCallback3 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="3a435-102">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="3a435-103">Proporciona un método de devolución de llamada que indica que se ha producido una notificación del depurador personalizada habilitada.</span><span class="sxs-lookup"><span data-stu-id="3a435-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a435-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a435-104">Methods</span></span>  
  
|<span data-ttu-id="3a435-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a435-105">Method</span></span>|<span data-ttu-id="3a435-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="3a435-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a435-107">Método CustomNotification</span><span class="sxs-lookup"><span data-stu-id="3a435-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="3a435-108">Indica que se ha generado una notificación de depurador personalizada habilitada.</span><span class="sxs-lookup"><span data-stu-id="3a435-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a435-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="3a435-109">Remarks</span></span>  

 <span data-ttu-id="3a435-110">Esta interfaz es una extensión lógica de las interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) e [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3a435-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a435-111">Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.</span><span class="sxs-lookup"><span data-stu-id="3a435-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a435-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a435-112">Requirements</span></span>  

 <span data-ttu-id="3a435-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a435-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a435-114">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a435-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a435-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a435-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a435-116">**.NET Framework versiones:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a435-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a435-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3a435-117">See also</span></span>

- [<span data-ttu-id="3a435-118">ICorDebugManagedCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="3a435-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="3a435-119">ICorDebugManagedCallback2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="3a435-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="3a435-120">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="3a435-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3a435-121">Depuración</span><span class="sxs-lookup"><span data-stu-id="3a435-121">Debugging</span></span>](index.md)
