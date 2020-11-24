---
title: Controlar excepciones de interoperabilidad COM
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: 058fb6446f69c2e10cb136ce5b5ad73b14d82647
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828145"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="07970-102">Controlar excepciones de interoperabilidad COM</span><span class="sxs-lookup"><span data-stu-id="07970-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="07970-103">El código administrado y el código no administrado pueden trabajar juntos para controlar excepciones.</span><span class="sxs-lookup"><span data-stu-id="07970-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="07970-104">Si un método produce una excepción en código administrado, Common Language Runtime puede pasar un HRESULT a un objeto COM.</span><span class="sxs-lookup"><span data-stu-id="07970-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="07970-105">Si un método produce un error en código no administrado y devuelve un HRESULT de error, el tiempo de ejecución produce una excepción que el código administrado puede capturar.</span><span class="sxs-lookup"><span data-stu-id="07970-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="07970-106">El tiempo de ejecución asigna automáticamente el HRESULT de la interoperabilidad COM a excepciones más específicas.</span><span class="sxs-lookup"><span data-stu-id="07970-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="07970-107">Por ejemplo, E_ACCESSDENIED se convierte en <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY se convierte en <xref:System.OutOfMemoryException>, y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="07970-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="07970-108">Si el HRESULT es un resultado personalizado o es desconocido para el tiempo de ejecución, este pasa una <xref:System.Runtime.InteropServices.COMException> genérica al cliente.</span><span class="sxs-lookup"><span data-stu-id="07970-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="07970-109">La propiedad **ErrorCode** de **COMException** contiene el valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="07970-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="07970-110">Trabajar con IErrorInfo</span><span class="sxs-lookup"><span data-stu-id="07970-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="07970-111">Cuando se pasa un error desde COM al código administrado, el tiempo de ejecución rellena el objeto de excepción con la información del error.</span><span class="sxs-lookup"><span data-stu-id="07970-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="07970-112">Los objetos COM que admiten IErrorInfo y devuelven HRESULTS proporcionan esta información a las excepciones de código administrado.</span><span class="sxs-lookup"><span data-stu-id="07970-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="07970-113">Por ejemplo, el tiempo de ejecución asigna la descripción del error COM a la propiedad <xref:System.Exception.Message%2A> de la excepción.</span><span class="sxs-lookup"><span data-stu-id="07970-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="07970-114">Si el valor HRESULT no proporciona ninguna información de error adicional, el tiempo de ejecución rellena muchas de las propiedades de la excepción con los valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="07970-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="07970-115">Si un método produce un error en código no administrado, se puede pasar una excepción a un segmento de código administrado.</span><span class="sxs-lookup"><span data-stu-id="07970-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="07970-116">El tema [HRESULT y excepciones](../../framework/interop/how-to-map-hresults-and-exceptions.md) contiene una tabla que muestra cómo se asignan los HRESULTS a los objetos de excepción en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="07970-116">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="07970-117">Vea también</span><span class="sxs-lookup"><span data-stu-id="07970-117">See also</span></span>

- [<span data-ttu-id="07970-118">Excepciones</span><span class="sxs-lookup"><span data-stu-id="07970-118">Exceptions</span></span>](index.md)
