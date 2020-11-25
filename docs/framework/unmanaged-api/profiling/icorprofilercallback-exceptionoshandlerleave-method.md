---
title: ICorProfilerCallback::ExceptionOSHandlerLeave (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: 37e3c9139a202e3cb31bd824d182389ae10b7389
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699942"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="5ca3b-102">ICorProfilerCallback::ExceptionOSHandlerLeave (Método)</span><span class="sxs-lookup"><span data-stu-id="5ca3b-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="5ca3b-103">Sin implementar.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-103">Not implemented.</span></span> <span data-ttu-id="5ca3b-104">Un generador de perfiles que necesita información de excepción no administrada debe obtener esta información a través de otros medios.</span><span class="sxs-lookup"><span data-stu-id="5ca3b-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca3b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5ca3b-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5ca3b-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ca3b-106">Requirements</span></span>  

 <span data-ttu-id="5ca3b-107">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ca3b-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ca3b-108">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ca3b-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ca3b-109">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ca3b-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ca3b-110">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ca3b-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca3b-111">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5ca3b-111">See also</span></span>

- [<span data-ttu-id="5ca3b-112">ICorProfilerCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="5ca3b-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
