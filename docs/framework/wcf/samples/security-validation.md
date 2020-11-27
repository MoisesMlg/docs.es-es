---
title: Validación de seguridad
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 1260aaa756e7be33ce2aa1bcce5fc79be553c990
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262624"
---
# <a name="security-validation"></a><span data-ttu-id="cf8ee-102">Validación de seguridad</span><span class="sxs-lookup"><span data-stu-id="cf8ee-102">Security validation</span></span>

<span data-ttu-id="cf8ee-103">Este ejemplo muestra cómo utilizar un comportamiento personalizado para validar los servicios en un equipo a fin de asegurarse de que cumplen criterios específicos.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="cf8ee-104">En este ejemplo, el comportamiento personalizado valida estos servicios analizando cada extremo en el servicio y comprobando si contienen elementos de enlace seguros.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="cf8ee-105">Este ejemplo se basa en el [Introducción](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ee-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf8ee-106">El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="cf8ee-107">Comportamiento personalizado de validación del punto de conexión</span><span class="sxs-lookup"><span data-stu-id="cf8ee-107">Endpoint Validation Custom Behavior</span></span>  

 <span data-ttu-id="cf8ee-108">Al agregar código de usuario al método `Validate` contenido en la interfaz <xref:System.ServiceModel.Description.IServiceBehavior>, se puede dar el comportamiento personalizado a un servicio o punto de conexión para realizar las acciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="cf8ee-109">El código siguiente se utiliza para recorrer a través de cada extremo contenido en un servicio, que busca en las colecciones de enlaces los enlaces seguros.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="cf8ee-110">Al agregar el código siguiente al archivo Web.config, se agrega la extensión de comportamiento `serviceValidate` para que el servicio la reconozca.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 <span data-ttu-id="cf8ee-111">Una vez agregada al servicio la extensión de comportamiento, ahora es posible agregar el comportamiento `endpointValidate` a la lista de comportamientos en el archivo Web.config y así al servicio.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="cf8ee-112">Los comportamientos y las extensiones que se agregan al archivo Web.config aplican el comportamiento a los servicios individuales, mientras que cuando se agregan al archivo Machine.config aplican el comportamiento a cada servicio activo del equipo.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf8ee-113">Al agregar el comportamiento a todos los servicios, la sugerencia es realizar una copia de seguridad del archivo Machine.config antes de realizar cualquier modificación.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="cf8ee-114">Ahora ejecute el cliente proporcionado en el directorio client\bin de este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="cf8ee-115">Se produce una excepción con el siguiente mensaje: "no se pudo activar el servicio solicitado," " http://localhost/servicemodelsamples/service.svc .</span><span class="sxs-lookup"><span data-stu-id="cf8ee-115">An exception is thrown with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="cf8ee-116">Se espera este mensaje porque el comportamiento que valida el punto de conexión considera inseguro al punto de conexión y evita que se inicie el servicio.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="cf8ee-117">El comportamiento también produce una excepción interna que describe qué punto de conexión es inseguro y escribe un mensaje en el visor de eventos en el origen "System.ServiceModel 4.0.0.0" y la categoría "WebHost".</span><span class="sxs-lookup"><span data-stu-id="cf8ee-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="cf8ee-118">También es posible activar el seguimiento en el servicio en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="cf8ee-119">Esto le permite al usuario ver las excepciones iniciadas por el comportamiento que valida el extremo abriendo los seguimientos de servicio resultantes mediante la herramienta Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="cf8ee-120">Ver los mensajes de excepción de validación de punto de conexión con errores en el Visor de eventos</span><span class="sxs-lookup"><span data-stu-id="cf8ee-120">View failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="cf8ee-121">Haga clic en el menú **Inicio** y seleccione **Ejecutar..**..</span><span class="sxs-lookup"><span data-stu-id="cf8ee-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="cf8ee-122">Escriba `eventvwr` y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="cf8ee-123">En la ventana de Visor de eventos, haga clic en **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="cf8ee-124">Haga doble clic en el evento "System. ServiceModel 4.0.0.0" recientemente agregado en la categoría "webhost" en la ventana de la **aplicación** para ver los mensajes de extremo no seguros.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="cf8ee-125">Configurar, compilar y ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="cf8ee-125">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cf8ee-126">Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ee-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cf8ee-127">Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ee-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cf8ee-128">Para ejecutar el ejemplo en una configuración de equipos única o cruzada, siga las instrucciones de [ejecución de los ejemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ee-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cf8ee-129">Puede que los ejemplos ya estén instalados en su equipo.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cf8ee-130">Compruebe el siguiente directorio (predeterminado) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cf8ee-131">Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf8ee-132">Este ejemplo se encuentra en el siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="cf8ee-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="cf8ee-133">Vea también</span><span class="sxs-lookup"><span data-stu-id="cf8ee-133">See also</span></span>

- <span data-ttu-id="cf8ee-134">[Ejemplos de supervisión de AppFabric](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="cf8ee-134">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
