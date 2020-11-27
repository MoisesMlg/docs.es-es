---
title: Configuración de los valores de tiempo de espera en un enlace
description: Obtenga información acerca de cómo administrar la configuración de tiempo de espera de los enlaces de WCF para mejorar el rendimiento, la facilidad de uso y la seguridad del servicio.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 6582568f3579f784d4c91c707dbb35c38533551d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284048"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="5fefa-103">Configuración de los valores de tiempo de espera en un enlace</span><span class="sxs-lookup"><span data-stu-id="5fefa-103">Configuring Timeout Values on a Binding</span></span>

<span data-ttu-id="5fefa-104">Hay varias configuraciones de tiempo de espera disponibles en los enlaces de WCF.</span><span class="sxs-lookup"><span data-stu-id="5fefa-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="5fefa-105">Establecer estas configuraciones de tiempo de espera correctamente puede mejorar no solo el rendimiento del servicio sino también desempeñar un papel en la facilidad de uso y la seguridad del servicio.</span><span class="sxs-lookup"><span data-stu-id="5fefa-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="5fefa-106">Los tiempos de espera siguientes están disponibles en los enlaces de WCF:</span><span class="sxs-lookup"><span data-stu-id="5fefa-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="5fefa-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="5fefa-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="5fefa-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="5fefa-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="5fefa-109">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="5fefa-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="5fefa-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5fefa-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="5fefa-111">Tiempos de espera de enlace de WCF</span><span class="sxs-lookup"><span data-stu-id="5fefa-111">WCF Binding Timeouts</span></span>  

 <span data-ttu-id="5fefa-112">Cada uno de los valores descritos en este tema se crea en el propio enlace, en código o configuración.</span><span class="sxs-lookup"><span data-stu-id="5fefa-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="5fefa-113">El código siguiente muestra cómo establecer mediante programación los tiempos de espera en un enlace de WCF en el contexto de un servicio autohospedado.</span><span class="sxs-lookup"><span data-stu-id="5fefa-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="5fefa-114">En el ejemplo siguiente se muestra cómo configurar tiempos de espera en un enlace en un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="5fefa-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="5fefa-115">Se puede encontrar más información sobre estos valores en la documentación de la clase <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="5fefa-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="5fefa-116">Tiempos de espera del lado cliente</span><span class="sxs-lookup"><span data-stu-id="5fefa-116">Client-side Timeouts</span></span>  

 <span data-ttu-id="5fefa-117">En el lado cliente:</span><span class="sxs-lookup"><span data-stu-id="5fefa-117">On the client side:</span></span>  
  
1. <span data-ttu-id="5fefa-118">SendTimeout – se usa para inicializar OperationTimeout, que controla el proceso completo de enviar un mensaje, incluido recibir un mensaje de respuesta para una operación de servicio de solicitud y respuesta.</span><span class="sxs-lookup"><span data-stu-id="5fefa-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="5fefa-119">Este tiempo de espera también se aplica al enviar mensajes de respuesta de un método de contrato de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="5fefa-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="5fefa-120">OpenTimeout: se usa al abrir los canales cuando no se especifica ningún valor de tiempo de espera explícito.</span><span class="sxs-lookup"><span data-stu-id="5fefa-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="5fefa-121">CloseTimeout: se usa al cerrar los canales cuando no se especifica ningún valor de tiempo de espera explícito.</span><span class="sxs-lookup"><span data-stu-id="5fefa-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="5fefa-122">ReceiveTimeout: no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="5fefa-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="5fefa-123">Tiempos de espera del servicio</span><span class="sxs-lookup"><span data-stu-id="5fefa-123">Service-side Timeouts</span></span>  

 <span data-ttu-id="5fefa-124">En el lado de servicio:</span><span class="sxs-lookup"><span data-stu-id="5fefa-124">On the service side:</span></span>  
  
1. <span data-ttu-id="5fefa-125">SendTimeout, OpenTimeout y CloseTimeout son los mismos que en el cliente.</span><span class="sxs-lookup"><span data-stu-id="5fefa-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="5fefa-126">ReceiveTimeout – lo usa el nivel de marco de trabajo de servicio para inicializar el tiempo de espera de sesión inactiva que controla cuánto tiempo puede estar inactiva una sesión antes de que se agote el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="5fefa-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
