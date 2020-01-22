---
title: Migración de proyectos de C++/CLI a .NET Core
description: Obtenga información sobre la migración de proyectos de C++/CLI a .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964864"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a><span data-ttu-id="68b12-103">Migración de un proyecto de C++/CLI a .NET Core</span><span class="sxs-lookup"><span data-stu-id="68b12-103">How to port a C++/CLI project to .NET Core</span></span>

<span data-ttu-id="68b12-104">A partir de .NET Core 3.1 y Visual Studio 2019 versión 16.4, los [proyectos de C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) pueden tener como destino .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-104">Beginning with .NET Core 3.1 and Visual Studio 2019 version 16.4, [C++/CLI projects](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) can target .NET Core.</span></span> <span data-ttu-id="68b12-105">Esta compatibilidad permite migrar aplicaciones de escritorio de Windows con capas de interoperabilidad de C++/CLI a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-105">This support makes it possible to port Windows desktop applications with C++/CLI interop layers to .NET Core.</span></span> <span data-ttu-id="68b12-106">En este artículo se explica cómo migrar proyectos de C++/CLI desde .NET Framework a .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="68b12-106">This article describes how to port C++/CLI projects from .NET Framework to .NET Core 3.1.</span></span>

## <a name="ccli-net-core-limitations"></a><span data-ttu-id="68b12-107">Limitaciones de .NET Core respecto a C++/CLI</span><span class="sxs-lookup"><span data-stu-id="68b12-107">C++/CLI .NET Core limitations</span></span>

<span data-ttu-id="68b12-108">Hay algunas limitaciones importantes en cuanto a la migración de proyectos de C++/CLI a .NET Core en comparación con otros lenguajes:</span><span class="sxs-lookup"><span data-stu-id="68b12-108">There are some important limitations to porting C++/CLI projects to .NET Core compared to other languages:</span></span>

