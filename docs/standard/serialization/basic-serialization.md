---
title: Serialización básica
description: En este artículo se muestra cómo hacer que una clase sea serializable con SerializableAttribute y se incluyen ejemplos de serialización y deserialización.
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: 2b75ba6875b2a4430b6776c27dead72476884fff
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282080"
---
# <a name="basic-serialization"></a><span data-ttu-id="1562d-103">Serialización básica</span><span class="sxs-lookup"><span data-stu-id="1562d-103">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="1562d-104">La manera más sencilla de convertir una clase en serializable es marcarla con <xref:System.SerializableAttribute> como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="1562d-104">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="1562d-105">El ejemplo de código siguiente muestra cómo serializar una instancia de esta clase en un archivo.</span><span class="sxs-lookup"><span data-stu-id="1562d-105">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="1562d-106">Este ejemplo utiliza un formateador binario para hacer la serialización.</span><span class="sxs-lookup"><span data-stu-id="1562d-106">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="1562d-107">Todo lo que necesita hacer es crear una instancia del flujo y el formateador que piensa usar y luego llamar al método **Serialize** en el formateador.</span><span class="sxs-lookup"><span data-stu-id="1562d-107">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="1562d-108">La secuencia y el objeto para serializar se proporcionan como parámetros a esta llamada.</span><span class="sxs-lookup"><span data-stu-id="1562d-108">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="1562d-109">Aunque no se muestra explícitamente en este ejemplo, todas las variables miembro de una clase serán serializadas, incluso las variables marcadas como privadas.</span><span class="sxs-lookup"><span data-stu-id="1562d-109">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="1562d-110">En este aspecto, la serialización binaria difiere de la clase <xref:System.Xml.Serialization.XmlSerializer>, que solo serializa campos públicos.</span><span class="sxs-lookup"><span data-stu-id="1562d-110">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="1562d-111">Para más información sobre cómo excluir variables miembro de la serialización binaria, vea [Serialización selectiva](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="1562d-111">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="1562d-112">Restaurar el objeto a su estado anterior es así de fácil.</span><span class="sxs-lookup"><span data-stu-id="1562d-112">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="1562d-113">Primero, cree un flujo para leer y un <xref:System.Runtime.Serialization.Formatter> y luego indique al formateador que deserialice el objeto.</span><span class="sxs-lookup"><span data-stu-id="1562d-113">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="1562d-114">El ejemplo de código siguiente muestra cómo se realiza la acción.</span><span class="sxs-lookup"><span data-stu-id="1562d-114">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="1562d-115">El <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> usado arriba es muy eficaz y genera un flujo de bytes compacto.</span><span class="sxs-lookup"><span data-stu-id="1562d-115">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="1562d-116">Todos los objetos serializados con este formateador también se pueden deserializar con él, lo que lo convierte en una herramienta ideal para serializar objetos que se deserializarán en .NET.</span><span class="sxs-lookup"><span data-stu-id="1562d-116">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on .NET.</span></span> <span data-ttu-id="1562d-117">Es importante tener en cuenta que no se llama a los constructores cuando se deserializa un objeto.</span><span class="sxs-lookup"><span data-stu-id="1562d-117">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="1562d-118">Esta restricción se coloca en deserialización por las razones de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="1562d-118">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="1562d-119">Sin embargo, esto infringe algunos de los contratos usuales hechos en tiempo de ejecución con la escritura de objeto y los programadores debería asegurarse que entienden las ramificaciones al marcar un objeto como serializable.</span><span class="sxs-lookup"><span data-stu-id="1562d-119">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="1562d-120">Si la portabilidad es un requisito, use <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> en su lugar.</span><span class="sxs-lookup"><span data-stu-id="1562d-120">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="1562d-121">Simplemente reemplace **BinaryFormatter** en el código anterior por **SoapFormatter** y llame a **Serialize** y **Deserialize** como antes.</span><span class="sxs-lookup"><span data-stu-id="1562d-121">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="1562d-122">Este formateador genera el resultado siguiente para obtener el ejemplo utilizado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1562d-122">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="1562d-123">Es importante tener en cuenta que el atributo [Serializable](xref:System.SerializableAttribute) no se puede heredar.</span><span class="sxs-lookup"><span data-stu-id="1562d-123">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="1562d-124">Si deriva una nueva clase de `MyObject`, la nueva clase también se debe marcar con el atributo o no se puede serializar.</span><span class="sxs-lookup"><span data-stu-id="1562d-124">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="1562d-125">Por ejemplo, al intentar serializar una instancia de la clase siguiente, se obtiene una <xref:System.Runtime.Serialization.SerializationException> que informa de que el tipo `MyStuff` no está marcado como serializable.</span><span class="sxs-lookup"><span data-stu-id="1562d-125">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="1562d-126">Es conveniente usar el atributo [Serializable](xref:System.SerializableAttribute), aunque tiene limitaciones, como se ha mostrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1562d-126">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="1562d-127">Vea [Directrices de serialización](serialization-guidelines.md) para más información sobre cuándo se debe marcar una clase para la serialización.</span><span class="sxs-lookup"><span data-stu-id="1562d-127">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="1562d-128">La serialización no se puede agregar a una clase después de que se haya compilado.</span><span class="sxs-lookup"><span data-stu-id="1562d-128">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1562d-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="1562d-129">See also</span></span>

- [<span data-ttu-id="1562d-130">Serialización binaria</span><span class="sxs-lookup"><span data-stu-id="1562d-130">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="1562d-131">Serialización SOAP y XML</span><span class="sxs-lookup"><span data-stu-id="1562d-131">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
