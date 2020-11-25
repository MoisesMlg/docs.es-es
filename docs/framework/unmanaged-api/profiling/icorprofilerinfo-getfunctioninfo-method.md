---
title: ICorProfilerInfo::GetFunctionInfo (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 6aaa02d72dd10fe72d773246d55216143786dabb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722552"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="85ef1-102">ICorProfilerInfo::GetFunctionInfo (Método)</span><span class="sxs-lookup"><span data-stu-id="85ef1-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>

<span data-ttu-id="85ef1-103">Obtiene la clase primaria y el token de metadatos para la función especificada.</span><span class="sxs-lookup"><span data-stu-id="85ef1-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ef1-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="85ef1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85ef1-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="85ef1-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="85ef1-106">de IDENTIFICADOR de la función para la que se va a obtener la clase primaria y el token de metadatos.</span><span class="sxs-lookup"><span data-stu-id="85ef1-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="85ef1-107">[out] Puntero a la clase primaria de la función.</span><span class="sxs-lookup"><span data-stu-id="85ef1-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="85ef1-108">[out] Puntero al módulo en el que se define la clase primaria de la función.</span><span class="sxs-lookup"><span data-stu-id="85ef1-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="85ef1-109">[out] Puntero al token de metadatos para la función.</span><span class="sxs-lookup"><span data-stu-id="85ef1-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85ef1-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="85ef1-110">Remarks</span></span>  

 <span data-ttu-id="85ef1-111">El código del generador de perfiles puede llamar a [ICorProfilerInfo:: GetModuleMetaData (](icorprofilerinfo-getmodulemetadata-method.md) para obtener una interfaz de metadatos para un módulo determinado.</span><span class="sxs-lookup"><span data-stu-id="85ef1-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="85ef1-112">Después, el token de metadatos que se devuelve a la ubicación a la que `pToken` hace referencia puede usarse para acceder a los metadatos de la función.</span><span class="sxs-lookup"><span data-stu-id="85ef1-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="85ef1-113">`ClassID`Es posible que el de una función de una clase genérica no se pueda obtener sin más información contextual sobre el uso de la función.</span><span class="sxs-lookup"><span data-stu-id="85ef1-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="85ef1-114">En este caso, será `pClassId` 0.</span><span class="sxs-lookup"><span data-stu-id="85ef1-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="85ef1-115">El código del generador de perfiles debe usar [ICorProfilerInfo2:: getfunctioninfo2 (](icorprofilerinfo2-getfunctioninfo2-method.md) con un valor COR_PRF_FRAME_INFO para proporcionar más contexto.</span><span class="sxs-lookup"><span data-stu-id="85ef1-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85ef1-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85ef1-116">Requirements</span></span>  

 <span data-ttu-id="85ef1-117">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85ef1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ef1-118">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85ef1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85ef1-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85ef1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85ef1-120">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ef1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ef1-121">Consulte también</span><span class="sxs-lookup"><span data-stu-id="85ef1-121">See also</span></span>

- [<span data-ttu-id="85ef1-122">ICorProfilerInfo (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="85ef1-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
