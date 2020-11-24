---
title: Procedimiento Leer texto de un archivo
description: En este artículo, verá ejemplos sobre cómo leer texto de forma sincrónica y asincrónica desde un archivo de texto mediante la clase StreamReader de .NET para aplicaciones de escritorio.
ms.date: 01/03/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 7c772ec1de41d0ba2b4ef0d924a252326ee6909e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823373"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="664b6-103">Procedimiento Leer texto de un archivo</span><span class="sxs-lookup"><span data-stu-id="664b6-103">How to: Read text from a file</span></span>

<span data-ttu-id="664b6-104">En los ejemplos siguientes se muestra cómo leer texto desde un archivo de texto de forma sincrónica y asincrónica mediante .NET para aplicaciones de escritorio.</span><span class="sxs-lookup"><span data-stu-id="664b6-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="664b6-105">En ambos ejemplos, cuando se crea la instancia de la clase <xref:System.IO.StreamReader>, se proporciona la ruta de acceso relativa o absoluta del archivo.</span><span class="sxs-lookup"><span data-stu-id="664b6-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="664b6-106">Estos ejemplos de código no se aplican a aplicaciones universales de Windows (UWP) porque Windows Runtime ofrece otros tipos de flujos para leer archivos o escribir en ellos.</span><span class="sxs-lookup"><span data-stu-id="664b6-106">These code examples do not apply to Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="664b6-107">Para obtener un ejemplo en el que se muestra cómo leer el texto de un archivo en una aplicación para UWP, consulte [Inicio rápido: lectura y escritura de un archivo](/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="664b6-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="664b6-108">Para obtener ejemplos en los que se muestra cómo convertir entre los flujos de .NET Framework y los de Windows Runtime, consulte [Cómo: Convertir flujos de .NET Framework en flujos de Windows Runtime y viceversa](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="664b6-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="664b6-109">Ejemplo: Lectura sincrónica en una aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="664b6-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="664b6-110">En el siguiente ejemplo se muestra una operación de lectura sincrónica dentro de una aplicación de consola.</span><span class="sxs-lookup"><span data-stu-id="664b6-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="664b6-111">En este ejemplo se abre el archivo de texto con un lector de flujos, copia el contenido en una cadena y genera la cadena en la consola.</span><span class="sxs-lookup"><span data-stu-id="664b6-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="664b6-112">En el ejemplo, se da por supuesto que un archivo llamado *TestFile.txt* ya existe en la misma carpeta que la aplicación.</span><span class="sxs-lookup"><span data-stu-id="664b6-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="664b6-113">Ejemplo: Lectura asincrónica en una aplicación WPF</span><span class="sxs-lookup"><span data-stu-id="664b6-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="664b6-114">En el siguiente ejemplo se muestra una operación de lectura asincrónica en una aplicación de Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="664b6-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="664b6-115">En el ejemplo, se da por supuesto que un archivo llamado *TestFile.txt* ya existe en la misma carpeta que la aplicación.</span><span class="sxs-lookup"><span data-stu-id="664b6-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a><span data-ttu-id="664b6-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="664b6-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="664b6-117">E/S de archivos asincrónica</span><span class="sxs-lookup"><span data-stu-id="664b6-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="664b6-118">[Cómo: Crear una lista de directorios](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="664b6-118">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- <span data-ttu-id="664b6-119">[Inicio rápido: lectura y escritura de archivos](/previous-versions/windows/apps/hh758325(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="664b6-119">[Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10))</span></span>  
- [<span data-ttu-id="664b6-120">Cómo: Convertir flujos de .NET Framework en flujos de Windows Runtime y viceversa</span><span class="sxs-lookup"><span data-stu-id="664b6-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="664b6-121">Cómo: Leer y escribir en un archivo de datos recién creado</span><span class="sxs-lookup"><span data-stu-id="664b6-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="664b6-122">Cómo: Abrir y anexar a un archivo de registro</span><span class="sxs-lookup"><span data-stu-id="664b6-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="664b6-123">Cómo: Escribir texto en un archivo</span><span class="sxs-lookup"><span data-stu-id="664b6-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="664b6-124">Cómo: Leer caracteres de una cadena</span><span class="sxs-lookup"><span data-stu-id="664b6-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="664b6-125">Cómo: Escribir caracteres en una cadena</span><span class="sxs-lookup"><span data-stu-id="664b6-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="664b6-126">E/S de archivos y secuencias</span><span class="sxs-lookup"><span data-stu-id="664b6-126">File and stream I/O</span></span>](index.md)
