---
title: 'Cómo: Agregar la funcionalidad de límite y bloqueo a una colección'
ms.date: 03/30/2017
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 52ba264c5a0fc9cfffb00ee30b50f6b89dc1e660
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825044"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Cómo: Agregar la funcionalidad de límite y bloqueo a una colección
En este ejemplo se muestra cómo agregar la funcionalidad de límite y bloqueo a una clase de colección personalizada. Para ello, se implementa la interfaz <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> en la clase y, después, se usa una instancia de clase como mecanismo de almacenamiento interno para <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Para obtener más información acerca de la funcionalidad de límite y bloqueo, consulte [Información general sobre BlockingCollection](blockingcollection-overview.md).  
  
## <a name="example"></a>Ejemplo  
 La clase de colección personalizada es una cola de prioridad básica en la que los niveles de prioridad se representan como una matriz de objetos <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>. No se realiza ningún orden adicional en cada cola.  
  
 En el código de cliente, se inician tres tareas. La primera tarea se limita a sondear las pulsaciones de teclado para habilitar la cancelación en cualquier momento durante la ejecución. La segunda tarea es el subproceso de productor que agrega nuevos elementos a la colección de bloqueo y proporciona a cada elemento una prioridad basándose en un valor aleatorio. La tercera tarea quita elementos de la colección en cuanto estén disponibles.  
  
 Puede ajustar el comportamiento de la aplicación haciendo que uno de los subprocesos se ejecute más rápido que el otro. Si el productor se ejecuta más rápido, observará la funcionalidad de límite porque la colección de bloqueo impide que los elementos se agreguen si ya contiene el número de elementos que se especifican en el constructor. Si el consumidor se ejecuta más rápido, observará la funcionalidad de bloqueo porque el consumidor espera que se agregue un nuevo elemento.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 De forma predeterminada, el almacenamiento de <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> es <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Vea también

- [Colecciones seguras para subprocesos](index.md)
