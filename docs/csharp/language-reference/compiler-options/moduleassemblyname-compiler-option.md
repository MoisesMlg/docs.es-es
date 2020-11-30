---
description: -moduleassemblyname (Opción del compilador de C#)
title: -moduleassemblyname (Opción del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9131db17d767c76fe6a57f5d5353474153e0c269
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194094"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="9843c-103">-moduleassemblyname (Opción del compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="9843c-103">-moduleassemblyname (C# Compiler Option)</span></span>

<span data-ttu-id="9843c-104">Especifica un ensamblado con tipos no públicos a los que puede acceder un archivo .netmodule.</span><span class="sxs-lookup"><span data-stu-id="9843c-104">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9843c-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9843c-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="9843c-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9843c-106">Arguments</span></span>  

 `assembly_name`  
 <span data-ttu-id="9843c-107">El nombre del ensamblado a cuyos tipos no públicos .netmodule puede tener acceso.</span><span class="sxs-lookup"><span data-stu-id="9843c-107">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9843c-108">Observaciones</span><span class="sxs-lookup"><span data-stu-id="9843c-108">Remarks</span></span>  

 <span data-ttu-id="9843c-109">Se debería usar **-moduleassemblyname** al compilar un .netmodule cuando se den las condiciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="9843c-109">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="9843c-110">.netmodule necesita tener acceso a los tipos no públicos de un ensamblado existente.</span><span class="sxs-lookup"><span data-stu-id="9843c-110">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="9843c-111">Sabe el nombre del ensamblado en el que se compilará .netmodule.</span><span class="sxs-lookup"><span data-stu-id="9843c-111">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="9843c-112">El ensamblado existente ha concedido acceso de ensamblado de confianza al ensamblado en el que se compilará .netmodule.</span><span class="sxs-lookup"><span data-stu-id="9843c-112">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="9843c-113">Para más información sobre cómo compilar .netmodule, vea [-target:module (Opciones del compilador de C#)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9843c-113">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="9843c-114">Para obtener más información sobre los ensamblados de confianza, vea [Ensamblados de confianza](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="9843c-114">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="9843c-115">Esta opción no está disponible en el entorno de desarrollo; solo está disponible cuando se compila desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="9843c-115">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="9843c-116">Esta opción del compilador no está disponible en Visual Studio y no se puede cambiar mediante programación.</span><span class="sxs-lookup"><span data-stu-id="9843c-116">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9843c-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9843c-117">Example</span></span>  

 <span data-ttu-id="9843c-118">Este ejemplo compila un ensamblado con un tipo privado que concede acceso de ensamblado de confianza a un ensamblado llamado csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="9843c-118">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class
{  
    public void Test()
    {
        Console.WriteLine("An_Internal_Class.Test called");
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="9843c-119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9843c-119">Example</span></span>  

 <span data-ttu-id="9843c-120">Este ejemplo compila un .netmodule que tiene acceso a un tipo no público del ensamblado moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="9843c-120">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="9843c-121">Sabiendo que este .netmodule se integrará en un ensamblado denominado csman_an_assembly, se puede especificar **-moduleassemblyname**, lo que permite que .netmodule tenga acceso a los tipos no públicos de un ensamblado que ha concedido acceso de ensamblado de confianza a csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="9843c-121">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="9843c-122">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9843c-122">Example</span></span>  

 <span data-ttu-id="9843c-123">Este ejemplo de código compila el ensamblado csman_an_assembly, haciendo referencia al ensamblado compilado previamente y a .netmodule.</span><span class="sxs-lookup"><span data-stu-id="9843c-123">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="9843c-124">**Se ha llamado a An_Internal_Class.Test**</span><span class="sxs-lookup"><span data-stu-id="9843c-124">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="9843c-125">Vea también</span><span class="sxs-lookup"><span data-stu-id="9843c-125">See also</span></span>

- [<span data-ttu-id="9843c-126">Opciones del compilador de C#</span><span class="sxs-lookup"><span data-stu-id="9843c-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9843c-127">Administrar propiedades de soluciones y proyectos</span><span class="sxs-lookup"><span data-stu-id="9843c-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
