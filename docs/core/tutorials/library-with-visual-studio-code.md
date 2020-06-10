---
title: Creación de una biblioteca de clases de .NET Standard en Visual Studio Code
description: Obtenga información sobre cómo crear una biblioteca de clases de .NET Standard mediante Visual Studio Code.
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446957"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a><span data-ttu-id="1b46a-103">Tutorial: Creación de una biblioteca de .NET Standard en Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b46a-103">Tutorial: Create a .NET Standard library in Visual Studio Code</span></span>

<span data-ttu-id="1b46a-104">Una *biblioteca de clases* define los tipos y los métodos que se llaman desde una aplicación.</span><span class="sxs-lookup"><span data-stu-id="1b46a-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="1b46a-105">Una biblioteca de clases que tiene como destino .NET Standard 2.0, lo que permite que cualquier implementación .NET que admita esa versión de .NET Standard pueda llamar a su biblioteca.</span><span class="sxs-lookup"><span data-stu-id="1b46a-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="1b46a-106">Cuando termine la biblioteca de clases, puede decidir si quiere distribuirla como un paquete NuGet o si la quiere incluir como un componente empaquetado con una o varias aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1b46a-106">When you finish your class library, you can decide whether you want to distribute it as a NuGet package or include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="1b46a-107">Para ver una lista de las versiones de .NET Standard y las plataformas que admiten, vea [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="1b46a-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="1b46a-108">En este tutorial, creará una sencilla biblioteca de utilidades que contiene un único método de control de cadenas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="1b46a-109">Lo implementará como un [método de extensión](../../csharp/programming-guide/classes-and-structs/extension-methods.md) de modo que se pueda llamar como si fuera un miembro de la clase <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="1b46a-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1b46a-110">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1b46a-110">Prerequisites</span></span>

