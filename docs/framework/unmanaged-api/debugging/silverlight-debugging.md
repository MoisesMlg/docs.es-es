---
title: Depuración en Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 49f026b8e1a3dd78a62091e77a5aba0c9a2e09d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671842"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="2e845-102">Depuración en Silverlight</span><span class="sxs-lookup"><span data-stu-id="2e845-102">Silverlight Debugging</span></span>

<span data-ttu-id="2e845-103">En los temas de esta sección describen el entorno y las interfaces que Common Language Runtime (CLR) proporciona para admitir la depuración de aplicaciones basadas en Silverlight que se ejecutan en el sistema operativo Windows, o en la plataforma Macintosh.</span><span class="sxs-lookup"><span data-stu-id="2e845-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e845-104">En esta sección</span><span class="sxs-lookup"><span data-stu-id="2e845-104">In This Section</span></span>  

 [<span data-ttu-id="2e845-105">EnumerateCLRs (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="2e845-106">Proporciona un mecanismo para enumerar los CLR de un proceso.</span><span class="sxs-lookup"><span data-stu-id="2e845-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="2e845-107">CloseCLREnumeration (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="2e845-108">Cierra los eventos válidos continue-startup de CLR que se encuentran en una matriz de identificadores devueltos por la [función enumerateclrs (](enumerateclrs-function.md)y libera la memoria para las matrices de rutas de acceso de identificador y de cadena.</span><span class="sxs-lookup"><span data-stu-id="2e845-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="2e845-109">CreateCoreClrDebugTarget (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="2e845-110">Crea una conexión a un destino remoto para la enumeración de procesos y tiempos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2e845-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="2e845-111">CreateCordbObject (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="2e845-112">Crea una interfaz de depurador que proporciona la funcionalidad para crear instancias de una sesión de depuración administrada en un proceso remoto.</span><span class="sxs-lookup"><span data-stu-id="2e845-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="2e845-113">CreateVersionStringFromModule (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="2e845-114">Crea una cadena de versión a partir de una ruta de acceso de CLR en un proceso de destino.</span><span class="sxs-lookup"><span data-stu-id="2e845-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="2e845-115">CreateDebuggingInterfaceFromVersion (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="2e845-116">Acepta una cadena de versión de CLR devuelta por la función de [función createversionstringfrommodule (](createversionstringfrommodule-function.md)y devuelve una interfaz de depurador correspondiente.</span><span class="sxs-lookup"><span data-stu-id="2e845-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="2e845-117">CoreClrDebugProcInfo (Estructura)</span><span class="sxs-lookup"><span data-stu-id="2e845-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="2e845-118">Representa un proceso que se ejecuta en un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="2e845-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="2e845-119">CoreClrDebugRuntimeInfo (Estructura)</span><span class="sxs-lookup"><span data-stu-id="2e845-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="2e845-120">Representa una instancia de CLR que se carga en un proceso en un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="2e845-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="2e845-121">GetStartupNotificationEvent (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="2e845-122">Crea o abre un identificador de evento al que apuntará cualquier Common Language Runtime (CLR) que se cargue en el proceso de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="2e845-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="2e845-123">ICoreClrDebugTarget (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2e845-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="2e845-124">Crea una conexión a un destino remoto para la enumeración de procesos y tiempos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2e845-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="2e845-125">InitDbgTransportManager (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="2e845-126">Inicializa el administrador de transporte para conectarse a un destino remoto para la enumeración de procesos y tiempos de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2e845-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="2e845-127">ShutdownDbgTransportManager (Función)</span><span class="sxs-lookup"><span data-stu-id="2e845-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="2e845-128">Cierra el administrador de transporte para una conexión a un equipo de destino remoto.</span><span class="sxs-lookup"><span data-stu-id="2e845-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e845-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2e845-129">See also</span></span>

- [<span data-ttu-id="2e845-130">Coclases para la depuración</span><span class="sxs-lookup"><span data-stu-id="2e845-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="2e845-131">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="2e845-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2e845-132">Funciones estáticas globales para la depuración</span><span class="sxs-lookup"><span data-stu-id="2e845-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="2e845-133">Enumeraciones de depuración</span><span class="sxs-lookup"><span data-stu-id="2e845-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="2e845-134">Estructuras de depuración</span><span class="sxs-lookup"><span data-stu-id="2e845-134">Debugging Structures</span></span>](debugging-structures.md)
