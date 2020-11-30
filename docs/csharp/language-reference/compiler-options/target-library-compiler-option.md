---
description: -target:library (Opciones del compilador de C#)
title: -target:library (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0f5b1e1bec8fd601bf111e1c2c64adf22d0a064e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193730"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="03113-103">-target:library (Opciones del compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="03113-103">-target:library (C# Compiler Options)</span></span>

<span data-ttu-id="03113-104">La opción **-target:library** hace que el compilador cree una biblioteca de vínculos dinámicos (DLL) en lugar de un archivo ejecutable (EXE).</span><span class="sxs-lookup"><span data-stu-id="03113-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03113-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="03113-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="03113-106">Observaciones</span><span class="sxs-lookup"><span data-stu-id="03113-106">Remarks</span></span>  

 <span data-ttu-id="03113-107">El archivo DLL se creará con la extensión .dll.</span><span class="sxs-lookup"><span data-stu-id="03113-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="03113-108">A menos que se especifique lo contrario con la opción [-out](./out-compiler-option.md), el archivo de salida adopta el nombre del primer archivo de entrada.</span><span class="sxs-lookup"><span data-stu-id="03113-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="03113-109">Cuando se especifica en la línea de comandos, se usan todos los archivos hasta la siguiente opción **-out** o **-target:module** para crear el archivo .dll.</span><span class="sxs-lookup"><span data-stu-id="03113-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="03113-110">Al compilar un archivo .dll, no es necesario un método [Main](../../programming-guide/main-and-command-args/index.md).</span><span class="sxs-lookup"><span data-stu-id="03113-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="03113-111">Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03113-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="03113-112">Abra la página **Propiedades** del proyecto.</span><span class="sxs-lookup"><span data-stu-id="03113-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="03113-113">Haga clic en la página de propiedades **Aplicación**.</span><span class="sxs-lookup"><span data-stu-id="03113-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="03113-114">Modifique la propiedad **Tipo de salida**.</span><span class="sxs-lookup"><span data-stu-id="03113-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="03113-115">Para obtener información sobre cómo establecer esta opción del compilador mediante programación, vea <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="03113-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03113-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="03113-116">Example</span></span>  

 <span data-ttu-id="03113-117">Compilación de `in.cs` y creación de `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="03113-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="03113-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="03113-118">See also</span></span>

- [<span data-ttu-id="03113-119">-target (Opciones del compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="03113-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="03113-120">Opciones del compilador de C#</span><span class="sxs-lookup"><span data-stu-id="03113-120">C# Compiler Options</span></span>](./index.md)
