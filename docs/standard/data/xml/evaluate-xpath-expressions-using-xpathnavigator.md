---
title: Evaluación de expresiones XPath con XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 7ee487012453c7edfef4f071e0cfc843efff0c4f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818627"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="377e1-102">Evaluación de expresiones XPath con XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="377e1-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="377e1-103">La clase <xref:System.Xml.XPath.XPathNavigator> incluye el método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> para evaluar una expresión XPath.</span><span class="sxs-lookup"><span data-stu-id="377e1-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="377e1-104">El método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> toma una expresión XPath, la evalúa y devuelve un tipo XPath del W3C de tipo booleano, numérico, de cadena o de conjunto de nodos basándose en el resultado de la expresión XPath.</span><span class="sxs-lookup"><span data-stu-id="377e1-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="377e1-105">Método de evaluación</span><span class="sxs-lookup"><span data-stu-id="377e1-105">The Evaluate Method</span></span>  
 <span data-ttu-id="377e1-106">El método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> toma una expresión XPath, la evalúa y devuelve un resultado con tipo de tipo booleano (<xref:System.Boolean>), numérico (<xref:System.Double>), de cadena (<xref:System.String>) o de conjunto de nodos (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="377e1-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="377e1-107">Por ejemplo, el método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> se podría utilizar en un método matemático.</span><span class="sxs-lookup"><span data-stu-id="377e1-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="377e1-108">El siguiente código de ejemplo calcula el precio total de todos los libros del archivo `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="377e1-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="377e1-109">En el ejemplo se toma como entrada el archivo `books.xml`.</span><span class="sxs-lookup"><span data-stu-id="377e1-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="377e1-110">Funciones position y last</span><span class="sxs-lookup"><span data-stu-id="377e1-110">position and last Functions</span></span>  
 <span data-ttu-id="377e1-111">El método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> está sobrecargado.</span><span class="sxs-lookup"><span data-stu-id="377e1-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="377e1-112">Uno de los métodos <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> toma un objeto <xref:System.Xml.XPath.XPathNodeIterator> como parámetro.</span><span class="sxs-lookup"><span data-stu-id="377e1-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="377e1-113">Este método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> en concreto es idéntico al método <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> que solo toma un objeto <xref:System.Xml.XPath.XPathExpression> como parámetro, excepto en que permite que un argumento de un conjunto de nodos especifique el contexto actual en el que realizar la evaluación.</span><span class="sxs-lookup"><span data-stu-id="377e1-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="377e1-114">Este contexto es necesario para las funciones XPath `position()` y `last()`, ya que son relativas al nodo de contexto actual.</span><span class="sxs-lookup"><span data-stu-id="377e1-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="377e1-115">A menos que se utilicen como predicado en un paso de ubicación, las funciones `position()` y `last()` necesitan una referencia a un conjunto de nodos para poder ser evaluadas; de lo contrario, las funciones `position` y `last` devuelven `0`.</span><span class="sxs-lookup"><span data-stu-id="377e1-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377e1-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="377e1-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="377e1-117">Procesamiento de datos XML con el modelo de datos XPath</span><span class="sxs-lookup"><span data-stu-id="377e1-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="377e1-118">Seleccionar datos XML con XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="377e1-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="377e1-119">Coincidencia de nodos con XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="377e1-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="377e1-120">Tipos de nodos reconocidos con consultas XPath</span><span class="sxs-lookup"><span data-stu-id="377e1-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="377e1-121">Espacios de nombres y consultas XPath</span><span class="sxs-lookup"><span data-stu-id="377e1-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="377e1-122">Expresiones XPath compiladas</span><span class="sxs-lookup"><span data-stu-id="377e1-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
