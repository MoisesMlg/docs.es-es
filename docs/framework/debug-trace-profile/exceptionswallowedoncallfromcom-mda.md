---
title: MDA de exceptionSwallowedOnCallFromCom
description: Revise el Asistente para la depuración administrada de exceptionSwallowedOnCallFromCOM en .NET. Este MDA se produce si se produce una excepción, pero no hay ninguna manera adecuada de notificarla.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 11daccb4d1e757bf2fae25858d706eee5921c509
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244358"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>MDA de exceptionSwallowedOnCallFromCom

El asistente para la depuración administrada (MDA, por sus siglas en inglés) `exceptionSwallowedOnCallFromCOM` se activa cuando se produce una excepción del código de Common Language Runtime (CLR) llamado desde COM a través de un método que no tiene un tipo de resultado HRESULT sin administrar.  
  
## <a name="symptoms"></a>Síntomas  

 Una llamada de COM a un componente administrado devuelve un valor FALSE o 0. También puede ser que, si el método tiene un tipo de valor devuelto void, no haya indicación de que se produjese una excepción durante la ejecución del método. En este caso, la excepción se detectará de forma silenciosa y la ejecución regresará al emisor de la llamada COM.  
  
## <a name="cause"></a>Causa  

 Se produjo una excepción, pero no hay ningún modo válido de notificarla.  
  
## <a name="resolution"></a>Solución  

 Solo tiene carácter informativo, no es necesariamente indicativo de un error.  
  
## <a name="effect-on-the-runtime"></a>Efecto en el Runtime  

 Este MDA no tiene ningún efecto en el CLR. Solo recoge los datos sobre excepciones detectadas de forma silenciosa.  
  
## <a name="output"></a>Resultados  

 Mensaje informativo que contiene el nombre del método, el nombre del tipo y el mensaje de la excepción.  
  
## <a name="configuration"></a>Configuración  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnóstico de errores con asistentes de depuraciones administradas](diagnosing-errors-with-managed-debugging-assistants.md)
- [Serialización de interoperabilidad](../interop/interop-marshaling.md)
