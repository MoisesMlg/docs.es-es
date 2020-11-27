---
title: Cómo usar los filtros
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 149c0809820d6a4a9c8dabfb545258b9a3ffb40b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280850"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="35293-102">Cómo usar los filtros</span><span class="sxs-lookup"><span data-stu-id="35293-102">How To: Use Filters</span></span>

<span data-ttu-id="35293-103">Este tema describe los pasos básicos necesarios para crear una configuración de enrutamiento que utiliza múltiples filtros.</span><span class="sxs-lookup"><span data-stu-id="35293-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="35293-104">En este ejemplo, los mensajes se enrutan a dos implementaciones de un servicio de la calculadora, regularCalc y roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="35293-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="35293-105">Ambas implementaciones admiten las mismas operaciones; sin embargo, un servicio redondea todos los cálculos al valor entero más cercano antes de devolverlos.</span><span class="sxs-lookup"><span data-stu-id="35293-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="35293-106">Una aplicación cliente debe poder indicar si se debe utilizar la versión del redondeo del servicio; si no se especifica ninguna preferencia de servicio, la carga del mensaje se equilibra entre los dos servicios.</span><span class="sxs-lookup"><span data-stu-id="35293-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="35293-107">Las operaciones expuestas por ambos servicios son:</span><span class="sxs-lookup"><span data-stu-id="35293-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="35293-108">Agregar</span><span class="sxs-lookup"><span data-stu-id="35293-108">Add</span></span>  
  
- <span data-ttu-id="35293-109">Restar</span><span class="sxs-lookup"><span data-stu-id="35293-109">Subtract</span></span>  
  
- <span data-ttu-id="35293-110">Multiplicar</span><span class="sxs-lookup"><span data-stu-id="35293-110">Multiply</span></span>  
  
- <span data-ttu-id="35293-111">Dividir</span><span class="sxs-lookup"><span data-stu-id="35293-111">Divide</span></span>  
  
 <span data-ttu-id="35293-112">Dado que ambos servicios implementan las mismas operaciones, no puede utilizar el filtro Action porque la acción especificada en el mensaje no será única.</span><span class="sxs-lookup"><span data-stu-id="35293-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="35293-113">En su lugar, debe realizar un trabajo adicional para asegurarse de que los mensajes se enrutan a los puntos de conexión adecuados.</span><span class="sxs-lookup"><span data-stu-id="35293-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="35293-114">Determinación de datos únicos</span><span class="sxs-lookup"><span data-stu-id="35293-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="35293-115">Como ambas implementaciones del servicio administran las mismas operaciones y son prácticamente idénticas exceptuando los datos que devuelven, los datos base incluidos en mensajes enviados de las aplicaciones cliente no son lo suficientemente exclusivos como para permitirle determinar cómo enrutar la solicitud.</span><span class="sxs-lookup"><span data-stu-id="35293-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="35293-116">Sin embargo, si la aplicación cliente agrega un valor de encabezado único al mensaje, puede utilizar este valor para determinar cómo se debería enrutar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="35293-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="35293-117">En este ejemplo, si la aplicación cliente necesita procesar el mensaje mediante la calculadora de redondeo, agrega un encabezado personalizado mediante el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="35293-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="35293-118">Ahora, puede utilizar el filtro XPath para inspeccionar los mensajes de este encabezado y enrutar mensajes que contengan el encabezado al servicio roundCalc.</span><span class="sxs-lookup"><span data-stu-id="35293-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="35293-119">Además el servicio de enrutamiento expone dos extremos de servicio virtuales que se pueden utilizar con los filtros EndpointName, EndpointAddress o PrefixEndpointAddress para enrutar de forma exclusiva los mensajes entrantes a una implementación de la calculadora concreta en función del extremo al que la aplicación cliente envía la solicitud.</span><span class="sxs-lookup"><span data-stu-id="35293-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="35293-120">Definición de los puntos de conexión</span><span class="sxs-lookup"><span data-stu-id="35293-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="35293-121">Al definir los extremos utilizados por el servicio de enrutamiento, debería determinar primero la forma del canal empleado por sus clientes y servicios.</span><span class="sxs-lookup"><span data-stu-id="35293-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="35293-122">En este escenario, ambos servicios de destino utilizan un patrón de solicitud-respuesta, de modo que se utiliza <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span><span class="sxs-lookup"><span data-stu-id="35293-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="35293-123">En el siguiente ejemplo, se definen los puntos de conexión de servicio expuestos por el servicio de enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="35293-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="35293-124">Con esta configuración, el servicio de enrutamiento expone tres puntos de conexión independientes.</span><span class="sxs-lookup"><span data-stu-id="35293-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="35293-125">Según las opciones de tiempo de ejecución, la aplicación cliente envía mensajes a una de estas direcciones.</span><span class="sxs-lookup"><span data-stu-id="35293-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="35293-126">Los mensajes que llegan a uno de los puntos de conexión de servicio "virtuales" ("redondeo/calculadora" o "normal/calculadora") se reenvían a la implementación de la calculadora correspondiente.</span><span class="sxs-lookup"><span data-stu-id="35293-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="35293-127">Si la aplicación cliente no envía la solicitud a un punto de conexión determinado, el mensaje se dirige al punto de conexión general.</span><span class="sxs-lookup"><span data-stu-id="35293-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="35293-128">Independientemente del extremo elegido, la aplicación cliente también puede decidir incluir el encabezado personalizado para indicar que el mensaje se debería reenviar a la implementación de calculadora de redondeo.</span><span class="sxs-lookup"><span data-stu-id="35293-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="35293-129">El siguiente ejemplo define los extremos del cliente (destino) a los que el servicio de enrutamiento enruta los mensajes.</span><span class="sxs-lookup"><span data-stu-id="35293-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="35293-130">Estos puntos de conexión se utilizan en la tabla de filtros para indicar el punto de conexión de destino al que se envía el mensaje cuando coincide con un filtro concreto.</span><span class="sxs-lookup"><span data-stu-id="35293-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="35293-131">Definir filtros</span><span class="sxs-lookup"><span data-stu-id="35293-131">Define Filters</span></span>  
  
