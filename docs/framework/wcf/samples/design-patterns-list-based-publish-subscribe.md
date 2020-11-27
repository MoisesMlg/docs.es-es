---
title: 'Modelos de diseño: suscripción-publicación basada en la lista'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 4e679980df8a720eb4aa22741bbdd067940c7723
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292680"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="abbed-102">Modelos de diseño: suscripción-publicación basada en la lista</span><span class="sxs-lookup"><span data-stu-id="abbed-102">Design Patterns: List-Based Publish-Subscribe</span></span>

<span data-ttu-id="abbed-103">Este ejemplo muestra el patrón de Publish-Subscribe basado en lista implementado como un programa de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="abbed-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abbed-104">El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="abbed-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="abbed-105">El modelo de diseño de Publish-Subscribe basado en lista se describe en la publicación Microsoft Patterns & Practices, [patrones de integración](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="abbed-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="abbed-106">El patrón suscripción-publicación pasa información a una colección de destinatarios que se han suscrito a un tema de la información.</span><span class="sxs-lookup"><span data-stu-id="abbed-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="abbed-107">La suscripción-publicación basada en la lista mantiene una lista de suscriptores.</span><span class="sxs-lookup"><span data-stu-id="abbed-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="abbed-108">Cuando hay información para compartir, se envía una copia a cada suscriptor en la lista.</span><span class="sxs-lookup"><span data-stu-id="abbed-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="abbed-109">Este ejemplo muestra un patrón dinámico de suscripción-publicación basada en la lista, donde los clientes pueden suscribirse o cancelar su suscripción tan a menudo como sea necesario.</span><span class="sxs-lookup"><span data-stu-id="abbed-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="abbed-110">El ejemplo de suscripción-publicación basada en la lista está compuesto de un cliente, un servicio y un programa de origen de datos.</span><span class="sxs-lookup"><span data-stu-id="abbed-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="abbed-111">Puede haber más de un cliente y más de un funcionamiento de programa de origen de datos.</span><span class="sxs-lookup"><span data-stu-id="abbed-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="abbed-112">Los clientes se suscriben al servicio, reciben las notificaciones y cancelan su suscripción.</span><span class="sxs-lookup"><span data-stu-id="abbed-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="abbed-113">Los programas de origen de datos envían información al servicio para a compartir con todos los suscriptores actuales.</span><span class="sxs-lookup"><span data-stu-id="abbed-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="abbed-114">En este ejemplo, el cliente y el origen de datos son los programas de consola (archivos .exe) y el servicio es una biblioteca (.dll) hospedada en IIS (Servicios de Internet Information Server) (IIS).</span><span class="sxs-lookup"><span data-stu-id="abbed-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="abbed-115">El cliente y la actividad de origen de datos están visibles en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="abbed-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="abbed-116">El servicio utiliza la comunicación dúplex.</span><span class="sxs-lookup"><span data-stu-id="abbed-116">The service uses duplex communication.</span></span> <span data-ttu-id="abbed-117">El contrato de servicios `ISampleContract` se empareja a con un contrato de devolución de llamada `ISampleClientCallback`.</span><span class="sxs-lookup"><span data-stu-id="abbed-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="abbed-118">El servicio implementa la operaciones del servicio Suscripción y Cancelación, que los clientes utilizan para unirse a la lista de suscriptores o para dejar la misma.</span><span class="sxs-lookup"><span data-stu-id="abbed-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="abbed-119">El servicio también implementa la operación de servicio `PublishPriceChange` que el programa de origen de datos llama para proporcionar la nueva información al servicio.</span><span class="sxs-lookup"><span data-stu-id="abbed-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="abbed-120">El programa cliente implementa la operación de servicio `PriceChange` a la que el servicio llama para notificar a todos los suscriptores de un cambio del precio.</span><span class="sxs-lookup"><span data-stu-id="abbed-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```csharp  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="abbed-121">El servicio utiliza un evento de .NET Framework como mecanismo para informar a todos los suscriptores sobre la nueva información.</span><span class="sxs-lookup"><span data-stu-id="abbed-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="abbed-122">Cuando un cliente se une el servicio llamando a Suscripción, proporciona un controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="abbed-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="abbed-123">Cuando un cliente sale de la lista, cancela la suscripción de su controlador de eventos desde el evento.</span><span class="sxs-lookup"><span data-stu-id="abbed-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="abbed-124">Cuando un origen de datos llama al servicio para crear un informe sobre un cambio de precio, el servicio genera el evento.</span><span class="sxs-lookup"><span data-stu-id="abbed-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="abbed-125">Esto llama a cada instancia del servicio, una para cada cliente que se ha suscrito, y hace que sus controladores de eventos se ejecuten.</span><span class="sxs-lookup"><span data-stu-id="abbed-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="abbed-126">Cada controlador de eventos pasa la información a su cliente a través de su función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="abbed-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```csharp
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="abbed-127">Al ejecutar el ejemplo, se inician varios clientes.</span><span class="sxs-lookup"><span data-stu-id="abbed-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="abbed-128">Los clientes se suscriben al servicio.</span><span class="sxs-lookup"><span data-stu-id="abbed-128">The clients subscribe to the service.</span></span> <span data-ttu-id="abbed-129">A continuación, ejecute el programa de origen de datos, que envía información al servicio.</span><span class="sxs-lookup"><span data-stu-id="abbed-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="abbed-130">El servicio pasa la información a todos los suscriptores.</span><span class="sxs-lookup"><span data-stu-id="abbed-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="abbed-131">Puede ver la actividad en cada consola del cliente que confirma que se ha recibido la información.</span><span class="sxs-lookup"><span data-stu-id="abbed-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="abbed-132">Presione ENTRAR en la ventana de cliente para cerrar el cliente.</span><span class="sxs-lookup"><span data-stu-id="abbed-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="abbed-133">Para configurar y compilar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="abbed-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="abbed-134">Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="abbed-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="abbed-135">Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="abbed-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="abbed-136">Para ejecutar el ejemplo en el mismo equipo</span><span class="sxs-lookup"><span data-stu-id="abbed-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="abbed-137">Pruebe que puede tener acceso al servicio mediante un explorador escribiendo la dirección siguiente: `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="abbed-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="abbed-138">Como respuesta se debe mostrar una página de confirmación.</span><span class="sxs-lookup"><span data-stu-id="abbed-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="abbed-139">Ejecute Client.exe desde \client\bin\ \\ , en la carpeta específica del lenguaje.</span><span class="sxs-lookup"><span data-stu-id="abbed-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="abbed-140">La actividad del cliente se muestra en la ventana de consola del cliente.</span><span class="sxs-lookup"><span data-stu-id="abbed-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="abbed-141">Inicie varios clientes.</span><span class="sxs-lookup"><span data-stu-id="abbed-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="abbed-142">Ejecute Datasource.exe desde \datasource\bin \\ , en la carpeta específica del lenguaje.</span><span class="sxs-lookup"><span data-stu-id="abbed-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="abbed-143">La actividad del origen de los datos se muestra en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="abbed-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="abbed-144">Cuando el origen de datos envía la información al servicio, se debería pasar a cada cliente.</span><span class="sxs-lookup"><span data-stu-id="abbed-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="abbed-145">Si el cliente, el origen de datos y los programas de servicio no pueden comunicarse, vea [sugerencias para la solución de problemas de ejemplos de WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="abbed-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="abbed-146">Para ejecutar el ejemplo en los equipos</span><span class="sxs-lookup"><span data-stu-id="abbed-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="abbed-147">Preparar el equipo del servicio:</span><span class="sxs-lookup"><span data-stu-id="abbed-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="abbed-148">En el equipo del servicio, cree un directorio virtual denominado ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="abbed-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="abbed-149">El archivo por lotes Setupvroot.bat del [procedimiento de instalación único para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md) se puede usar para crear el directorio de disco y el directorio virtual.</span><span class="sxs-lookup"><span data-stu-id="abbed-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="abbed-150">Copie los archivos de programa de servicio del directorio %SystemDrive%\Inetpub \wwwroot\servicemodelsamples al directorio virtual ServiceModelSamples del equipo de servicio.</span><span class="sxs-lookup"><span data-stu-id="abbed-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="abbed-151">Asegúrese de incluir los archivos en el directorio \bin.</span><span class="sxs-lookup"><span data-stu-id="abbed-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="abbed-152">Pruebe que puede tener acceso al servicio desde el equipo cliente utilizando un explorador.</span><span class="sxs-lookup"><span data-stu-id="abbed-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="abbed-153">Preparar los equipos cliente:</span><span class="sxs-lookup"><span data-stu-id="abbed-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="abbed-154">Copie los archivos de programa del cliente de la carpeta \client\bin\, bajo la carpeta específica del lenguaje, a los equipos del cliente.</span><span class="sxs-lookup"><span data-stu-id="abbed-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="abbed-155">En cada archivo de configuración del cliente, cambie el valor de la dirección de la definición del punto de conexión para que coincida con la nueva dirección de su servicio.</span><span class="sxs-lookup"><span data-stu-id="abbed-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="abbed-156">Reemplace cualquier referencia a "localhost" con un nombre de dominio completo en la dirección.</span><span class="sxs-lookup"><span data-stu-id="abbed-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="abbed-157">Preparar el equipo del origen de datos:</span><span class="sxs-lookup"><span data-stu-id="abbed-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="abbed-158">Copie los archivos de programa de origen de datos de la carpeta \ datasource \bin\, en la carpeta específica del lenguaje, al equipo del origen de datos.</span><span class="sxs-lookup"><span data-stu-id="abbed-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="abbed-159">En el archivo de configuración del origen de datos, cambie el valor de la dirección de la definición del punto de conexión para que coincida con la nueva dirección de su servicio.</span><span class="sxs-lookup"><span data-stu-id="abbed-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="abbed-160">Reemplace cualquier referencia a "localhost" con un nombre de dominio completo en la dirección.</span><span class="sxs-lookup"><span data-stu-id="abbed-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="abbed-161">En los equipos cliente, inicie Client.exe desde el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="abbed-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="abbed-162">En el equipo del origen de datos, inicie Datasource.exe desde un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="abbed-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="abbed-163">Puede que los ejemplos ya estén instalados en su equipo.</span><span class="sxs-lookup"><span data-stu-id="abbed-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="abbed-164">Compruebe el siguiente directorio (predeterminado) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="abbed-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="abbed-165">Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos.</span><span class="sxs-lookup"><span data-stu-id="abbed-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="abbed-166">Este ejemplo se encuentra en el siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="abbed-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`
