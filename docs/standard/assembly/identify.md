---
title: Procedimiento para determinar si un archivo es un ensamblado
description: En este artículo se muestra cómo determinar si un archivo es un ensamblado .NET, tanto de forma manual como mediante programación.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: b78acaad31996f8fc2b965f51f541e99aeceb111
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731506"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="6698d-103">Procedimiento para determinar si un archivo es un ensamblado</span><span class="sxs-lookup"><span data-stu-id="6698d-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="6698d-104">Un archivo es un ensamblado únicamente si está administrado y contiene una entrada de ensamblado en sus metadatos.</span><span class="sxs-lookup"><span data-stu-id="6698d-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="6698d-105">Para más información sobre ensamblados y metadatos, vea [Manifiesto del ensamblado](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="6698d-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="6698d-106">Cómo determinar manualmente si un archivo es un ensamblado</span><span class="sxs-lookup"><span data-stu-id="6698d-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="6698d-107">Inicie [Ildasm.exe (el desensamblador de lenguaje intermedio)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="6698d-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="6698d-108">Cargue el archivo que quiere probar.</span><span class="sxs-lookup"><span data-stu-id="6698d-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="6698d-109">Si **ILDASM** notifica que el archivo no es un archivo ejecutable portable (PE), entonces no es un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="6698d-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="6698d-110">Para obtener más información, vea el tema [Cómo: Ver el contenido de un ensamblado](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="6698d-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="6698d-111">Cómo determinar mediante programación si un archivo es un ensamblado</span><span class="sxs-lookup"><span data-stu-id="6698d-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="6698d-112">Llame al método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>; para ello, pase el nombre y la ruta de acceso de archivo completa del archivo que está probando.</span><span class="sxs-lookup"><span data-stu-id="6698d-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="6698d-113">Si se genera una excepción <xref:System.BadImageFormatException>, el archivo no es un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="6698d-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6698d-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6698d-114">Example</span></span>  

<span data-ttu-id="6698d-115">En este ejemplo se prueba un archivo DLL para ver si es un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="6698d-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<span data-ttu-id="6698d-116">El método <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> carga el archivo de prueba y, después, lo libera cuando se lee la información.</span><span class="sxs-lookup"><span data-stu-id="6698d-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6698d-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="6698d-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="6698d-118">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="6698d-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6698d-119">Conceptos de programación (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6698d-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="6698d-120">Ensamblados de .NET</span><span class="sxs-lookup"><span data-stu-id="6698d-120">Assemblies in .NET</span></span>](index.md)
