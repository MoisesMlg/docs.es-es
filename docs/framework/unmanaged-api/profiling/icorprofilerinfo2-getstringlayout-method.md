---
title: ICorProfilerInfo2::GetStringLayout (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: d141a78a953d4e0ab922535ad2363c79f2e18ecd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727047"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="77d40-102">ICorProfilerInfo2::GetStringLayout (Método)</span><span class="sxs-lookup"><span data-stu-id="77d40-102">ICorProfilerInfo2::GetStringLayout Method</span></span>

<span data-ttu-id="77d40-103">Obtiene información sobre la distribución de un objeto de cadena.</span><span class="sxs-lookup"><span data-stu-id="77d40-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="77d40-104">Este método está en desuso en el .NET Framework 4 y se ha sustituido por el método [ICorProfilerInfo3:: GetStringLayout2 (](icorprofilerinfo3-getstringlayout2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="77d40-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d40-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="77d40-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77d40-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="77d40-106">Parameters</span></span>  

 `pBufferLengthOffset`  
 <span data-ttu-id="77d40-107">enuncia Puntero al desplazamiento de la ubicación, en relación con el `ObjectID` puntero, que almacena la longitud de la cadena.</span><span class="sxs-lookup"><span data-stu-id="77d40-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="77d40-108">La longitud se almacena como un `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="77d40-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77d40-109">Este parámetro devuelve la longitud de la cadena en sí, no la longitud del búfer.</span><span class="sxs-lookup"><span data-stu-id="77d40-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="77d40-110">La longitud del búfer ya no está disponible.</span><span class="sxs-lookup"><span data-stu-id="77d40-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="77d40-111">enuncia Puntero al desplazamiento de la ubicación, en relación con el `ObjectID` puntero, que almacena la longitud de la propia cadena.</span><span class="sxs-lookup"><span data-stu-id="77d40-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="77d40-112">La longitud se almacena como un `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="77d40-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="77d40-113">enuncia Puntero al desplazamiento del búfer, relativo al `ObjectID` puntero, que almacena la cadena de caracteres anchos.</span><span class="sxs-lookup"><span data-stu-id="77d40-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d40-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="77d40-114">Remarks</span></span>  

 <span data-ttu-id="77d40-115">El `GetStringLayout` método obtiene los desplazamientos, con relación al `ObjectID` puntero, de las ubicaciones en las que se almacenan los elementos siguientes:</span><span class="sxs-lookup"><span data-stu-id="77d40-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="77d40-116">Longitud del búfer de la cadena.</span><span class="sxs-lookup"><span data-stu-id="77d40-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="77d40-117">La longitud de la propia cadena.</span><span class="sxs-lookup"><span data-stu-id="77d40-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="77d40-118">Búfer que contiene la cadena real de caracteres anchos.</span><span class="sxs-lookup"><span data-stu-id="77d40-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="77d40-119">Las cadenas pueden terminar en NULL.</span><span class="sxs-lookup"><span data-stu-id="77d40-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d40-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77d40-120">Requirements</span></span>  

 <span data-ttu-id="77d40-121">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d40-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d40-122">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77d40-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77d40-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77d40-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77d40-124">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d40-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d40-125">Consulte también</span><span class="sxs-lookup"><span data-stu-id="77d40-125">See also</span></span>

- [<span data-ttu-id="77d40-126">ICorProfilerInfo (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="77d40-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="77d40-127">ICorProfilerInfo2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="77d40-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
