---
title: Procedimiento para deshabilitar la característica de omisión de nombres seguros
description: La omisión de nombres seguros omite la validación de firmas en dominios de plena confianza de .NET. Se puede invalidar esta característica para una sola aplicación o para todas las aplicaciones.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 2846efbbd76cf677a42a7031e53661d302c6c964
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687468"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="4a1d5-104">Procedimiento para deshabilitar la característica de omisión de nombres seguros</span><span class="sxs-lookup"><span data-stu-id="4a1d5-104">How to: Disable the strong-name bypass feature</span></span>

<span data-ttu-id="4a1d5-105">A partir de .NET Framework versión 3.5 Service Pack 1 (SP1), las firmas de nombre seguro no se validan cuando un ensamblado se carga en un objeto <xref:System.AppDomain> de plena confianza, como el objeto <xref:System.AppDomain> predeterminado para la zona `MyComputer`.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="4a1d5-106">Esta característica se denomina omisión de nombres seguros.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="4a1d5-107">En un entorno de plena confianza, las peticiones de <xref:System.Security.Permissions.StrongNameIdentityPermission> siempre se realizan correctamente para los ensamblados de plena confianza firmados, independientemente de su firma.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="4a1d5-108">La única restricción es que el ensamblado debe ser de plena confianza porque su zona es de plena confianza.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="4a1d5-109">Dado que el nombre seguro no es un factor determinante en estas condiciones, no hay ninguna razón para que se valide.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="4a1d5-110">La omisión de la validación de firmas de nombre seguro proporciona importantes mejoras en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="4a1d5-111">La característica de omisión se aplica a todos los ensamblados de plena confianza que no tienen firma retrasada y que se cargan en un objeto <xref:System.AppDomain> de plena confianza desde el directorio especificado por la propiedad <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="4a1d5-112">Puede invalidar la característica de omisión para todas las aplicaciones de un equipo. Para ello, establezca un valor de clave del Registro.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="4a1d5-113">Puede invalidar la configuración de una aplicación mediante un archivo de configuración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="4a1d5-114">No se puede restablecer la característica de omisión de una sola aplicación si se ha deshabilitado mediante la clave del Registro.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="4a1d5-115">Cuando se invalida la característica de omisión, el nombre seguro se valida únicamente para comprobar que es correcto; no se comprueba su <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="4a1d5-116">Si quiere confirmar un nombre seguro específico, tendrá que hacerlo por separado.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a1d5-117">La capacidad de forzar la validación del nombre seguro depende de una clave del Registro, como se indica en el procedimiento siguiente.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="4a1d5-118">Si una aplicación se ejecuta en una cuenta que no tiene permiso de lista de control de acceso (ACL) para tener acceso a esa clave del Registro, el valor no tiene efecto.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="4a1d5-119">Debe asegurarse de que se han configurado permisos de ACL para esta clave de modo que se pueda leer para todos los ensamblados.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="4a1d5-120">Cómo deshabilitar la característica de omisión de nombres seguros para todas las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="4a1d5-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="4a1d5-121">En equipos de 32 bits, en el Registro del sistema, cree una entrada DWORD con un valor de 0 denominada `AllowStrongNameBypass` en la clave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="4a1d5-122">En equipos de 64 bits, en el Registro del sistema, cree una entrada DWORD con un valor de 0 denominada `AllowStrongNameBypass` en las claves HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework y HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="4a1d5-123">Cómo deshabilitar la característica de omisión de nombres seguros para una sola aplicación</span><span class="sxs-lookup"><span data-stu-id="4a1d5-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="4a1d5-124">Abra o cree el archivo de configuración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="4a1d5-125">Para obtener más información sobre este archivo, vea la sección sobre archivos de configuración de la aplicación en [Configuración de aplicaciones](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a1d5-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="4a1d5-126">Agregue la siguiente entrada:</span><span class="sxs-lookup"><span data-stu-id="4a1d5-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="4a1d5-127">Puede restaurar la característica de omisión de la aplicación. Para ello, elimine el valor del archivo de configuración o establezca el atributo en `true`.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a1d5-128">Puede activar y desactivar la validación del nombre seguro de una aplicación únicamente si la característica de omisión está habilitada para el equipo.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="4a1d5-129">Si la característica de omisión se ha desactivado para el equipo, los nombres seguros se validan para todas las aplicaciones y no se puede omitir la validación de una sola aplicación.</span><span class="sxs-lookup"><span data-stu-id="4a1d5-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a1d5-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="4a1d5-130">See also</span></span>

- [<span data-ttu-id="4a1d5-131">Sn.exe (Herramienta de nombre seguro)</span><span class="sxs-lookup"><span data-stu-id="4a1d5-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="4a1d5-132">Elemento \<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="4a1d5-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="4a1d5-133">Creación y uso de ensamblados con nombre seguro</span><span class="sxs-lookup"><span data-stu-id="4a1d5-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
