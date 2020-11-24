---
title: Migración desde la clase XslTransform
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: b441e23b13983a0fdb54b7785e249a04bf1407c8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830212"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="3d83d-102">Migración desde la clase XslTransform</span><span class="sxs-lookup"><span data-stu-id="3d83d-102">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="3d83d-103">En la versión de Visual Studio 2005 se ha rediseñado la arquitectura XSLT.</span><span class="sxs-lookup"><span data-stu-id="3d83d-103">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="3d83d-104">La clase <xref:System.Xml.Xsl.XslTransform> se reemplazó por la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-104">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="3d83d-105">En las siguientes secciones se describen algunas de las principales diferencias existentes entre las clases <xref:System.Xml.Xsl.XslCompiledTransform> y <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="3d83d-106">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="3d83d-106">Performance</span></span>

<span data-ttu-id="3d83d-107">La clase <xref:System.Xml.Xsl.XslCompiledTransform> incluye muchas mejoras del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="3d83d-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="3d83d-108">El nuevo procesador XSLT compila la hoja de estilos XSLT en un formato intermedio común, que es similar a lo que hace Common Language Runtime (CLR) para otros lenguajes de programación.</span><span class="sxs-lookup"><span data-stu-id="3d83d-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="3d83d-109">Una vez compilada la hoja de estilos, se puede almacenar en caché y volver a utilizar.</span><span class="sxs-lookup"><span data-stu-id="3d83d-109">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="3d83d-110">La clase <xref:System.Xml.Xsl.XslCompiledTransform> también incluye otras optimizaciones que hacen que sea mucho más rápida que la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="3d83d-111">Aunque el rendimiento total de la clase <xref:System.Xml.Xsl.XslCompiledTransform> es mejor que la clase <xref:System.Xml.Xsl.XslTransform>, el método <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> de la clase <xref:System.Xml.Xsl.XslCompiledTransform> podría ser más lento que el método <xref:System.Xml.Xsl.XslTransform.Load%2A> de la clase <xref:System.Xml.Xsl.XslTransform> cuando se le llama por primera vez para una transformación.</span><span class="sxs-lookup"><span data-stu-id="3d83d-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="3d83d-112">Esto se debe a que el archivo XSLT debe compilarse antes de cargarse.</span><span class="sxs-lookup"><span data-stu-id="3d83d-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="3d83d-113">Para más información, vea la entrada de blog siguiente: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform) (¿Es más lento XslCompiledTransform que XslTransform?)</span><span class="sxs-lookup"><span data-stu-id="3d83d-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="3d83d-114">Seguridad</span><span class="sxs-lookup"><span data-stu-id="3d83d-114">Security</span></span>

