---
title: Procedimiento para configurar el comportamiento inactivo con WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8491fccee9f148412aed89280ccd20b315d25da6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257371"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="ad47b-102">Procedimiento para configurar el comportamiento inactivo con WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="ad47b-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="ad47b-103">Los flujos de trabajo pasan a estar inactivos cuando encuentran un marcador que se debe reanudar mediante algún estímulo externo, por ejemplo cuando la instancia de flujo de trabajo está esperando la entrega de un mensaje usando una actividad <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="ad47b-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="ad47b-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> es un comportamiento que le permite especificar el tiempo transcurrido desde que una instancia de servicio pasa a estado inactivo hasta que la instancia se guarda o se descarga.</span><span class="sxs-lookup"><span data-stu-id="ad47b-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="ad47b-105">Contiene dos propiedades que permiten establecer estas duraciones.</span><span class="sxs-lookup"><span data-stu-id="ad47b-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="ad47b-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> especifica el período de tiempo entre el momento en el que una instancia de servicio del flujo de trabajo se inactiva y el momento en el que dicha instancia se guarda.</span><span class="sxs-lookup"><span data-stu-id="ad47b-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="ad47b-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> especifica el intervalo de tiempo entre el momento en el que una instancia de servicio del flujo de trabajo se inactiva y el momento en el que dicha instancia se descarga, donde la descarga significa guardar la instancia en el almacén de instancia y eliminarla de la memoria.</span><span class="sxs-lookup"><span data-stu-id="ad47b-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="ad47b-108">En este tema, se explica cómo configurar la clase <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> en un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="ad47b-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="ad47b-109">Para configurar WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="ad47b-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="ad47b-110">Agregue un elemento de> de <`workflowIdle` al `behavior` elemento de> <en el elemento <> `serviceBehaviors` como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ad47b-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="ad47b-111">El atributo `timeToUnload` especifica el período de tiempo entre el momento en el que una instancia de servicio del flujo de trabajo se inactiva y el momento en el que dicho servicio se descarga.</span><span class="sxs-lookup"><span data-stu-id="ad47b-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="ad47b-112">El atributo `timeToPersist` especifica el período de tiempo entre el momento en el que una instancia de servicio del flujo de trabajo se inactiva y el momento en el que dicha instancia se guarda.</span><span class="sxs-lookup"><span data-stu-id="ad47b-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="ad47b-113">El valor predeterminado de `timeToUnload` es 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="ad47b-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="ad47b-114">El valor predeterminado de `timeToPersist` es <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="ad47b-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="ad47b-115">Si desea conservar las instancias inactivas en memoria pero hacer que persistan por integridad, establezca los valores de modo que `timeToPersist` < `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="ad47b-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="ad47b-116">Si desea impedir que las instancias inactivas se carguen, establezca `timeToUnload` en <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="ad47b-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="ad47b-117">Para obtener más información acerca de <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> , consulte [extensibilidad de host de servicio de flujo de trabajo](workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="ad47b-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ad47b-118">En el ejemplo de configuración anterior, se usa la configuración simplificada.</span><span class="sxs-lookup"><span data-stu-id="ad47b-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="ad47b-119">Para obtener más información, vea [configuración simplificada](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ad47b-119">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="ad47b-120">Para cambiar el comportamiento inactivo en el código</span><span class="sxs-lookup"><span data-stu-id="ad47b-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="ad47b-121">En el siguiente ejemplo se cambia el tiempo que se espera antes de persistir y descargar mediante programación.</span><span class="sxs-lookup"><span data-stu-id="ad47b-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ad47b-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="ad47b-122">See also</span></span>

- [<span data-ttu-id="ad47b-123">Extensibilidad de host de servicio de flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="ad47b-123">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="ad47b-124">Configuración simplificada</span><span class="sxs-lookup"><span data-stu-id="ad47b-124">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="ad47b-125">Servicios de flujo de trabajo</span><span class="sxs-lookup"><span data-stu-id="ad47b-125">Workflow Services</span></span>](workflow-services.md)
