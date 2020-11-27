---
title: Procedimiento para usar el proveedor de roles del administrador de autorización de ASP.NET con un servicio
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: bbdafdd96a32b41d7c6892944ed872e3f8702f0e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280603"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Procedimiento para usar el proveedor de roles del administrador de autorización de ASP.NET con un servicio

Cuando ASP.NET hospeda un servicio Web, puede integrar el administrador de autorización en la aplicación para proporcionar autorización para el servicio. El administrador de autorización permite a los desarrolladores de aplicaciones definir operaciones individuales que, a su vez, pueden agruparse para formar tareas. Un administrador puede autorizar funciones que realicen tareas específicas u operaciones individuales. El administrador de autorización proporciona una herramienta de administración, como complemento de Microsoft Management Console (MMC), para administrar funciones, tareas, operaciones y usuarios. Los administradores configuran un almacén de directivas del administrador de autorización en un archivo XML, en Active Directory, o en un almacén de Active Directory Application Mode (ADAM).  
  
 El administrador de autorización se integra en la aplicación mediante la configuración del proveedor de funciones ASP.NET de administrador de autorización para la aplicación ASP.NET que hospeda el servicio Web. Al igual que otros proveedores de roles de ASP.NET, el proveedor de roles ASP.NET de administrador de autorización se configura mediante el `providers` elemento <>.  
  
 El siguiente ejemplo de código forma parte del archivo de configuración de un servicio web que integra el administrador de autorización en la aplicación.  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 Para obtener más información sobre la integración de un proveedor de roles de ASP.NET con una aplicación WCF, consulte [Cómo: usar el proveedor de roles ASP.net con un servicio](how-to-use-the-aspnet-role-provider-with-a-service.md). Para obtener más información acerca del uso del administrador de autorización con ASP.NET, consulte [Cómo: usar el administrador de autorización (AzMan) con ASP.NET 2,0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Vea también

- [Procedimiento para usar el proveedor de roles ASP.NET con un servicio](how-to-use-the-aspnet-role-provider-with-a-service.md)
