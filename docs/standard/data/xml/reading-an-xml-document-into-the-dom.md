---
title: Lectura de un documento XML en el DOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 61275e9232b3d9e516636869d7153f33133cbd03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686870"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="796b0-102">Lectura de un documento XML en el DOM</span><span class="sxs-lookup"><span data-stu-id="796b0-102">Reading an XML Document into the DOM</span></span>

<span data-ttu-id="796b0-103">La información XML se lee en memoria desde diferentes formatos.</span><span class="sxs-lookup"><span data-stu-id="796b0-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="796b0-104">Se puede leer desde una cadena, una secuencia, una URL, un sistema de lectura de texto o una clase derivada de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="796b0-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="796b0-105">El método <xref:System.Xml.XmlDocument.Load%2A> pone el documento en memoria y dispone de métodos sobrecargados para tomar datos de cada uno de los diferentes formatos.</span><span class="sxs-lookup"><span data-stu-id="796b0-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="796b0-106">También hay un método <xref:System.Xml.XmlDocument.LoadXml%2A> que lee XML de una cadena.</span><span class="sxs-lookup"><span data-stu-id="796b0-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="796b0-107">Los diferentes métodos <xref:System.Xml.XmlDocument.Load%2A> influyen en qué nodos se crean cuando se carga el Modelo de objetos de documento (DOM).</span><span class="sxs-lookup"><span data-stu-id="796b0-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="796b0-108">En la siguiente tabla se enumeran las diferencias entre algunos de los métodos <xref:System.Xml.XmlDocument.Load%2A> y los temas en los que se tratan.</span><span class="sxs-lookup"><span data-stu-id="796b0-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="796b0-109">Contenido</span><span class="sxs-lookup"><span data-stu-id="796b0-109">Subject</span></span>|<span data-ttu-id="796b0-110">Tema</span><span class="sxs-lookup"><span data-stu-id="796b0-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="796b0-111">Creación de nodos de espacios en blanco</span><span class="sxs-lookup"><span data-stu-id="796b0-111">Creation of white space nodes</span></span>|<span data-ttu-id="796b0-112">El objeto utilizado para cargar el DOM tiene un efecto en los nodos de espacios en blanco y espacios en blanco significativos que se generan en el DOM.</span><span class="sxs-lookup"><span data-stu-id="796b0-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="796b0-113">Para obtener más información, vea [Control de espacios en blanco y de espacios en blanco significativos al cargar DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="796b0-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="796b0-114">Carga de XML comenzando en un nodo específico o carga de todo el documento XML</span><span class="sxs-lookup"><span data-stu-id="796b0-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="796b0-115">Si se utiliza el método <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType>, los datos se pueden cargar desde un nodo específico en el DOM.</span><span class="sxs-lookup"><span data-stu-id="796b0-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="796b0-116">Para obtener más información, vea [Carga de datos desde un sistema de lectura](load-data-from-a-reader.md).</span><span class="sxs-lookup"><span data-stu-id="796b0-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="796b0-117">Validación de XML a medida que se carga</span><span class="sxs-lookup"><span data-stu-id="796b0-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="796b0-118">Los datos XML cargados en el DOM se pueden validar a medida que se cargan.</span><span class="sxs-lookup"><span data-stu-id="796b0-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="796b0-119">Para ello, se utiliza un <xref:System.Xml.XmlReader> de validación.</span><span class="sxs-lookup"><span data-stu-id="796b0-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="796b0-120">Para obtener más información sobre la validación de documentos XML a medida que se cargan, vea [Validación de un documento XML en el DOM](validating-an-xml-document-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="796b0-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="796b0-121">En los siguientes ejemplos se muestra cómo se carga el XML con el método <xref:System.Xml.XmlDocument.LoadXml%2A> y cómo se guardan posteriormente los datos en un archivo de texto denominado `data.xml`.</span><span class="sxs-lookup"><span data-stu-id="796b0-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="796b0-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="796b0-122">See also</span></span>

- [<span data-ttu-id="796b0-123">Document Object Model (DOM) para XML</span><span class="sxs-lookup"><span data-stu-id="796b0-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
