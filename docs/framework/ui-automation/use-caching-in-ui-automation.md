---
title: Utilizar el almacenamiento en caché en la UI Automation
description: Vea cómo usar el almacenamiento en caché en la automatización de la interfaz de usuario. Revise los pasos para activar una solicitud de caché, almacenar en caché propiedades de AutomationElement y obtener patrones almacenados en caché.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: f99fb724130c359a77c72db66dd9f837ef1a2219
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258613"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="6d075-104">Utilizar el almacenamiento en caché en la UI Automation</span><span class="sxs-lookup"><span data-stu-id="6d075-104">Use Caching in UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="6d075-105">Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="6d075-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6d075-106">Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6d075-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6d075-107">En esta sección se muestra cómo implementar el almacenamiento en caché de patrones de control y propiedades de <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="6d075-107">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="6d075-108">Activar una solicitud de almacenamiento en caché</span><span class="sxs-lookup"><span data-stu-id="6d075-108">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="6d075-109">Creará un control <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="6d075-109">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="6d075-110">Especifique las propiedades y los patrones que se almacenarán en caché mediante el uso de <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d075-110">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="6d075-111">Especifique el ámbito del almacenamiento en caché estableciendo la propiedad <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d075-111">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="6d075-112">Especifique la vista del subárbol estableciendo la propiedad <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="6d075-112">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="6d075-113">Establezca la propiedad <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> en <xref:System.Windows.Automation.AutomationElementMode.None> si quiere aumentar la eficacia sin recuperar una referencia completa a objetos.</span><span class="sxs-lookup"><span data-stu-id="6d075-113">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="6d075-114">(Esto hará que no sea posible recuperar los valores actuales de esos objetos).</span><span class="sxs-lookup"><span data-stu-id="6d075-114">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="6d075-115">Active la solicitud mediante el uso <xref:System.Windows.Automation.CacheRequest.Activate%2A> de dentro de un `using` bloque ( `Using` en Microsoft Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="6d075-115">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="6d075-116">Después de obtener objetos <xref:System.Windows.Automation.AutomationElement> o de suscribirse a eventos, desactive la solicitud mediante <xref:System.Windows.Automation.CacheRequest.Pop%2A> (si se usó <xref:System.Windows.Automation.CacheRequest.Push%2A> ) o eliminando el objeto creado por <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d075-116">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="6d075-117">(Utilice <xref:System.Windows.Automation.CacheRequest.Activate%2A> en un `using` bloque ( `Using` en Microsoft Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="6d075-117">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="6d075-118">Propiedades de AutomationElement de almacenamiento en caché</span><span class="sxs-lookup"><span data-stu-id="6d075-118">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="6d075-119">Mientras un elemento <xref:System.Windows.Automation.CacheRequest> está activo, obtenga objetos <xref:System.Windows.Automation.AutomationElement> mediante <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> o <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; u obtenga un elemento <xref:System.Windows.Automation.AutomationElement> como el origen de un evento para el que se registró para cuando el elemento <xref:System.Windows.Automation.CacheRequest> estaba activo.</span><span class="sxs-lookup"><span data-stu-id="6d075-119">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="6d075-120">(También puede crear una caché pasando un elemento <xref:System.Windows.Automation.CacheRequest> a GetUpdatedCache o uno de los métodos <xref:System.Windows.Automation.TreeWalker> ).</span><span class="sxs-lookup"><span data-stu-id="6d075-120">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="6d075-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> o recupere una propiedad desde la propiedad <xref:System.Windows.Automation.AutomationElement.Cached%2A> del elemento <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="6d075-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="6d075-122">Obtener patrones almacenados en caché y sus propiedades</span><span class="sxs-lookup"><span data-stu-id="6d075-122">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="6d075-123">Mientras un elemento <xref:System.Windows.Automation.CacheRequest> está activo, obtenga objetos <xref:System.Windows.Automation.AutomationElement> mediante <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> o <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; u obtenga un elemento <xref:System.Windows.Automation.AutomationElement> como el origen de un evento para el que se registró para cuando el elemento <xref:System.Windows.Automation.CacheRequest> estaba activo.</span><span class="sxs-lookup"><span data-stu-id="6d075-123">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="6d075-124">(También puede crear una caché pasando un elemento <xref:System.Windows.Automation.CacheRequest> a GetUpdatedCache o uno de los métodos <xref:System.Windows.Automation.TreeWalker> ).</span><span class="sxs-lookup"><span data-stu-id="6d075-124">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="6d075-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> o <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> para recuperar un patrón almacenado en caché.</span><span class="sxs-lookup"><span data-stu-id="6d075-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="6d075-126">Recupere valores de propiedad de la propiedad `Cached` del patrón de control.</span><span class="sxs-lookup"><span data-stu-id="6d075-126">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d075-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d075-127">Example</span></span>  

 <span data-ttu-id="6d075-128">En el ejemplo de código siguiente se muestran varios aspectos del almacenamiento en caché en los que se usa <xref:System.Windows.Automation.CacheRequest.Activate%2A> para activar el elemento <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="6d075-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="6d075-129">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6d075-129">Example</span></span>  

 <span data-ttu-id="6d075-130">En el ejemplo de código siguiente se muestran varios aspectos del almacenamiento en caché en los que se usa <xref:System.Windows.Automation.CacheRequest.Push%2A> para activar el elemento <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="6d075-130">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="6d075-131">Excepto cuando quiera anidar solicitudes de almacenamiento en caché, es preferible utilizar <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d075-131">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="6d075-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="6d075-132">See also</span></span>

- [<span data-ttu-id="6d075-133">Almacenar en caché en los clientes de automatización de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="6d075-133">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
