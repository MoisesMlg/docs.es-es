---
title: ICorProfilerInfo2::GetCodeInfo2 (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: e88fe1b3c93ca278d0e64a5eb3274c86bd8f0f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727138"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="7c514-102">ICorProfilerInfo2::GetCodeInfo2 (Método)</span><span class="sxs-lookup"><span data-stu-id="7c514-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>

<span data-ttu-id="7c514-103">Obtiene las extensiones del código nativo asociado al `FunctionID` especificado.</span><span class="sxs-lookup"><span data-stu-id="7c514-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c514-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="7c514-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c514-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7c514-105">Parameters</span></span>  

 `functionID`  
 <span data-ttu-id="7c514-106">[in] Identificador de función con la que está asociado el código nativo.</span><span class="sxs-lookup"><span data-stu-id="7c514-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="7c514-107">[in] Tamaño de la matriz `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="7c514-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="7c514-108">enuncia Puntero al número total de estructuras de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponibles.</span><span class="sxs-lookup"><span data-stu-id="7c514-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="7c514-109">[out] Búfer proporcionado por el llamador.</span><span class="sxs-lookup"><span data-stu-id="7c514-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="7c514-110">Después de que el método vuelva, contiene una matriz de estructuras `COR_PRF_CODE_INFO`, cada una de las cuales describe un bloque de código nativo.</span><span class="sxs-lookup"><span data-stu-id="7c514-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c514-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="7c514-111">Remarks</span></span>  

 <span data-ttu-id="7c514-112">Las extensiones se clasifican por orden de desplazamiento creciente del lenguaje intermedio de Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="7c514-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="7c514-113">Después de la devolución de `GetCodeInfo2`, debe comprobar que el búfer `codeInfos` era lo suficientemente grande como para contener todas las estructuras `COR_PRF_CODE_INFO`.</span><span class="sxs-lookup"><span data-stu-id="7c514-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="7c514-114">Para ello, compare el valor de `cCodeInfos` con el valor del parámetro `cchName`.</span><span class="sxs-lookup"><span data-stu-id="7c514-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="7c514-115">Si `cCodeInfos` dividido entre el tamaño de una estructura `COR_PRF_CODE_INFO` es menor que `pcCodeInfos`, asigne un búfer `codeInfos` mayor, actualice `cCodeInfos` con el nuevo tamaño de mayores dimensiones y vuelva a llamar a `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="7c514-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="7c514-116">También tiene la opción de llamar primero a `GetCodeInfo2` con un búfer `codeInfos` de longitud de cero para obtener el tamaño de búfer correcto.</span><span class="sxs-lookup"><span data-stu-id="7c514-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7c514-117">A continuación, puede establecer el tamaño del búfer `codeInfos` para el valor devuelto en `pcCodeInfos` multiplicándolo por el tamaño de una estructura `COR_PRF_CODE_INFO` y volver a llamar a `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="7c514-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c514-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c514-118">Requirements</span></span>  

 <span data-ttu-id="7c514-119">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c514-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c514-120">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c514-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c514-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c514-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c514-122">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c514-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c514-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7c514-123">See also</span></span>

- [<span data-ttu-id="7c514-124">Método GetCodeInfo3</span><span class="sxs-lookup"><span data-stu-id="7c514-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="7c514-125">ICorProfilerInfo2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="7c514-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="7c514-126">Interfaces para generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="7c514-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7c514-127">Generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="7c514-127">Profiling</span></span>](index.md)
