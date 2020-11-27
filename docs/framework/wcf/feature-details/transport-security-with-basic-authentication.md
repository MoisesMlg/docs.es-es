---
title: Seguridad de transporte con autenticación básica
description: Revise este escenario de WCF, que muestra la autenticación básica para un servicio y un cliente WCF. El servicio necesita un certificado válido en el que el cliente confíe.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: e821f8ed3996e9119c6f2c06ec6533c575bf75dd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251846"
---
# <a name="transport-security-with-basic-authentication"></a>Seguridad de transporte con autenticación básica

En la ilustración siguiente se muestra un servicio y un cliente de Windows Communication Foundation (WCF). El servidor necesita un certificado X.509 válido que se puede utilizar para Capa de sockets seguros (SSL) y los clientes deben confiar en el certificado del servidor. Además, el servicio web ya tiene una implementación SSL que se puede usar. Para obtener más información acerca de cómo habilitar la autenticación básica en Internet Information Services (IIS), vea <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> .  
  
 ![Captura de pantalla que muestra la seguridad de transporte con autenticación básica.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Modo de seguridad|Transporte|  
|Interoperabilidad|Con clientes de servicios Web existentes y servicios|  
|Autenticación (servidor)<br /><br /> Autenticación (cliente)|Sí (utilizar HTTPS)<br /><br /> Sí (a través del nombre de usuario/Contraseña)|  
|Integridad|Yes|  
|Confidencialidad|Sí|  
|Transporte|HTTPS|  
|Enlaces|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Servicio  

 El código y la configuración siguientes están diseñados para ejecutarse de forma independiente. Lleve a cabo una de las siguientes acciones:  
  
- Cree un servicio independiente mediante el código sin configuración.  
  
- Cree un servicio mediante la configuración proporcionada, pero sin definir ningún punto de conexión.  
  
### <a name="code"></a>Código  

 El código siguiente muestra cómo crear un extremo de servicio que utiliza un nombre de usuario del dominio de Windows y contraseña para la seguridad de la transferencia. Tenga en cuenta que el servicio exige un certificado X.509 que autentique al cliente. Para obtener más información, consulte [trabajar con certificados](working-with-certificates.md) y [Cómo: configurar un puerto con un certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Configuración  

 Lo siguiente configura un servicio para utilizar la autenticación básica con seguridad de nivel de transporte:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
  
### <a name="code"></a>Código  

 El código siguiente muestra el código de cliente que incluye el nombre de usuario y contraseña. Tenga en cuenta que el usuario debe proporcionar un nombre de usuario de Windows válido y contraseña. El código para devolver el nombre de usuario y la contraseña no se muestra aquí. Utilice un cuadro de diálogo u otra interfaz para solicitar la información al usuario.  
  
> [!NOTE]
> El nombre de usuario y contraseña solo se pueden establecer utilizando el código.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Configuración  

 El código siguiente muestra la configuración del cliente.  
  
> [!NOTE]
> No puede utilizar la configuración para establecer el nombre de usuario y contraseña. La configuración mostrada aquí se debe aumentar utilizando el código para establecer el nombre de usuario y contraseña.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Trabajar con certificados](working-with-certificates.md)
- [Procedimiento para configurar un puerto con un certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Información general sobre seguridad](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- [Modelo de seguridad para Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))
