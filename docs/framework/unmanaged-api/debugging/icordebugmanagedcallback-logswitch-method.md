---
title: ICorDebugManagedCallback::LogSwitch (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: db6ccd63bbeadd7dcff1c7f8491b59017d431d12
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720703"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="e7af2-102">ICorDebugManagedCallback::LogSwitch (Método)</span><span class="sxs-lookup"><span data-stu-id="e7af2-102">ICorDebugManagedCallback::LogSwitch Method</span></span>

<span data-ttu-id="e7af2-103">Notifica al depurador que un subproceso administrado Common Language Runtime (CLR) ha llamado a un método en la <xref:System.Diagnostics.Switch> clase para crear, modificar o eliminar un modificador de depuración o traza.</span><span class="sxs-lookup"><span data-stu-id="e7af2-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7af2-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e7af2-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7af2-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e7af2-105">Parameters</span></span>  

 `PAppDomain`  
 <span data-ttu-id="e7af2-106">de Un puntero a un objeto ICorDebugAppDomain que representa el dominio de aplicación que contiene el subproceso administrado que creó, modificó o eliminó un modificador de depuración/seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e7af2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e7af2-107">de Un puntero a un objeto ICorDebugThread que representa el subproceso administrado.</span><span class="sxs-lookup"><span data-stu-id="e7af2-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="e7af2-108">de Valor que indica el nivel de gravedad del mensaje descriptivo que se escribió en el registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="e7af2-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="e7af2-109">de Un valor de la enumeración [logswitchcallreason (](logswitchcallreason-enumeration.md) que indica la operación realizada en el modificador de depuración/seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e7af2-109">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="e7af2-110">de Puntero al nombre del modificador de depuración/seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e7af2-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="e7af2-111">de Puntero al nombre del elemento primario del modificador de depuración/seguimiento.</span><span class="sxs-lookup"><span data-stu-id="e7af2-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7af2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e7af2-112">Requirements</span></span>  

 <span data-ttu-id="e7af2-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7af2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7af2-114">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7af2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7af2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7af2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7af2-116">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7af2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7af2-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e7af2-117">See also</span></span>

- [<span data-ttu-id="e7af2-118">ICorDebugManagedCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="e7af2-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
