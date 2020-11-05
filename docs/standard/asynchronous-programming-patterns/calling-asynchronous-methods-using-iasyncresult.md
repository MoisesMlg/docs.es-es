---
title: Llamar a métodos asincrónicos mediante IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 8e11f734410e266aa4c175551e8a3fbf5d9236c9
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888911"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="6eae5-102">Llamar a métodos asincrónicos mediante IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="6eae5-102">Calling Asynchronous Methods Using IAsyncResult</span></span>

<span data-ttu-id="6eae5-103">Los tipos de las bibliotecas de .NET y las bibliotecas de clases de terceros pueden proporcionar métodos que permiten la continuidad de la ejecución de una aplicación mientras se realizan operaciones asincrónicas en subprocesos distintos del subproceso de aplicación principal.</span><span class="sxs-lookup"><span data-stu-id="6eae5-103">Types in the .NET libraries and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="6eae5-104">En las secciones siguientes se describen y proporcionan ejemplos de código que muestran las diferentes formas en que se puede llamar a métodos asincrónicos que usan el modelo de diseño <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="6eae5-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="6eae5-105">[Bloquear la ejecución de una aplicación al finalizar una operación asincrónica](blocking-application-execution-by-ending-an-async-operation.md)</span><span class="sxs-lookup"><span data-stu-id="6eae5-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="6eae5-106">[Bloquear la ejecución de una aplicación mediante AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md)</span><span class="sxs-lookup"><span data-stu-id="6eae5-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="6eae5-107">[Sondear el estado de una operación asincrónica](polling-for-the-status-of-an-asynchronous-operation.md)</span><span class="sxs-lookup"><span data-stu-id="6eae5-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="6eae5-108">[Utilizar un delegado AsyncCallback para finalizar una operación asincrónica](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)</span><span class="sxs-lookup"><span data-stu-id="6eae5-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eae5-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="6eae5-109">See also</span></span>

- [<span data-ttu-id="6eae5-110">Modelo asincrónico basado en eventos (EAP)</span><span class="sxs-lookup"><span data-stu-id="6eae5-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- <span data-ttu-id="6eae5-111">[Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md) (Información general sobre el modelo asincrónico basado en eventos)</span><span class="sxs-lookup"><span data-stu-id="6eae5-111">[Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md)</span></span>
