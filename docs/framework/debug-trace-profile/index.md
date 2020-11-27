---
title: Depurar, trazar y generar perfiles
description: Obtenga información sobre la depuración, el seguimiento y la generación de perfiles en .NET. Consulte los artículos que abarcan las aplicaciones de depuración Just-in-Time (JIT), seguimiento e instrumentación, etc.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 33dd840f4c1421bbff54499af56ab3e147cc694b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272779"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="e9850-104">Depurar, trazar y generar perfiles</span><span class="sxs-lookup"><span data-stu-id="e9850-104">Debugging, Tracing, and Profiling</span></span>

<span data-ttu-id="e9850-105">Para depurar una aplicación de .NET Framework, el compilador y el entorno de CLR deben configurarse para poder asociar un depurador a la aplicación y para poder producir símbolos y mapas de líneas, si es posible, para la aplicación y su Lenguaje Intermedio de Microsoft (MSIL) correspondiente.</span><span class="sxs-lookup"><span data-stu-id="e9850-105">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="e9850-106">Una vez depurada una aplicación administrada, se puede generar un perfil para mejorar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e9850-106">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="e9850-107">La generación de perfiles evalúa y describe las líneas de código fuente que generan el código que se ejecuta con más frecuencia, y cuánto tiempo se necesita para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="e9850-107">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="e9850-108">Las aplicaciones de .NET Framework se depuran fácilmente con Visual Studio, que controla muchos de los detalles de la configuración.</span><span class="sxs-lookup"><span data-stu-id="e9850-108">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="e9850-109">Si Visual Studio no está instalado, puede examinar y mejorar el rendimiento de las aplicaciones de .NET Framework usando las clases de depuración del espacio de nombres <xref:System.Diagnostics> de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9850-109">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="e9850-110">Este espacio de nombres incluye las clases <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.TraceSource> para el seguimiento del flujo de ejecución, y las clases <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> y <xref:System.Diagnostics.PerformanceCounter> para generar perfiles de código.</span><span class="sxs-lookup"><span data-stu-id="e9850-110">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9850-111">En esta sección</span><span class="sxs-lookup"><span data-stu-id="e9850-111">In This Section</span></span>  

 [<span data-ttu-id="e9850-112">Habilitar la depuración de adjuntos JIT</span><span class="sxs-lookup"><span data-stu-id="e9850-112">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="e9850-113">Muestra cómo configurar el Registro para adjuntar con JIT un motor de depuración a una aplicación de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9850-113">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="e9850-114">Facilitar la depuración de una imagen</span><span class="sxs-lookup"><span data-stu-id="e9850-114">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="e9850-115">Muestra cómo activar el seguimiento de JIT y desactivar la optimización para facilitar la depuración de un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="e9850-115">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="e9850-116">Seguimiento e instrumentación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="e9850-116">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="e9850-117">Describe cómo supervisar la ejecución de la aplicación mientras se está ejecutando y cómo instrumentarla para mostrar si se ha ejecutado correctamente o si tiene errores.</span><span class="sxs-lookup"><span data-stu-id="e9850-117">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="e9850-118">Diagnóstico de errores con asistentes de depuraciones administradas</span><span class="sxs-lookup"><span data-stu-id="e9850-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="e9850-119">Describe los asistentes para la depuración administrada (MDA), que ayudan en la depuración y trabajan con Common Language Runtime (CLR) para proporcionar información sobre el estado en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e9850-119">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="e9850-120">Mejorar la depuración con los atributos de visualización del depurador</span><span class="sxs-lookup"><span data-stu-id="e9850-120">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="e9850-121">Describe el procedimiento que puede seguir el desarrollador de un tipo para especificar cómo se mostrará ese tipo en un depurador.</span><span class="sxs-lookup"><span data-stu-id="e9850-121">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="e9850-122">Contadores de rendimiento</span><span class="sxs-lookup"><span data-stu-id="e9850-122">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="e9850-123">Describe los contadores que puede usar para supervisar el rendimiento de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="e9850-123">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9850-124">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="e9850-124">Related Sections</span></span>  

 [<span data-ttu-id="e9850-125">Depuración de aplicaciones de ASP.NET o ASP.NET Core en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e9850-125">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="e9850-126">Indica los requisitos previos y las instrucciones para depurar una aplicación de ASP.NET durante el desarrollo o después de la implementación.</span><span class="sxs-lookup"><span data-stu-id="e9850-126">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="e9850-127">Guía de desarrollo para .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9850-127">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="e9850-128">Proporciona una guía para todas las áreas y tareas tecnológicas principales para el desarrollo de aplicaciones, como la creación, configuración, depuración, seguridad e implementación de la aplicación, e información sobre programación dinámica, interoperabilidad, extensibilidad, administración de memoria y subprocesamiento.</span><span class="sxs-lookup"><span data-stu-id="e9850-128">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