1. <span data-ttu-id="1b46a-111">[Visual Studio Code](https://code.visualstudio.com/) con la [extensión de C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) instalada.</span><span class="sxs-lookup"><span data-stu-id="1b46a-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="1b46a-112">Para saber cómo instalar extensiones en Visual Studio Code, vea el [Marketplace de extensiones de VS Code](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="1b46a-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="1b46a-113">[SDK de .NET Core 3.1 o posterior](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="1b46a-113">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="1b46a-114">Crear una solución</span><span class="sxs-lookup"><span data-stu-id="1b46a-114">Create a solution</span></span>

<span data-ttu-id="1b46a-115">Empiece por crear una solución en blanco para colocar el proyecto de biblioteca de clases en ella.</span><span class="sxs-lookup"><span data-stu-id="1b46a-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="1b46a-116">Una solución sirve como contenedor de uno o varios proyectos.</span><span class="sxs-lookup"><span data-stu-id="1b46a-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="1b46a-117">Agregará otros proyectos relacionados a la misma solución.</span><span class="sxs-lookup"><span data-stu-id="1b46a-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="1b46a-118">Abra Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1b46a-118">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="1b46a-119">Seleccione **Archivo** > **Abrir carpeta**/**Abrir...** en el menú principal, cree una carpeta *ClassLibraryProjects* y haga clic en **Seleccionar carpeta**/**Abrir**.</span><span class="sxs-lookup"><span data-stu-id="1b46a-119">Select **File** > **Open Folder**/**Open...** from the main menu, create a *ClassLibraryProjects* folder, and click **Select Folder**/**Open**.</span></span>

1. <span data-ttu-id="1b46a-120">Para abrir el **Terminal**  en Visual Studio Code, seleccione **Ver** > **Terminal** en el menú principal.</span><span class="sxs-lookup"><span data-stu-id="1b46a-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="1b46a-121">Se abre el **terminal** con el símbolo del sistema en la carpeta *ClassLibraryProjects*.</span><span class="sxs-lookup"><span data-stu-id="1b46a-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="1b46a-122">En el **Terminal**, escriba este comando:</span><span class="sxs-lookup"><span data-stu-id="1b46a-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="1b46a-123">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="1b46a-124">Crear un proyecto de biblioteca de clases</span><span class="sxs-lookup"><span data-stu-id="1b46a-124">Create a class library project</span></span>

<span data-ttu-id="1b46a-125">Agregue un nuevo proyecto de biblioteca de clases de .NET Standard denominado "StringLibrary" a la solución.</span><span class="sxs-lookup"><span data-stu-id="1b46a-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="1b46a-126">En el terminal, ejecute el siguiente comando para crear un proyecto de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="1b46a-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="1b46a-127">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="1b46a-128">Ejecute el siguiente comando para agregar el proyecto de biblioteca a la solución:</span><span class="sxs-lookup"><span data-stu-id="1b46a-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="1b46a-129">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="1b46a-130">Asegúrese de que la biblioteca tiene como destino la versión correcta de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1b46a-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="1b46a-131">En **Explorer**, abra el archivo *StringLibrary/StringLibrary.csproj*.</span><span class="sxs-lookup"><span data-stu-id="1b46a-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="1b46a-132">En el elemento `TargetFramework` se muestra que el proyecto tiene como destino .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="1b46a-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="1b46a-133">Abra *Class1.cs* y reemplace el código por el siguiente.</span><span class="sxs-lookup"><span data-stu-id="1b46a-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="1b46a-134">La biblioteca de clases, `UtilityLibraries.StringLibrary`, contiene un método denominado `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="1b46a-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="1b46a-135">Este método devuelve un valor <xref:System.Boolean> que indica si la instancia de cadena actual comienza con un carácter en mayúscula.</span><span class="sxs-lookup"><span data-stu-id="1b46a-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="1b46a-136">El estándar Unicode distingue caracteres en mayúsculas de caracteres en minúsculas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="1b46a-137">El método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> devuelve `true` si un carácter está en mayúsculas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="1b46a-138">Guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="1b46a-138">Save the file.</span></span>

1. <span data-ttu-id="1b46a-139">Ejecute el siguiente comando para compilar la solución y comprobar que el proyecto se compila sin errores.</span><span class="sxs-lookup"><span data-stu-id="1b46a-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="1b46a-140">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-140">The terminal output looks like the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="1b46a-141">Incorporación de una aplicación de consola a la solución</span><span class="sxs-lookup"><span data-stu-id="1b46a-141">Add a console app to the solution</span></span>

<span data-ttu-id="1b46a-142">Agregue una aplicación de consola que use la biblioteca de clases.</span><span class="sxs-lookup"><span data-stu-id="1b46a-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="1b46a-143">La aplicación solicitará al usuario que escriba una cadena y notificará si la cadena comienza con un carácter en mayúsculas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="1b46a-144">En el terminal, ejecute el siguiente comando para crear un proyecto de consola de aplicación:</span><span class="sxs-lookup"><span data-stu-id="1b46a-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="1b46a-145">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="1b46a-146">Ejecute el siguiente comando para agregar el proyecto de aplicación de consola a la solución:</span><span class="sxs-lookup"><span data-stu-id="1b46a-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="1b46a-147">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="1b46a-148">En un principio, el nuevo proyecto de aplicación de consola no tiene acceso a la biblioteca de clases.</span><span class="sxs-lookup"><span data-stu-id="1b46a-148">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="1b46a-149">Para que pueda llamar a los métodos de la biblioteca de clases, cree una referencia de proyecto al proyecto de biblioteca de clases; para ello, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-149">To allow it to call methods in the class library, create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="1b46a-150">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-150">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. <span data-ttu-id="1b46a-151">Abra *ShowCase/Program.cs* y reemplace todo el código por el siguiente.</span><span class="sxs-lookup"><span data-stu-id="1b46a-151">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="1b46a-152">El código usa la variable `row` para mantener un recuento del número de filas de datos escritas en la ventana de consola.</span><span class="sxs-lookup"><span data-stu-id="1b46a-152">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="1b46a-153">Siempre que sea mayor o igual a 25, el código borra la ventana de consola y muestra un mensaje al usuario.</span><span class="sxs-lookup"><span data-stu-id="1b46a-153">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="1b46a-154">El programa le pide al usuario que escriba una cadena.</span><span class="sxs-lookup"><span data-stu-id="1b46a-154">The program prompts the user to enter a string.</span></span> <span data-ttu-id="1b46a-155">Indica si la cadena comienza con un carácter en mayúsculas.</span><span class="sxs-lookup"><span data-stu-id="1b46a-155">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="1b46a-156">Si el usuario presiona la tecla Entrar sin especificar una cadena, la aplicación finaliza y la ventana de la consola se cierra.</span><span class="sxs-lookup"><span data-stu-id="1b46a-156">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="1b46a-157">Guarde los cambios.</span><span class="sxs-lookup"><span data-stu-id="1b46a-157">Save your changes.</span></span>

1. <span data-ttu-id="1b46a-158">Ejecute el programa.</span><span class="sxs-lookup"><span data-stu-id="1b46a-158">Run the program.</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="1b46a-159">Para probar el programa, escriba cadenas y presione <kbd>Entrar</kbd> y, después, presione <kbd>Entrar</kbd> para salir.</span><span class="sxs-lookup"><span data-stu-id="1b46a-159">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="1b46a-160">La salida del terminal se parece al ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1b46a-160">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="1b46a-161">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="1b46a-161">Additional resources</span></span>

* [<span data-ttu-id="1b46a-162">Desarrollo de bibliotecas con la CLI de .NET Core</span><span class="sxs-lookup"><span data-stu-id="1b46a-162">Develop libraries with the .NET Core CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="1b46a-163">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="1b46a-163">Next steps</span></span>

<span data-ttu-id="1b46a-164">En este tutorial, ha creado una solución, ha agregado un proyecto de biblioteca y ha agregado un proyecto de aplicación de consola que usa la biblioteca.</span><span class="sxs-lookup"><span data-stu-id="1b46a-164">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="1b46a-165">En el siguiente tutorial, agregará un proyecto de prueba unitaria a la solución.</span><span class="sxs-lookup"><span data-stu-id="1b46a-165">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1b46a-166">Prueba de una biblioteca .NET Standard con .NET Core en Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b46a-166">Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)