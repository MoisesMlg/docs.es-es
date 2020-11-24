---
title: Método ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 56795c6879d95253383c26c92e060f252a018914
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690218"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="40045-102">Método ICorDebugProcess6::EnableVirtualModuleSplitting</span><span class="sxs-lookup"><span data-stu-id="40045-102">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>

<span data-ttu-id="40045-103">Habilita o deshabilita la división de módulos virtuales.</span><span class="sxs-lookup"><span data-stu-id="40045-103">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40045-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="40045-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40045-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="40045-105">Parameters</span></span>  

 `enableSplitting`  
 <span data-ttu-id="40045-106">`true` para habilitar la división de módulos virtuales; `false` para deshabilitarla.</span><span class="sxs-lookup"><span data-stu-id="40045-106">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40045-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="40045-107">Remarks</span></span>  

 <span data-ttu-id="40045-108">La división de módulos virtuales hace que [ICorDebug](icordebug-interface.md) reconozca los módulos que se combinaron durante el proceso de compilación y los presenta como un grupo de módulos independientes en lugar de un único módulo grande.</span><span class="sxs-lookup"><span data-stu-id="40045-108">Virtual module splitting causes [ICorDebug](icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="40045-109">Esto cambia el comportamiento de los diversos métodos [ICorDebug](icordebug-interface.md) descritos a continuación.</span><span class="sxs-lookup"><span data-stu-id="40045-109">Doing this changes the behavior of various [ICorDebug](icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40045-110">Este método solo está disponible con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40045-110">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="40045-111">Puede llamar a este método y cambiar el valor de `enableSplitting` en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="40045-111">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="40045-112">No provoca ningún cambio funcional con estado en un objeto [ICorDebug](icordebug-interface.md) , a excepción de la modificación del comportamiento de los métodos enumerados en las secciones [División de módulos virtuales y API de depuración no administradas](#APIs) en el momento en que se llaman.</span><span class="sxs-lookup"><span data-stu-id="40045-112">It does not cause any stateful functional changes in an [ICorDebug](icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="40045-113">El uso de módulos virtuales hace que el rendimiento disminuya cuando se llama a estos métodos.</span><span class="sxs-lookup"><span data-stu-id="40045-113">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="40045-114">Además, es posible que se necesite un almacenamiento en caché considerable de los metadatos virtualizados para implementar correctamente las API de [IMetaDataImport](../metadata/imetadataimport-interface.md) , y estas cachés se pueden conservar incluso después de que se haya desactivado la división de módulos virtuales.</span><span class="sxs-lookup"><span data-stu-id="40045-114">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="40045-115">Terminología</span><span class="sxs-lookup"><span data-stu-id="40045-115">Terminology</span></span>  

 <span data-ttu-id="40045-116">Los siguientes términos sirven para describir la división de módulos virtuales:</span><span class="sxs-lookup"><span data-stu-id="40045-116">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="40045-117">módulos de contenedor o contenedores</span><span class="sxs-lookup"><span data-stu-id="40045-117">container modules, or containers</span></span>  
 <span data-ttu-id="40045-118">Son los módulos agregados.</span><span class="sxs-lookup"><span data-stu-id="40045-118">The aggregate modules.</span></span>  
  
 <span data-ttu-id="40045-119">submódulos o módulos virtuales</span><span class="sxs-lookup"><span data-stu-id="40045-119">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="40045-120">Son los módulos incluidos en un contenedor.</span><span class="sxs-lookup"><span data-stu-id="40045-120">The modules found in a container.</span></span>  
  
 <span data-ttu-id="40045-121">módulos regulares</span><span class="sxs-lookup"><span data-stu-id="40045-121">regular modules</span></span>  
 <span data-ttu-id="40045-122">Módulos que no se han combinado en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="40045-122">Modules that were not merged at build time.</span></span> <span data-ttu-id="40045-123">No son ni módulos de contenedor ni submódulos.</span><span class="sxs-lookup"><span data-stu-id="40045-123">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="40045-124">Tanto los módulos de contenedor como los submódulos se representan mediante objetos de interfaz ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="40045-124">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="40045-125">Sin embargo, el comportamiento de la interfaz es ligeramente diferente en cada caso, como \<x-ref to section> se describe en la sección.</span><span class="sxs-lookup"><span data-stu-id="40045-125">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="40045-126">Módulos y ensamblados</span><span class="sxs-lookup"><span data-stu-id="40045-126">Modules and assemblies</span></span>  

 <span data-ttu-id="40045-127">En los escenarios donde se combinan ensamblados no se admiten ensamblados con varios módulos, por lo que hay una relación de uno a uno entre un módulo y un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="40045-127">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="40045-128">Cada objeto ICorDebugModule, independientemente de si representa a un módulo de contenedor o a un submódulo, se corresponde con un objeto ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="40045-128">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="40045-129">El método [ICorDebugModule:: getassembly (](icordebugmodule-getassembly-method.md) convierte el módulo en el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="40045-129">The [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="40045-130">Para asignar en la otra dirección, el método [ICorDebugAssembly:: enumeratemodules (](icordebugassembly-enumeratemodules-method.md) solo enumera 1 módulo.</span><span class="sxs-lookup"><span data-stu-id="40045-130">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="40045-131">Dado que ensamblado y módulo conforman un par estrechamente unido en este caso, los términos módulo y ensamblado se han convertido en prácticamente intercambiables.</span><span class="sxs-lookup"><span data-stu-id="40045-131">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="40045-132">Diferencias de comportamiento</span><span class="sxs-lookup"><span data-stu-id="40045-132">Behavioral differences</span></span>  

 <span data-ttu-id="40045-133">Los módulos del contenedor tienen los siguientes comportamientos y características:</span><span class="sxs-lookup"><span data-stu-id="40045-133">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="40045-134">Sus metadatos para todos los submódulos que lo conforman se combinan entre sí.</span><span class="sxs-lookup"><span data-stu-id="40045-134">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="40045-135">Sus nombres de tipo se pueden alterar.</span><span class="sxs-lookup"><span data-stu-id="40045-135">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="40045-136">El método [ICorDebugModule:: GetName](icordebugmodule-getname-method.md) devuelve la ruta de acceso a un módulo en disco.</span><span class="sxs-lookup"><span data-stu-id="40045-136">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="40045-137">El método [ICorDebugModule::FUL](icordebugmodule-getsize-method.md) devuelve el tamaño de la imagen.</span><span class="sxs-lookup"><span data-stu-id="40045-137">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="40045-138">El método ICorDebugAssembly3.EnumerateContainedAssemblies enumera los submódulos.</span><span class="sxs-lookup"><span data-stu-id="40045-138">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="40045-139">El método ICorDebugAssembly3.GetContainerAssembly devuelve `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="40045-139">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="40045-140">Los submódulos tienen los siguientes comportamientos y características:</span><span class="sxs-lookup"><span data-stu-id="40045-140">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="40045-141">Tienen un conjunto reducido de metadatos que corresponde únicamente al ensamblado original que se ha combinado.</span><span class="sxs-lookup"><span data-stu-id="40045-141">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="40045-142">Los nombres de los metadatos no se alteran.</span><span class="sxs-lookup"><span data-stu-id="40045-142">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="40045-143">Es improbable que los tokens de los metadatos coincidan con los tokens del ensamblado original antes de que combinarse en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="40045-143">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="40045-144">El método [ICorDebugModule:: GetName](icordebugmodule-getname-method.md) devuelve el nombre del ensamblado, no una ruta de acceso del archivo.</span><span class="sxs-lookup"><span data-stu-id="40045-144">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="40045-145">El método [ICorDebugModule::FUL](icordebugmodule-getsize-method.md) devuelve el tamaño original de la imagen sin combinar.</span><span class="sxs-lookup"><span data-stu-id="40045-145">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="40045-146">El método ICorDebugModule3.EnumerateContainedAssemblies devuelve `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="40045-146">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="40045-147">El método ICorDebugAssembly3.GetContainerAssembly devuelve el módulo contenedor.</span><span class="sxs-lookup"><span data-stu-id="40045-147">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="40045-148">Interfaces obtenidas de los módulos</span><span class="sxs-lookup"><span data-stu-id="40045-148">Interfaces retrieved from modules</span></span>  

 <span data-ttu-id="40045-149">Se pueden crear y recuperar diversas interfaces de los módulos.</span><span class="sxs-lookup"><span data-stu-id="40045-149">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="40045-150">Algunas son:</span><span class="sxs-lookup"><span data-stu-id="40045-150">Some of these include:</span></span>  
  
- <span data-ttu-id="40045-151">Un objeto ICorDebugClass, devuelto por el método [ICorDebugModule:: GetClassFromToken (](icordebugmodule-getclassfromtoken-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40045-151">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="40045-152">Un objeto ICorDebugAssembly, devuelto por el método [ICorDebugModule:: getassembly (](icordebugmodule-getassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="40045-152">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="40045-153">Este tipo de objetos siempre se almacenan en caché por [ICorDebug](icordebug-interface.md)y tendrán la misma identidad de puntero independientemente de si se crearon o consultaron desde el módulo contenedor o un submódulo.</span><span class="sxs-lookup"><span data-stu-id="40045-153">These objects are always cached by [ICorDebug](icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="40045-154">El submódulo proporciona una vista filtrada de estos objetos en caché, no una memoria caché independiente con sus propias copias.</span><span class="sxs-lookup"><span data-stu-id="40045-154">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>

## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="40045-155">División de módulos virtuales y API de depuración no administradas</span><span class="sxs-lookup"><span data-stu-id="40045-155">Virtual module splitting and the unmanaged debugging APIs</span></span>  

 <span data-ttu-id="40045-156">En la siguiente tabla se muestra cómo la división de módulos virtuales afecta al comportamiento de otros métodos en una API de depuración no administrada.</span><span class="sxs-lookup"><span data-stu-id="40045-156">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="40045-157">Método</span><span class="sxs-lookup"><span data-stu-id="40045-157">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="40045-158">ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="40045-158">ICorDebugFunction::GetModule</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="40045-159">Devuelve el submódulo en el que esta función se definió originalmente.</span><span class="sxs-lookup"><span data-stu-id="40045-159">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="40045-160">Devuelve el módulo contenedor con el que esta función se combinó.</span><span class="sxs-lookup"><span data-stu-id="40045-160">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="40045-161">ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="40045-161">ICorDebugClass::GetModule</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="40045-162">Devuelve el submódulo en el que esta clase se definió originalmente.</span><span class="sxs-lookup"><span data-stu-id="40045-162">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="40045-163">Devuelve el módulo contenedor con el que esta clase se combinó.</span><span class="sxs-lookup"><span data-stu-id="40045-163">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="40045-164">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="40045-164">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="40045-165">Devuelve el módulo contenedor que se cargó.</span><span class="sxs-lookup"><span data-stu-id="40045-165">Returns the container module that was loaded.</span></span> <span data-ttu-id="40045-166">Los submódulos no tienen eventos load, independientemente de esta configuración.</span><span class="sxs-lookup"><span data-stu-id="40045-166">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="40045-167">Devuelve el módulo contenedor que se cargó.</span><span class="sxs-lookup"><span data-stu-id="40045-167">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="40045-168">ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="40045-168">ICorDebugAppDomain::EnumerateAssemblies</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="40045-169">Devuelve una lista de los subensamblados y ensamblados regulares; no se incluyen ensamblados de contenedor.</span><span class="sxs-lookup"><span data-stu-id="40045-169">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="40045-170">**Nota:**  Si faltan símbolos en algún ensamblado de contenedor, no se enumerará ninguno de sus Subensamblados.</span><span class="sxs-lookup"><span data-stu-id="40045-170">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="40045-171">Si faltan símbolos en algún ensamblado regular, puede que se enumere o no.</span><span class="sxs-lookup"><span data-stu-id="40045-171">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="40045-172">Devuelve una lista de ensamblados de contenedor y ensamblados regulares; no se incluyen subensamblados.</span><span class="sxs-lookup"><span data-stu-id="40045-172">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="40045-173">**Nota:**  Si faltan símbolos en algún ensamblado normal, se puede enumerar o no.</span><span class="sxs-lookup"><span data-stu-id="40045-173">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="40045-174">[ICorDebugCode:: getCode](icordebugcode-getcode-method.md) (solo cuando se hace referencia a código Il)</span><span class="sxs-lookup"><span data-stu-id="40045-174">[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="40045-175">Devuelve el código IL que sería válido en una imagen de ensamblado antes de la fusión mediante combinación.</span><span class="sxs-lookup"><span data-stu-id="40045-175">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="40045-176">En concreto, cualquier token de metadatos en línea será correctamente un token TypeRef o MemberRef cuando los tipos a los que se hace referencia no están definidos en el módulo virtual que contiene el IL.</span><span class="sxs-lookup"><span data-stu-id="40045-176">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="40045-177">Estos tokens TypeRef o MemberRef se pueden buscar en el objeto [IMetaDataImport](../metadata/imetadataimport-interface.md) del objeto ICorDebugModule virtual correspondiente.</span><span class="sxs-lookup"><span data-stu-id="40045-177">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="40045-178">Devuelve el IL de la imagen de ensamblado posterior a la combinación.</span><span class="sxs-lookup"><span data-stu-id="40045-178">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40045-179">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40045-179">Requirements</span></span>  

 <span data-ttu-id="40045-180">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40045-180">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40045-181">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40045-181">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40045-182">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40045-182">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40045-183">**.NET Framework versiones:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40045-183">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40045-184">Consulte también</span><span class="sxs-lookup"><span data-stu-id="40045-184">See also</span></span>

- [<span data-ttu-id="40045-185">Interfaz ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="40045-185">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="40045-186">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="40045-186">Debugging Interfaces</span></span>](debugging-interfaces.md)
