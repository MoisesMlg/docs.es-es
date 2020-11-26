---
title: Programación de la seguridad de WCF
description: Obtenga información sobre cómo crear una aplicación WCF segura, incluida la autenticación, la confidencialidad y la integridad.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 4ffbf6a05abd3ed9ebcea4b2e85f0dc305a4f2db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244774"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="2b87e-103">Programación de la seguridad de WCF</span><span class="sxs-lookup"><span data-stu-id="2b87e-103">Programming WCF Security</span></span>

<span data-ttu-id="2b87e-104">En este tema se describen las tareas de programación fundamentales que se usan para crear una aplicación Secure Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2b87e-104">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="2b87e-105">En este tema solo se trata la autenticación, la confidencialidad y la integridad, que se conocen colectivamente como *seguridad de transferencia*.</span><span class="sxs-lookup"><span data-stu-id="2b87e-105">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="2b87e-106">En este tema no se trata la autorización (el control de acceso a los recursos o servicios). para obtener información sobre la autorización, vea [autorización](authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="2b87e-106">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b87e-107">Para obtener una introducción valiosa a los conceptos de seguridad, especialmente en relación con WCF, vea el conjunto de tutoriales de patrones y prácticas de MSDN en [escenarios, patrones e instrucciones de implementación para Web Services Enhancements (WSE) 3,0](/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="2b87e-107">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="2b87e-108">La programación de la seguridad de WCF se basa en tres pasos que establecen lo siguiente: el modo de seguridad, un tipo de credencial de cliente y los valores de credenciales.</span><span class="sxs-lookup"><span data-stu-id="2b87e-108">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="2b87e-109">Puede realizar estos pasos mediante código o configuración.</span><span class="sxs-lookup"><span data-stu-id="2b87e-109">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="2b87e-110">Establecimiento del modo de seguridad</span><span class="sxs-lookup"><span data-stu-id="2b87e-110">Setting the Security Mode</span></span>  

 <span data-ttu-id="2b87e-111">A continuación se explican los pasos generales para programar con el modo de seguridad en WCF:</span><span class="sxs-lookup"><span data-stu-id="2b87e-111">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="2b87e-112">Seleccione uno de los enlaces predefinidos adecuado a sus requisitos de aplicación.</span><span class="sxs-lookup"><span data-stu-id="2b87e-112">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="2b87e-113">Para obtener una lista de las opciones de enlace, vea [enlaces proporcionados](../system-provided-bindings.md)por el sistema.</span><span class="sxs-lookup"><span data-stu-id="2b87e-113">For a list of the binding choices, see [System-Provided Bindings](../system-provided-bindings.md).</span></span> <span data-ttu-id="2b87e-114">De forma predeterminada, prácticamente todos los enlaces tienen la seguridad habilitada.</span><span class="sxs-lookup"><span data-stu-id="2b87e-114">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="2b87e-115">La única excepción es la <xref:System.ServiceModel.BasicHttpBinding> clase (mediante la configuración, [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ).</span><span class="sxs-lookup"><span data-stu-id="2b87e-115">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="2b87e-116">El enlace que seleccione determina el transporte.</span><span class="sxs-lookup"><span data-stu-id="2b87e-116">The binding you select determines the transport.</span></span> <span data-ttu-id="2b87e-117">Por ejemplo, <xref:System.ServiceModel.WSHttpBinding> utiliza HTTP como el transporte; <xref:System.ServiceModel.NetTcpBinding> utiliza TCP.</span><span class="sxs-lookup"><span data-stu-id="2b87e-117">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="2b87e-118">Seleccione uno de los modos de seguridad para el enlace.</span><span class="sxs-lookup"><span data-stu-id="2b87e-118">Select one of the security modes for the binding.</span></span> <span data-ttu-id="2b87e-119">Tenga en cuenta que el enlace que seleccione determinará las opciones de modo disponibles.</span><span class="sxs-lookup"><span data-stu-id="2b87e-119">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="2b87e-120">Por ejemplo, <xref:System.ServiceModel.WSDualHttpBinding> no permite la seguridad de transporte (no es una opción).</span><span class="sxs-lookup"><span data-stu-id="2b87e-120">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="2b87e-121">De igual forma, ni <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ni <xref:System.ServiceModel.NetNamedPipeBinding> permiten el modo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="2b87e-121">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="2b87e-122">Dispone de tres opciones:</span><span class="sxs-lookup"><span data-stu-id="2b87e-122">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="2b87e-123">La seguridad de transporte depende del mecanismo que use el enlace que ha seleccionado.</span><span class="sxs-lookup"><span data-stu-id="2b87e-123">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="2b87e-124">Por ejemplo, si utiliza `WSHttpBinding`, el mecanismo de seguridad es Secure Sockets Layer (SSL) (también es el mecanismo para el protocolo HTTPS).</span><span class="sxs-lookup"><span data-stu-id="2b87e-124">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="2b87e-125">Generalmente hablando, la principal ventaja de la seguridad de transporte es que proporciona un buen rendimiento independientemente del transporte que esté utilizando.</span><span class="sxs-lookup"><span data-stu-id="2b87e-125">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="2b87e-126">No obstante, tiene dos limitaciones: la primera es que el mecanismo de transporte dicta el tipo de credencial utilizado para autenticar a un usuario.</span><span class="sxs-lookup"><span data-stu-id="2b87e-126">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="2b87e-127">Ésta es una desventaja solo si un servicio necesita interoperar con otros servicios que exigen tipos diferentes de credenciales.</span><span class="sxs-lookup"><span data-stu-id="2b87e-127">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="2b87e-128">La segunda es que, puesto que la seguridad no se aplica en el nivel de mensaje, la seguridad se implementa salto por salto en lugar de de extremo a extremo.</span><span class="sxs-lookup"><span data-stu-id="2b87e-128">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="2b87e-129">Esta última limitación es un problema solo si la ruta de mensajes entre el cliente y el servicio incluye intermediarios.</span><span class="sxs-lookup"><span data-stu-id="2b87e-129">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="2b87e-130">Para obtener más información acerca del transporte que se va a usar, consulte [elección de un transporte](choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="2b87e-130">For more information about which transport to use, see [Choosing a Transport](choosing-a-transport.md).</span></span> <span data-ttu-id="2b87e-131">Para obtener más información sobre el uso de la seguridad de transporte, vea [información general](transport-security-overview.md)sobre la seguridad de transporte.</span><span class="sxs-lookup"><span data-stu-id="2b87e-131">For more information about using transport security, see [Transport Security Overview](transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="2b87e-132">El modo de seguridad significa que cada mensaje incluye los encabezados y datos necesarios para mantener el mensaje protegido.</span><span class="sxs-lookup"><span data-stu-id="2b87e-132">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="2b87e-133">Dado que la composición de los encabezados varía, puede incluir cualquier número de credenciales.</span><span class="sxs-lookup"><span data-stu-id="2b87e-133">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="2b87e-134">Este es un factor a tener en cuenta si está interoperando con otros servicios que exigen un tipo de credencial concreto que un mecanismo de transporte no puede proporcionar o si el mensaje se debe utilizar con más de un servicio, donde cada servicio exige un tipo de credencial diferente.</span><span class="sxs-lookup"><span data-stu-id="2b87e-134">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="2b87e-135">Para obtener más información, vea [seguridad de mensajes](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="2b87e-135">For more information, see [Message Security](message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="2b87e-136">Esta opción utiliza el nivel de transporte para proteger la transferencia del mensaje, mientras que cada mensaje incluye las credenciales enriquecidas que otros servicios necesitan.</span><span class="sxs-lookup"><span data-stu-id="2b87e-136">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="2b87e-137">Esto combina la ventaja de rendimiento de la seguridad de transporte con la ventaja de las credenciales enriquecidas de la seguridad de mensaje.</span><span class="sxs-lookup"><span data-stu-id="2b87e-137">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="2b87e-138">Esto está disponible con los siguientes enlaces: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding> y <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="2b87e-138">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="2b87e-139">Si decide utilizar la seguridad de transporte para HTTP (en otras palabras, HTTPS), debe configurar también el host con un certificado SSL y habilitar SSL en un puerto.</span><span class="sxs-lookup"><span data-stu-id="2b87e-139">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="2b87e-140">Para obtener más información, vea [seguridad de transporte http](http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="2b87e-140">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="2b87e-141">Si está utilizando el <xref:System.ServiceModel.WSHttpBinding> y no necesita establecer una sesión segura, establezca la propiedad <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> en `false`.</span><span class="sxs-lookup"><span data-stu-id="2b87e-141">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="2b87e-142">Una sesión segura se produce cuando un cliente y servicio crean un canal mediante una clave simétrica (tanto el cliente como el servidor usan la misma clave durante la duración de una conversación, hasta que se cierre el diálogo).</span><span class="sxs-lookup"><span data-stu-id="2b87e-142">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="2b87e-143">Establecimiento del tipo de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="2b87e-143">Setting the Client Credential Type</span></span>  

 <span data-ttu-id="2b87e-144">Seleccione según corresponda un tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="2b87e-144">Select a client credential type as appropriate.</span></span> <span data-ttu-id="2b87e-145">Para obtener más información, consulte [seleccionar un tipo de credencial](selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="2b87e-145">For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).</span></span> <span data-ttu-id="2b87e-146">Los siguientes tipos de credencial de cliente están disponibles:</span><span class="sxs-lookup"><span data-stu-id="2b87e-146">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="2b87e-147">Dependiendo de cómo establezca el modo, deberá establecer el tipo de credencial.</span><span class="sxs-lookup"><span data-stu-id="2b87e-147">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="2b87e-148">Por ejemplo, si ha seleccionado el `wsHttpBinding`, y ha establecido el modo en "Mensaje", también puede establecer el atributo `clientCredentialType` del elemento Message en uno de los valores siguientes: `None`, `Windows`, `UserName`, `Certificate` y `IssuedToken`, como se muestra en el ejemplo de configuración siguiente.</span><span class="sxs-lookup"><span data-stu-id="2b87e-148">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2b87e-149">O bien, en el código:</span><span class="sxs-lookup"><span data-stu-id="2b87e-149">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="2b87e-150">Establecimiento de valores de credenciales de servicio</span><span class="sxs-lookup"><span data-stu-id="2b87e-150">Setting Service Credential Values</span></span>  

 <span data-ttu-id="2b87e-151">Cuando selecciona un tipo de credencial de cliente, debe establecer las credenciales reales que el servicio y el cliente han de utilizar.</span><span class="sxs-lookup"><span data-stu-id="2b87e-151">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="2b87e-152">En el servicio, las credenciales se establecen utilizando la clase <xref:System.ServiceModel.Description.ServiceCredentials> y se devuelven mediante la propiedad <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> de la clase <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="2b87e-152">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="2b87e-153">El enlace en uso implica el tipo de credencial de servicio, el modo de seguridad elegido y el tipo de la credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="2b87e-153">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="2b87e-154">El código siguiente establece un certificado para una credencial de servicio.</span><span class="sxs-lookup"><span data-stu-id="2b87e-154">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="2b87e-155">Establecimiento de los valores de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="2b87e-155">Setting Client Credential Values</span></span>  

 <span data-ttu-id="2b87e-156">En el cliente, establezca valores de credencial de cliente mediante la clase <xref:System.ServiceModel.Description.ClientCredentials> y devueltos por la propiedad <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la clase <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="2b87e-156">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="2b87e-157">El código siguiente establece un certificado como una credencial en un cliente utilizando el protocolo TCP.</span><span class="sxs-lookup"><span data-stu-id="2b87e-157">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2b87e-158">Vea también</span><span class="sxs-lookup"><span data-stu-id="2b87e-158">See also</span></span>

- [<span data-ttu-id="2b87e-159">Programación básica de WCF</span><span class="sxs-lookup"><span data-stu-id="2b87e-159">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="2b87e-160">Escenarios de seguridad comunes</span><span class="sxs-lookup"><span data-stu-id="2b87e-160">Common Security Scenarios</span></span>](common-security-scenarios.md)
