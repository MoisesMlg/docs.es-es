---
title: 'Codificador de mensajes personalizado: codificador de texto personalizado'
description: Use este ejemplo para implementar un codificador de mensajes de texto personalizado mediante WCF. Este codificador admite todas las codificaciones de caracteres compatibles con la plataforma para la interoperabilidad.
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 89f0bf09ba6408e24f642a67f2e7ac8243608dcb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240971"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="c015c-104">Codificador de mensajes personalizado: codificador de texto personalizado</span><span class="sxs-lookup"><span data-stu-id="c015c-104">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="c015c-105">Este ejemplo muestra cómo implementar un codificador de mensajes de texto personalizado mediante Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c015c-105">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="c015c-106">Puede que los ejemplos ya estén instalados en su equipo.</span><span class="sxs-lookup"><span data-stu-id="c015c-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c015c-107">Compruebe el siguiente directorio (predeterminado) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c015c-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c015c-108">Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos.</span><span class="sxs-lookup"><span data-stu-id="c015c-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c015c-109">Este ejemplo se encuentra en el siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="c015c-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="c015c-110"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>De WCF solo admite las codificaciones UTF-8, UTF-16 y Big-Endian Unicode.</span><span class="sxs-lookup"><span data-stu-id="c015c-110">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="c015c-111">El codificador de mensajes de texto personalizado en este ejemplo es compatible con todas las codificaciones de caracteres compatibles con la plataforma que pueden ser necesarias para la interoperabilidad.</span><span class="sxs-lookup"><span data-stu-id="c015c-111">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="c015c-112">El ejemplo está compuesto de un programa de consola de cliente (. exe), una biblioteca de servicios (. dll) hospedada por Internet Information Services (IIS) y una biblioteca de codificador de mensajes de texto (. dll).</span><span class="sxs-lookup"><span data-stu-id="c015c-112">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="c015c-113">El servicio implementa un contrato que define un modelo de comunicación de solicitud y respuesta.</span><span class="sxs-lookup"><span data-stu-id="c015c-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c015c-114">La interfaz `ICalculator`, que expone las operaciones matemáticas (sumar, restar, multiplicar y dividir), define el contrato.</span><span class="sxs-lookup"><span data-stu-id="c015c-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="c015c-115">El cliente realiza solicitudes sincrónicas a una operación matemática determinada y el servicio responde con el resultado.</span><span class="sxs-lookup"><span data-stu-id="c015c-115">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="c015c-116">Tanto el cliente como el servicio utilizan `CustomTextMessageEncoder` en lugar del <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> predeterminado.</span><span class="sxs-lookup"><span data-stu-id="c015c-116">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="c015c-117">La implementación del codificador personalizado está compuesta de un generador de codificadores de mensajes, un codificador de mensajes, un elemento de enlace de la codificación de mensajes y un controlador de configuración. Muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c015c-117">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="c015c-118">Compilar un codificador personalizado y un generador de codificadores.</span><span class="sxs-lookup"><span data-stu-id="c015c-118">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="c015c-119">Crear un elemento de enlace para un codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="c015c-119">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="c015c-120">Utilizar la configuración de enlace personalizado para integrar los elementos de enlace personalizado.</span><span class="sxs-lookup"><span data-stu-id="c015c-120">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="c015c-121">Desarrollar un controlador de configuración personalizado para permitir la configuración del archivo de un elemento de enlace personalizado.</span><span class="sxs-lookup"><span data-stu-id="c015c-121">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c015c-122">Configurar, compilar y ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="c015c-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c015c-123">Instale ASP.NET 4,0 con el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="c015c-123">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="c015c-124">Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c015c-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="c015c-125">Para compilar la solución, siga las instrucciones de [creación de los ejemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c015c-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="c015c-126">Para ejecutar el ejemplo en una configuración de equipos única o cruzada, siga las instrucciones de [ejecución de los ejemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c015c-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="c015c-127">Generador de codificadores de mensajes y el codificador de mensajes</span><span class="sxs-lookup"><span data-stu-id="c015c-127">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="c015c-128">Cuando se abre <xref:System.ServiceModel.ServiceHost> o el canal de cliente, el componente de tiempo de diseño `CustomTextMessageBindingElement` crea `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="c015c-128">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="c015c-129">El generador crea `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="c015c-129">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="c015c-130">El codificador de mensajes funciona tanto en el modo de transmisión por secuencias como en el modo de almacenamiento en búfer.</span><span class="sxs-lookup"><span data-stu-id="c015c-130">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="c015c-131">Utiliza respectivamente <xref:System.Xml.XmlReader> y <xref:System.Xml.XmlWriter> para leer y escribir mensajes respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c015c-131">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="c015c-132">En contraposición a los lectores y escritores XML optimizados de WCF que solo admiten UTF-8, UTF-16 y Big-Endian Unicode, estos lectores y escritores admiten toda la codificación compatible con la plataforma.</span><span class="sxs-lookup"><span data-stu-id="c015c-132">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="c015c-133">El ejemplo de código siguiente muestra CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="c015c-133">The following code example shows the CustomTextMessageEncoder.</span></span>

