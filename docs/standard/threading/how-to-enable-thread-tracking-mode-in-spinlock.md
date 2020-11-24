---
title: 'Cómo: Habilitar el modo de seguimiento de subproceso en el bloqueo SpinLock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: 83aebc45cdeaa2330c49ef6e90dcbedcd36de6b5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826461"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Cómo: Habilitar el modo de seguimiento de subproceso en el bloqueo SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType> es un bloqueo de exclusión mutua de bajo nivel que se puede usar para escenarios que tienen tiempos de espera muy cortos. <xref:System.Threading.SpinLock> no es reentrante. Una vez que el subproceso activa el bloqueo, debe desactivarlo correctamente para volver a entrar. Por lo general, cualquier intento de reentrada en el bloqueo produciría un interbloqueo, y los interbloqueos pueden ser muy difíciles de depurar. Como ayuda para el desarrollo, <xref:System.Threading.SpinLock?displayProperty=nameWithType> admite un modo de seguimiento de subprocesos que provoca la emisión de una excepción cuando un subproceso intenta reentrar en un bloqueo que ya tenía. Esto le permite que localizar con mayor facilidad el punto en el que el bloqueo no se cerró correctamente. Puede activar el modo de seguimiento de subprocesos mediante el uso del constructor <xref:System.Threading.SpinLock> que toma un valor booleano de entrada y pasando un argumento de `true`. Después de completar las fases de desarrollo y pruebas, desactive el modo de seguimiento de subprocesos para mejorar el rendimiento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el modo de seguimiento de subprocesos. Las líneas que salen correctamente del bloqueo están comentadas para simular un error de código que genera uno de los siguientes resultados:  
  
- Se produce una excepción si <xref:System.Threading.SpinLock> se creó mediante un argumento de `true` (`True` en Visual Basic).  
  
- Se produce un interbloqueo si <xref:System.Threading.SpinLock> se creó mediante un argumento de `false` (`False` en Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Vea también

- [SpinLock](spinlock.md)
