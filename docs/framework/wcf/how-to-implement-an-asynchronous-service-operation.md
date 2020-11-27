---
title: Procedimiento para implementar una operación de servicios asincrónica
description: Obtenga información sobre la estructura de una operación de servicio asincrónica en WFC. Una operación de servicio se puede implementar de forma asincrónica o sincrónica.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 157311f29b203e0c26be21a89d2d5b560543094b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267837"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="a38f9-104">Procedimiento para implementar una operación de servicios asincrónica</span><span class="sxs-lookup"><span data-stu-id="a38f9-104">How to: Implement an Asynchronous Service Operation</span></span>

<span data-ttu-id="a38f9-105">En las aplicaciones Windows Communication Foundation (WCF), una operación de servicio se puede implementar de forma asincrónica o sincrónica sin indicar al cliente cómo llamarla.</span><span class="sxs-lookup"><span data-stu-id="a38f9-105">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="a38f9-106">Por ejemplo, se puede llamar a las operaciones de servicio asincrónicas de forma sincrónica y se puede llamar a las operaciones de servicio sincrónicamente.</span><span class="sxs-lookup"><span data-stu-id="a38f9-106">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="a38f9-107">Para obtener un ejemplo en el que se muestra cómo llamar a una operación de forma asincrónica en una aplicación cliente, vea [Cómo: llamar a operaciones de servicio de forma asincrónica](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="a38f9-107">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="a38f9-108">Para obtener más información sobre las operaciones sincrónicas y asincrónicas, vea [diseñar contratos de servicio](designing-service-contracts.md) y [operaciones sincrónicas y asincrónicas](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a38f9-108">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="a38f9-109">En este tema se describe la estructura básica de una operación de servicio asincrónica, el código no está completo.</span><span class="sxs-lookup"><span data-stu-id="a38f9-109">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="a38f9-110">Para obtener un ejemplo completo de los lados del servicio y del cliente, consulte [asincrónica](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a38f9-110">For a complete example of both the service and client sides, see [Asynchronous](/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="a38f9-111">Implementación de una operación de servicio de manera asincrónica</span><span class="sxs-lookup"><span data-stu-id="a38f9-111">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="a38f9-112">En su contrato de servicio, declare un par de métodos asincrónicos según las instrucciones de diseño asincrónico de .NET.</span><span class="sxs-lookup"><span data-stu-id="a38f9-112">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="a38f9-113">El método `Begin` toma un parámetro, un objeto de devolución de llamada y un objeto de estado, y devuelve un <xref:System.IAsyncResult?displayProperty=nameWithType> y un método `End` correspondiente que toma <xref:System.IAsyncResult?displayProperty=nameWithType> y devuelven el valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="a38f9-113">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="a38f9-114">Para obtener más información sobre las llamadas asincrónicas, consulte [patrones de diseño de programación asincrónica](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="a38f9-114">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="a38f9-115">Marque el método `Begin` del par de métodos asincrónicos con el atributo <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> y establezca la propiedad <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> en `true`.</span><span class="sxs-lookup"><span data-stu-id="a38f9-115">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="a38f9-116">Por ejemplo, el código siguiente realiza los pasos 1 y 2.</span><span class="sxs-lookup"><span data-stu-id="a38f9-116">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="a38f9-117">Implemente el par de método `Begin/End` en su clase de servicio según las instrucciones de diseño asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="a38f9-117">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="a38f9-118">Por ejemplo, el siguiente ejemplo de código muestra una implementación en la que una cadena se escribe en la consola en porciones `Begin` y `End` de la operación de servicio asincrónica y el valor devuelto de la operación `End` se devuelve al cliente.</span><span class="sxs-lookup"><span data-stu-id="a38f9-118">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="a38f9-119">Para obtener el ejemplo de código completo, consulte la sección Ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a38f9-119">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a38f9-120">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a38f9-120">Example</span></span>  

 <span data-ttu-id="a38f9-121">Los siguientes ejemplos de código muestran:</span><span class="sxs-lookup"><span data-stu-id="a38f9-121">The following code examples show:</span></span>  
  
1. <span data-ttu-id="a38f9-122">Una interfaz del contrato de servicio con:</span><span class="sxs-lookup"><span data-stu-id="a38f9-122">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="a38f9-123">Una operación `SampleMethod` sincrónica.</span><span class="sxs-lookup"><span data-stu-id="a38f9-123">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="a38f9-124">Una operación `BeginSampleMethod` asincrónica.</span><span class="sxs-lookup"><span data-stu-id="a38f9-124">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="a38f9-125">Un par de `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` operación asincrónica.</span><span class="sxs-lookup"><span data-stu-id="a38f9-125">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="a38f9-126">Una implementación de servicio mediante un objeto <xref:System.IAsyncResult?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a38f9-126">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a38f9-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="a38f9-127">See also</span></span>

- [<span data-ttu-id="a38f9-128">Diseño de contratos de servicios</span><span class="sxs-lookup"><span data-stu-id="a38f9-128">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="a38f9-129">Operaciones sincrónicas y asincrónicas</span><span class="sxs-lookup"><span data-stu-id="a38f9-129">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
