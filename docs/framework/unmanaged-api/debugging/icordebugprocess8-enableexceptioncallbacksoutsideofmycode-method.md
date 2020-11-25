---
title: Método de ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 750d2a2d69c74e147c34c9c496079ee48ac04b42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732546"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="1b842-102">Método de ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode</span><span class="sxs-lookup"><span data-stu-id="1b842-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>

<span data-ttu-id="1b842-103">[Se admite en el .NET Framework 4,6 y versiones posteriores]</span><span class="sxs-lookup"><span data-stu-id="1b842-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="1b842-104">Habilita o deshabilita determinados tipos de devoluciones de llamada de excepción de [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1b842-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b842-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1b842-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b842-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1b842-106">Parameters</span></span>  

 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="1b842-107">[in]</span><span class="sxs-lookup"><span data-stu-id="1b842-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b842-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="1b842-108">Remarks</span></span>  

 <span data-ttu-id="1b842-109">Si el valor de `enableExceptionsOutsideOfJMC` es `false`:</span><span class="sxs-lookup"><span data-stu-id="1b842-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="1b842-110">Una excepción DEBUG_EXCEPTION_FIRST_CHANCE no generará una devolución de llamada al depurador.</span><span class="sxs-lookup"><span data-stu-id="1b842-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="1b842-111">Una excepción DEBUG_EXCEPTION_CATCH_HANDLER_FOUND no generará una devolución de llamada al depurador si la excepción nunca se convierte en código de usuario (es decir, la ruta de acceso desde el origen de una excepción al controlador de excepciones no tiene métodos marcados como JustMyCode o JMC).</span><span class="sxs-lookup"><span data-stu-id="1b842-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="1b842-112">El valor predeterminado de `enableExceptionsOutsideOfJMC` es `true`.</span><span class="sxs-lookup"><span data-stu-id="1b842-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b842-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b842-113">Requirements</span></span>  

 <span data-ttu-id="1b842-114">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b842-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b842-115">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b842-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b842-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b842-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b842-117">**.NET Framework versiones:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b842-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b842-118">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1b842-118">See also</span></span>

- [<span data-ttu-id="1b842-119">Interfaz de ICorDebugProcess8</span><span class="sxs-lookup"><span data-stu-id="1b842-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="1b842-120">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="1b842-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
