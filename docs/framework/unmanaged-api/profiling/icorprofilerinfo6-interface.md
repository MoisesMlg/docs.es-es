---
title: Interfaz ICorProfilerInfo6
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: b3aed97e19694675fd5e0c1070dbbf6d9321eedd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733846"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="ee138-102">Interfaz ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="ee138-102">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="ee138-103">[Se admite en el .NET Framework 4,6 y versiones posteriores]</span><span class="sxs-lookup"><span data-stu-id="ee138-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="ee138-104">Una subclase de [ICorProfilerInfo5](icorprofilerinfo5-interface.md) que proporciona un enumerador para todos los métodos que se definen en un módulo Ngen determinado e insertan un método determinado.</span><span class="sxs-lookup"><span data-stu-id="ee138-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee138-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ee138-105">Methods</span></span>  
  
|<span data-ttu-id="ee138-106">Método</span><span class="sxs-lookup"><span data-stu-id="ee138-106">Method</span></span>|<span data-ttu-id="ee138-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="ee138-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee138-108">Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="ee138-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="ee138-109">Devuelve un enumerador para todos los métodos que pertenecen a un módulo NGen determinado y que están insertados en el cuerpo de un método determinado.</span><span class="sxs-lookup"><span data-stu-id="ee138-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee138-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee138-110">Requirements</span></span>  

 <span data-ttu-id="ee138-111">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee138-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee138-112">**Encabezado:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee138-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee138-113">**.NET Framework versiones:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee138-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee138-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ee138-114">See also</span></span>

- [<span data-ttu-id="ee138-115">Interfaces para generación de perfiles</span><span class="sxs-lookup"><span data-stu-id="ee138-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
