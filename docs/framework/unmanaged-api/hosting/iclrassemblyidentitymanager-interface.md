---
title: ICLRAssemblyIdentityManager (Interfaz)
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: 41d049c931091d2cc0b41bd1e9d74b3c15d7878d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679265"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="2a0b8-102">ICLRAssemblyIdentityManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2a0b8-102">ICLRAssemblyIdentityManager Interface</span></span>

<span data-ttu-id="2a0b8-103">Proporciona métodos que admiten la comunicación entre el host y el Common Language Runtime (CLR) acerca de los ensamblados.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a0b8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2a0b8-104">Methods</span></span>  
  
|<span data-ttu-id="2a0b8-105">Método</span><span class="sxs-lookup"><span data-stu-id="2a0b8-105">Method</span></span>|<span data-ttu-id="2a0b8-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="2a0b8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a0b8-107">Método GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="2a0b8-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="2a0b8-108">Obtiene los datos de enlace de identidad del ensamblado en la ruta de acceso de archivo especificada.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="2a0b8-109">Método GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="2a0b8-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="2a0b8-110">Obtiene los datos de identidad del ensamblado canónico para el ensamblado en la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="2a0b8-111">Método GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="2a0b8-111">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="2a0b8-112">Obtiene una instancia de [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) de la lista proporcionada de identidades de ensamblado parciales.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="2a0b8-113">Método GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="2a0b8-113">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="2a0b8-114">Obtiene un enumerador [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) para las identidades de ensamblado a las que hace referencia el ensamblado con la identidad especificada.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="2a0b8-115">Método GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="2a0b8-115">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="2a0b8-116">Obtiene una instancia de [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) que contiene una lista de ensamblados a los que hace referencia el ensamblado en la ruta de acceso de archivo especificada.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="2a0b8-117">Método GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="2a0b8-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="2a0b8-118">Obtiene un puntero a un `ICLRReferenceAssemblyEnum` objeto que contiene datos de identidad de ensamblado para los ensamblados a los que hace referencia el ensamblado en la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="2a0b8-119">Método IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="2a0b8-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="2a0b8-120">Obtiene un valor que indica si el ensamblado especificado tiene un nombre seguro.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a0b8-121">Comentarios</span><span class="sxs-lookup"><span data-stu-id="2a0b8-121">Remarks</span></span>  

 <span data-ttu-id="2a0b8-122">Utilice `ICLRAssemblyIdentityManager` para obtener instancias de `ICLRAssemblyReferenceList` y para enumerar las identidades de ensamblado.</span><span class="sxs-lookup"><span data-stu-id="2a0b8-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a0b8-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a0b8-123">Requirements</span></span>  

 <span data-ttu-id="2a0b8-124">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a0b8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a0b8-125">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a0b8-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a0b8-126">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a0b8-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a0b8-127">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a0b8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0b8-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2a0b8-128">See also</span></span>

- [<span data-ttu-id="2a0b8-129">ICLRAssemblyReferenceList (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2a0b8-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2a0b8-130">ICLRProbingAssemblyEnum (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2a0b8-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="2a0b8-131">Interfaces de hospedaje</span><span class="sxs-lookup"><span data-stu-id="2a0b8-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
