---
title: Configuración de servicios mediante archivos de configuración
description: Obtenga información sobre cómo un archivo de configuración para un servicio WCF ofrece la flexibilidad de proporcionar datos de punto de conexión y comportamiento de servicio durante la implementación.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 25a6891564054878e7bdf7f43d431547ea1dee6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253354"
---
# <a name="configuring-services-using-configuration-files"></a>Configuración de servicios mediante archivos de configuración

La configuración de un servicio de Windows Communication Foundation (WCF) con un archivo de configuración ofrece la flexibilidad de proporcionar datos de punto de conexión y de comportamiento de servicio en el punto de implementación en lugar de en tiempo de diseño. En este tema se describen las principales técnicas disponibles.  
  
 Un servicio WCF se puede configurar mediante la tecnología de configuración de .NET Framework. Normalmente, los elementos XML se agregan al archivo Web.config para un sitio Internet Information Services (IIS) que hospeda un servicio WCF. Los elementos le permiten cambiar detalles como las direcciones de extremos (las direcciones reales utilizadas para comunicarse con el servicio) equipo a equipo. Además, WCF incluye varios elementos proporcionados por el sistema que le permiten seleccionar rápidamente las características más básicas de un servicio. A partir de .NET Framework 4, WCF incluye un nuevo modelo de configuración predeterminado que simplifica los requisitos de configuración de WCF. Si no proporciona ninguna configuración de WCF para un servicio determinado, el tiempo de ejecución configura automáticamente el servicio con algunos extremos estándar y un enlace o comportamiento predeterminados. En la práctica, escribir la configuración es una parte importante de la programación de aplicaciones WCF.  
  
 Para obtener más información, consulte [configuración de enlaces para servicios](configuring-bindings-for-wcf-services.md). Para obtener una lista de los elementos que se usan con más frecuencia, vea [enlaces proporcionados por el sistema](system-provided-bindings.md). Para obtener más información sobre los puntos de conexión, enlaces y comportamientos predeterminados, vea [Configuración simplificada](simplified-configuration.md) y [Configuración simplificada de los servicios de WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> Al implementar escenarios en paralelo con dos versiones diferentes de un servicio, es necesario especificar los nombres parciales de los ensamblados a los que se hace referencia en los archivos de configuración. Esto se debe a que el archivo de configuración se comparte entre todas las versiones de un servicio y se podrían estar ejecutando con versiones diferentes de .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config y App.config  

 WCF usa el sistema de configuración de System.Configprimario del .NET Framework.  
  
 Al configurar un servicio en Visual Studio, use un archivo de Web.config o un archivo de App.config para especificar la configuración. El entorno de hospedaje determina la elección realizada del nombre del archivo de configuración para el servicio. Si está utilizando IIS para hospedar su servicio, utilice un archivo Web.config. Si está utilizando cualquier otro entorno de hospedaje, utilice un archivo App.config.  
  
 En Visual Studio, el archivo denominado App.config se usa para crear el archivo de configuración final. El nombre final realmente utilizado para la configuración depende del nombre de ensamblado. Por ejemplo, un ensamblado denominado "Cohowinery.exe" tiene un nombre final de archivo de configuración de "Cohowinery.exe.config". Sin embargo, solo necesita modificar el archivo App.config. Los cambios realizados en ese archivo se realizan automáticamente en tiempo de compilación en el archivo final de configuración de la aplicación.  
  
 Al utilizar un archivo App.config, el sistema de configuración combina el archivo App.config con el contenido del archivo Machine.config cuando se inicia la aplicación y se aplica la configuración. Este mecanismo permite definir los valores de equipo en el archivo Machine.config. El archivo App.config se puede utilizar para reemplazar los valores del archivo Machine.config; también puede bloquear los valores en el archivo Machine.config para que se utilicen. En el caso de Web.config, el sistema de configuración combina los archivos Web.config de todos los directorios que conducen al directorio de la aplicación en la configuración que se aplica. Para obtener más información sobre la configuración y las prioridades de configuración, vea los temas del <xref:System.Configuration> espacio de nombres.  
  
## <a name="major-sections-of-the-configuration-file"></a>Secciones principales del archivo de configuración  

 Las secciones principales del archivo de configuración incluyen los elementos siguientes.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> Las secciones de enlaces y comportamientos son opcionales y solo se incluyen si son necesarias.  
  
### <a name="the-services-element"></a>El \<services> elemento  

 El elemento `services` contiene las especificaciones para todos los servicios que la aplicación hospeda. A partir del modelo de configuración simplificado en .NET Framework 4, esta sección es opcional.  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>El \<service> elemento  

 Cada elemento service tiene estos atributos:  
  
- `name`. Especifica el tipo que proporciona una implementación de un contrato de servicios. Este es un nombre completo que consta del espacio de nombres, un punto y el nombre del tipo. Por ejemplo, `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. Especifica el nombre de uno de los elementos `behavior` encontrados en el elemento `behaviors` . El comportamiento especificado rige las acciones como si el servicio permitiese la suplantación. Si su valor es el nombre vacío o no se proporciona ningún atributo `behaviorConfiguration` , se agrega al servicio el conjunto predeterminado de comportamientos de servicio.  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>El \<endpoint> elemento  

 Cada extremo requiere una dirección, un enlace y un contrato, que están representados por los atributos siguientes:  
  
- `address`. Especifica el Identificador uniforme de recursos (URI) del servicio, que puede ser una dirección absoluta o una relativa a la dirección base del servicio. Si está establecido en una cadena vacía, indica que el extremo está disponible en la dirección base que se especifica al crear <xref:System.ServiceModel.ServiceHost> para el servicio.  
  
- `binding`. Normalmente especifica un enlace proporcionado por el sistema como <xref:System.ServiceModel.WSHttpBinding>, pero también puede especificar un enlace definido por el usuario. El enlace especificado determina el tipo de transporte, seguridad y codificación utilizados y si se admiten o habilitan sesiones confiables, transacciones, o la transmisión por secuencias.  
  
- `bindingConfiguration`. Si se deben modificar los valores predeterminados de un enlace, esto se puede hacer configurando el elemento de `binding` adecuado en el elemento `bindings` . Este atributo debería recibir el mismo valor que el atributo `name` del elemento de `binding` que se utiliza para cambiar los valores predeterminados. Si no se proporciona ningún nombre, o no se especifica ningún atributo `bindingConfiguration` en el enlace, se usa el enlace predeterminado del tipo de enlace en el extremo.  
  
- `contract`. Especifica la interfaz que define el contrato. Ésta es la interfaz implementada en el tipo de Common Language Runtime (CLR) especificado por el atributo `name` del elemento `service` .  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>El \<bindings> elemento  

 El elemento `bindings` contiene las especificaciones para todos los enlaces que puede utilizar cualquier extremo definido en cualquier servicio.  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>El \<binding> elemento  

 El elemento `binding` contenidos en el elemento `bindings` pueden ser uno de los enlaces proporcionados por el sistema (consulte [System-Provided Bindings](system-provided-bindings.md)) o un enlace personalizado (consulte [Custom Bindings](./extending/custom-bindings.md)). El elemento `binding` tiene un atributo `name` que pone en correlación el enlace con el extremo especificado en el atributo `bindingConfiguration` del elemento `endpoint` . Si no se especifica ningún nombre, dicho enlace corresponde al enlace predeterminado de ese tipo de enlace.  
  
Para obtener más información sobre la configuración de servicios y clientes, vea [configuración de servicios WCF](configuring-services.md).
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>El \<behaviors> elemento  

 Éste es un elemento contenedor para los elementos `behavior` que definen los comportamientos de un servicio.  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>El \<behavior> elemento  

 Cada `behavior` elemento se identifica mediante un `name` atributo y proporciona un comportamiento proporcionado por el sistema, como <`throttling`> o un comportamiento personalizado. Si no se especifica ningún nombre, dicho elemento de comportamiento corresponde al servicio predeterminado o al comportamiento de extremo.  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Uso de las configuraciones de comportamientos y enlaces  

 WCF facilita el uso compartido de las configuraciones entre los puntos de conexión mediante un sistema de referencia en la configuración. En lugar de asignar directamente los valores de configuración a un extremo, los valores de configuración relacionados con el enlace se agrupan en elementos `bindingConfiguration` de la sección `<binding>` . Una configuración de enlace es un grupo con nombre de valores en un enlace. Entonces, los extremos pueden hacer referencia a `bindingConfiguration` por nombre.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint
          address="myAddress" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint
          address="myAddress2" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint
          address="myAddress3" binding="basicHttpBinding"
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 El `name` de la `bindingConfiguration` se establece en el elemento `<binding>` . El `name` debe ser una cadena única dentro del ámbito del tipo de enlace, en este caso el [<basicHttpBinding \> ](../configure-apps/file-schema/wcf/basichttpbinding.md), o un valor vacío para hacer referencia al enlace predeterminado. El extremo vincula a la configuración estableciendo el atributo `bindingConfiguration` en esta cadena.  
  
 Una `behaviorConfiguration` se implementa de la misma manera, tal y como se muestra en el ejemplo siguiente.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 Observe que el conjunto predeterminado de comportamientos de servicio se agrega al servicio. Este sistema permite a los extremos compartir configuraciones comunes sin volver a definir la configuración. Si se requiere el ámbito de todo el equipo, cree la configuración de enlace o comportamiento en Machine.config. Los valores de configuración están disponibles en todos los archivos App.config. [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) facilita la creación de configuraciones.  
  
## <a name="behavior-merge"></a>Combinación de comportamientos  

 La característica de combinación de comportamientos simplifica la administración de los comportamientos cuando se desea el uso coherente de un conjunto de comportamientos comunes. Esta característica permite especificar comportamientos en niveles diferentes de la jerarquía de configuración y hacer que los servicios hereden los comportamientos de varios niveles de la jerarquía de configuración. Para mostrar cómo funciona, supongamos que tiene el siguiente diseño de directorio virtual en IIS:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 Y el `~\Web.config` archivo tiene el siguiente contenido:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Y tiene un archivo Web.config secundario ubicado en ~\Child\Web.config con el siguiente contenido:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 El servicio ubicado en ~\Child\Service.svc se comportará como si tuviese los comportamientos de serviceMetadata y serviceDebug. El servicio ubicado en ~\Service.svc tendrá solo el comportamiento de serviceDebug. Lo que sucede es que se combinan las dos colecciones de comportamientos con el mismo nombre (en este caso, la cadena vacía).  
  
 También puede borrar colecciones de comportamientos con la \<clear> etiqueta y quitar los comportamientos individuales de la colección mediante la \<remove> etiqueta. Por ejemplo, las dos configuraciones siguientes hacen que el servicio secundario tenga únicamente el comportamiento de serviceMetadata:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 La combinación de comportamientos se lleva a cabo para colecciones de comportamientos sin nombre, como se muestra arriba, y colecciones de comportamientos con nombre.  
  
 La combinación de comportamientos funciona en el entorno de hospedaje de IIS, en el que Web.config los archivos se combinan jerárquicamente con el archivo raíz Web.config y machine.config. Pero también funciona en el entorno de la aplicación, donde machine.config puede fusionar mediante combinación con el archivo App.config.  
  
 La combinación de comportamientos se aplica a comportamientos de extremo y comportamientos de servicio en la configuración.  
  
 Si una colección de comportamientos secundarios contiene un comportamiento que ya se encuentra en la colección de comportamientos primarios, el comportamiento secundario invalida el primario. Por tanto, si una colección de comportamientos primarios tuviera `<serviceMetadata httpGetEnabled="False" />` y una colección de comportamientos secundarios tuviese `<serviceMetadata httpGetEnabled="True" />` , el comportamiento secundario invalidaría el comportamiento primario en la colección de comportamientos y httpGetEnabled sería "true".  
  
## <a name="see-also"></a>Vea también

- [Configuración simplificada](simplified-configuration.md)
- [Configuración de servicios WCF](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
