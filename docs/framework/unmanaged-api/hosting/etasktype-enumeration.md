---
title: ETaskType (Enumeración)
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 332488fee4c982fdbaecceeaa2a6a3876f1602a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733703"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="ffa4c-102">ETaskType (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="ffa4c-102">ETaskType Enumeration</span></span>

<span data-ttu-id="ffa4c-103">Contiene valores que indican el tipo de tarea que está representada por una interfaz [ICLRTask](iclrtask-interface.md) o [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ffa4c-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffa4c-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ffa4c-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="ffa4c-105">Miembros</span><span class="sxs-lookup"><span data-stu-id="ffa4c-105">Members</span></span>  
  
|<span data-ttu-id="ffa4c-106">Miembro</span><span class="sxs-lookup"><span data-stu-id="ffa4c-106">Member</span></span>|<span data-ttu-id="ffa4c-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="ffa4c-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="ffa4c-108">La interfaz representa una tarea de descarga de dominio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="ffa4c-109">La interfaz representa una tarea auxiliar del depurador.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="ffa4c-110">La interfaz representa una tarea de finalizador.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="ffa4c-111">La interfaz representa una tarea de recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="ffa4c-112">La interfaz representa una tarea de subproceso de puerta.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="ffa4c-113">La interfaz representa una tarea de subproceso de e/s o una tarea de subproceso de puerto de finalización.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="ffa4c-114">La interfaz representa una tarea de subproceso de temporizador.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="ffa4c-115">La interfaz representa una tarea de subproceso de espera.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="ffa4c-116">La interfaz representa una tarea de subproceso de trabajo.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="ffa4c-117">La tarea es desconocida.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="ffa4c-118">La interfaz representa una tarea de usuario.</span><span class="sxs-lookup"><span data-stu-id="ffa4c-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ffa4c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffa4c-119">Requirements</span></span>  

 <span data-ttu-id="ffa4c-120">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffa4c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffa4c-121">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ffa4c-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffa4c-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffa4c-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffa4c-123">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffa4c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa4c-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ffa4c-124">See also</span></span>

- [<span data-ttu-id="ffa4c-125">Enumeraciones para hosts</span><span class="sxs-lookup"><span data-stu-id="ffa4c-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
