---
title: Generar y compilar código fuente a partir de un gráfico CodeDOM
description: Genere y compile código fuente a partir de un gráfico CodeDOM en .NET. Use un proveedor de código CodeDOM para generar código fuente y compilar ensamblados.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
ms.openlocfilehash: aec7d6b44e63558ae70bc0eb41f94e55c8a6c325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266342"
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="13dcc-104">Generar y compilar código fuente a partir de un gráfico CodeDOM</span><span class="sxs-lookup"><span data-stu-id="13dcc-104">Generating and Compiling Source Code from a CodeDOM Graph</span></span>

<span data-ttu-id="13dcc-105">El espacio de nombres <xref:System.CodeDom.Compiler> proporciona interfaces para generar código fuente a partir de gráficos de objetos CodeDOM y para administrar la compilación con compiladores compatibles.</span><span class="sxs-lookup"><span data-stu-id="13dcc-105">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="13dcc-106">Un proveedor de código puede generar código fuente en un lenguaje de programación determinado según un gráfico CodeDOM.</span><span class="sxs-lookup"><span data-stu-id="13dcc-106">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="13dcc-107">Una clase que deriva de <xref:System.CodeDom.Compiler.CodeDomProvider> normalmente puede proporcionar métodos para generar y compilar código para el lenguaje admitido por el proveedor.</span><span class="sxs-lookup"><span data-stu-id="13dcc-107">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="13dcc-108">Uso de un proveedor de código CodeDOM para generar el código fuente</span><span class="sxs-lookup"><span data-stu-id="13dcc-108">Using a CodeDOM code provider to generate source code</span></span>  

 <span data-ttu-id="13dcc-109">Para generar código fuente en un lenguaje determinado, se necesita un gráfico CodeDOM que represente la estructura del código fuente que se va a generar.</span><span class="sxs-lookup"><span data-stu-id="13dcc-109">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="13dcc-110">En el ejemplo siguiente se muestra cómo crear una instancia de <xref:Microsoft.CSharp.CSharpCodeProvider>:</span><span class="sxs-lookup"><span data-stu-id="13dcc-110">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="13dcc-111">El gráfico para la generación de código normalmente se encuentra en un elemento <xref:System.CodeDom.CodeCompileUnit>.</span><span class="sxs-lookup"><span data-stu-id="13dcc-111">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="13dcc-112">Para generar código para un elemento **CodeCompileUnit** que contiene un gráfico CodeDOM, llame al método <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> del proveedor de código.</span><span class="sxs-lookup"><span data-stu-id="13dcc-112">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="13dcc-113">Este método tiene un parámetro para <xref:System.IO.TextWriter> que se usa para generar el código fuente, por lo que a veces es necesario crear primero un elemento **TextWriter** en el que se pueda escribir.</span><span class="sxs-lookup"><span data-stu-id="13dcc-113">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="13dcc-114">En el ejemplo siguiente se muestra la generación de código a partir de un elemento **CodeCompileUnit** y la escritura del código fuente generado en un archivo denominado HelloWorld.cs.</span><span class="sxs-lookup"><span data-stu-id="13dcc-114">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="13dcc-115">Uso de un proveedor de código CodeDOM para compilar ensamblados</span><span class="sxs-lookup"><span data-stu-id="13dcc-115">Using a CodeDOM code provider to compile assemblies</span></span>  

 <span data-ttu-id="13dcc-116">**Invocación de la compilación**</span><span class="sxs-lookup"><span data-stu-id="13dcc-116">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="13dcc-117">Para compilar un ensamblado mediante un proveedor CodeDom, se debe tener código fuente para compilar en un lenguaje para el que se tenga un compilador, o bien se debe disponer de un gráfico CodeDOM a partir del que se pueda generar ese código fuente que se va a compilar.</span><span class="sxs-lookup"><span data-stu-id="13dcc-117">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="13dcc-118">Si está compilando a partir de un gráfico CodeDOM, pase el elemento <xref:System.CodeDom.CodeCompileUnit> que contiene el gráfico al método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> del proveedor de código.</span><span class="sxs-lookup"><span data-stu-id="13dcc-118">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="13dcc-119">Si tiene un archivo de código fuente en un lenguaje que el compilador entiende, pase el nombre del archivo que contiene el código fuente al método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> del proveedor CodeDom.</span><span class="sxs-lookup"><span data-stu-id="13dcc-119">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="13dcc-120">También puede pasar una cadena que contiene el código fuente en un lenguaje que el compilador entiende al método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> del proveedor CodeDom.</span><span class="sxs-lookup"><span data-stu-id="13dcc-120">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="13dcc-121">**Configuración de parámetros de compilación**</span><span class="sxs-lookup"><span data-stu-id="13dcc-121">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="13dcc-122">Todos los métodos de invocación de compilación estándar de un proveedor CodeDom tienen un parámetro de tipo <xref:System.CodeDom.Compiler.CompilerParameters> que indica las opciones que se van a usar para la compilación.</span><span class="sxs-lookup"><span data-stu-id="13dcc-122">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="13dcc-123">Puede especificar un nombre de archivo para el ensamblado de salida en la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> de **CompilerParameters**.</span><span class="sxs-lookup"><span data-stu-id="13dcc-123">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="13dcc-124">De lo contrario, se usará un nombre de archivo de salida predeterminado.</span><span class="sxs-lookup"><span data-stu-id="13dcc-124">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="13dcc-125">De forma predeterminada, se inicializa un nuevo elemento **CompilerParameters** con su propiedad <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> establecida en **false**.</span><span class="sxs-lookup"><span data-stu-id="13dcc-125">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="13dcc-126">Si está compilando un programa ejecutable, debe establecer la propiedad **GenerateExecutable** en **true**.</span><span class="sxs-lookup"><span data-stu-id="13dcc-126">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="13dcc-127">Cuando **GenerateExecutable** está establecida en **false**, el compilador genera una biblioteca de clases.</span><span class="sxs-lookup"><span data-stu-id="13dcc-127">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="13dcc-128">Si está compilando un ejecutable a partir de un gráfico CodeDOM, se debe definir un elemento <xref:System.CodeDom.CodeEntryPointMethod> en el gráfico.</span><span class="sxs-lookup"><span data-stu-id="13dcc-128">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="13dcc-129">Si hay varios puntos de entrada de código, puede ser necesario establecer la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> de **CompilerParameters** en el nombre de la clase que define el punto de entrada que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="13dcc-129">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="13dcc-130">Para incluir información de depuración en un archivo ejecutable generado, establezca la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> en **true**.</span><span class="sxs-lookup"><span data-stu-id="13dcc-130">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="13dcc-131">Si el proyecto hace referencia a algún ensamblado, debe especificar los nombres de ensamblado como elementos de una <xref:System.Collections.Specialized.StringCollection> como la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> de **CompilerParameters** que usa al invocar la compilación.</span><span class="sxs-lookup"><span data-stu-id="13dcc-131">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="13dcc-132">Puede compilar un ensamblado que se escribe en memoria en lugar de en disco si establece la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> en **true**.</span><span class="sxs-lookup"><span data-stu-id="13dcc-132">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="13dcc-133">Cuando se genera un ensamblado en memoria, el código puede obtener una referencia al ensamblado generado a partir de la propiedad <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> de <xref:System.CodeDom.Compiler.CompilerResults>.</span><span class="sxs-lookup"><span data-stu-id="13dcc-133">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="13dcc-134">Si un ensamblado se escribe en disco, puede obtener la ruta de acceso al ensamblado generado a partir de la propiedad <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> de **CompilerResults**.</span><span class="sxs-lookup"><span data-stu-id="13dcc-134">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="13dcc-135">Para especificar una cadena de argumentos de línea de comandos personalizada que se usará al invocar al proceso de compilación, establezca la cadena en la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="13dcc-135">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="13dcc-136">Si se necesita un token de seguridad de Win32 para invocar al proceso de compilación, especifique el token en la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A>.</span><span class="sxs-lookup"><span data-stu-id="13dcc-136">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="13dcc-137">Para vincular un archivo de recursos de Win32 al ensamblado compilado, especifique el nombre del archivo de recursos de Win32 en la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A>.</span><span class="sxs-lookup"><span data-stu-id="13dcc-137">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="13dcc-138">Para especificar un nivel de advertencia en el que detener la compilación, establezca la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> en un entero que represente el nivel de advertencia en el que detener la compilación.</span><span class="sxs-lookup"><span data-stu-id="13dcc-138">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="13dcc-139">También puede establecer la propiedad <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> en **true** para que se detenga la compilación si se producen advertencias.</span><span class="sxs-lookup"><span data-stu-id="13dcc-139">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="13dcc-140">En el ejemplo de código siguiente se muestra cómo compilar un archivo de origen con un proveedor CodeDom derivado de la clase <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="13dcc-140">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="13dcc-141">Lenguajes con compatibilidad inicial</span><span class="sxs-lookup"><span data-stu-id="13dcc-141">Languages with Initial Support</span></span>  

 <span data-ttu-id="13dcc-142">.NET Framework proporciona compiladores y generadores de código para los lenguajes siguientes: C#, Visual Basic, C++ y JScript.</span><span class="sxs-lookup"><span data-stu-id="13dcc-142">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="13dcc-143">La compatibilidad de CodeDOM se puede extender a otros lenguajes si se implementan generadores y compiladores de código específicos del lenguaje.</span><span class="sxs-lookup"><span data-stu-id="13dcc-143">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13dcc-144">Vea también</span><span class="sxs-lookup"><span data-stu-id="13dcc-144">See also</span></span>

- <xref:System.CodeDom>
- <xref:System.CodeDom.Compiler>
- [<span data-ttu-id="13dcc-145">Generación y compilación dinámicas de código fuente</span><span class="sxs-lookup"><span data-stu-id="13dcc-145">Dynamic Source Code Generation and Compilation</span></span>](dynamic-source-code-generation-and-compilation.md)
- <span data-ttu-id="13dcc-146">[Referencia rápida de CodeDOM](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="13dcc-146">[CodeDOM Quick Reference](/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>
