---
description: -filealign (Opciones del compilador de C#)
title: -filealign (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: 4b61217a3d6812ea3ab036f82d49bba05c20629e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173248"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="c9ea0-103">-filealign (Opciones del compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="c9ea0-103">-filealign (C# Compiler Options)</span></span>

<span data-ttu-id="c9ea0-104">La opción **-filealign** permite especificar el tamaño de las secciones en el archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ea0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c9ea0-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9ea0-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c9ea0-106">Arguments</span></span>  

 `number`  
 <span data-ttu-id="c9ea0-107">Un valor que especifica el tamaño de las secciones del archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="c9ea0-108">Los valores válidos son 512, 1024, 2048, 4096 y 8192.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="c9ea0-109">Estos valores están en bytes.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9ea0-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c9ea0-110">Remarks</span></span>  

 <span data-ttu-id="c9ea0-111">Cada sección se alineará en un límite que es un múltiplo del valor **-filealign**.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="c9ea0-112">No hay ningún valor predeterminado fijo.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-112">There is no fixed default.</span></span> <span data-ttu-id="c9ea0-113">Si no se especifica **-filealign**, Common Language Runtime elige un valor predeterminado en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="c9ea0-114">Al especificar el tamaño de la sección, el tamaño del archivo de salida se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="c9ea0-115">Modificar el tamaño de la sección puede ser útil para los programas que se ejecutan en dispositivos más pequeños.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="c9ea0-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) para ver información sobre las secciones en el archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c9ea0-117">Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c9ea0-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c9ea0-118">Abra la página **Propiedades** del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="c9ea0-119">Haga clic en la página de propiedades de **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="c9ea0-120">Haga clic en el botón **Avanzadas** .</span><span class="sxs-lookup"><span data-stu-id="c9ea0-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="c9ea0-121">Modifique la propiedad **Alineación de archivo**.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="c9ea0-122">Para obtener información sobre cómo establecer esta opción del compilador mediante programación, vea <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9ea0-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ea0-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="c9ea0-123">See also</span></span>

- [<span data-ttu-id="c9ea0-124">Opciones del compilador de C#</span><span class="sxs-lookup"><span data-stu-id="c9ea0-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c9ea0-125">Administrar propiedades de soluciones y proyectos</span><span class="sxs-lookup"><span data-stu-id="c9ea0-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
