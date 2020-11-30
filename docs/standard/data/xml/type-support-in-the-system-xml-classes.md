---
title: Compatibilidad de tipos en las clases System.Xml
ms.date: 03/30/2017
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: 6fe55c64bc9bd17d5416eebf77060f2be27b81bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675664"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="5d3ac-102">Compatibilidad de tipos en las clases System.Xml</span><span class="sxs-lookup"><span data-stu-id="5d3ac-102">Type Support in the System.Xml Classes</span></span>

<span data-ttu-id="5d3ac-103">En la versión 2.0 de .NET Framework, se han mejorado las clases XML principales para incluir características de compatibilidad de tipos.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="5d3ac-104">Las clases <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> y <xref:System.Xml.XPath.XPathNavigator> tienen características de compatibilidad de tipos, incluyendo la capacidad de realizar conversiones entre tipos de esquemas XML y tipos de Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="5d3ac-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="5d3ac-105">En la versión 2.0 de .NET Framework, se han mejorado las clases <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter> y <xref:System.Xml.XPath.XPathNavigator> para incluir características de compatibilidad de tipos.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="5d3ac-106">Cada una de las clases <xref:System.Xml.XmlReader> y <xref:System.Xml.XPath.XPathNavigator> incluye una propiedad **SchemaInfo** que devuelve la información de esquema en un nodo.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="5d3ac-107">**ReadContentAs** y **ReadElementContentAs** y los métodos de la clase <xref:System.Xml.XmlReader> leen un valor de texto y lo convierten en un valor CLR en una sola llamada de método.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="5d3ac-108">El método <xref:System.Xml.XmlWriter.WriteValue%2A> de la clase <xref:System.Xml.XmlWriter> convierte un tipo CLR en un tipo de esquema XML cuando escribe XML.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="5d3ac-109">Las propiedades **ValueAs** y <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> de la clase <xref:System.Xml.XPath.XPathNavigator> devuelven un valor de nodo y lo convierten en un valor CLR en una sola llamada de método.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d3ac-110">En la versión 1.0 de .NET Framework, se necesitaba la clase <xref:System.Xml.XmlConvert> para realizar la conversión entre esquemas XML y tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d3ac-111">En esta sección</span><span class="sxs-lookup"><span data-stu-id="5d3ac-111">In This Section</span></span>  

 [<span data-ttu-id="5d3ac-112">Asignación de tipos de datos XML a tipos CLR</span><span class="sxs-lookup"><span data-stu-id="5d3ac-112">Mapping XML Data Types to CLR Types</span></span>](mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="5d3ac-113">Describe las asignaciones predeterminadas de tipos de datos XML en tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="5d3ac-114">Notas de implementación de la compatibilidad con tipos XML</span><span class="sxs-lookup"><span data-stu-id="5d3ac-114">XML Type Support Implementation Notes</span></span>](xml-type-support-implementation-notes.md)  
 <span data-ttu-id="5d3ac-115">Explica algunos de los detalles de la implementación de la compatibilidad de tipos.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="5d3ac-116">Conversión de tipos de datos XML</span><span class="sxs-lookup"><span data-stu-id="5d3ac-116">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)  
 <span data-ttu-id="5d3ac-117">Describe cómo utilizar la clase <xref:System.Xml.XmlConvert> para realizar la conversión entre esquemas XML y tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="5d3ac-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5d3ac-118">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="5d3ac-118">Related Sections</span></span>  

 [<span data-ttu-id="5d3ac-119">Acceso a datos XML fuertemente tipados utilizando XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d3ac-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
