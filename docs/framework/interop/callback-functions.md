---
title: Funciones de devolución de llamada
description: Lea sobre las funciones de devolución de llamada, que son código dentro de una aplicación administrada que ayuda a una función DLL no administrada a completar una tarea.
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 659f384f7bfc3a2326a40a9536c977d7c41ab076
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283164"
---
# <a name="callback-functions"></a><span data-ttu-id="f2239-103">Funciones de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="f2239-103">Callback Functions</span></span>

<span data-ttu-id="f2239-104">Una función de devolución de llamada es código dentro de una aplicación administrada que ayuda a una función DLL no administrada a completar una tarea.</span><span class="sxs-lookup"><span data-stu-id="f2239-104">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="f2239-105">Las llamadas a una función de devolución de llamada pasan indirectamente desde una aplicación administrada, a través de una función DLL, y de nuevo a la implementación administrada.</span><span class="sxs-lookup"><span data-stu-id="f2239-105">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="f2239-106">Algunas de las muchas funciones DLL que se llaman con la invocación de plataforma requieren una función de devolución de llamada en código administrado para ejecutarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="f2239-106">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="f2239-107">Para llamar a la mayoría de las funciones DLL desde el código administrado, se crea una definición administrada de la función y, después, se llama.</span><span class="sxs-lookup"><span data-stu-id="f2239-107">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="f2239-108">El proceso es sencillo.</span><span class="sxs-lookup"><span data-stu-id="f2239-108">The process is straightforward.</span></span>  
  
 <span data-ttu-id="f2239-109">El uso de una función DLL que requiere una función de devolución de llamada tiene algunos pasos adicionales.</span><span class="sxs-lookup"><span data-stu-id="f2239-109">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="f2239-110">En primer lugar, se debe determinar si la función requiere una devolución de llamada examinando la documentación de la función.</span><span class="sxs-lookup"><span data-stu-id="f2239-110">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="f2239-111">Después, habrá que crear la función de devolución de llamada en la aplicación administrada.</span><span class="sxs-lookup"><span data-stu-id="f2239-111">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="f2239-112">Por último, se llama a la función DLL, pasando un puntero a la función de devolución de llamada como argumento.</span><span class="sxs-lookup"><span data-stu-id="f2239-112">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="f2239-113">En la siguiente ilustración se resumen la función de devolución de llamada y los pasos de implementación:</span><span class="sxs-lookup"><span data-stu-id="f2239-113">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Diagrama que muestra el proceso de devolución de llamada para la invocación de plataforma.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="f2239-115">Las funciones de devolución de llamada son ideales para su uso en situaciones en las que se realiza una tarea repetidamente.</span><span class="sxs-lookup"><span data-stu-id="f2239-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="f2239-116">Otro uso frecuente es con funciones de enumeración, como **EnumFontFamilies**, **EnumPrinters** y **EnumWindows** en la API de Windows.</span><span class="sxs-lookup"><span data-stu-id="f2239-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="f2239-117">La función **EnumWindows** enumera todas las ventanas existentes en el equipo, y llama a la función de devolución de llamada para realizar una tarea en cada ventana.</span><span class="sxs-lookup"><span data-stu-id="f2239-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="f2239-118">Para obtener instrucciones y un ejemplo, vea [Cómo: Implementar funciones de devolución de llamada](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f2239-118">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2239-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="f2239-119">See also</span></span>

- [<span data-ttu-id="f2239-120">Cómo: Implementar funciones de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="f2239-120">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="f2239-121">Llamar a una función DLL</span><span class="sxs-lookup"><span data-stu-id="f2239-121">Calling a DLL Function</span></span>](calling-a-dll-function.md)