1. <span data-ttu-id="35293-132">Para enrutar los mensajes según el encabezado personalizado "RoundingCalculator" que la aplicación cliente agrega al mensaje, defina un filtro que use una consulta XPath para comprobar la presencia de este encabezado.</span><span class="sxs-lookup"><span data-stu-id="35293-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="35293-133">Dado que este encabezado se define mediante un espacio de nombres personalizado, agregue también una entrada de espacio de nombres que defina un prefijo de espacio de nombres personalizado "Custom" que se usa en la consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="35293-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="35293-134">En el siguiente ejemplo, se define la sección de enrutamiento necesaria, la tabla de espacio de nombres y el filtro XPath.</span><span class="sxs-lookup"><span data-stu-id="35293-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="35293-135">Este **MessageFilter** busca un encabezado RoundingCalculator en el mensaje que contiene un valor de "Rounding".</span><span class="sxs-lookup"><span data-stu-id="35293-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="35293-136">El cliente establece este encabezado para indicar que el mensaje se debería enrutar al servicio de roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="35293-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="35293-137">El prefijo de espacio de nombres S12 se define de forma predeterminada en la tabla de espacio de nombres y representa el espacio de nombres `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="35293-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="35293-138">También debe definir los filtros que buscan mensajes recibidos en los dos puntos de conexión virtuales.</span><span class="sxs-lookup"><span data-stu-id="35293-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="35293-139">El primer punto de conexión virtual es el punto de conexión "normal/calculadora".</span><span class="sxs-lookup"><span data-stu-id="35293-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="35293-140">El cliente puede enviar solicitudes a este extremo para indicar que el mensaje se debería enrutar al servicio de regularCalc.</span><span class="sxs-lookup"><span data-stu-id="35293-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="35293-141">La siguiente configuración define un filtro que utiliza <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> para determinar si el mensaje llegó a través de un punto de conexión con el nombre especificado en filterData.</span><span class="sxs-lookup"><span data-stu-id="35293-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="35293-142">Si el punto de conexión de servicio recibe un mensaje denominado "calculatorEndpoint", este filtro se evalúa como `true` .</span><span class="sxs-lookup"><span data-stu-id="35293-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="35293-143">A continuación, defina un filtro que busque los mensajes enviados a la dirección de roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="35293-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="35293-144">El cliente puede enviar solicitudes a este punto de conexión para indicar que el mensaje se debería enrutar al servicio de roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="35293-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="35293-145">La configuración siguiente define un filtro que utiliza <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> para determinar si el mensaje llegó al punto de conexión de "redondeo/calculadora".</span><span class="sxs-lookup"><span data-stu-id="35293-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="35293-146">Si se recibe un mensaje en una dirección que comienza con `http://localhost/routingservice/router/rounding/` , este filtro se evalúa como **true**.</span><span class="sxs-lookup"><span data-stu-id="35293-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="35293-147">Dado que la dirección base utilizada por esta configuración es `http://localhost/routingservice/router` y la dirección especificada para roundingEndpoint es "Rounding/Calculator", la dirección completa que se usa para comunicarse con este extremo es `http://localhost/routingservice/router/rounding/calculator` , que coincide con este filtro.</span><span class="sxs-lookup"><span data-stu-id="35293-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="35293-148">El filtro PrefixEndpointAddress no evalúa el nombre de host al realizar una coincidencia, porque se puede hacer referencia a un host único utilizando diversos nombres de host que pueden ser todos ellos métodos válidos para hacer referencia al host de la aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="35293-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="35293-149">Por ejemplo, todos los nombres siguientes pueden hacer referencia al mismo host:</span><span class="sxs-lookup"><span data-stu-id="35293-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="35293-150">localhost</span><span class="sxs-lookup"><span data-stu-id="35293-150">localhost</span></span>  
    > - <span data-ttu-id="35293-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="35293-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="35293-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="35293-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="35293-153">El filtro final debe admitir el enrutamiento de mensajes que llegan al punto de conexión general sin el encabezado personalizado.</span><span class="sxs-lookup"><span data-stu-id="35293-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="35293-154">En este escenario, los mensajes deberían alternar entre los servicios de regularCalc y roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="35293-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="35293-155">Para admitir el enrutamiento "round robin" de estos mensajes, use un filtro personalizado que permita que una instancia de filtro coincida para cada mensaje procesado.</span><span class="sxs-lookup"><span data-stu-id="35293-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="35293-156">A continuación, se definen dos instancias de RoundRobinMessageFilter, que se agrupan para indicar que deberían alternar entre sí.</span><span class="sxs-lookup"><span data-stu-id="35293-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="35293-157">Durante el tiempo de ejecución, este tipo de filtro alterna entre todas las instancias de filtro definidas de este tipo que están configuradas como el mismo grupo en una recopilación.</span><span class="sxs-lookup"><span data-stu-id="35293-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="35293-158">Esto hace que los mensajes procesados por este filtro personalizado alternen entre devolver `true` para `RoundRobinFilter1` y `RoundRobinFilter2` .</span><span class="sxs-lookup"><span data-stu-id="35293-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="35293-159">Definición de tablas de filtros</span><span class="sxs-lookup"><span data-stu-id="35293-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="35293-160">Para asociar los filtros a extremos de cliente concretos, debe colocarlos dentro de una tabla de filtros.</span><span class="sxs-lookup"><span data-stu-id="35293-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="35293-161">Este ejemplo de escenario también utiliza una configuración de prioridad de filtros, que es una configuración opcional que le permite indicar el orden en el que se procesan los filtros.</span><span class="sxs-lookup"><span data-stu-id="35293-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="35293-162">Si no se especifica ninguna prioridad de filtro, todos los filtros se evalúan simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="35293-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="35293-163">Aunque una prioridad de filtro le permite controlar el orden en el que se procesan los filtros, puede afectar negativamente al rendimiento del servicio de enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="35293-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="35293-164">Cuando sea posible, cree una lógica de filtro para que no se requiera el uso de prioridades de filtro.</span><span class="sxs-lookup"><span data-stu-id="35293-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="35293-165">A continuación se define la tabla de filtros y se agrega el "XPathFilter" definido anteriormente a la tabla con una prioridad de 2.</span><span class="sxs-lookup"><span data-stu-id="35293-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="35293-166">Esta entrada también especifica que, si `XPathFilter` coincide con el mensaje, el mensaje se enrutará a `roundingCalcEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="35293-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="35293-167">Al especificar una prioridad de filtro, los filtros con prioridad máxima se evalúan primero.</span><span class="sxs-lookup"><span data-stu-id="35293-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="35293-168">Si coinciden uno o más filtros en un nivel de prioridad concreto, no se evaluará ningún filtro en los niveles de menor prioridad.</span><span class="sxs-lookup"><span data-stu-id="35293-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="35293-169">Para este escenario, 2 es la prioridad máxima especificada y ésta es la única entrada de filtro en este nivel.</span><span class="sxs-lookup"><span data-stu-id="35293-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="35293-170">Las entradas de filtro se han definido para comprobar si se recibe un mensaje se recibe en un extremo concreto inspeccionando el nombre de extremo o el prefijo de dirección.</span><span class="sxs-lookup"><span data-stu-id="35293-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="35293-171">Las siguientes entradas suman ambas entradas de filtro a la tabla de filtros y las asocian a los puntos de conexión de destino a los que se enrutará el mensaje.</span><span class="sxs-lookup"><span data-stu-id="35293-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="35293-172">Estos filtros están establecidos con una prioridad 1 para indicar que solo se deberían ejecutar si el filtro XPath anterior no coincidiera con el mensaje.</span><span class="sxs-lookup"><span data-stu-id="35293-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="35293-173">Dado que estos filtros tienen una prioridad de filtro de 1, solo se evaluarán si el filtro de nivel de prioridad 2 no coincide con el mensaje.</span><span class="sxs-lookup"><span data-stu-id="35293-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="35293-174">Asimismo, como ambos filtros tienen el mismo nivel de prioridad, se evaluarán simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="35293-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="35293-175">Dado que ambos filtros son mutuamente excluyentes, es posible que solo uno u otro coincida con un mensaje.</span><span class="sxs-lookup"><span data-stu-id="35293-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="35293-176">Si un mensaje no coincide con ninguno de los filtros anteriores, dicho mensaje se recibió a través del punto de conexión de servicio genérico y no contenía ninguna información de encabezado que indicara dónde enrutarlo.</span><span class="sxs-lookup"><span data-stu-id="35293-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="35293-177">El filtro personalizado administrará estos mensajes para equilibrar su carga entre los dos servicios de la calculadora.</span><span class="sxs-lookup"><span data-stu-id="35293-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="35293-178">En el siguiente ejemplo, se muestra cómo agregar las entradas de filtro a la tabla de filtros; cada filtro se asocia a uno de los dos puntos de conexión de destino.</span><span class="sxs-lookup"><span data-stu-id="35293-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="35293-179">Dado que estas entradas especifican una prioridad de 0, solo se evaluarán si ningún filtro con una prioridad más alta coincide con el mensaje.</span><span class="sxs-lookup"><span data-stu-id="35293-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="35293-180">Asimismo, como ambos tienen la misma prioridad, se evaluarán simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="35293-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="35293-181">Tal y como se ha indicado previamente, el filtro personalizado utilizado por estas definiciones de filtro solo evalúa uno u otro como `true` por cada mensaje recibido.</span><span class="sxs-lookup"><span data-stu-id="35293-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="35293-182">Dado que solo se han definido dos filtros utilizando este filtro, con la misma configuración de grupo especificada, el efecto es que el servicio de enrutamiento alterna entre el envío a regularCalcEndpoint y a RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="35293-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="35293-183">Para evaluar los mensajes con respecto a los filtros, la tabla de filtros debe estar asociada primero a los puntos de conexión de servicio que se utilizarán para recibir mensajes.</span><span class="sxs-lookup"><span data-stu-id="35293-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="35293-184">En el siguiente ejemplo, se muestra cómo asociar la tabla de enrutamiento a los extremos de servicio utilizando el comportamiento de enrutamiento:</span><span class="sxs-lookup"><span data-stu-id="35293-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="35293-185">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="35293-185">Example</span></span>  

 <span data-ttu-id="35293-186">A continuación, se muestra una lista completa del archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="35293-186">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35293-187">Vea también</span><span class="sxs-lookup"><span data-stu-id="35293-187">See also</span></span>

- [<span data-ttu-id="35293-188">Servicios de enrutamiento</span><span class="sxs-lookup"><span data-stu-id="35293-188">Routing Services</span></span>](../samples/routing-services.md)
