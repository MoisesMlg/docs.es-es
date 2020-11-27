---
title: Operaciones sincrónicas y asincrónicas
description: Obtenga información sobre cómo implementar y llamar a operaciones de servicio asincrónicas. Los servicios y clientes WCF pueden usar operaciones asincrónicas en dos niveles de la aplicación.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: f14e206bb99215a7a9b2535f99feb9971274532b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254199"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="2a248-104">Operaciones sincrónicas y asincrónicas</span><span class="sxs-lookup"><span data-stu-id="2a248-104">Synchronous and Asynchronous Operations</span></span>

<span data-ttu-id="2a248-105">Este tema explica cómo implementar y llamar a operaciones de servicio asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="2a248-105">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="2a248-106">Muchas aplicaciones llaman a métodos de forma asincrónica porque permite que la aplicación siga realizando un trabajo útil mientras la llamada al método se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="2a248-106">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="2a248-107">Los servicios y clientes de Windows Communication Foundation (WCF) pueden participar en llamadas de operación asincrónica en dos niveles distintos de la aplicación, que proporcionan a las aplicaciones de WCF aún más flexibilidad para maximizar el rendimiento equilibrado con interactividad.</span><span class="sxs-lookup"><span data-stu-id="2a248-107">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="2a248-108">Tipos de operaciones asincrónicas</span><span class="sxs-lookup"><span data-stu-id="2a248-108">Types of Asynchronous Operations</span></span>  

 <span data-ttu-id="2a248-109">Todos los contratos de servicio en WCF, independientemente de los tipos y los valores devueltos de los parámetros, usan atributos de WCF para especificar un patrón de intercambio de mensajes determinado entre el cliente y el servicio.</span><span class="sxs-lookup"><span data-stu-id="2a248-109">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="2a248-110">WCF enruta automáticamente los mensajes de entrada y de salida a la operación de servicio o al código de cliente adecuado.</span><span class="sxs-lookup"><span data-stu-id="2a248-110">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="2a248-111">El cliente posee solo el contrato de servicio, que especifica el patrón de intercambio de mensajes para una operación determinada.</span><span class="sxs-lookup"><span data-stu-id="2a248-111">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="2a248-112">Los clientes pueden ofrecer cualquier modelo de programación que elijan al programador, siempre y cuando se observe el patrón de intercambio de mensajes subyacente.</span><span class="sxs-lookup"><span data-stu-id="2a248-112">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="2a248-113">Así, también, los servicios pueden implementar operaciones de cualquier manera, siempre que se observe el patrón del mensaje especificado.</span><span class="sxs-lookup"><span data-stu-id="2a248-113">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="2a248-114">La independencia del contrato de servicio del servicio o de la implementación del cliente habilita los formularios siguientes de ejecución asincrónica en aplicaciones de WCF:</span><span class="sxs-lookup"><span data-stu-id="2a248-114">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="2a248-115">Los clientes pueden invocar operaciones de solicitud/respuesta asincrónicamente mediante un intercambio de mensajes sincrónico.</span><span class="sxs-lookup"><span data-stu-id="2a248-115">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="2a248-116">Los servicios pueden implementar una operación de solicitud/respuesta asincrónicamente mediante un intercambio de mensajes sincrónico.</span><span class="sxs-lookup"><span data-stu-id="2a248-116">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="2a248-117">Los intercambios de mensajes pueden ser unidireccionales, sin tener en cuenta la implementación del cliente o servicio.</span><span class="sxs-lookup"><span data-stu-id="2a248-117">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="2a248-118">Escenarios asincrónicos sugeridos</span><span class="sxs-lookup"><span data-stu-id="2a248-118">Suggested Asynchronous Scenarios</span></span>  

 <span data-ttu-id="2a248-119">Use un enfoque asincrónico en una implementación de operación de servicio si la implementación del servicio de la operación realiza una llamada en bloque, como al realizar operaciones de E/S.</span><span class="sxs-lookup"><span data-stu-id="2a248-119">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="2a248-120">En una implementación de operación asincrónica, intente llamar a métodos y operaciones asincrónicos para extender la ruta de acceso de la llamada asincrónica al máximo.</span><span class="sxs-lookup"><span data-stu-id="2a248-120">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="2a248-121">Por ejemplo, llame a una `BeginOperationTwo()` desde `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="2a248-121">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="2a248-122">Use un enfoque asincrónico en una aplicación de cliente o que realiza la llamada en los casos siguientes:</span><span class="sxs-lookup"><span data-stu-id="2a248-122">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="2a248-123">Si invoca operaciones desde una aplicación de nivel intermedio.</span><span class="sxs-lookup"><span data-stu-id="2a248-123">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="2a248-124">(Para obtener más información acerca de estos escenarios, vea [Aplicaciones cliente de nivel intermedio](./feature-details/middle-tier-client-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="2a248-124">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="2a248-125">Si invoca operaciones desde una página ASP.NET, use páginas asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="2a248-125">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="2a248-126">Si invoca operaciones desde cualquier aplicación de proceso simple, como Windows Forms o Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="2a248-126">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="2a248-127">Si utiliza el modelo de llamada asincrónica basado en evento, el evento resultante se genera en el proceso de interfaz de usuario, agregando capacidad de respuesta a la aplicación sin que sea necesario controlar procesos múltiples.</span><span class="sxs-lookup"><span data-stu-id="2a248-127">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="2a248-128">En general, si puede elegir entre una llamada sincrónica y una asincrónica, elija la asincrónica.</span><span class="sxs-lookup"><span data-stu-id="2a248-128">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="2a248-129">Implementar una operación de servicio asincrónica</span><span class="sxs-lookup"><span data-stu-id="2a248-129">Implementing an Asynchronous Service Operation</span></span>  

 <span data-ttu-id="2a248-130">Las operaciones asincrónicas se pueden implementar mediante uno de los tres métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="2a248-130">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="2a248-131">El patrón asincrónico basado en tareas</span><span class="sxs-lookup"><span data-stu-id="2a248-131">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="2a248-132">El patrón asincrónico basado en eventos</span><span class="sxs-lookup"><span data-stu-id="2a248-132">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="2a248-133">El patrón asincrónico de IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="2a248-133">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="2a248-134">Modelo asincrónico basado en tareas</span><span class="sxs-lookup"><span data-stu-id="2a248-134">Task-Based Asynchronous Pattern</span></span>  

 <span data-ttu-id="2a248-135">El patrón asincrónico basado en tareas es la forma recomendada de implementar operaciones asincrónicas porque es la más sencilla.</span><span class="sxs-lookup"><span data-stu-id="2a248-135">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="2a248-136">Para usar este método, implemente simplemente la operación de servicio y especifique un tipo de valor devuelto de task \<T> , donde T es el tipo devuelto por la operación lógica.</span><span class="sxs-lookup"><span data-stu-id="2a248-136">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="2a248-137">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2a248-137">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService
{
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)
   {
      return Task<string>.Factory.StartNew(() =>
      {
         return msg;
      });
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="2a248-138">La operación SampleMethodTaskAsync devuelve task \<string> porque la operación lógica devuelve una cadena.</span><span class="sxs-lookup"><span data-stu-id="2a248-138">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="2a248-139">Para obtener más información sobre el patrón asincrónico basado en tareas, [Información general sobre el patrón asincrónico basado en tareas](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="2a248-139">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2a248-140">Cuando se usa el patrón asincrónico basado en tareas, se puede iniciar T:System.AggregateException si se produce una excepción mientras se espera la finalización de la operación.</span><span class="sxs-lookup"><span data-stu-id="2a248-140">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="2a248-141">Esta excepción puede producirse en el cliente o servicios</span><span class="sxs-lookup"><span data-stu-id="2a248-141">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="2a248-142">Patrón asincrónico basado en eventos</span><span class="sxs-lookup"><span data-stu-id="2a248-142">Event-Based Asynchronous Pattern</span></span>  

 <span data-ttu-id="2a248-143">Todo servicio que admita el modelo asincrónico basado en eventos tendrá una o varias operaciones denominadas MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="2a248-143">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="2a248-144">Estos métodos pueden reflejar versiones sincrónicas, que desempeñan la misma operación en el subproceso actual.</span><span class="sxs-lookup"><span data-stu-id="2a248-144">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="2a248-145">La clase también puede tener un evento MethodNameCompleted y un método MethodNameAsyncCancel (o simplemente CancelAsync).</span><span class="sxs-lookup"><span data-stu-id="2a248-145">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="2a248-146">Un cliente que desea llamar a la operación definirá un controlador de eventos para que se llame cuando la operación se complete,</span><span class="sxs-lookup"><span data-stu-id="2a248-146">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="2a248-147">El fragmento de código siguiente muestra cómo declarar operaciones asincrónicas mediante el patrón asincrónico basado en eventos.</span><span class="sxs-lookup"><span data-stu-id="2a248-147">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="2a248-148">Para obtener más información sobre el modelo asincrónico basado en eventos, [Información general sobre el modelo asincrónico basado en eventos](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2a248-148">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="2a248-149">Modelo asincrónico de IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="2a248-149">IAsyncResult Asynchronous Pattern</span></span>  

 <span data-ttu-id="2a248-150">Una operación de servicio se puede implementar de forma asincrónica mediante el .NET Framework modelo de programación asincrónico y marcando el `<Begin>` método con la <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> propiedad establecida en `true` .</span><span class="sxs-lookup"><span data-stu-id="2a248-150">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="2a248-151">En este caso, la operación asincrónica se expone en metadatos de la misma manera que una operación sincrónica: se expone como una operación única con un mensaje de solicitud y un mensaje de respuesta correlativo.</span><span class="sxs-lookup"><span data-stu-id="2a248-151">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="2a248-152">Los modelos de programación de cliente tienen entonces una opción.</span><span class="sxs-lookup"><span data-stu-id="2a248-152">Client programming models then have a choice.</span></span> <span data-ttu-id="2a248-153">Pueden representar este patrón como una operación sincrónica o como una asincrónica, siempre que se origine un intercambio de mensajes solicitud-respuesta cuando se invoque el servicio.</span><span class="sxs-lookup"><span data-stu-id="2a248-153">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="2a248-154">En general, con la naturaleza asincrónica de los sistemas, no se debería adoptar la dependencia de los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="2a248-154">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="2a248-155">La manera más fiable de pasar los datos a varias fases del procesamiento de envío de la operación es usar extensiones.</span><span class="sxs-lookup"><span data-stu-id="2a248-155">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="2a248-156">Para ver un ejemplo, consulte [Cómo implementar una operación de servicios asincrónica](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2a248-156">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="2a248-157">Para definir una operación de contrato `X` que se ejecuta asincrónicamente sin tener en cuenta cómo se llama en la aplicación cliente:</span><span class="sxs-lookup"><span data-stu-id="2a248-157">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="2a248-158">Defina dos métodos mediante el patrón `BeginOperation` y `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="2a248-158">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="2a248-159">El método `BeginOperation` incluye parámetros `in` y `ref` para la operación y devuelve un tipo <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="2a248-159">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="2a248-160">El método `EndOperation` incluye un parámetro <xref:System.IAsyncResult> así como los parámetros `out` y `ref` y devuelve el tipo de valor devuelto de las operaciones.</span><span class="sxs-lookup"><span data-stu-id="2a248-160">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="2a248-161">Por ejemplo, vea el método siguiente.</span><span class="sxs-lookup"><span data-stu-id="2a248-161">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="2a248-162">Para crear una operación asincrónica, los dos métodos serían:</span><span class="sxs-lookup"><span data-stu-id="2a248-162">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="2a248-163">El atributo <xref:System.ServiceModel.OperationContractAttribute> se aplica solamente a los métodos de `BeginDoWork`.</span><span class="sxs-lookup"><span data-stu-id="2a248-163">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="2a248-164">El contrato resultante tiene una operación WSDL denominada `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="2a248-164">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="2a248-165">Llamadas asincrónicas del cliente</span><span class="sxs-lookup"><span data-stu-id="2a248-165">Client-Side Asynchronous Invocations</span></span>  

 <span data-ttu-id="2a248-166">Una aplicación cliente de WCF puede usar cualquiera de los tres modelos de llamada asincrónica descritos previamente</span><span class="sxs-lookup"><span data-stu-id="2a248-166">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="2a248-167">Cuando se usa el modelo basado en tareas, basta con llamar a la operación mediante la palabra clave await como se muestra en el fragmento de código siguiente.</span><span class="sxs-lookup"><span data-stu-id="2a248-167">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="2a248-168">El uso del patrón asincrónico basado en eventos solo requiere agregar un controlador de eventos para recibir una notificación de la respuesta, y el evento resultante se genera automáticamente en el subproceso de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="2a248-168">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="2a248-169">Para aplicar este enfoque, especifique las opciones de comando **/async** y **/tcv:Version35** con la [Herramienta de utilidad de metadatos ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), como en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="2a248-169">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="2a248-170">Una vez hecho esto, Svcutil.exe genera una clase de cliente de WCF con la infraestructura de cliente que permite a la aplicación de llamada implementar y asignar un controlador de eventos para recibir la respuesta y realizar la acción apropiada.</span><span class="sxs-lookup"><span data-stu-id="2a248-170">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="2a248-171">Para ver un ejemplo completo, consulte [Llamada a operaciones de servicio de forma asincrónica](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="2a248-171">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="2a248-172">El modelo asincrónico basado en eventos, sin embargo, solo está disponible en .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="2a248-172">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="2a248-173">Además, no se admite incluso en .NET Framework 3,5 cuando se crea un canal de cliente de WCF mediante <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2a248-173">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2a248-174">Con objetos de canal de cliente de WCF, debe utilizar objetos <xref:System.IAsyncResult?displayProperty=nameWithType> para invocar sus operaciones asincrónicamente.</span><span class="sxs-lookup"><span data-stu-id="2a248-174">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="2a248-175">Para aplicar este enfoque, especifique la opción de comando **/async** con la [Herramienta de utilidad de metadatos ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), como en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="2a248-175">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="2a248-176">Esto genera un contrato de servicio en el cual cada operación se modela como un método `<Begin>` con la propiedad <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> establecida en `true` y un método `<End>` correspondiente.</span><span class="sxs-lookup"><span data-stu-id="2a248-176">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="2a248-177">Para ver un ejemplo completo en el que se usa <xref:System.ServiceModel.ChannelFactory%601>, consulte [Llamada a operaciones de manera asincrónica mediante un generador de canales](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="2a248-177">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="2a248-178">En cualquier caso, las aplicaciones pueden invocar una operación asincrónicamente aun cuando se implementa el servicio sincrónicamente, del mismo modo que una aplicación puede usar el mismo patrón para invocar de forma asincrónica un método sincrónico local.</span><span class="sxs-lookup"><span data-stu-id="2a248-178">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="2a248-179">El modo en que se implementa la operación no es significativo para el cliente; Cuando llega el mensaje de respuesta, su contenido se envía al método> <asincrónico del cliente `End` y el cliente recupera la información.</span><span class="sxs-lookup"><span data-stu-id="2a248-179">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="2a248-180">Patrones de intercambio de mensajes unidireccional</span><span class="sxs-lookup"><span data-stu-id="2a248-180">One-Way Message Exchange Patterns</span></span>  

 <span data-ttu-id="2a248-181">También puede crear un patrón de intercambio de mensajes asincrónico en el que las operaciones unidireccionales (las operaciones para las que <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> es `true` no tienen ninguna respuesta puesta en correlación) se pueden enviar en cualquier dirección por el cliente o por el servicio, independientemente del otro lado.</span><span class="sxs-lookup"><span data-stu-id="2a248-181">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="2a248-182">(Usa el patrón de intercambio de mensajes dúplex con mensajes unidireccionales). En este caso, el contrato de servicio especifica un intercambio de mensajes unidireccional que cualquier lado puede implementar como llamadas o implementaciones asincrónicas, o no, según corresponda.</span><span class="sxs-lookup"><span data-stu-id="2a248-182">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="2a248-183">Por lo general, cuando el contrato es un intercambio de mensajes unidireccionales, las implementaciones pueden ser muchas veces asincrónicas porque una vez se envía un mensaje, la aplicación no espera a una respuesta y puede continuar haciendo otro trabajo.</span><span class="sxs-lookup"><span data-stu-id="2a248-183">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="2a248-184">Clientes asincrónicos y contratos de mensajes basados en eventos</span><span class="sxs-lookup"><span data-stu-id="2a248-184">Event-based Asynchronous Clients and Message Contracts</span></span>  

 <span data-ttu-id="2a248-185">Las directrices de diseño del modelo asincrónico basado en eventos afirman que si se devuelve más de un valor, uno de los valores se devuelve como propiedad `Result` y los demás se devuelven como propiedades del objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2a248-185">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="2a248-186">De esto resulta que si un cliente importa metadatos mediante opciones de comando asincrónicas basadas en eventos y la operación devuelve más de un valor, el objeto <xref:System.EventArgs> predeterminado devuelve un valor como propiedad `Result` y el resto son propiedades del objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2a248-186">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="2a248-187">Si desea recibir el objeto del mensaje como propiedad `Result` y que los valores devueltos sean propiedades de ese objeto, use la opción de comando **/messageContract**.</span><span class="sxs-lookup"><span data-stu-id="2a248-187">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="2a248-188">Esto genera una firma que devuelve el mensaje de respuesta como la propiedad `Result` del objeto <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="2a248-188">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="2a248-189">Todos los valores de devolución internos se convierten, pues, en propiedades del objeto de mensaje de respuesta.</span><span class="sxs-lookup"><span data-stu-id="2a248-189">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a248-190">Vea también</span><span class="sxs-lookup"><span data-stu-id="2a248-190">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
