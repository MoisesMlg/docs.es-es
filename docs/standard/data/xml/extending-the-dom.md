---
title: Extender DOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 173d36f534f951cfafefd3bd69b7ab245d575747
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829510"
---
# <a name="extending-the-dom"></a>Extender DOM

Microsoft .NET Framework incluye un conjunto básico de clases que proporcionan una implementación de Document Object Model (DOM) XML. <xref:System.Xml.XmlNode> y sus clases derivadas proporcionan métodos y propiedades que permiten navegar, consultar y modificar el contenido y la estructura de un documento XML.

Cuando se carga el contenido XML en la memoria mediante DOM, los nodos creados contienen información como el nombre y el tipo de nodo, entre otros datos. Puede haber ocasiones en las que necesite información de nodo específica que no proporcionan las clases base. Por ejemplo, es posible que desee conocer el número de línea y posición del nodo. En este caso, puede derivar clases nuevas de las clases DOM existentes y agregar funcionalidad adicional.

Al derivar clases nuevas hay que seguir dos directrices generales:

- Se recomienda no derivar nunca desde la clase <xref:System.Xml.XmlNode>. En su lugar, se aconseja derivar clases desde la clase que corresponda al tipo de nodo en el que esté interesado. Por ejemplo, si desea devolver información adicional sobre nodos de atributo, puede derivar desde la clase <xref:System.Xml.XmlAttribute>.

- Excepto en los métodos de creación de nodos, se recomienda que al invalidar una función, llame siempre a la versión base de la misma y, a continuación, agregue el procesamiento adicional.

## <a name="creating-your-own-node-instances"></a>Crear sus propias instancias de nodo

La clase <xref:System.Xml.XmlDocument> contiene métodos de creación de nodos. Cuando se carga un archivo XML, se llama a estos métodos para crear los nodos. Se pueden invalidar los métodos de forma que sus instancias de nodo se creen al cargar un documento. Por ejemplo, si ha extendido la clase <xref:System.Xml.XmlElement>, heredará la clase <xref:System.Xml.XmlDocument> e invalidará el método <xref:System.Xml.XmlDocument.CreateElement%2A>.

En el ejemplo siguiente se muestra cómo invalidar el método <xref:System.Xml.XmlDocument.CreateElement%2A>para devolver su implementación de la clase <xref:System.Xml.XmlElement>.

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI)
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a>Extender una clase

Para extender una clase, derive su clase de una de las clases DOM existentes. Se puede invalidar cualquiera de los métodos virtuales o propiedades de la clase base, o bien agregar los suyos propios.

En el ejemplo siguiente se crea una clase nueva, que implementa la clase <xref:System.Xml.XmlElement> y la interfaz <xref:System.Xml.IXmlLineInfo>. Se definen métodos y propiedades adicionales que permiten a los usuarios recopilar información de línea.

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se cuenta el número de elementos de un documento XML:

```vb
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a>Entrada

book.xml

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>Salida

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>Controlador de eventos de nodo

La implementación .NET Framework de DOM incluye también un sistema de eventos que permite recibir y controlar eventos cuando se cambian nodos en un documento XML. Mediante las clases <xref:System.Xml.XmlNodeChangedEventHandler> y <xref:System.Xml.XmlNodeChangedEventArgs>, puede capturar los eventos `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, y `NodeRemoving`.

El proceso de control de eventos funciona exactamente igual en las clases derivadas que en las clases DOM originales.

Para obtener más información sobre el control de eventos de nodo, vea [Eventos](../../events/index.md) y <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Atributos predeterminados y el método CreateElement

Si va a invalidar el método <xref:System.Xml.XmlDocument.CreateElement%2A> en una clase derivada, los atributos predeterminados no se agregan al crear elementos nuevos mientras se edita el documento. Esto solo constituye un problema durante la edición. Puesto que el método <xref:System.Xml.XmlDocument.CreateElement%2A> es responsable de la adición de atributos predeterminados a un <xref:System.Xml.XmlDocument>, debe programar esta funcionalidad en dicho método <xref:System.Xml.XmlDocument.CreateElement%2A>. Si va a cargar un <xref:System.Xml.XmlDocument> que incluye atributos predeterminados, se controlarán correctamente. Para obtener más información sobre los atributos predeterminados, vea [Crear nuevos atributos para elementos en DOM](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Vea también

- [Document Object Model (DOM) para XML](xml-document-object-model-dom.md)
