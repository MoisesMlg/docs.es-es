---
title: MDA de overlappedFreeError
description: Revise el Asistente para la depuración administrada (MDA) de overlappedFreeError en .NET, que puede activarse en infracciones de acceso o daños en el montón de recolección de elementos no utilizados.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 1bedb8ad3b9801f0d235371a397c8951ff8723b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254537"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="bce7a-103">MDA de overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="bce7a-103">overlappedFreeError MDA</span></span>

<span data-ttu-id="bce7a-104">El Asistente para la depuración administrada (MDA) `overlappedFreeError` se activa cuando se llama al método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> antes de que se haya completado la operación superpuesta.</span><span class="sxs-lookup"><span data-stu-id="bce7a-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bce7a-105">Síntomas</span><span class="sxs-lookup"><span data-stu-id="bce7a-105">Symptoms</span></span>  

 <span data-ttu-id="bce7a-106">Infracciones de acceso o daños en el montón de recolección de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="bce7a-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bce7a-107">Causa</span><span class="sxs-lookup"><span data-stu-id="bce7a-107">Cause</span></span>  

 <span data-ttu-id="bce7a-108">Una estructura superpuesta se liberó antes de finalizar la operación.</span><span class="sxs-lookup"><span data-stu-id="bce7a-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="bce7a-109">Es posible que la función que está usando el puntero superpuesto escriba en la estructura más adelante, después de que se haya liberado.</span><span class="sxs-lookup"><span data-stu-id="bce7a-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="bce7a-110">Esto puede provocar daños en el montón porque es posible que ahora otro objeto ocupe esa región.</span><span class="sxs-lookup"><span data-stu-id="bce7a-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="bce7a-111">Es posible que este MDA no represente un error si la operación superpuesta no se inició correctamente.</span><span class="sxs-lookup"><span data-stu-id="bce7a-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bce7a-112">Solución</span><span class="sxs-lookup"><span data-stu-id="bce7a-112">Resolution</span></span>  

 <span data-ttu-id="bce7a-113">Asegúrese de que se complete la operación de E/S que usa la estructura superpuesta antes de llamar al método <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29>.</span><span class="sxs-lookup"><span data-stu-id="bce7a-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bce7a-114">Efecto en el Runtime</span><span class="sxs-lookup"><span data-stu-id="bce7a-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="bce7a-115">Este MDA no tiene ningún efecto en el CLR.</span><span class="sxs-lookup"><span data-stu-id="bce7a-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bce7a-116">Resultados</span><span class="sxs-lookup"><span data-stu-id="bce7a-116">Output</span></span>  

 <span data-ttu-id="bce7a-117">A continuación puede ver un resultado de ejemplo para este MDA.</span><span class="sxs-lookup"><span data-stu-id="bce7a-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="bce7a-118">Configuración</span><span class="sxs-lookup"><span data-stu-id="bce7a-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bce7a-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="bce7a-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="bce7a-120">Diagnóstico de errores con asistentes de depuraciones administradas</span><span class="sxs-lookup"><span data-stu-id="bce7a-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="bce7a-121">Serialización de interoperabilidad</span><span class="sxs-lookup"><span data-stu-id="bce7a-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
