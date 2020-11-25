---
title: ICorDebug::DebugActiveProcess (Método)
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 1713623fa575bea6df649106b37212f7aeaee6db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723472"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="e9f2e-102">ICorDebug::DebugActiveProcess (Método)</span><span class="sxs-lookup"><span data-stu-id="e9f2e-102">ICorDebug::DebugActiveProcess Method</span></span>

<span data-ttu-id="e9f2e-103">Asocia el depurador a un proceso existente.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f2e-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e9f2e-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9f2e-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e9f2e-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="e9f2e-106">de IDENTIFICADOR del proceso al que se va a adjuntar el depurador.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="e9f2e-107">de Valor booleano que se establece en `true` si el depurador debe comportarse como el depurador de Win32 para el proceso y enviar las devoluciones de llamada no administradas; de lo contrario, `false` .</span><span class="sxs-lookup"><span data-stu-id="e9f2e-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e9f2e-108">enuncia Puntero a la dirección de un objeto "ICorDebugProcess" que representa el proceso al que se ha adjuntado el depurador.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9f2e-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="e9f2e-109">Remarks</span></span>  

 <span data-ttu-id="e9f2e-110">No se admite la depuración de interoperabilidad en las plataformas Win9x y no x86, como las plataformas basadas en IA-64 y AMD64.</span><span class="sxs-lookup"><span data-stu-id="e9f2e-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9f2e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9f2e-111">Requirements</span></span>  

 <span data-ttu-id="e9f2e-112">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9f2e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f2e-113">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9f2e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9f2e-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9f2e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9f2e-115">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9f2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f2e-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e9f2e-116">See also</span></span>

- [<span data-ttu-id="e9f2e-117">ICorDebug (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="e9f2e-117">ICorDebug Interface</span></span>](icordebug-interface.md)
