---
description: -bugreport (Opciones del compilador de C#)
title: -bugreport (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 1fb2efc9b12680e95767746c7e4e1ddacbdd2594
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "93281511"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="fd18a-103">-bugreport (Opciones del compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="fd18a-103">-bugreport (C# Compiler Options)</span></span>

<span data-ttu-id="fd18a-104">Especifica que esa información de depuración debe colocarse en un archivo para su análisis posterior.</span><span class="sxs-lookup"><span data-stu-id="fd18a-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd18a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fd18a-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd18a-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="fd18a-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="fd18a-107">El nombre del archivo que quiere que contenga su informe de errores.</span><span class="sxs-lookup"><span data-stu-id="fd18a-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd18a-108">Observaciones</span><span class="sxs-lookup"><span data-stu-id="fd18a-108">Remarks</span></span>  

 <span data-ttu-id="fd18a-109">La opción **-bugreport** especifica que la siguiente información debe colocarse en `file`:</span><span class="sxs-lookup"><span data-stu-id="fd18a-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="fd18a-110">Una copia de todos los archivos de código fuente de la compilación.</span><span class="sxs-lookup"><span data-stu-id="fd18a-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="fd18a-111">Una lista de las opciones del compilador que se han usado en la compilación.</span><span class="sxs-lookup"><span data-stu-id="fd18a-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="fd18a-112">Información de la versión sobre su compilador, tiempo de ejecución y sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="fd18a-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="fd18a-113">Módulos y ensamblados a los que se hace referencia, guardados como dígitos hexadecimales, excepto los ensamblados que se proporcionan con .NET y el SDK de .NET.</span><span class="sxs-lookup"><span data-stu-id="fd18a-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that are shipped with .NET and the .NET SDK.</span></span>  
  
- <span data-ttu-id="fd18a-114">Resultados del compilador, si los hay.</span><span class="sxs-lookup"><span data-stu-id="fd18a-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="fd18a-115">Una descripción del problema, que se le pedirá.</span><span class="sxs-lookup"><span data-stu-id="fd18a-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="fd18a-116">Una descripción de cómo cree que debe corregirse el problema, que se le pedirá.</span><span class="sxs-lookup"><span data-stu-id="fd18a-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="fd18a-117">Si esta opción se usa con **-errorreport:prompt** o **-errorreport:send**, la información del archivo se enviará a Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="fd18a-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="fd18a-118">Como una copia de todos los archivos de código fuente se colocarán en `file`, puede que quiera reproducir el defecto en el código sospechoso en el programa más corto posible.</span><span class="sxs-lookup"><span data-stu-id="fd18a-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="fd18a-119">Esta opción del compilador no está disponible en Visual Studio y no se puede cambiar mediante programación.</span><span class="sxs-lookup"><span data-stu-id="fd18a-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="fd18a-120">Tenga en cuenta que el contenido del código fuente expuesto del archivo generado puede provocar la divulgación de información involuntaria.</span><span class="sxs-lookup"><span data-stu-id="fd18a-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd18a-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="fd18a-121">See also</span></span>

- [<span data-ttu-id="fd18a-122">Opciones del compilador de C#</span><span class="sxs-lookup"><span data-stu-id="fd18a-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fd18a-123">-errorreport (Opciones del compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="fd18a-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="fd18a-124">Administrar propiedades de soluciones y proyectos</span><span class="sxs-lookup"><span data-stu-id="fd18a-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
