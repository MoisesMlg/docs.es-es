---
title: Comunicación asincrónica
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: db5a8f415479967d7579357bd0c8058c7fb961c5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255850"
---
# <a name="asynchronous-communication"></a>Comunicación asincrónica

Este ejemplo muestra cómo la comunicación entre dos servicios de Windows Workflow Foundation (WF) diferentes se realiza de forma asincrónica de forma predeterminada.  
  
## <a name="demonstrates"></a>Muestra  

 Comunicación asincrónica entre servicios de [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  
  
## <a name="discussion"></a>Discusión  

 En este ejemplo se muestra cómo la comunicación entre aplicaciones de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] se realiza de forma asincrónica utilizando las actividades de mensajería proporcionadas por .NET Framework.  
  
 Este ejemplo consta de los tres proyectos siguientes.  
  
 CreditCheckService  
 Este servicio recibe la puntuación crediticia de una persona determinada o el valor del elemento que se va a adquirir y a continuación, decide si la persona recibe el crédito.  
  
 RentalApprovalService  
 Este servicio recibe una solicitud de una persona que necesita crédito. Este servicio se comunica de forma asincrónica con `CreditCheckService` para decidir si la solicitud de crédito es válida.  
  
 Cliente  
 El cliente se comunica sincrónicamente con `RentalApprovalService` para saber si se aprueba el crédito.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Configurar, compilar y ejecutar el ejemplo  
  
1. Haga clic con el botón derecho en la solución **AsynchronousCommunication** y seleccione **propiedades**.  
  
2. En **propiedades comunes**, seleccione **proyecto de inicio** y seleccione **proyectos de inicio múltiples**.  
  
3. Mueva **RentalApprovalService** a la primera posición de la lista, seguida de **CreditCheckService**, seguido del **cliente**. Establezca la acción **iniciar** en los tres proyectos.  
  
4. Haga clic en **Aceptar** y presione F5 para ejecutar el ejemplo.  
  
> [!IMPORTANT]
> Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si este directorio no existe, vaya a [ejemplos de Windows Communication Foundation (WCF) y Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
