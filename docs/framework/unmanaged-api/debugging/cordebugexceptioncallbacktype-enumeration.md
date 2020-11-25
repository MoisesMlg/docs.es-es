---
title: CorDebugExceptionCallbackType (Enumeración)
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: cddcf66939a2ae7ab9e7f63a6fd61b72c56f6c7a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712734"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="893a9-102">CorDebugExceptionCallbackType (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="893a9-102">CorDebugExceptionCallbackType Enumeration</span></span>

<span data-ttu-id="893a9-103">Indica el tipo de devolución de llamada que se realiza desde un evento [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="893a9-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="893a9-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="893a9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="893a9-105">Miembros</span><span class="sxs-lookup"><span data-stu-id="893a9-105">Members</span></span>  
  
|<span data-ttu-id="893a9-106">Miembro</span><span class="sxs-lookup"><span data-stu-id="893a9-106">Member</span></span>|<span data-ttu-id="893a9-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="893a9-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="893a9-108">Se ha producido una excepción.</span><span class="sxs-lookup"><span data-stu-id="893a9-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="893a9-109">El proceso Windup de la excepción entró en el código de usuario.</span><span class="sxs-lookup"><span data-stu-id="893a9-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="893a9-110">El proceso Windup de excepción encontró un `catch` bloque en el código de usuario.</span><span class="sxs-lookup"><span data-stu-id="893a9-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="893a9-111">No se controló la excepción.</span><span class="sxs-lookup"><span data-stu-id="893a9-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="893a9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="893a9-112">Requirements</span></span>  

 <span data-ttu-id="893a9-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="893a9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="893a9-114">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="893a9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="893a9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="893a9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="893a9-116">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="893a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893a9-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="893a9-117">See also</span></span>

- [<span data-ttu-id="893a9-118">Enumeraciones de depuración</span><span class="sxs-lookup"><span data-stu-id="893a9-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