* <span data-ttu-id="68b12-109">La compatibilidad de C++/CLI con .NET Core es solo en Windows.</span><span class="sxs-lookup"><span data-stu-id="68b12-109">C++/CLI support for .NET Core is Windows only.</span></span>
* <span data-ttu-id="68b12-110">Los proyectos de C++/CLI no pueden tener como destino .NET Standard, solo .NET Core (o .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="68b12-110">C++/CLI projects can't target .NET Standard, only .NET Core (or .NET Framework).</span></span>
* <span data-ttu-id="68b12-111">Los proyectos de C++/CLI no admiten el nuevo formato de archivo de proyecto de estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="68b12-111">C++/CLI projects don't support the new SDK-style project file format.</span></span> <span data-ttu-id="68b12-112">En su lugar, aun cuando el destino sea .NET Core, los proyectos de C++/CLI usan el formato de archivo vcxproj existente.</span><span class="sxs-lookup"><span data-stu-id="68b12-112">Instead, even when targeting .NET Core, C++/CLI projects use the existing vcxproj file format.</span></span>
* <span data-ttu-id="68b12-113">Los proyectos de C++/CLI no pueden tener como destino varias plataformas de .NET.</span><span class="sxs-lookup"><span data-stu-id="68b12-113">C++/CLI projects can't multitarget multiple .NET platforms.</span></span> <span data-ttu-id="68b12-114">Si necesita compilar un proyecto de C++/CLI para .NET Framework y .NET Core, use archivos de proyecto independientes.</span><span class="sxs-lookup"><span data-stu-id="68b12-114">If you need to build a C++/CLI project for both .NET Framework and .NET Core, use separate project files.</span></span>
* <span data-ttu-id="68b12-115">.NET Core no admite la compilación `-clr:pure` o `-clr:safe`, solo la nueva opción `-clr:netcore` (que es equivalente a `-clr` para .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="68b12-115">.NET Core doesn't support `-clr:pure` or `-clr:safe` compilation, only the new `-clr:netcore` option (which is equivalent to `-clr` for .NET Framework).</span></span>

## <a name="port-a-ccli-project"></a><span data-ttu-id="68b12-116">Migración de un proyecto de C++/CLI</span><span class="sxs-lookup"><span data-stu-id="68b12-116">Port a C++/CLI project</span></span>

<span data-ttu-id="68b12-117">Para migrar un proyecto de C++/CLI a .NET Core, realice los cambios siguientes en el archivo vcxproj.</span><span class="sxs-lookup"><span data-stu-id="68b12-117">To port a C++/CLI project to .NET Core, make the following changes to the vcxproj file.</span></span> <span data-ttu-id="68b12-118">Estos pasos de migración difieren de los necesarios para otros tipos de proyectos, ya que los proyectos de C++/CLI no usan archivos de proyecto de estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="68b12-118">These migration steps differ from the steps needed for other project types because C++/CLI projects don't use SDK-style project files.</span></span>

1. <span data-ttu-id="68b12-119">Reemplace las propiedades de `<CLRSupport>true</CLRSupport>` por `<CLRSupport>NetCore</CLRSupport>`.</span><span class="sxs-lookup"><span data-stu-id="68b12-119">Replace `<CLRSupport>true</CLRSupport>` properties with `<CLRSupport>NetCore</CLRSupport>`.</span></span> <span data-ttu-id="68b12-120">Esta propiedad suele estar en grupos de propiedades específicas de la configuración, por lo que puede que tenga que reemplazarla en varios lugares.</span><span class="sxs-lookup"><span data-stu-id="68b12-120">This property is often in configuration-specific property groups, so you may need to replace it in multiple places.</span></span>
2. <span data-ttu-id="68b12-121">Reemplace las propiedades de `<TargetFrameworkVersion>` por `<TargetFramework>netcoreapp3.1</TargetFramework>`.</span><span class="sxs-lookup"><span data-stu-id="68b12-121">Replace `<TargetFrameworkVersion>` properties with `<TargetFramework>netcoreapp3.1</TargetFramework>`.</span></span>
3. <span data-ttu-id="68b12-122">Quite todas las referencias de .NET Framework (como `<Reference Include="System" />`).</span><span class="sxs-lookup"><span data-stu-id="68b12-122">Remove any .NET Framework references (like `<Reference Include="System" />`).</span></span> <span data-ttu-id="68b12-123">Cuando se usa `<CLRSupport>NetCore</CLRSupport>`, se hace referencia automáticamente a los ensamblados del SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-123">.NET Core SDK assemblies are automatically referenced when using `<CLRSupport>NetCore</CLRSupport>`.</span></span>
4. <span data-ttu-id="68b12-124">Actualice el uso de API en los archivos cpp, según sea necesario, para quitar las API que no están disponibles en .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-124">Update API usage in cpp files, as necessary, to remove APIs unavailable to .NET Core.</span></span> <span data-ttu-id="68b12-125">Dado que los proyectos de C++/CLI tienden a ser capas de interoperabilidad bastante finas, no se suelen necesitar muchos cambios.</span><span class="sxs-lookup"><span data-stu-id="68b12-125">Because C++/CLI projects tend to be fairly thin interop layers, there are often not many changes needed.</span></span> <span data-ttu-id="68b12-126">Se puede usar el [Analizador de portabilidad de .NET](../../standard/analyzers/portability-analyzer.md) para identificar las API de .NET no compatibles que usan los binarios de C++/CLI, como con los binarios puramente administrados.</span><span class="sxs-lookup"><span data-stu-id="68b12-126">The [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) can be used to identify unsupported .NET APIs used by C++/CLI binaries just as with purely managed binaries.</span></span> <span data-ttu-id="68b12-127">Las instrucciones para determinar la portabilidad del código y para actualizar los proyectos de modo que funcionen con las API de .NET Core están disponibles en la [guía de portabilidad de bibliotecas](./libraries.md#determine-portability).</span><span class="sxs-lookup"><span data-stu-id="68b12-127">Guidelines for determining code portability and updating projects to work with .NET Core APIs are available in the [library porting guidance](./libraries.md#determine-portability).</span></span>

### <a name="wpf-and-windows-forms-usage"></a><span data-ttu-id="68b12-128">Uso de WPF y Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68b12-128">WPF and Windows Forms usage</span></span>

<span data-ttu-id="68b12-129">Los proyectos de C++/CLI de .NET Core pueden usar las API de Windows Forms y WPF.</span><span class="sxs-lookup"><span data-stu-id="68b12-129">.NET Core C++/CLI projects can use Windows Forms and WPF APIs.</span></span> <span data-ttu-id="68b12-130">Para usar estas API de escritorio de Windows, debe agregar referencias de marco de trabajo explícitas a las bibliotecas de interfaces de usuario.</span><span class="sxs-lookup"><span data-stu-id="68b12-130">To use these Windows desktop APIs, you need to add explicit framework references to the UI libraries.</span></span> <span data-ttu-id="68b12-131">Los proyectos de estilo SDK que usan las API de escritorio de Windows hacen referencia a las bibliotecas de marcos de trabajo necesarias de forma automática mediante el SDK de `Microsoft.NET.Sdk.WindowsDesktop`.</span><span class="sxs-lookup"><span data-stu-id="68b12-131">SDK-style projects that use Windows desktop APIs reference the necessary framework libraries automatically by using the `Microsoft.NET.Sdk.WindowsDesktop` SDK.</span></span> <span data-ttu-id="68b12-132">Dado que los proyectos de C++/CLI no usan el formato de proyecto de estilo SDK, necesitan agregar referencias de marco de trabajo explícitas si el destino es .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-132">Because C++/CLI projects don't use the SDK-style project format, they need to add explicit framework references when targeting .NET Core.</span></span>

<span data-ttu-id="68b12-133">Para usar API de Windows Forms, agregue esta referencia al archivo vcxproj:</span><span class="sxs-lookup"><span data-stu-id="68b12-133">To use Windows Forms APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

<span data-ttu-id="68b12-134">Para usar API de WPF, agregue esta referencia al archivo vcxproj:</span><span class="sxs-lookup"><span data-stu-id="68b12-134">To use WPF APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

<span data-ttu-id="68b12-135">Para usar API de Windows Forms y WPF, agregue esta referencia al archivo vcxproj:</span><span class="sxs-lookup"><span data-stu-id="68b12-135">To use both Windows Forms and WPF APIs, add this reference to the vcxproj file:</span></span>

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

<span data-ttu-id="68b12-136">De momento no es posible agregar estas referencias mediante el administrador de referencias de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68b12-136">Currently, it's not possible to add these references using Visual Studio's reference manager.</span></span> <span data-ttu-id="68b12-137">En su lugar, actualice el archivo de proyecto de forma manual.</span><span class="sxs-lookup"><span data-stu-id="68b12-137">Instead, update the project file manually.</span></span> <span data-ttu-id="68b12-138">Esta actualización se puede realizar en Visual Studio si se descarga el proyecto y luego se edita el archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="68b12-138">This update can be done in Visual Studio by unloading the project and then editing the project file.</span></span> <span data-ttu-id="68b12-139">También puede usar otro editor, como VS Code.</span><span class="sxs-lookup"><span data-stu-id="68b12-139">You can also use another editor like VS Code.</span></span>

## <a name="build-without-msbuild"></a><span data-ttu-id="68b12-140">Compilación sin MSBuild</span><span class="sxs-lookup"><span data-stu-id="68b12-140">Build without MSBuild</span></span>

<span data-ttu-id="68b12-141">También es posible compilar proyectos de C++/CLI sin usar MSBuild.</span><span class="sxs-lookup"><span data-stu-id="68b12-141">It's also possible to build C++/CLI projects without using MSBuild.</span></span> <span data-ttu-id="68b12-142">Siga estos pasos para compilar un proyecto de C++/CLI para .NET Core directamente con *cl.exe* y *link.exe*:</span><span class="sxs-lookup"><span data-stu-id="68b12-142">Follow these steps to build a C++/CLI project for .NET Core directly with *cl.exe* and *link.exe*:</span></span>

1. <span data-ttu-id="68b12-143">Al compilar, pase `-clr:netcore` a *cl.exe*.</span><span class="sxs-lookup"><span data-stu-id="68b12-143">When compiling, pass `-clr:netcore` to *cl.exe*.</span></span>
2. <span data-ttu-id="68b12-144">Haga referencia a los ensamblados de referencia de .NET Core necesarios.</span><span class="sxs-lookup"><span data-stu-id="68b12-144">Reference necessary .NET Core reference assemblies.</span></span>
3. <span data-ttu-id="68b12-145">Al vincular, proporcione el directorio de host de la aplicación .NET Core como `LibPath` (de modo que se pueda encontrar *ijwhost.lib*).</span><span class="sxs-lookup"><span data-stu-id="68b12-145">When linking, provide the .NET Core app host directory as a `LibPath` (so that *ijwhost.lib* can be found).</span></span>
4. <span data-ttu-id="68b12-146">Copie *ijwhost.dll* (desde el directorio de host de la aplicación .NET Core) en el directorio de salida del proyecto.</span><span class="sxs-lookup"><span data-stu-id="68b12-146">Copy *ijwhost.dll* (from the .NET Core app host directory) to the project's output directory.</span></span>
5. <span data-ttu-id="68b12-147">Asegúrese de que exista un archivo [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) para el primer componente de la aplicación que va a ejecutar el código administrado.</span><span class="sxs-lookup"><span data-stu-id="68b12-147">Make sure a [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) file exists for the first component of the application that will run managed code.</span></span> <span data-ttu-id="68b12-148">Si la aplicación tiene un punto de entrada administrado, se crea un archivo `runtime.config` y se copia automáticamente.</span><span class="sxs-lookup"><span data-stu-id="68b12-148">If the application has a managed entry point, a `runtime.config` file will be created and copied automatically.</span></span> <span data-ttu-id="68b12-149">Pero si la aplicación tiene un punto de entrada nativo, debe crear un archivo `runtimeconfig.json` para que la primera biblioteca de C++/CLI use el runtime de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-149">If the application has a native entry point, though, you need to create a `runtimeconfig.json` file for the first C++/CLI library to use the .NET Core runtime.</span></span>

## <a name="known-issues"></a><span data-ttu-id="68b12-150">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="68b12-150">Known issues</span></span>

<span data-ttu-id="68b12-151">Hay un par de problemas conocidos que se deben tener en cuentan a la hora de trabajar con proyectos de C++/CLI cuyo destino es .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-151">There are a couple known issues to look out for when working with C++/CLI projects targeting .NET Core.</span></span>

* <span data-ttu-id="68b12-152">Una referencia de marco de trabajo de WPF en proyectos de C++/CLI de .NET Core actualmente provoca algunas advertencias superfluas sobre la imposibilidad de importar símbolos.</span><span class="sxs-lookup"><span data-stu-id="68b12-152">A WPF framework reference in .NET Core C++/CLI projects currently causes some extraneous warnings about being unable to import symbols.</span></span> <span data-ttu-id="68b12-153">Estas advertencias se pueden pasar por alto sin problemas y se deberían corregir en breve.</span><span class="sxs-lookup"><span data-stu-id="68b12-153">These warnings can be safely ignored and should be fixed soon.</span></span>
* <span data-ttu-id="68b12-154">Si la aplicación tiene un punto de entrada nativo, la biblioteca de C++/CLI que primero ejecuta el código administrado necesita un archivo [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="68b12-154">If the application has a native entry point, the C++/CLI library that first executes managed code needs a [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) file.</span></span> <span data-ttu-id="68b12-155">Este archivo de configuración se usa cuando se inicia el runtime de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68b12-155">This config file is used when the .NET Core runtime starts.</span></span> <span data-ttu-id="68b12-156">Los proyectos de C++/CLI aún no crean archivos `runtimeconfig.json` automáticamente en tiempo de compilación, por lo que el archivo debe generarse manualmente.</span><span class="sxs-lookup"><span data-stu-id="68b12-156">C++/CLI projects don't create `runtimeconfig.json` files automatically at build time yet, so the file must be generated manually.</span></span> <span data-ttu-id="68b12-157">Si se llama a una biblioteca de C++/CLI desde un punto de entrada administrado, esta no necesita un archivo `runtimeconfig.json` (puesto que el ensamblado del punto de entrada tiene uno que se usa al iniciar el runtime).</span><span class="sxs-lookup"><span data-stu-id="68b12-157">If a C++/CLI library is called from a managed entry point, then the C++/CLI library doesn't need a `runtimeconfig.json` file (since the entry point assembly will have one that is used when starting the runtime).</span></span> <span data-ttu-id="68b12-158">A continuación se muestra un archivo `runtimeconfig.json` de ejemplo sencillo.</span><span class="sxs-lookup"><span data-stu-id="68b12-158">A simple sample `runtimeconfig.json` file is shown below.</span></span> <span data-ttu-id="68b12-159">Para obtener más información, vea la [especificación en GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="68b12-159">For more information, see the [spec on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```