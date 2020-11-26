---
title: Especificación de transferencia de datos en contratos de servicio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 30cdae7e15b80ca826eeea652566a535271477d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246399"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="78553-102">Especificación de transferencia de datos en contratos de servicio</span><span class="sxs-lookup"><span data-stu-id="78553-102">Specifying Data Transfer in Service Contracts</span></span>

<span data-ttu-id="78553-103">El Windows Communication Foundation (WCF) se puede considerar como una infraestructura de mensajería.</span><span class="sxs-lookup"><span data-stu-id="78553-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="78553-104">Las operaciones de servicio pueden recibir mensajes, procesarlos y enviarles mensajes.</span><span class="sxs-lookup"><span data-stu-id="78553-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="78553-105">Los mensajes se describen mediante contratos de operaciones.</span><span class="sxs-lookup"><span data-stu-id="78553-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="78553-106">Por ejemplo, considere el siguiente contrato:</span><span class="sxs-lookup"><span data-stu-id="78553-106">For example, consider the following contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 <span data-ttu-id="78553-107">Aquí, la operación `GetAirfare` acepta un mensaje con información sobre `fromCity` y `toCity`y, a continuación, devuelve un mensaje que contiene un número.</span><span class="sxs-lookup"><span data-stu-id="78553-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="78553-108">En este tema se explican las varias maneras en las que un contrato de operación puede describir los mensajes.</span><span class="sxs-lookup"><span data-stu-id="78553-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="78553-109">Descripción de mensajes mediante parámetros</span><span class="sxs-lookup"><span data-stu-id="78553-109">Describing Messages by Using Parameters</span></span>  

 <span data-ttu-id="78553-110">La manera más simple de describir un mensaje consiste en utilizar una lista de parámetros y el valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="78553-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="78553-111">En el ejemplo anterior, los parámetros de cadena `fromCity` y `toCity` se utilizaron para describir el mensaje de solicitud y el valor devuelto flotante se utilizó para describir el mensaje de respuesta.</span><span class="sxs-lookup"><span data-stu-id="78553-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="78553-112">Si el valor devuelto por sí solo no es suficiente para describir un mensaje de respuesta, se pueden utilizar parámetros out.</span><span class="sxs-lookup"><span data-stu-id="78553-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="78553-113">Por ejemplo, la siguiente operación tiene `fromCity` y `toCity` en su mensaje de solicitud y un número junto con una divisa en su mensaje de respuesta:</span><span class="sxs-lookup"><span data-stu-id="78553-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="78553-114">Además, puede utilizar parámetros de referencia para hacer que un parámetro forme parte tanto del mensaje de solicitud como del de respuesta.</span><span class="sxs-lookup"><span data-stu-id="78553-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="78553-115">Los parámetros deben ser de tipos que se pueden serializar (convertidos a XML).</span><span class="sxs-lookup"><span data-stu-id="78553-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="78553-116">De forma predeterminada, WCF usa un componente denominado <xref:System.Runtime.Serialization.DataContractSerializer> clase para realizar esta conversión.</span><span class="sxs-lookup"><span data-stu-id="78553-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="78553-117">Se admite la mayoría de datos primitivos (como `int`, `string`, `float`, y `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="78553-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="78553-118">Los tipos definidos por el usuario deben tener normalmente un contrato de datos.</span><span class="sxs-lookup"><span data-stu-id="78553-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="78553-119">Para obtener más información, consulte [uso de contratos de datos](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="78553-119">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 <span data-ttu-id="78553-120">En ocasiones, `DataContractSerializer` no es adecuado para serializar sus tipos.</span><span class="sxs-lookup"><span data-stu-id="78553-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="78553-121">WCF admite un motor de serialización alternativo, <xref:System.Xml.Serialization.XmlSerializer> que también se puede usar para serializar parámetros.</span><span class="sxs-lookup"><span data-stu-id="78553-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="78553-122"><xref:System.Xml.Serialization.XmlSerializer> le permite utilizar más control sobre el XML resultante mediante atributos como el `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="78553-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="78553-123">Para pasar a utilizar <xref:System.Xml.Serialization.XmlSerializer> para una operación determinada o para el servicio completo, aplique el atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> a una operación o un servicio.</span><span class="sxs-lookup"><span data-stu-id="78553-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="78553-124">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="78553-124">For example:</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 <span data-ttu-id="78553-125">Para obtener más información, vea [usar la clase XmlSerializer](using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="78553-125">For more information, see [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="78553-126">Recuerde que intercambiar manualmente a <xref:System.Xml.Serialization.XmlSerializer>, tal y como se muestra aquí, no se recomienda a menos que tenga razones concretas para hacerlo tal y como se detalla en ese tema.</span><span class="sxs-lookup"><span data-stu-id="78553-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="78553-127">Para aislar los nombres de parámetro .NET de los nombres de contrato, puede utilizar el atributo <xref:System.ServiceModel.MessageParameterAttribute> y utilizar la propiedad `Name` para establecer el nombre de contrato.</span><span class="sxs-lookup"><span data-stu-id="78553-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="78553-128">Por ejemplo, el contrato de operación siguiente es equivalente al primer ejemplo de este tema.</span><span class="sxs-lookup"><span data-stu-id="78553-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a><span data-ttu-id="78553-129">Descripción de mensajes vacíos</span><span class="sxs-lookup"><span data-stu-id="78553-129">Describing Empty Messages</span></span>  

 <span data-ttu-id="78553-130">Un mensaje de solicitud vacío se puede describir no teniendo ninguna entrada ni parámetro de referencia.</span><span class="sxs-lookup"><span data-stu-id="78553-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="78553-131">Por ejemplo, en C#:</span><span class="sxs-lookup"><span data-stu-id="78553-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="78553-132">Por ejemplo, en Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="78553-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="78553-133">Un mensaje de respuesta vacío se puede describir teniendo un tipo de valor devuelto `void` y ningún resultado ni parámetro de referencia.</span><span class="sxs-lookup"><span data-stu-id="78553-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="78553-134">Por ejemplo en:</span><span class="sxs-lookup"><span data-stu-id="78553-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="78553-135">Esto es diferente de una operación unidireccional, como:</span><span class="sxs-lookup"><span data-stu-id="78553-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="78553-136">La operación `SetTemperatureStatus` devuelve un mensaje vacío.</span><span class="sxs-lookup"><span data-stu-id="78553-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="78553-137">Puede devolver en su lugar un error si hay un problema al procesar un mensaje de entrada.</span><span class="sxs-lookup"><span data-stu-id="78553-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="78553-138">La operación `SetLightbulbStatus` no devuelve nada.</span><span class="sxs-lookup"><span data-stu-id="78553-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="78553-139">No hay ninguna manera de comunicar una condición de error de esta operación.</span><span class="sxs-lookup"><span data-stu-id="78553-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="78553-140">Descripción de mensajes mediante el uso de contratos de mensaje</span><span class="sxs-lookup"><span data-stu-id="78553-140">Describing Messages by Using Message Contracts</span></span>  

 <span data-ttu-id="78553-141">Puede desear utilizar un tipo único para representar el mensaje completo.</span><span class="sxs-lookup"><span data-stu-id="78553-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="78553-142">Aunque es posible de utilizar un contrato de datos para este propósito, la manera recomendada para ello consiste en utilizar un contrato de mensaje; esto evita niveles innecesarios de ajuste en el XML resultante.</span><span class="sxs-lookup"><span data-stu-id="78553-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="78553-143">Además, los contratos de mensaje le permiten ejercer más control sobre los mensajes resultantes.</span><span class="sxs-lookup"><span data-stu-id="78553-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="78553-144">Por ejemplo, puede decidir qué partes de información deberían estar en el cuerpo del mensaje y cuáles deberían estar en los encabezados del mensaje.</span><span class="sxs-lookup"><span data-stu-id="78553-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="78553-145">En el siguiente ejemplo se muestra el uso de contratos de mensaje.</span><span class="sxs-lookup"><span data-stu-id="78553-145">The following example shows the use of message contracts.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 <span data-ttu-id="78553-146">Para obtener más información, consulta [using Message Contracts](using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="78553-146">For more information, see [Using Message Contracts](using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="78553-147">En el ejemplo anterior, la clase <xref:System.Runtime.Serialization.DataContractSerializer> se sigue utilizando de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="78553-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="78553-148">La clase <xref:System.Xml.Serialization.XmlSerializer> también se puede usar con contratos de mensaje.</span><span class="sxs-lookup"><span data-stu-id="78553-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="78553-149">Para ello, aplique el atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> a la operación o al contrato y utilice tipos compatibles con la clase <xref:System.Xml.Serialization.XmlSerializer> en los encabezados del mensaje y miembros del cuerpo.</span><span class="sxs-lookup"><span data-stu-id="78553-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="78553-150">Descripción de mensajes mediante el uso de secuencias</span><span class="sxs-lookup"><span data-stu-id="78553-150">Describing Messages by Using Streams</span></span>  

 <span data-ttu-id="78553-151">Otra manera de describir mensajes en operaciones consiste en usar la clase <xref:System.IO.Stream> o una de sus clases derivadas en un contrato de operación o como miembro del cuerpo del contrato de mensaje (debe ser el único miembro en este caso).</span><span class="sxs-lookup"><span data-stu-id="78553-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="78553-152">Para los mensajes entrantes, el tipo debe ser `Stream`; no puede utilizar clases derivadas.</span><span class="sxs-lookup"><span data-stu-id="78553-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="78553-153">En lugar de invocar el serializador, WCF recupera datos de una secuencia y los coloca directamente en un mensaje saliente, o recupera datos de un mensaje entrante y los coloca directamente en un flujo.</span><span class="sxs-lookup"><span data-stu-id="78553-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="78553-154">En el siguiente ejemplo se muestra la forma de utilizar secuencias.</span><span class="sxs-lookup"><span data-stu-id="78553-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="78553-155">No puede combinar datos que no sean de secuencia y datos de `Stream` en un cuerpo de mensaje único.</span><span class="sxs-lookup"><span data-stu-id="78553-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="78553-156">Utilice un contrato de mensaje para colocar los datos adicionales en encabezados de mensaje.</span><span class="sxs-lookup"><span data-stu-id="78553-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="78553-157">El ejemplo siguiente muestra el uso incorrecto de secuencias al definir el contrato de operación.</span><span class="sxs-lookup"><span data-stu-id="78553-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 <span data-ttu-id="78553-158">El ejemplo siguiente muestra el uso correcto de los flujos al definir un contrato de operación.</span><span class="sxs-lookup"><span data-stu-id="78553-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 <span data-ttu-id="78553-159">Para obtener más información, consulte [datos y streaming de gran tamaño](large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="78553-159">For more information, see [Large Data and Streaming](large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="78553-160">Uso de la clase de mensajes</span><span class="sxs-lookup"><span data-stu-id="78553-160">Using the Message Class</span></span>  

 <span data-ttu-id="78553-161">Para tener control completo de programación sobre los mensajes enviados o recibidos, puede utilizar directamente la clase <xref:System.ServiceModel.Channels.Message>, tal y como se muestra en el siguiente código de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="78553-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="78553-162">Este es un escenario avanzado, que se describe en detalle en [uso de la clase de mensaje](using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="78553-162">This is an advanced scenario, which is described in detail in [Using the Message Class](using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="78553-163">Descripción de mensajes de error</span><span class="sxs-lookup"><span data-stu-id="78553-163">Describing Fault Messages</span></span>  

 <span data-ttu-id="78553-164">Además de los mensajes que son descritos por el valor devuelto y los parámetros de referencia o salida, cualquier operación que no sea unidireccional puede devolver al menos dos posibles mensajes: su mensaje de respuesta normal y un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="78553-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="78553-165">Considere el contrato de operación siguiente.</span><span class="sxs-lookup"><span data-stu-id="78553-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="78553-166">Esta operación puede devolver un mensaje normal que contenga un número `float` o un mensaje de error que contenga un código de error y una descripción.</span><span class="sxs-lookup"><span data-stu-id="78553-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="78553-167">Puede lograr esto generando una <xref:System.ServiceModel.FaultException> en su implementación del servicio.</span><span class="sxs-lookup"><span data-stu-id="78553-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="78553-168">Puede especificar posibles mensajes de error adicionales utilizando el atributo <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="78553-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="78553-169">Los errores adicionales se han de poder serializar mediante el <xref:System.Runtime.Serialization.DataContractSerializer>, tal y como se muestra en el código de ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="78553-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 <span data-ttu-id="78553-170">Estos errores adicionales se pueden generar mediante la generación de una <xref:System.ServiceModel.FaultException%601> del tipo de contrato de datos adecuado.</span><span class="sxs-lookup"><span data-stu-id="78553-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="78553-171">Para obtener más información, vea [controlar excepciones y errores](../extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="78553-171">For more information, see [Handling Exceptions and Faults](../extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="78553-172">No puede utilizar la clase <xref:System.Xml.Serialization.XmlSerializer> para describir los errores.</span><span class="sxs-lookup"><span data-stu-id="78553-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="78553-173">El <xref:System.ServiceModel.XmlSerializerFormatAttribute> no tiene efecto en contratos de error.</span><span class="sxs-lookup"><span data-stu-id="78553-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="78553-174">Uso de tipos derivados</span><span class="sxs-lookup"><span data-stu-id="78553-174">Using Derived Types</span></span>  

 <span data-ttu-id="78553-175">Puede desear utilizar un tipo base en una operación o un contrato de mensaje y, a continuación, utilizar un tipo derivado al invocar verdaderamente la operación.</span><span class="sxs-lookup"><span data-stu-id="78553-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="78553-176">En este caso, debe utilizar el atributo <xref:System.ServiceModel.ServiceKnownTypeAttribute> o algún mecanismo alternativo para permitir el uso de tipos derivados.</span><span class="sxs-lookup"><span data-stu-id="78553-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="78553-177">Considere la siguiente operación.</span><span class="sxs-lookup"><span data-stu-id="78553-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="78553-178">Suponga que dos tipos, `Book` y `Magazine`, derivan de `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="78553-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="78553-179">Para utilizar estos tipos en la operación `IsLibraryItemAvailable`, puede cambiar la operación tal y como sigue:</span><span class="sxs-lookup"><span data-stu-id="78553-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="78553-180">Alternativamente, puede utilizar el atributo <xref:System.Runtime.Serialization.KnownTypeAttribute> cuando el <xref:System.Runtime.Serialization.DataContractSerializer> predeterminado se esté utilizando, tal y como se muestra en el código de ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="78553-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 <span data-ttu-id="78553-181">Puede utilizar el atributo <xref:System.Xml.Serialization.XmlIncludeAttribute> al usar el <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="78553-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="78553-182">Puede aplicar el atributo <xref:System.ServiceModel.ServiceKnownTypeAttribute> a una operación o al servicio completo.</span><span class="sxs-lookup"><span data-stu-id="78553-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="78553-183">Acepta un tipo o el nombre del método para llamar para obtener una lista de tipos conocidos, como el atributo <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="78553-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="78553-184">Para obtener más información, vea [tipos conocidos de contratos de datos](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="78553-184">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="78553-185">Especificación del uso y estilo</span><span class="sxs-lookup"><span data-stu-id="78553-185">Specifying the Use and Style</span></span>  

 <span data-ttu-id="78553-186">Al describir servicios mediante el lenguaje de descripción de servicios Web (WSDL), los dos estilos utilizados comúnmente son Documento y llamada a procedimiento remoto (RPC).</span><span class="sxs-lookup"><span data-stu-id="78553-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="78553-187">En el estilo Documento, el cuerpo del mensaje completo se describe utilizando el esquema, y el WSDL describe las diversas partes del cuerpo del mensaje haciendo referencia a elementos dentro de ese esquema.</span><span class="sxs-lookup"><span data-stu-id="78553-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="78553-188">En el estilo RPC, el WSDL hace referencia a un tipo de esquema para cada parte del mensaje en lugar de a un elemento.</span><span class="sxs-lookup"><span data-stu-id="78553-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="78553-189">En algunos casos, tiene que seleccionar manualmente uno de estos estilos.</span><span class="sxs-lookup"><span data-stu-id="78553-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="78553-190">Puede hacer esto aplicando el atributo <xref:System.ServiceModel.DataContractFormatAttribute> y estableciendo la propiedad `Style` (cuando se esté usando <xref:System.Runtime.Serialization.DataContractSerializer>), o estableciendo el `Style` en el atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> (al usar el <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="78553-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="78553-191">Además, <xref:System.Xml.Serialization.XmlSerializer> admite dos formas de XML serializado: `Literal` y `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="78553-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="78553-192">`Literal` es la forma más aceptada y es el único formato que <xref:System.Runtime.Serialization.DataContractSerializer> admite.</span><span class="sxs-lookup"><span data-stu-id="78553-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="78553-193">`Encoded` es un formato heredado descrito en la sección 5 de la especificación SOAP, y no se recomienda para los nuevos servicios.</span><span class="sxs-lookup"><span data-stu-id="78553-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="78553-194">Para cambiar al modo `Encoded`, establezca la propiedad `Use` en el atributo <xref:System.ServiceModel.XmlSerializerFormatAttribute> en `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="78553-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="78553-195">En la mayoría de los casos, no debería cambiar la configuración predeterminada para el `Style` ni las propiedades `Use`.</span><span class="sxs-lookup"><span data-stu-id="78553-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="78553-196">Control del proceso de serialización</span><span class="sxs-lookup"><span data-stu-id="78553-196">Controlling the Serialization Process</span></span>  

 <span data-ttu-id="78553-197">Puede hacer varias cosas para personalizar la manera en la que se serializan los datos.</span><span class="sxs-lookup"><span data-stu-id="78553-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="78553-198">Cambio de los ajustes de serialización del servidor</span><span class="sxs-lookup"><span data-stu-id="78553-198">Changing Server Serialization Settings</span></span>  

 <span data-ttu-id="78553-199">Cuando el <xref:System.Runtime.Serialization.DataContractSerializer> predeterminado se está utilizando, puede controlar algunos aspectos del proceso de serialización en el servicio aplicando el atributo <xref:System.ServiceModel.ServiceBehaviorAttribute> al servicio.</span><span class="sxs-lookup"><span data-stu-id="78553-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="78553-200">Específicamente, puede utilizar la propiedad `MaxItemsInObjectGraph` para establecer la cuota que limita el número máximo de objetos que <xref:System.Runtime.Serialization.DataContractSerializer> deserializa.</span><span class="sxs-lookup"><span data-stu-id="78553-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="78553-201">Puede usar la propiedad `IgnoreExtensionDataObject` para desactivar la característica de control de versiones de ida y vuelta.</span><span class="sxs-lookup"><span data-stu-id="78553-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="78553-202">Para obtener más información sobre las cuotas, vea [Consideraciones de seguridad para datos](security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="78553-202">For more information about quotas, see [Security Considerations for Data](security-considerations-for-data.md).</span></span> <span data-ttu-id="78553-203">Para obtener más información acerca de los recorridos de ida y vuelta, consulte [contratos de datos compatibles con el avance](forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="78553-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a><span data-ttu-id="78553-204">Comportamientos de serialización</span><span class="sxs-lookup"><span data-stu-id="78553-204">Serialization Behaviors</span></span>  

 <span data-ttu-id="78553-205">Hay dos comportamientos disponibles en WCF, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> y <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> que se conectan automáticamente en función del serializador en uso para una operación determinada.</span><span class="sxs-lookup"><span data-stu-id="78553-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="78553-206">Dado que se aplican automáticamente estos comportamientos, normalmente no tiene que estar al tanto sobre ellos.</span><span class="sxs-lookup"><span data-stu-id="78553-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="78553-207">Sin embargo, `DataContractSerializerOperationBehavior` tiene `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, y las propiedades `DataContractSurrogate` que puede utilizar para personalizar el proceso de serialización.</span><span class="sxs-lookup"><span data-stu-id="78553-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="78553-208">Las primeras dos propiedades tienen el mismo significado que se mencionó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="78553-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="78553-209">Puede utilizar la propiedad `DataContractSurrogate` para habilitar suplentes del contrato de datos, que son un mecanismo eficaz para personalizar y extender el proceso de serialización.</span><span class="sxs-lookup"><span data-stu-id="78553-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="78553-210">Para obtener más información, vea [suplentes del contrato de datos](../extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="78553-210">For more information, see [Data Contract Surrogates](../extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="78553-211">Puede utilizar el `DataContractSerializerOperationBehavior` para personalizar la serialización de cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="78553-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="78553-212">El ejemplo siguiente muestra cómo aumentar la cuota `MaxItemsInObjectGraph` en el cliente.</span><span class="sxs-lookup"><span data-stu-id="78553-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
<span data-ttu-id="78553-213">El siguiente es el código equivalente en el servicio, en el caso de autohospedaje:</span><span class="sxs-lookup"><span data-stu-id="78553-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 <span data-ttu-id="78553-214">En el caso de hospedaje mediante web, debe crear una nueva clase derivada `ServiceHost` y utilizar un generador de host de servicio para conectarla.</span><span class="sxs-lookup"><span data-stu-id="78553-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="78553-215">Control de los ajustes de serialización en la configuración</span><span class="sxs-lookup"><span data-stu-id="78553-215">Controlling Serialization Settings in Configuration</span></span>  

 <span data-ttu-id="78553-216">El `MaxItemsInObjectGraph` e `IgnoreExtensionDataObject` se pueden controlar a través de la configuración utilizando el extremo `dataContractSerializer` o comportamiento de servicio, tal y como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="78553-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="78553-217">Serialización de tipo compartido, preservación de gráfico de objeto y serializadores personalizados</span><span class="sxs-lookup"><span data-stu-id="78553-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  

 <span data-ttu-id="78553-218"><xref:System.Runtime.Serialization.DataContractSerializer> serializa utilizando nombres de contrato de datos y no nombres de tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="78553-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="78553-219">Esto es coherente con los principios de la arquitectura orientada a servicios y permite un gran grado de flexibilidad; los tipos .NET pueden cambiar sin afectar al contrato de conexión.</span><span class="sxs-lookup"><span data-stu-id="78553-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="78553-220">En algún caso aislado, puede que desee serializar nombres de tipo .NET reales, introduciendo, de este modo, un acoplamiento robusto entre el cliente y el servidor, similar a la tecnología remota de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="78553-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="78553-221">Esta no es una práctica recomendada, excepto en casos excepcionales que normalmente se producen al migrar a WCF desde .NET Framework remoto.</span><span class="sxs-lookup"><span data-stu-id="78553-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="78553-222">En este caso, debe utilizar la clase <xref:System.Runtime.Serialization.NetDataContractSerializer>, en lugar de la clase <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="78553-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="78553-223">El <xref:System.Runtime.Serialization.DataContractSerializer> serializa normalmente gráficos de objetos como árboles de objeto.</span><span class="sxs-lookup"><span data-stu-id="78553-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="78553-224">Es decir, si se hace referencia al mismo objeto más de una vez, se serializa más de una vez.</span><span class="sxs-lookup"><span data-stu-id="78553-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="78553-225">Por ejemplo, considere una instancia `PurchaseOrder` que tiene dos campos de tipo Dirección llamados `billTo` y `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="78553-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="78553-226">Si ambos campos están establecidos en la misma instancia de Dirección, hay dos instancias de Dirección idénticas después de la serialización y deserialización.</span><span class="sxs-lookup"><span data-stu-id="78553-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="78553-227">Esto se hace porque no hay ninguna manera interoperable estándar de representar gráficos de objetos en XML (excepto para el estándar codificado SOAP heredado disponible en el <xref:System.Xml.Serialization.XmlSerializer>, tal y como se describe en la sección anterior en `Style` y `Use`).</span><span class="sxs-lookup"><span data-stu-id="78553-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="78553-228">Serializar gráficos de objetos como árboles tiene ciertas desventajas, como, por ejemplo, que los gráficos con referencias circulares no se pueden serializar.</span><span class="sxs-lookup"><span data-stu-id="78553-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="78553-229">De vez en cuando, es necesario intercambiar a serialización de gráficos de objetos verdadera, incluso aunque no sea interoperable.</span><span class="sxs-lookup"><span data-stu-id="78553-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="78553-230">Esto se puede realizar mediante el uso del <xref:System.Runtime.Serialization.DataContractSerializer> construido mediante el parámetro `preserveObjectReferences` establecido en `true`.</span><span class="sxs-lookup"><span data-stu-id="78553-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="78553-231">De vez en cuando, los serializadores integrados no son suficientes para su escenario.</span><span class="sxs-lookup"><span data-stu-id="78553-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="78553-232">En la mayoría de los casos, puede seguir utilizando la abstracción <xref:System.Runtime.Serialization.XmlObjectSerializer> desde la que se derivan <xref:System.Runtime.Serialization.DataContractSerializer> y <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="78553-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="78553-233">Los tres casos anteriores (preservación de tipo .NET, preservación de gráfico de objetos y serialización basada en `XmlObjectSerializer` completamente personalizada) necesitan que se conecte un serializador personalizado.</span><span class="sxs-lookup"><span data-stu-id="78553-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="78553-234">Para ello, realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="78553-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="78553-235">Escriba su propio comportamiento que deriva del <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="78553-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="78553-236">Invalide los dos métodos `CreateSerializer` para devolver su propio serializador (<xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> con `preserveObjectReferences` establecido en `true` o su propio <xref:System.Runtime.Serialization.XmlObjectSerializer> personalizado).</span><span class="sxs-lookup"><span data-stu-id="78553-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="78553-237">Antes de abrir el host de servicio o crear un canal de cliente, elimine el comportamiento <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> existente y conecte la clase derivada personalizada que cree en los pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="78553-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="78553-238">Para obtener más información sobre los conceptos de serialización avanzada, vea [serialización y deserialización](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="78553-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78553-239">Vea también</span><span class="sxs-lookup"><span data-stu-id="78553-239">See also</span></span>

- [<span data-ttu-id="78553-240">Utilización de la clase XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="78553-240">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)
- [<span data-ttu-id="78553-241">Procedimiento para habilitar el streaming</span><span class="sxs-lookup"><span data-stu-id="78553-241">How to: Enable Streaming</span></span>](how-to-enable-streaming.md)
- [<span data-ttu-id="78553-242">Procedimiento para crear un contrato de datos básico para una clase o estructura</span><span class="sxs-lookup"><span data-stu-id="78553-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