```csharp
public class CustomTextMessageEncoder : MessageEncoder
{
    private CustomTextMessageEncoderFactory factory;
    private XmlWriterSettings writerSettings;
    private string contentType;

    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)
    {
        this.factory = factory;

        this.writerSettings = new XmlWriterSettings();
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
    }

    public override string ContentType
    {
        get
        {
            return this.contentType;
        }
    }

    public override string MediaType
    {
        get
        {
            return factory.MediaType;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.factory.MessageVersion;
        }
    }

    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)
    {
        byte[] msgContents = new byte[buffer.Count];
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);
        bufferManager.ReturnBuffer(buffer.Array);

        MemoryStream stream = new MemoryStream(msgContents);
        return ReadMessage(stream, int.MaxValue);
    }

    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)
    {
        XmlReader reader = XmlReader.Create(stream);
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);
    }

    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)
    {
        MemoryStream stream = new MemoryStream();
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();

        byte[] messageBytes = stream.GetBuffer();
        int messageLength = (int)stream.Position;
        stream.Close();

        int totalLength = messageLength + messageOffset;
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);

        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);
        return byteArray;
    }

    public override void WriteMessage(Message message, Stream stream)
    {
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();
    }
}
```

<span data-ttu-id="c015c-134">El ejemplo de código siguiente muestra cómo compilar el generador de codificadores de mensajes.</span><span class="sxs-lookup"><span data-stu-id="c015c-134">The following code example shows how to build the message encoder factory.</span></span>

```csharp
public class CustomTextMessageEncoderFactory : MessageEncoderFactory
{
    private MessageEncoder encoder;
    private MessageVersion version;
    private string mediaType;
    private string charSet;

    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,
        MessageVersion version)
    {
        this.version = version;
        this.mediaType = mediaType;
        this.charSet = charSet;
        this.encoder = new CustomTextMessageEncoder(this);
    }

    public override MessageEncoder Encoder
    {
        get
        {
            return this.encoder;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.version;
        }
    }

    internal string MediaType
    {
        get
        {
            return this.mediaType;
        }
    }

    internal string CharSet
    {
        get
        {
            return this.charSet;
        }
    }
}
```

## <a name="message-encoding-binding-element"></a><span data-ttu-id="c015c-135">Elemento de enlace de codificación de mensajes</span><span class="sxs-lookup"><span data-stu-id="c015c-135">Message Encoding Binding Element</span></span>

