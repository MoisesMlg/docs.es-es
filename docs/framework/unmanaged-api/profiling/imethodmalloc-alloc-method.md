---
title: IMethodMalloc::Alloc (Método)
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: 58809f12e4dd4419b754caafc3f8b883b8bc5089
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721171"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="38d6c-102">IMethodMalloc::Alloc (Método)</span><span class="sxs-lookup"><span data-stu-id="38d6c-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="38d6c-103">Intenta asignar una cantidad de memoria especificada para un nuevo cuerpo de la función del lenguaje intermedio de Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="38d6c-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="38d6c-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="38d6c-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="38d6c-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="38d6c-105">Parameters</span></span>

`cb`\
<span data-ttu-id="38d6c-106">de Número de bytes que se van a asignar para el cuerpo del método.</span><span class="sxs-lookup"><span data-stu-id="38d6c-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="38d6c-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="38d6c-107">Remarks</span></span>

 <span data-ttu-id="38d6c-108">La memoria asignada comenzará en una dirección mayor que la dirección base del módulo que está asociado a este asignador.</span><span class="sxs-lookup"><span data-stu-id="38d6c-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="38d6c-109">En otras palabras, cada asignador se crea para un módulo determinado e intentará asignar memoria en un desplazamiento positivo desde su dirección base.</span><span class="sxs-lookup"><span data-stu-id="38d6c-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="38d6c-110">Si `Alloc` no puede asignar el número solicitado de bytes en una dirección mayor que la dirección base del módulo, devuelve E_OUTOFMEMORY, independientemente de la cantidad real de espacio de memoria disponible.</span><span class="sxs-lookup"><span data-stu-id="38d6c-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="38d6c-111">El `Alloc` método se debe usar junto con el método [ICorProfilerInfo:: SetILFunctionBody (](icorprofilerinfo-setilfunctionbody-method.md) .</span><span class="sxs-lookup"><span data-stu-id="38d6c-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="38d6c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38d6c-112">Requirements</span></span>

 <span data-ttu-id="38d6c-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d6c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="38d6c-114">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38d6c-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="38d6c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38d6c-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="38d6c-116">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d6c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="38d6c-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="38d6c-117">See also</span></span>

- [<span data-ttu-id="38d6c-118">IMethodMalloc (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="38d6c-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
