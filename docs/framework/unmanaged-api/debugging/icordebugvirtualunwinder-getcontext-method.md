---
title: ICorDebugVirtualUnwinder::GetContext (método)
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: a5a1afa47e52eff7c930698a3354a03d8c62259f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679460"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="65a4f-102">ICorDebugVirtualUnwinder::GetContext (método)</span><span class="sxs-lookup"><span data-stu-id="65a4f-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>

<span data-ttu-id="65a4f-103">Obtiene el contexto actual de este responsable del desenredado.</span><span class="sxs-lookup"><span data-stu-id="65a4f-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65a4f-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="65a4f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65a4f-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="65a4f-105">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="65a4f-106">[in] Marcas que indican qué partes del contexto se devuelven (definidas en WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="65a4f-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="65a4f-107">[in] Número de bytes en `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="65a4f-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="65a4f-108">[out] Puntero al número de bytes escritos realmente en `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="65a4f-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="65a4f-109">[out] Matriz de bytes que contiene el contexto actual de este responsable del desenredado.</span><span class="sxs-lookup"><span data-stu-id="65a4f-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65a4f-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="65a4f-110">Return Value</span></span>  

 <span data-ttu-id="65a4f-111">Cualquier valor HRESULT de error recibido por mscordbi es irrecuperable y hará que las API ICorDebug devuelvan `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="65a4f-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65a4f-112">Comentarios</span><span class="sxs-lookup"><span data-stu-id="65a4f-112">Remarks</span></span>  

 <span data-ttu-id="65a4f-113">Establezca el valor inicial del `contextBuf` argumento en el búfer de contexto devuelto mediante una llamada al método [ICorDebugStackWalk:: getContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="65a4f-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65a4f-114">Este método solo está disponible con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="65a4f-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="65a4f-115">Dado que es posible que el desenredado solo restaure un subconjunto de los registros, por ejemplo, solo los registros no volátiles, puede que el contexto no coincida exactamente con el estado del registro en el momento de la llamada al método real.</span><span class="sxs-lookup"><span data-stu-id="65a4f-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65a4f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65a4f-116">Requirements</span></span>  

 <span data-ttu-id="65a4f-117">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65a4f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65a4f-118">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65a4f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65a4f-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65a4f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65a4f-120">**.NET Framework versiones:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65a4f-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a4f-121">Consulte también</span><span class="sxs-lookup"><span data-stu-id="65a4f-121">See also</span></span>

- [<span data-ttu-id="65a4f-122">Método ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="65a4f-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="65a4f-123">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="65a4f-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