<span data-ttu-id="c015c-136">Los elementos de enlace permiten la configuración de la pila en tiempo de ejecución de WCF.</span><span class="sxs-lookup"><span data-stu-id="c015c-136">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="c015c-137">Para usar el codificador de mensajes personalizado en una aplicación WCF, se requiere un elemento de enlace que cree el generador del codificador del mensaje con la configuración adecuada en el nivel adecuado en la pila en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="c015c-137">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="c015c-138">`CustomTextMessageBindingElement` deriva de la clase base <xref:System.ServiceModel.Channels.BindingElement> y hereda de la clase <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c015c-138">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="c015c-139">Esto permite que otros componentes de WCF reconozcan este elemento de enlace como un elemento de enlace de codificación de mensajes.</span><span class="sxs-lookup"><span data-stu-id="c015c-139">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="c015c-140">La implementación de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> devuelve una instancia del generador de codificadores de mensajes coincidente con los valores adecuados.</span><span class="sxs-lookup"><span data-stu-id="c015c-140">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="c015c-141">`CustomTextMessageBindingElement` expone los valores para `MessageVersion`, `ContentType` y `Encoding` a través de las propiedades.</span><span class="sxs-lookup"><span data-stu-id="c015c-141">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="c015c-142">El codificador admite tanto las versiones Soap11Addressing como Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="c015c-142">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="c015c-143">El valor predeterminado es Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="c015c-143">The default is Soap11Addressing1.</span></span> <span data-ttu-id="c015c-144">El valor predeterminado de `ContentType` se establece como "text/xml".</span><span class="sxs-lookup"><span data-stu-id="c015c-144">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="c015c-145">La propiedad `Encoding` le permite establecer el valor de la codificación de caracteres deseada.</span><span class="sxs-lookup"><span data-stu-id="c015c-145">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="c015c-146">El cliente y el servicio de ejemplo utilizan la codificación de caracteres ISO-8859-1 (latin1), que no es compatible con <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> de WCF.</span><span class="sxs-lookup"><span data-stu-id="c015c-146">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="c015c-147">El código siguiente muestra cómo crear mediante programación el enlace usando el codificador de mensajes de texto personalizado.</span><span class="sxs-lookup"><span data-stu-id="c015c-147">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="c015c-148">Adición de compatibilidad de metadatos al elemento de enlace de la codificación de mensajes</span><span class="sxs-lookup"><span data-stu-id="c015c-148">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="c015c-149">Cualquier tipo que deriva de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> es responsable de actualizar la versión del enlace SOAP en el documento WSDL generado para el servicio.</span><span class="sxs-lookup"><span data-stu-id="c015c-149">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="c015c-150">Esto se hace implementando el método `ExportEndpoint` en la interfaz <xref:System.ServiceModel.Description.IWsdlExportExtension> y modificando a continuación el WSDL generado.</span><span class="sxs-lookup"><span data-stu-id="c015c-150">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="c015c-151">En este ejemplo, `CustomTextMessageBindingElement` utiliza la lógica de exportación de WSDL desde `TextMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="c015c-151">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="c015c-152">Para este ejemplo, la configuración del cliente se hace manualmente.</span><span class="sxs-lookup"><span data-stu-id="c015c-152">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="c015c-153">No puede utilizar Svcutil.exe para generar la configuración del cliente porque `CustomTextMessageBindingElement` no exporta una aserción de directiva para describir su comportamiento.</span><span class="sxs-lookup"><span data-stu-id="c015c-153">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="c015c-154">Generalmente debería implementar la interfaz <xref:System.ServiceModel.Description.IPolicyExportExtension> en un elemento de enlace personalizado para exportar una aserción de directiva personalizada que describa el comportamiento o la función implementada por el elemento de enlace.</span><span class="sxs-lookup"><span data-stu-id="c015c-154">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="c015c-155">Para obtener un ejemplo de cómo exportar una aserción de directiva para un elemento de enlace personalizado, vea el ejemplo [Transport: UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="c015c-155">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="c015c-156">Controlador de configuración de enlace de codificación de mensajes</span><span class="sxs-lookup"><span data-stu-id="c015c-156">Message Encoding Binding Configuration Handler</span></span>

<span data-ttu-id="c015c-157">La sección anterior muestra cómo utilizar mediante programación el codificador de mensajes de texto personalizado.</span><span class="sxs-lookup"><span data-stu-id="c015c-157">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="c015c-158">`CustomTextMessageEncodingBindingSection` implementa un controlador de configuración que le permite especificar el uso de un codificador de mensajes de texto personalizado dentro de un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="c015c-158">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="c015c-159">La clase `CustomTextMessageEncodingBindingSection` se deriva de la clase <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="c015c-159">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="c015c-160">La propiedad `BindingElementType` informa al sistema de configuración del tipo de elemento de enlace que se va a crear para esta sección.</span><span class="sxs-lookup"><span data-stu-id="c015c-160">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="c015c-161">Todos los valores definidos por `CustomTextMessageBindingElement` se exponen como propiedades en `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="c015c-161">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="c015c-162"><xref:System.Configuration.ConfigurationPropertyAttribute> ayuda en la asignación de atributos de elemento de configuración para las propiedades y en la definición de valores predeterminados si el atributo no está definido.</span><span class="sxs-lookup"><span data-stu-id="c015c-162">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="c015c-163">Después de cargar y aplicar los valores de la configuración a las propiedades del tipo, se llama al método <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A>, que convierte las propiedades en una instancia concreta de un elemento de enlace.</span><span class="sxs-lookup"><span data-stu-id="c015c-163">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="c015c-164">Este controlador de configuración asigna a la representación siguiente en App.config o Web.config para el servicio o cliente.</span><span class="sxs-lookup"><span data-stu-id="c015c-164">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="c015c-165">El ejemplo utiliza la codificación ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="c015c-165">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="c015c-166">Para utilizar este controlador de configuración, se debe registrar utilizando el elemento de configuración siguiente.</span><span class="sxs-lookup"><span data-stu-id="c015c-166">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
