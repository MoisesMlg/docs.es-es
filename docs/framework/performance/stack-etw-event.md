---
title: Evento ETW de pila
description: Obtenga información sobre el evento ETW de pila, que se debe usar junto con otros eventos para generar seguimientos de pila después de que se produzca un evento.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: 3b890e587abd5cb1b7315fe41897f24638fd4604
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236213"
---
# <a name="stack-etw-event"></a>Evento ETW de pila

El evento de pila se debe usar junto con otros eventos para generar seguimientos de la pila una vez generado un evento. Se registra cuando se habilita el proveedor en tiempo de ejecución. Se trata de un evento de muy alta frecuencia, porque se genera cada vez que se genera otro evento en tiempo de ejecución. Por este motivo, le recomendamos que use este evento con precaución.  
  
 En la tabla siguiente se muestra la palabra clave y el nivel. (Para obtener más información, vea [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)).  
  
|Palabra clave para generar el evento|Nivel|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 En la siguiente tabla se muestra la información del evento.  
  
|Evento|Id. de evento|Se genera cuando|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Junto con otros eventos para generar seguimientos de la pila tras un evento.|  
  
 En la siguiente tabla se muestran los datos del evento.  
  
|Nombre del campo|Tipo de datos|Descripción|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:Uint16|Identificador único en tiempo de ejecución.|  
|Reserved1|win:UInt8|Reservado.|  
|Reserved2|win:UInt8|Reservado.|  
|FrameCount|win:UInt32|Número de marcos del seguimiento de la pila.|  
|Pila|win:Pointer|Columnas de punteros de instrucción.|  
  
## <a name="see-also"></a>Vea también

- [CLR ETW Events (Eventos ETW de CLR)](clr-etw-events.md)
