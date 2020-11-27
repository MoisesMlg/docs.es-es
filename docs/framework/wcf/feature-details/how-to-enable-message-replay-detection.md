---
title: Procedimiento para habilitar la detección de repetición de mensajes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 4a4d304a1316fe534e09f02ac1cd2900bf798011
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265536"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="585df-102">Procedimiento para habilitar la detección de repetición de mensajes</span><span class="sxs-lookup"><span data-stu-id="585df-102">How to: Enable Message Replay Detection</span></span>

<span data-ttu-id="585df-103">Un ataque de reproducción se produce cuando un atacante copia una secuencia de mensajes entre dos partes y reproduce la secuencia a una o más partes.</span><span class="sxs-lookup"><span data-stu-id="585df-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="585df-104">A menos que se mitigue, los equipos sujetos al ataque procesarán el flujo como mensajes legítimos, generando un intervalo de consecuencias erróneas, como las órdenes redundantes de un elemento.</span><span class="sxs-lookup"><span data-stu-id="585df-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="585df-105">Para obtener más información acerca de la detección de reproducción de mensajes, vea [detección de reproducción de mensajes](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="585df-105">For more information about message replay detection, see [Message Replay Detection](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="585df-106">En el procedimiento siguiente se muestran varias propiedades que puede usar para controlar la detección de reproducción mediante Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="585df-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="585df-107">Para controlar la detección de reproducción en el cliente utilizando código</span><span class="sxs-lookup"><span data-stu-id="585df-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="585df-108">Cree <xref:System.ServiceModel.Channels.SecurityBindingElement> para utilizar en <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="585df-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="585df-109">Para obtener más información, vea [Cómo: crear un enlace personalizado mediante SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="585df-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="585df-110">En el siguiente ejemplo se utiliza <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> creado con <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> de la clase <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="585df-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="585df-111">Utilizar la propiedad <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> para devolver una referencia a la clase <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> y establecer cualquiera de las propiedades siguientes, según corresponda:</span><span class="sxs-lookup"><span data-stu-id="585df-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="585df-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="585df-112">`DetectReplay`.</span></span> <span data-ttu-id="585df-113">Valor booleano.</span><span class="sxs-lookup"><span data-stu-id="585df-113">A Boolean value.</span></span> <span data-ttu-id="585df-114">Esto rige si el cliente debería detectar las reproducciones del servidor.</span><span class="sxs-lookup"><span data-stu-id="585df-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="585df-115">De manera predeterminada, es `true`.</span><span class="sxs-lookup"><span data-stu-id="585df-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="585df-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="585df-116">`MaxClockSkew`.</span></span> <span data-ttu-id="585df-117">Valor <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="585df-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="585df-118">Rige qué sesgo temporal puede tolerar el mecanismo de reproducción entre el cliente y el servidor.</span><span class="sxs-lookup"><span data-stu-id="585df-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="585df-119">El mecanismo de seguridad examina la marca de tiempo enviada y determina si se fue enviada demasiado lejos en el pasado.</span><span class="sxs-lookup"><span data-stu-id="585df-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="585df-120">El valor predeterminado es 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="585df-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="585df-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="585df-121">`ReplayWindow`.</span></span> <span data-ttu-id="585df-122">Valor `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="585df-122">A `TimeSpan` value.</span></span> <span data-ttu-id="585df-123">Esto rige cuánto tiempo un mensaje puede vivir en la red después de que el servidor lo envíe (a través de los intermediarios) antes de alcanzar el cliente.</span><span class="sxs-lookup"><span data-stu-id="585df-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="585df-124">El cliente realiza el seguimiento de las firmas de los mensajes enviados dentro del `ReplayWindow` último para los propósitos de detección de reproducción.</span><span class="sxs-lookup"><span data-stu-id="585df-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="585df-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="585df-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="585df-126">Valor de entero.</span><span class="sxs-lookup"><span data-stu-id="585df-126">An integer value.</span></span> <span data-ttu-id="585df-127">El cliente almacena las firmas del mensaje en una memoria caché.</span><span class="sxs-lookup"><span data-stu-id="585df-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="585df-128">Este valor especifica cuántas firmas que puede almacenar la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="585df-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="585df-129">Si el número de mensajes enviado dentro de la última ventana de reproducción alcanza el límite de la memoria caché, se rechazan los nuevos mensajes hasta que las firmas almacenadas en memoria caché más antiguas alcancen el límite horario.</span><span class="sxs-lookup"><span data-stu-id="585df-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="585df-130">El valor predeterminado es 500000.</span><span class="sxs-lookup"><span data-stu-id="585df-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="585df-131">Para controlar la detección de reproducción en el servicio utilizando código</span><span class="sxs-lookup"><span data-stu-id="585df-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="585df-132">Cree <xref:System.ServiceModel.Channels.SecurityBindingElement> para utilizar en <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="585df-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="585df-133">Utilice la propiedad <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> para devolver una referencia a la clase <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> y establezca las propiedades como descrito previamente.</span><span class="sxs-lookup"><span data-stu-id="585df-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="585df-134">Para controlar la detección de reproducción en configuración para el cliente o servicio</span><span class="sxs-lookup"><span data-stu-id="585df-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="585df-135">Cree un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="585df-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="585df-136">Cree un elemento `<security>`.</span><span class="sxs-lookup"><span data-stu-id="585df-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="585df-137">Cree un [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) o [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="585df-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="585df-138">Establezca los siguientes valores de atributo según sea apropiado: `detectReplays`, `maxClockSkew`, `replayWindow`, y `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="585df-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="585df-139">El ejemplo siguiente establece los atributos de `<localServiceSettings>`:</span><span class="sxs-lookup"><span data-stu-id="585df-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="585df-140">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="585df-140">Example</span></span>  

 <span data-ttu-id="585df-141">El ejemplo siguiente crea <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> mediante el método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> y establece las propiedades de reproducción del enlace.</span><span class="sxs-lookup"><span data-stu-id="585df-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="585df-142">Ámbito de reproducción: Solo seguridad del mensaje</span><span class="sxs-lookup"><span data-stu-id="585df-142">Scope of Replay: Message Security Only</span></span>  

 <span data-ttu-id="585df-143">Observe que los procedimientos siguientes solo se aplican al modo de seguridad de los mensajes.</span><span class="sxs-lookup"><span data-stu-id="585df-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="585df-144">Para Transporte y Transporte con modos de credencial de mensaje, los mecanismos de transporte detectan las reproducciones.</span><span class="sxs-lookup"><span data-stu-id="585df-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="585df-145">Notas de conversación seguras</span><span class="sxs-lookup"><span data-stu-id="585df-145">Secure Conversation Notes</span></span>  

 <span data-ttu-id="585df-146">Para los enlaces que habilitan las conversaciones seguras, puede ajustar estos valores tanto para la aplicación como para el enlace de arranque de conversación segura.</span><span class="sxs-lookup"><span data-stu-id="585df-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="585df-147">Por ejemplo, se pueden desactivar las reproducciones para el canal de la aplicación pero habilitarlas para el canal de arranque que establece la conversación segura.</span><span class="sxs-lookup"><span data-stu-id="585df-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="585df-148">Si no utiliza las sesiones de conversación seguras, la detección de reproducción no garantiza la detección de reproducciones en escenarios de granja de servidores y cuando se recicla el proceso.</span><span class="sxs-lookup"><span data-stu-id="585df-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="585df-149">Esto se aplica a los enlaces siguientes proporcionados por el sistema:</span><span class="sxs-lookup"><span data-stu-id="585df-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="585df-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="585df-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="585df-151"><xref:System.ServiceModel.WSHttpBinding> con la propiedad <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> establecida en `false`.</span><span class="sxs-lookup"><span data-stu-id="585df-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="585df-152">Compilar el código</span><span class="sxs-lookup"><span data-stu-id="585df-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="585df-153">Los espacios de nombres siguientes son necesarios para compilar el código:</span><span class="sxs-lookup"><span data-stu-id="585df-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="585df-154">Vea también</span><span class="sxs-lookup"><span data-stu-id="585df-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="585df-155">Conversaciones y sesiones seguras</span><span class="sxs-lookup"><span data-stu-id="585df-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="585df-156">Procedimiento para crear un enlace personalizado mediante SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="585df-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
