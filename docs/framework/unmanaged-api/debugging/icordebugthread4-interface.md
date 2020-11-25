---
title: ICorDebugThread4 (Interfaz)
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 5c108420772be9e6d0932f3759f18da9446f99d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727944"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="c9027-102">ICorDebugThread4 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="c9027-102">ICorDebugThread4 Interface</span></span>

<span data-ttu-id="c9027-103">Proporciona información de bloqueo de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="c9027-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9027-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c9027-104">Methods</span></span>  
  
|<span data-ttu-id="c9027-105">Método</span><span class="sxs-lookup"><span data-stu-id="c9027-105">Method</span></span>|<span data-ttu-id="c9027-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="c9027-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9027-107">Método GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="c9027-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="c9027-108">Proporciona una enumeración ordenada de las estructuras [CorDebugBlockingObject](cordebugblockingobject-structure.md) que proporcionan información de bloqueo de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="c9027-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="c9027-109">Método HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="c9027-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="c9027-110">Indica si el subproceso ha tenido alguna vez una excepción no controlada.</span><span class="sxs-lookup"><span data-stu-id="c9027-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="c9027-111">Método GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="c9027-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="c9027-112">Obtiene el objeto [ICorDebugManagedCallback3 (:: customnotification (](icordebugmanagedcallback3-customnotification-method.md) actual en el subproceso actual.</span><span class="sxs-lookup"><span data-stu-id="c9027-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9027-113">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c9027-113">Remarks</span></span>  

 <span data-ttu-id="c9027-114">Esta interfaz es una extensión lógica de las interfaces ICorDebugThread, ICorDebugThread2 y [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c9027-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9027-115">Esta interfaz no admite que se la llame de forma remota, ya sea entre procesos o entre equipos.</span><span class="sxs-lookup"><span data-stu-id="c9027-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9027-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9027-116">Requirements</span></span>  

 <span data-ttu-id="c9027-117">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9027-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9027-118">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9027-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9027-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9027-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9027-120">**.NET Framework versiones:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9027-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9027-121">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c9027-121">See also</span></span>

- [<span data-ttu-id="c9027-122">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="c9027-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c9027-123">Depuración</span><span class="sxs-lookup"><span data-stu-id="c9027-123">Debugging</span></span>](index.md)
