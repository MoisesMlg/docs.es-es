---
title: ICorProfilerCallback::ModuleUnloadFinished (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 514c20455b95ecf74ffaecd349982fd8f8f49816
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723238"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="71f3f-102">ICorProfilerCallback::ModuleUnloadFinished (Método)</span><span class="sxs-lookup"><span data-stu-id="71f3f-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>

<span data-ttu-id="71f3f-103">Notifica al generador de perfiles que un módulo ha terminado de descargarse.</span><span class="sxs-lookup"><span data-stu-id="71f3f-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f3f-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="71f3f-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71f3f-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="71f3f-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="71f3f-106">de IDENTIFICADOR del módulo que se ha descargado.</span><span class="sxs-lookup"><span data-stu-id="71f3f-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="71f3f-107">de HRESULT que indica si el módulo se ha descargado correctamente.</span><span class="sxs-lookup"><span data-stu-id="71f3f-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71f3f-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="71f3f-108">Remarks</span></span>  

 <span data-ttu-id="71f3f-109">El valor de `moduleId` no es válido para una solicitud de información después de que el método [ICorProfilerCallback:: ModuleUnloadStarted (](icorprofilercallback-moduleunloadstarted-method.md) devuelva.</span><span class="sxs-lookup"><span data-stu-id="71f3f-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="71f3f-110">Algunas partes de la descarga de la clase podrían continuar después de la `ModuleUnloadFinished` devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="71f3f-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="71f3f-111">Un valor HRESULT de error en `hrStatus` indica un error.</span><span class="sxs-lookup"><span data-stu-id="71f3f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="71f3f-112">Sin embargo, un valor HRESULT correcto en `hrStatus` indica solo que la primera parte de la descarga del módulo se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="71f3f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f3f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71f3f-113">Requirements</span></span>  

 <span data-ttu-id="71f3f-114">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71f3f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f3f-115">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="71f3f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="71f3f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71f3f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71f3f-117">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f3f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f3f-118">Consulte también</span><span class="sxs-lookup"><span data-stu-id="71f3f-118">See also</span></span>

- [<span data-ttu-id="71f3f-119">ICorProfilerCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="71f3f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
