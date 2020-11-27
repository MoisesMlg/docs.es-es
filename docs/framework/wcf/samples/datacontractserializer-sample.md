---
title: Ejemplo de DataContractSerializer
description: En este ejemplo se muestra DataContractSerializer en WCF, que realiza servicios generales de serialización y deserialización para las clases de contrato de datos.
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: d38dddcaff7316f4933207c4aa0897ad47306352
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253627"
---
# <a name="datacontractserializer-sample"></a>Ejemplo de DataContractSerializer

El ejemplo de DataContractSerializer muestra el <xref:System.Runtime.Serialization.DataContractSerializer>, que realiza la serialización general y los servicios de deserialización para las clases de contrato de datos. El ejemplo crea un `Record` objeto, lo serializa en una secuencia de memoria y deserializa el flujo de memoria a otro `Record` objeto para mostrar el uso de <xref:System.Runtime.Serialization.DataContractSerializer> . El ejemplo serializa a continuación el objeto `Record` utilizando un sistema de escritura binario para mostrar cómo el sistema de escritura afecta a la serialización.  
  
> [!NOTE]
> El procedimiento de instalación y las instrucciones de compilación de este ejemplo se encuentran al final de este tema.  
  
 El contrato de datos para `Record` se muestra en el código muestra siguiente.  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 El código muestra crea un objeto `Record` denominado `record1` y, a continuación, muestra el objeto.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 El ejemplo utiliza la continuación <xref:System.Runtime.Serialization.DataContractSerializer> para serializar `record1` en una secuencia de la memoria.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Luego, el ejemplo utiliza <xref:System.Runtime.Serialization.DataContractSerializer> para deserializar la secuencia de la memoria en un nuevo objeto `Record` y lo muestra.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 De forma predeterminada, `DataContractSerializer` codifica los objetos en una secuencia utilizando una representación textual de XML. Sin embargo, puede influir en la codificación del XML pasando un sistema de escritura diferente. El ejemplo crea un sistema de escritura binario llamando <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Pasa a continuación el sistema de escritura y el objeto de registro al serializador cuando llama <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Finalmente, el ejemplo vacía el sistema de escritura e informa de la longitud de las secuencias.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Al ejecutarse el ejemplo, se muestra el registro original y el registro deserializado, seguido por la comparación entre la longitud de la codificación de texto y la codificación binaria. Presione ENTRAR en la ventana de cliente para cerrar el cliente.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo  
  
1. Asegúrese de que ha realizado el [procedimiento de instalación única para los ejemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar el código C# o Visual Basic .NET Edition de la solución, siga las instrucciones de [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Para ejecutar el ejemplo, inicie el cliente desde el símbolo del sistema escribiendo client\bin\client.exe.  
  
> [!IMPORTANT]
> Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
