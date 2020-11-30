---
title: Procedimiento para implementar un observador
description: Implemente un observador en .NET. El modelo de diseño de observador requiere una división entre un observador, que registra notificaciones, y un proveedor.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET], observer design pattern
- observer design pattern [.NET], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: 73f6d2c25c727717394c79268b71b44ea9ff7800
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697485"
---
# <a name="how-to-implement-an-observer"></a>Procedimiento para implementar un observador

El modelo de diseño de observador requiere una división entre un observador, que registra notificaciones, y un proveedor, que controla los datos y envía notificaciones a uno o varios observadores. En este tema se describe cómo crear un observador. En un tema relacionado, [Cómo: Implementar un proveedor](how-to-implement-a-provider.md), se describe cómo crear un proveedor.  
  
### <a name="to-create-an-observer"></a>Para crear un observador  
  
1. Defina el observador, que es un tipo que implementa la interfaz <xref:System.IObserver%601?displayProperty=nameWithType>. Por ejemplo, el código siguiente define un tipo llamado `TemperatureReporter`, que es una implementación <xref:System.IObserver%601?displayProperty=nameWithType> construida con un argumento de tipo genérico de `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Si el observador puede dejar de recibir notificaciones antes de que el proveedor llame a su implementación <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, defina una variable privada que contenga la implementación <xref:System.IDisposable> devuelta por el método <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> del proveedor. También debe definir un método de suscripción que llame al método <xref:System.IObservable%601.Subscribe%2A> del proveedor y almacene el objeto <xref:System.IDisposable> devuelto. Por ejemplo, el código siguiente define una variable privada denominada `unsubscriber` y define un método `Subscribe` que llama al método <xref:System.IObservable%601.Subscribe%2A> del proveedor y asigna el objeto devuelto a la variable `unsubscriber`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Defina un método que permita al observador dejar de recibir notificaciones antes de que el proveedor llame a su implementación <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, en caso de que esta característica sea necesaria. En el ejemplo siguiente, se define un método `Unsubscribe`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Proporcione implementaciones de los tres métodos definidos en la interfaz <xref:System.IObserver%601>: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> y <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. En función del proveedor y de las necesidades de la aplicación, los métodos <xref:System.IObserver%601.OnError%2A> y <xref:System.IObserver%601.OnCompleted%2A> pueden ser implementaciones de código auxiliar. Tenga en cuenta que el método <xref:System.IObserver%601.OnError%2A> no debe controlar el objeto <xref:System.Exception> pasado como una excepción y que el método <xref:System.IObserver%601.OnCompleted%2A> es libre de llamar a la implementación <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> del proveedor. El siguiente ejemplo muestra la implementación <xref:System.IObserver%601> de la clase `TemperatureReporter`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Ejemplo  

 El siguiente ejemplo contiene el código fuente completo para la clase `TemperatureReporter`, que ofrece la implementación <xref:System.IObserver%601> de una aplicación de supervisión de temperatura.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Vea también

- <xref:System.IObserver%601>
- [Modelo de diseño de observador](observer-design-pattern.md)
- [Cómo: Implementar un proveedor](how-to-implement-a-provider.md)
- [Procedimientos recomendados para modelos de diseño de observador](observer-design-pattern-best-practices.md)