<span data-ttu-id="3d83d-115">De forma predeterminada, la clase <xref:System.Xml.Xsl.XslCompiledTransform> deshabilita la compatibilidad para la función XSLT `document()` y los scripts incrustados.</span><span class="sxs-lookup"><span data-stu-id="3d83d-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="3d83d-116">Para habilitar estas características, se puede crear un objeto <xref:System.Xml.Xsl.XsltSettings> con las características habilitadas y pasarlo al método <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="3d83d-117">El siguiente ejemplo muestra cómo habilitar los scripts y cómo realizar una transformación XSLT.</span><span class="sxs-lookup"><span data-stu-id="3d83d-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="3d83d-118">Para obtener más información, vea [Consideraciones de seguridad de XSLT](xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="3d83d-118">For more information, see [XSLT Security Considerations](xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="3d83d-119">Características nuevas</span><span class="sxs-lookup"><span data-stu-id="3d83d-119">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="3d83d-120">Archivos temporales</span><span class="sxs-lookup"><span data-stu-id="3d83d-120">Temporary Files</span></span>

<span data-ttu-id="3d83d-121">En ocasiones, durante el procesamiento XSLT se generan archivos temporales.</span><span class="sxs-lookup"><span data-stu-id="3d83d-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="3d83d-122">Si una hoja de estilos contiene bloques de scripts, o si se ha compilado con la opción de depuración, se crearán archivos temporales en la carpeta %TEMP%.</span><span class="sxs-lookup"><span data-stu-id="3d83d-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="3d83d-123">Es posible que en algunos casos no se eliminen algunos archivos temporales por cuestión de tiempo.</span><span class="sxs-lookup"><span data-stu-id="3d83d-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="3d83d-124">Por ejemplo, si los archivos están siendo utilizados actualmente por AppDomain o por el depurador, el finalizador del objeto <xref:System.CodeDom.Compiler.TempFileCollection> no será capaz de eliminarlos.</span><span class="sxs-lookup"><span data-stu-id="3d83d-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="3d83d-125">La propiedad <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> se puede utilizar para realizar una limpieza adicional, con el fin de asegurarse de que se eliminan todos los archivos temporales del cliente.</span><span class="sxs-lookup"><span data-stu-id="3d83d-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="3d83d-126">Compatibilidad con el elemento xsl:output y con XmlWriter</span><span class="sxs-lookup"><span data-stu-id="3d83d-126">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="3d83d-127">La clase <xref:System.Xml.Xsl.XslTransform> ignora la configuración de `xsl:output` cuando la salida de una transformación se envía a un objeto <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="3d83d-128">La clase <xref:System.Xml.Xsl.XslCompiledTransform> tiene una propiedad <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> que devuelve un objeto <xref:System.Xml.XmlWriterSettings> que contiene la información de salida resultado del elemento `xsl:output` perteneciente a la hoja de estilos.</span><span class="sxs-lookup"><span data-stu-id="3d83d-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="3d83d-129">El objeto <xref:System.Xml.XmlWriterSettings> se utiliza para crear un objeto <xref:System.Xml.XmlWriter> con la configuración correcta, el cual se puede pasar al método <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="3d83d-130">El siguiente código escrito en C# ilustra este tipo de funcionamiento:</span><span class="sxs-lookup"><span data-stu-id="3d83d-130">The following C# code illustrates this behavior:</span></span>

```csharp
// Create the XslTransform object and load the style sheet.
XslCompiledTransform xslt = new XslCompiledTransform();
xslt.Load(stylesheet);

// Load the file to transform.
XPathDocument doc = new XPathDocument(filename);

// Create the writer.
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);

// Transform the file and send the output to the console.
xslt.Transform(doc, writer);
writer.Close();
```

### <a name="debug-option"></a><span data-ttu-id="3d83d-131">Opción de depuración</span><span class="sxs-lookup"><span data-stu-id="3d83d-131">Debug Option</span></span>

<span data-ttu-id="3d83d-132">La clase <xref:System.Xml.Xsl.XslCompiledTransform> puede generar información de depuración, lo que le permite depurar la hoja de estilos con el depurador de Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d83d-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="3d83d-133">Vea <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="3d83d-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="3d83d-134">Diferencias de funcionamiento</span><span class="sxs-lookup"><span data-stu-id="3d83d-134">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="3d83d-135">Transformar en un XmlReader</span><span class="sxs-lookup"><span data-stu-id="3d83d-135">Transforming to an XmlReader</span></span>

<span data-ttu-id="3d83d-136">La clase <xref:System.Xml.Xsl.XslTransform> dispone de numerosas sobrecargas de Transform, las cuales devuelven los resultados de la transformación como un objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="3d83d-137">Se pueden utilizar dichas sobrecargas para cargar los resultados de la transformación en una representación en memoria (como un <xref:System.Xml.XmlDocument> o un <xref:System.Xml.XPath.XPathDocument>) sin incurrir en una sobrecarga del proceso de serialización o deserialización del árbol XML resultante.</span><span class="sxs-lookup"><span data-stu-id="3d83d-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="3d83d-138">El siguiente código escrito en C# nuestra cómo cargar los resultados de la transformación en un objeto <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="3d83d-139">La clase <xref:System.Xml.Xsl.XslCompiledTransform> no admite la posibilidad de realizar una transformación en un objeto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="3d83d-140">Sin embargo, puede hacer algo muy parecido si utiliza el método <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> para cargar el árbol XML resultante directamente desde un <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="3d83d-141">El siguiente código escrito en C# muestra cómo llevar a cabo la misma tarea utilizando <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="3d83d-142">Comportamiento discrecional</span><span class="sxs-lookup"><span data-stu-id="3d83d-142">Discretionary Behavior</span></span>

<span data-ttu-id="3d83d-143">La recomendación de la versión 1.0 de las transformaciones XLT (XSLT) del W3C incluye áreas en las que el proveedor de las implementaciones puede decidir cómo controlar una situación.</span><span class="sxs-lookup"><span data-stu-id="3d83d-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="3d83d-144">Estas áreas se consideran comportamientos discrecionales.</span><span class="sxs-lookup"><span data-stu-id="3d83d-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="3d83d-145">Existen numerosas áreas en las que <xref:System.Xml.Xsl.XslCompiledTransform> se comporta de manera distinta a la clase <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="3d83d-146">Para más información, vea [Errores XSLT recuperables](recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="3d83d-146">For more information, see [Recoverable XSLT Errors](recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="3d83d-147">Objetos de extensión y funciones de scripts</span><span class="sxs-lookup"><span data-stu-id="3d83d-147">Extension Objects and Script Functions</span></span>

<span data-ttu-id="3d83d-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduce dos nuevas restricciones relativas al uso de funciones de script:</span><span class="sxs-lookup"><span data-stu-id="3d83d-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="3d83d-149">Desde las expresiones XPath solo es posible llamar a métodos públicos.</span><span class="sxs-lookup"><span data-stu-id="3d83d-149">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="3d83d-150">Las sobrecargas se pueden distinguir unas de otras en función del número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="3d83d-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="3d83d-151">Si existe más de una sobrecarga con el mismo número de argumentos, se producirá una excepción.</span><span class="sxs-lookup"><span data-stu-id="3d83d-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="3d83d-152">En <xref:System.Xml.Xsl.XslCompiledTransform> se produce un enlace (búsqueda de nombre de método) con las funciones del script en el tiempo de compilación y es posible que las hojas de estilos que habían funcionado con XslTransform generen una excepción si se cargan con <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="3d83d-153"><xref:System.Xml.Xsl.XslCompiledTransform> admiten la posibilidad de contener elementos secundarios `msxsl:using` y `msxsl:assembly` dentro del elemento `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="3d83d-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="3d83d-154">Los elementos `msxsl:using` y `msxsl:assembly` permiten declarar espacios de nombres y ensamblados adicionales que se utilizarán en el bloque del script.</span><span class="sxs-lookup"><span data-stu-id="3d83d-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="3d83d-155">Vea [Bloques de scripts con msxsl:script](script-blocks-using-msxsl-script.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="3d83d-155">See [Script Blocks Using msxsl:script](script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="3d83d-156"><xref:System.Xml.Xsl.XslCompiledTransform> no permite el uso de objetos de extensión que tengan múltiples sobrecargas con el mismo número de argumentos.</span><span class="sxs-lookup"><span data-stu-id="3d83d-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="3d83d-157">Funciones MSXML</span><span class="sxs-lookup"><span data-stu-id="3d83d-157">MSXML Functions</span></span>

<span data-ttu-id="3d83d-158">Se ha agregado a la clase <xref:System.Xml.Xsl.XslCompiledTransform> compatibilidad con funciones MSXML adicionales.</span><span class="sxs-lookup"><span data-stu-id="3d83d-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="3d83d-159">En la siguiente lista se describe toda la funcionalidad nueva o mejorada:</span><span class="sxs-lookup"><span data-stu-id="3d83d-159">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="3d83d-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> requiere que el argumento de la función [node-set Function](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) sea un fragmento del árbol resultante.</span><span class="sxs-lookup"><span data-stu-id="3d83d-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="3d83d-161">La clase <xref:System.Xml.Xsl.XslCompiledTransform> no tiene este requisito.</span><span class="sxs-lookup"><span data-stu-id="3d83d-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="3d83d-162">msxsl:version: está función se admite en <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="3d83d-163">Funciones de extensión de XPath: las funciones [ms:string-compare](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)) y [ms:format-time](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) ya son compatibles.</span><span class="sxs-lookup"><span data-stu-id="3d83d-163">XPath extension functions: The [ms:string-compare Function](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="3d83d-164">Funciones de extensión de XPath relacionadas con esquemas: estas funciones no se admiten de forma nativa en <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="3d83d-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="3d83d-165">No obstante, es posible implementarlas como funciones de extensión.</span><span class="sxs-lookup"><span data-stu-id="3d83d-165">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d83d-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="3d83d-166">See also</span></span>

- [<span data-ttu-id="3d83d-167">Transformaciones XSLT</span><span class="sxs-lookup"><span data-stu-id="3d83d-167">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="3d83d-168">Uso de la clase XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="3d83d-168">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
