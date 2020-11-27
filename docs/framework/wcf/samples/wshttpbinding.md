---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 6e5946dd7d107c34eafe55a62c51d089931b5b77
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252324"
---
# <a name="wshttpbinding"></a><span data-ttu-id="7e2b5-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="7e2b5-102">WSHttpBinding</span></span>

<span data-ttu-id="7e2b5-103">Este ejemplo muestra cómo implementar un servicio típico y un cliente típico mediante Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7e2b5-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="7e2b5-104">Este ejemplo está compuesto de un programa de consola de cliente (client.exe) y una biblioteca de servicios hospedada por Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="7e2b5-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7e2b5-105">El servicio implementa un contrato que define un modelo de comunicación de solicitud y respuesta.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="7e2b5-106">La interfaz `ICalculator`, que expone las operaciones matemáticas (sumar, restar, multiplicar y dividir), define el contrato.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="7e2b5-107">El cliente realiza solicitudes sincrónicas a una operación matemática determinada y el servicio responde con el resultado.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="7e2b5-108">La actividad del cliente es visible en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e2b5-109">Puede que los ejemplos ya estén instalados en su equipo.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e2b5-110">Compruebe el siguiente directorio (predeterminado) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7e2b5-111">Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e2b5-112">Este ejemplo se encuentra en el siguiente directorio.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="7e2b5-113">El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7e2b5-114">Este ejemplo expone el `ICalculator` contrato mediante [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="7e2b5-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="7e2b5-115">La configuración de este enlace se ha expandido en el archivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"
              transactionFlow="false"
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"
              textEncoding="utf-8"
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="7e2b5-116">En el elemento `binding` de base, el valor `maxReceivedMessageSize` le permite configurar el tamaño máximo de un mensaje entrante (en bytes).</span><span class="sxs-lookup"><span data-stu-id="7e2b5-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="7e2b5-117">El valor `hostNameComparisonMode` le permite configurar si se considera el nombre de host al demultiplexar los mensajes en el servicio.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="7e2b5-118">El valor `messageEncoding` le permite configurar si utilizar la codificación de texto o MTOM para los mensajes.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="7e2b5-119">El valor `textEncoding` le permite configurar la codificación de caracteres para los mensajes.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="7e2b5-120">El valor `bypassProxyOnLocal` le permite configurar si utilizar un proxy HTTP para la comunicación local.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="7e2b5-121">El valor `transactionFlow` configura si se fluye (si se configura una operación para el flujo de la transacción) la transacción actual.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="7e2b5-122">En el [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) elemento, el valor booleano habilitado configura si las sesiones confiables están habilitadas.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-122">On the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="7e2b5-123">El valor `ordered` configura si se va a conservar la clasificación del mensaje.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="7e2b5-124">El valor `inactivityTimeout` configura cuánto tiempo puede estar una sesión inactiva antes de que se produzcan errores.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="7e2b5-125">En [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) , el `mode` valor configura qué modo de seguridad se debe usar.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-125">On the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="7e2b5-126">En este ejemplo, se utiliza la seguridad de los mensajes, que es el motivo por el que [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) se especifica dentro de [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="7e2b5-126">In this sample, messages security is being used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="7e2b5-127">Al ejecutar el ejemplo, las solicitudes y respuestas de la operación se muestran en la ventana de la consola del cliente.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7e2b5-128">Presione ENTRAR en la ventana de cliente para cerrar el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e2b5-129">Configurar, compilar y ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e2b5-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7e2b5-130">Instale ASP.NET 4,0 con el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="7e2b5-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="7e2b5-131">Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e2b5-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="7e2b5-132">Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e2b5-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="7e2b5-133">Para ejecutar el ejemplo en una configuración de equipos única o cruzada, siga las instrucciones de [ejecución de los ejemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7e2b5-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
