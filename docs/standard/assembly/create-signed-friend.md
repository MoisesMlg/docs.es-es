---
title: Procedimiento para crear ensamblados de confianza firmados
description: En este artículo se muestra cómo usar ensamblados de confianza con ensamblados que tienen nombres seguros. Se incluye información sobre la seguridad de .NET.
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 4c441501ae0f939f69ac863a990d6e392bd35fc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734275"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="5d58d-104">Procedimiento para crear ensamblados de confianza firmados</span><span class="sxs-lookup"><span data-stu-id="5d58d-104">How to: Create signed friend assemblies</span></span>

<span data-ttu-id="5d58d-105">En este ejemplo se muestra cómo usar ensamblados de confianza con ensamblados que tienen nombres seguros.</span><span class="sxs-lookup"><span data-stu-id="5d58d-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="5d58d-106">Ambos ensamblados deben tener nombres seguros.</span><span class="sxs-lookup"><span data-stu-id="5d58d-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="5d58d-107">Aunque los dos ensamblados de este ejemplo usan las mismas claves, es posible usar claves diferentes para dos ensamblados.</span><span class="sxs-lookup"><span data-stu-id="5d58d-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="5d58d-108">Creación de un ensamblado firmado y un ensamblado de confianza</span><span class="sxs-lookup"><span data-stu-id="5d58d-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="5d58d-109">Abra un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="5d58d-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="5d58d-110">Use la siguiente secuencia de comandos con la herramienta de nombre seguro para generar un archivo de claves y mostrar su clave pública.</span><span class="sxs-lookup"><span data-stu-id="5d58d-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="5d58d-111">Para obtener más información, vea [Sn.exe (herramienta de nombre seguro)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5d58d-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="5d58d-112">Genere una clave de nombre seguro para este ejemplo y almacénela en el archivo *FriendAssemblies.snk*:</span><span class="sxs-lookup"><span data-stu-id="5d58d-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="5d58d-113">Extraiga la clave pública de *FriendAssemblies.snk* y colóquela en *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="5d58d-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="5d58d-114">Muestre la clave pública almacenada en el archivo *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="5d58d-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="5d58d-115">Cree un archivo de C# o de Visual Basic denominado *friend_signed_A* que contenga el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="5d58d-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="5d58d-116">El código usa el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para declarar *friend_signed_B* como un ensamblado de confianza.</span><span class="sxs-lookup"><span data-stu-id="5d58d-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="5d58d-117">La herramienta de nombre seguro genera una nueva clave pública cada vez que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="5d58d-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="5d58d-118">Por tanto, debe reemplazar la clave pública en el código siguiente con la clave pública que acaba de generar, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="5d58d-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="5d58d-119">Compile y firme *friend_signed_A* mediante el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="5d58d-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="5d58d-120">Cree un archivo de C# o de Visual Basic denominado *friend_signed_B* que contenga el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="5d58d-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="5d58d-121">Dado que *friend_signed_A* especifica que *friend_signed_B* es un ensamblado de confianza, el código de *friend_signed_B* puede tener acceso a tipos y miembros de C# (`internal`) o Visual Basic (`Friend`) desde *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="5d58d-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="5d58d-122">El archivo contiene el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="5d58d-122">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="5d58d-123">Compile y firme *friend_signed_B* mediante el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="5d58d-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="5d58d-124">El nombre del ensamblado generado por el compilador debe coincidir con el nombre del ensamblado de confianza que se ha pasado al atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5d58d-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="5d58d-125">Debe especificar explícitamente el nombre del ensamblado de salida ( *.exe* o *.dll*) mediante la opción `-out` del compilador.</span><span class="sxs-lookup"><span data-stu-id="5d58d-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="5d58d-126">Para obtener más información, consulte [-out (Opciones del compilador de C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) o [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="5d58d-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="5d58d-127">Ejecute el archivo *friend_signed_B.exe*.</span><span class="sxs-lookup"><span data-stu-id="5d58d-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="5d58d-128">El programa imprime la cadena **Class1.Test**.</span><span class="sxs-lookup"><span data-stu-id="5d58d-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="5d58d-129">Seguridad de .NET</span><span class="sxs-lookup"><span data-stu-id="5d58d-129">.NET security</span></span>  

 <span data-ttu-id="5d58d-130">Existen similitudes entre el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> y la clase <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="5d58d-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="5d58d-131">La diferencia principal es que <xref:System.Security.Permissions.StrongNameIdentityPermission> puede exigir permisos de seguridad para ejecutar una sección determinada de código, mientras el atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> controla la visibilidad de los miembros y tipos `internal` (C#) o `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5d58d-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d58d-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="5d58d-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="5d58d-133">Ensamblados de .NET</span><span class="sxs-lookup"><span data-stu-id="5d58d-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="5d58d-134">Ensamblados de confianza</span><span class="sxs-lookup"><span data-stu-id="5d58d-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="5d58d-135">Cómo: Crear ensamblados de confianza sin firmar</span><span class="sxs-lookup"><span data-stu-id="5d58d-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="5d58d-136">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="5d58d-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="5d58d-137">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d58d-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="5d58d-138">Sn.exe (herramienta de nombre seguro)</span><span class="sxs-lookup"><span data-stu-id="5d58d-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="5d58d-139">Creación y uso de ensamblados con nombre seguro</span><span class="sxs-lookup"><span data-stu-id="5d58d-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="5d58d-140">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="5d58d-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5d58d-141">Conceptos de programación (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d58d-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
