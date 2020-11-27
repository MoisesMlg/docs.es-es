---
title: MDA de dllMainReturnsFalse
description: Obtenga información sobre el Asistente para la depuración administrada de dllMainReturnsFalse en .NET. Este MDA se activa si se produce un error de inicialización de DLL.
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 83f38c4918c1354477627b70a62e60cbdc7de275
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273521"
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="f73f6-104">MDA de dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="f73f6-104">dllMainReturnsFalse MDA</span></span>

<span data-ttu-id="f73f6-105">El asistente para la depuración administrada (MDA) `dllMainReturnsFalse` se activa si la función administrada `DllMain` de un ensamblado de usuario denominado con la razón DLL_PROCESS_ATTACH devuelve FALSE.</span><span class="sxs-lookup"><span data-stu-id="f73f6-105">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f73f6-106">Síntomas</span><span class="sxs-lookup"><span data-stu-id="f73f6-106">Symptoms</span></span>  

 <span data-ttu-id="f73f6-107">La función `DllMain` devuelve FALSE, lo que indica que no se ha ejecutado correctamente.</span><span class="sxs-lookup"><span data-stu-id="f73f6-107">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="f73f6-108">Esto puede causar problemas indeterminados, ya que las funciones `DllMain` normalmente contienen código de inicialización importante.</span><span class="sxs-lookup"><span data-stu-id="f73f6-108">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f73f6-109">Causa</span><span class="sxs-lookup"><span data-stu-id="f73f6-109">Cause</span></span>  

 <span data-ttu-id="f73f6-110">La función `DllMain` se denomina con la razón DLL_PROCESS_ATTACH para la inicialización del archivo DLL tras la carga.</span><span class="sxs-lookup"><span data-stu-id="f73f6-110">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="f73f6-111">Si devuelve FALSE, significa que se ha producido un error en la inicialización del archivo DLL.</span><span class="sxs-lookup"><span data-stu-id="f73f6-111">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f73f6-112">Solución</span><span class="sxs-lookup"><span data-stu-id="f73f6-112">Resolution</span></span>  

 <span data-ttu-id="f73f6-113">Analice el código de la función `DllMain` del archivo DLL erróneo e identifique la causa del error de inicialización.</span><span class="sxs-lookup"><span data-stu-id="f73f6-113">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f73f6-114">Efecto en el Runtime</span><span class="sxs-lookup"><span data-stu-id="f73f6-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="f73f6-115">Este MDA no tiene ningún efecto en el CLR.</span><span class="sxs-lookup"><span data-stu-id="f73f6-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f73f6-116">Solo notifica datos sobre el valor devuelto de `DllMain`.</span><span class="sxs-lookup"><span data-stu-id="f73f6-116">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f73f6-117">Resultados</span><span class="sxs-lookup"><span data-stu-id="f73f6-117">Output</span></span>  

 <span data-ttu-id="f73f6-118">Un mensaje que indica que una función `DllMain`, denominada con la razón DLL_PROCESS_ATTACH, ha devuelto FALSE.</span><span class="sxs-lookup"><span data-stu-id="f73f6-118">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="f73f6-119">Tenga en cuenta que este MDA solo se activa si `DllMain` se implementa en código administrado.</span><span class="sxs-lookup"><span data-stu-id="f73f6-119">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f73f6-120">Configuración</span><span class="sxs-lookup"><span data-stu-id="f73f6-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f73f6-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="f73f6-121">See also</span></span>

- [<span data-ttu-id="f73f6-122">Diagnóstico de errores con asistentes de depuraciones administradas</span><span class="sxs-lookup"><span data-stu-id="f73f6-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
