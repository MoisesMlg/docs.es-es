---
title: Procedimiento para migrar el código XslTransform
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 42f721e56c803fb404f7885d126bea9560224f4c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824992"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="d67c1-102">Procedimiento para migrar el código XslTransform</span><span class="sxs-lookup"><span data-stu-id="d67c1-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="d67c1-103">Las nuevas clases XSLT se han diseñado para que sean muy similares a las clases existentes.</span><span class="sxs-lookup"><span data-stu-id="d67c1-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="d67c1-104">La clase <xref:System.Xml.Xsl.XslCompiledTransform> reemplaza a la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="d67c1-105">Las hojas de estilos se compilan utilizando el método <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="d67c1-106">Las transformaciones se ejecutan utilizando el método <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="d67c1-107">Los siguientes procedimientos muestran tareas XSLT comunes y comparan el código utilizando la clase <xref:System.Xml.Xsl.XslTransform> y la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="d67c1-108">Para transformar un archivo y una salida en un identificador URI</span><span class="sxs-lookup"><span data-stu-id="d67c1-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="d67c1-109">Programe con la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="d67c1-110">Programe con la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="d67c1-111">Para compilar una hoja de estilos y utilizar una resolución con credenciales predeterminadas</span><span class="sxs-lookup"><span data-stu-id="d67c1-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="d67c1-112">Programe con la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="d67c1-113">Programe con la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="d67c1-114">Para utilizar un parámetro XSLT</span><span class="sxs-lookup"><span data-stu-id="d67c1-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="d67c1-115">Programe con la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="d67c1-116">Programe con la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="d67c1-117">Para habilitar los scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="d67c1-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="d67c1-118">Programe con la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="d67c1-119">Programe con la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="d67c1-120">Para cargar los resultados en un objeto DOM</span><span class="sxs-lookup"><span data-stu-id="d67c1-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="d67c1-121">Programe con la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="d67c1-122">Programe con la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d67c1-123">La clase <xref:System.Xml.Xsl.XslCompiledTransform> no tiene un método que devuelva los resultados de la transformación XSLT como un objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="d67c1-124">Sin embargo, puede enviar la salida a un archivo XML y cargar el archivo XML en otro objeto.</span><span class="sxs-lookup"><span data-stu-id="d67c1-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="d67c1-125">Para secuenciar los resultados en otro almacén de datos</span><span class="sxs-lookup"><span data-stu-id="d67c1-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="d67c1-126">Programe con la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="d67c1-127">Programe con la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d67c1-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="d67c1-128">Vea también</span><span class="sxs-lookup"><span data-stu-id="d67c1-128">See also</span></span>

- [<span data-ttu-id="d67c1-129">Migración desde la clase XslTransform</span><span class="sxs-lookup"><span data-stu-id="d67c1-129">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="d67c1-130">Uso de la clase XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="d67c1-130">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
