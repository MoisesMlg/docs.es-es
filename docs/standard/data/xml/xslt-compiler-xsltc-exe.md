---
title: Compilador XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: 89e2291cb4eafe9ca9e5001061b960f348fe4719
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720833"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="181bf-102">Compilador XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="181bf-102">XSLT Compiler (xsltc.exe)</span></span>

<span data-ttu-id="181bf-103">El compilador XSLT (xsltc.exe) compila hojas de estilo XSLT y genera un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="181bf-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="181bf-104">La hoja de estilos compilada se puede pasar directamente al método <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="181bf-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="181bf-105">No se pueden generar ensamblados firmados con xsltc.exe.</span><span class="sxs-lookup"><span data-stu-id="181bf-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="181bf-106">La herramienta xsltc.exe está incluida en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="181bf-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="181bf-107">Para obtener más información, consulte [Descargas de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="181bf-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181bf-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="181bf-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="181bf-109">Argumento</span><span class="sxs-lookup"><span data-stu-id="181bf-109">Argument</span></span>  
  
|<span data-ttu-id="181bf-110">Argumento</span><span class="sxs-lookup"><span data-stu-id="181bf-110">Argument</span></span>|<span data-ttu-id="181bf-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="181bf-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="181bf-112">Especifica el nombre de la hoja de estilos.</span><span class="sxs-lookup"><span data-stu-id="181bf-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="181bf-113">La hoja de estilos debe ser un archivo local o bien estar ubicada en la intranet.</span><span class="sxs-lookup"><span data-stu-id="181bf-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="181bf-114">Opciones</span><span class="sxs-lookup"><span data-stu-id="181bf-114">Options</span></span>  
  
|<span data-ttu-id="181bf-115">Opción</span><span class="sxs-lookup"><span data-stu-id="181bf-115">Option</span></span>|<span data-ttu-id="181bf-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="181bf-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="181bf-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="181bf-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="181bf-118">Especifica el nombre de la clase para la hoja de estilos siguiente.</span><span class="sxs-lookup"><span data-stu-id="181bf-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="181bf-119">El nombre de la clase puede ser completo.</span><span class="sxs-lookup"><span data-stu-id="181bf-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="181bf-120">De forma predeterminada, el nombre de la clase es igual al de la hoja de estilos.</span><span class="sxs-lookup"><span data-stu-id="181bf-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="181bf-121">Por ejemplo, si se compila la hoja de estilos customer.xsl, el nombre predeterminado de la clase será customers.</span><span class="sxs-lookup"><span data-stu-id="181bf-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="181bf-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="181bf-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="181bf-123">Especifica si se debe generar o no información de depuración.</span><span class="sxs-lookup"><span data-stu-id="181bf-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="181bf-124">Si se especifica la opción `+` o `/debug`, el compilador generará información de depuración y la almacenará en el archivo de base de datos del programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="181bf-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="181bf-125">El nombre del archivo PDB generado será `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="181bf-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="181bf-126">Si se especifica la opción `-`, que será la utilizada en caso de que no especifique `/debug`, no se generará información de depuración.</span><span class="sxs-lookup"><span data-stu-id="181bf-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="181bf-127">Se genera un ensamblado listo para ser distribuido.</span><span class="sxs-lookup"><span data-stu-id="181bf-127">A retail assembly is generated.</span></span> <span data-ttu-id="181bf-128">**Nota:**  Si se compila en modo de depuración, es posible que ello afecte significativamente al rendimiento del XSLT.</span><span class="sxs-lookup"><span data-stu-id="181bf-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="181bf-129">Muestra las opciones y la sintaxis de los comandos para la herramienta.</span><span class="sxs-lookup"><span data-stu-id="181bf-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="181bf-130">Suprime el mensaje de copyright del compilador.</span><span class="sxs-lookup"><span data-stu-id="181bf-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="181bf-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="181bf-131">`/platform:` `string`</span></span>|<span data-ttu-id="181bf-132">Especifica las plataformas en las que se podrá ejecutar el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="181bf-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="181bf-133">A continuación se describen los valores permitidos para las plataformas:</span><span class="sxs-lookup"><span data-stu-id="181bf-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="181bf-134">`x86` compila el ensamblado de forma que el CLR de 32 bits compatible con x86 pueda ejecutarlo.</span><span class="sxs-lookup"><span data-stu-id="181bf-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="181bf-135">`x64` compila el ensamblado de forma que el CLR de 64 bits pueda ejecutarlo en equipos compatibles con el conjunto de instrucciones AMD64 o EM64T.</span><span class="sxs-lookup"><span data-stu-id="181bf-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="181bf-136">Itanium compila el ensamblado de forma que Common Language Runtime de 64 bits pueda ejecutarlo en equipos que tengan un procesador Itanium.</span><span class="sxs-lookup"><span data-stu-id="181bf-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="181bf-137">`anycpu` compila en ensamblado de forma que se pueda ejecutar en cualquier plataforma.</span><span class="sxs-lookup"><span data-stu-id="181bf-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="181bf-138">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="181bf-138">This is the default.</span></span>|  
|<span data-ttu-id="181bf-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="181bf-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="181bf-140">Especifica el nombre del ensamblado que se va a generar.</span><span class="sxs-lookup"><span data-stu-id="181bf-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="181bf-141">De forma predeterminada, el nombre del ensamblado es el mismo que el de la hoja de estilos, o bien de la primera hoja de estilos, en caso de existir varias.</span><span class="sxs-lookup"><span data-stu-id="181bf-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="181bf-142">Si la hoja de estilos contiene scripts, éstos se guardarán en un ensamblado aparte.</span><span class="sxs-lookup"><span data-stu-id="181bf-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="181bf-143">Los nombres de los ensamblados de scripts se generarán a partir del nombre del ensamblado principal.</span><span class="sxs-lookup"><span data-stu-id="181bf-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="181bf-144">Por ejemplo, si especificó que el nombre del ensamblado sería CustOrders.dll, el nombre del primer ensamblado de script será CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="181bf-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="181bf-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="181bf-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="181bf-146">Especifica si se permiten o no funciones `document()`, scripts XSLT o definiciones de tipo de documento (DTD) en la hoja de estilos.</span><span class="sxs-lookup"><span data-stu-id="181bf-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="181bf-147">De forma predeterminada, no habrá compatibilidad con DTD, con las funciones `document()` y con los scripts.</span><span class="sxs-lookup"><span data-stu-id="181bf-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="181bf-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="181bf-148">`@` `file`</span></span>|<span data-ttu-id="181bf-149">Le permite especificar un archivo que contenga las opciones del compilador.</span><span class="sxs-lookup"><span data-stu-id="181bf-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="181bf-150">Muestra las opciones y la sintaxis de los comandos para la herramienta.</span><span class="sxs-lookup"><span data-stu-id="181bf-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="181bf-151">Comentarios</span><span class="sxs-lookup"><span data-stu-id="181bf-151">Remarks</span></span>  

 <span data-ttu-id="181bf-152">Las soluciones XSLT puede estar compuestas por múltiples módulos de hojas de estilos.</span><span class="sxs-lookup"><span data-stu-id="181bf-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="181bf-153">La herramienta xsltc.exe genera ensamblados a partir de hojas de estilos.</span><span class="sxs-lookup"><span data-stu-id="181bf-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="181bf-154">Dichos ensamblados se pueden pasar al método <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="181bf-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="181bf-155">Esto puede ayudar a reducir los costos de implementación en ciertos escenarios de XSLT.</span><span class="sxs-lookup"><span data-stu-id="181bf-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="181bf-156">Por otro lado, deberá incluir en su aplicación el ensamblado compilado como una referencia.</span><span class="sxs-lookup"><span data-stu-id="181bf-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="181bf-157">La herramienta xsltc.exe no valida los nombres de la clase (`/class:`*nombre*) o del ensamblado (`/out:`*nombreDelEnsamblado*).</span><span class="sxs-lookup"><span data-stu-id="181bf-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="181bf-158">En caso de que estos nombres no sean válidos, el CLR se encargará de generar los errores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="181bf-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="181bf-159">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="181bf-159">Examples</span></span>  

 <span data-ttu-id="181bf-160">La siguiente instrucción compila la hoja de estilos y crea un ensamblado llamado booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="181bf-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="181bf-161">La siguiente instrucción compila la hoja de estilos, para después crear un ensamblado y un archivo PDB que se llaman booksort.dll y booksort.pdb, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="181bf-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="181bf-162">La instrucción siguiente compila una hoja de estilos que contiene un elemento msxsl:script y crea dos ensamblados, cuyos nombres son calc.dll y calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="181bf-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="181bf-163">La instrucción siguiente habilita el procesamiento DTD y el uso de scripts, para después crear dos ensamblados que se llamarán myTest.dll y myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="181bf-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="181bf-164">La siguiente instrucción compila dos módulos de hoja de estilos y crea un único ensamblado llamado booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="181bf-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="181bf-165">Vea también</span><span class="sxs-lookup"><span data-stu-id="181bf-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="181bf-166">Cómo: Realizar una transformación XSLT mediante un ensamblado</span><span class="sxs-lookup"><span data-stu-id="181bf-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="181bf-167">Transformaciones XSLT</span><span class="sxs-lookup"><span data-stu-id="181bf-167">XSLT Transformations</span></span>](xslt-transformations.md)
