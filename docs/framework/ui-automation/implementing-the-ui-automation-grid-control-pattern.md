---
title: Implementar el patrón de control Grid de UI Automation
description: Comprender las directrices y convenciones para implementar el patrón de control de cuadrícula GridPattern en la automatización de la interfaz de usuario. Aprenda a implementar la interfaz IGridProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 2290fd91c8eee0ab969eef2827d3c7440ef21e20
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274886"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="02730-104">Implementar el patrón de control Grid de UI Automation</span><span class="sxs-lookup"><span data-stu-id="02730-104">Implementing the UI Automation Grid Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="02730-105">Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="02730-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="02730-106">Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="02730-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="02730-107">En este tema se presentan las directrices y convenciones para implementar <xref:System.Windows.Automation.Provider.IGridProvider>, incluida la información sobre propiedades, métodos y eventos.</span><span class="sxs-lookup"><span data-stu-id="02730-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="02730-108">Al final de la información general se proporcionan vínculos a referencias adicionales.</span><span class="sxs-lookup"><span data-stu-id="02730-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="02730-109">El patrón de control <xref:System.Windows.Automation.GridPattern> se usa para admitir controles que actúen como contenedores para una colección de elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="02730-109">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="02730-110">Los elementos secundarios de este elemento deben implementar <xref:System.Windows.Automation.Provider.IGridItemProvider> y organizarse en un sistema de coordenadas lógico bidimensional que se pueda recorrer por filas y columnas.</span><span class="sxs-lookup"><span data-stu-id="02730-110">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="02730-111">Para obtener ejemplos de controles que implementan este patrón de control, vea [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="02730-111">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="02730-112">Directrices y convenciones de implementación</span><span class="sxs-lookup"><span data-stu-id="02730-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="02730-113">Al implementar el patrón de control Grid, tenga en cuenta las siguientes directrices y convenciones:</span><span class="sxs-lookup"><span data-stu-id="02730-113">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="02730-114">Las coordenadas de la cuadrícula son de base cero, donde la celda superior izquierda (o la superior derecha, según la configuración regional) tiene las coordenadas (0, 0).</span><span class="sxs-lookup"><span data-stu-id="02730-114">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="02730-115">Si una celda está vacía, todavía debe devolverse un elemento de Automatización de la interfaz de usuario para admitir la propiedad <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> en esa celda.</span><span class="sxs-lookup"><span data-stu-id="02730-115">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="02730-116">Esto es posible si el diseño de elementos secundarios de la cuadrícula es similar a una matriz irregular (consulte el ejemplo siguiente).</span><span class="sxs-lookup"><span data-stu-id="02730-116">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="02730-117">![Vista del Explorador de Windows con un diseño irregular.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="02730-117">![Windows Explorer view showing ragged layout.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="02730-118">Ejemplo de un control Grid con coordenadas vacías</span><span class="sxs-lookup"><span data-stu-id="02730-118">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="02730-119">Sigue siendo necesaria una cuadrícula con un elemento único para implementar <xref:System.Windows.Automation.Provider.IGridProvider> si lógicamente se considera una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="02730-119">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="02730-120">El número de elementos secundarios de la cuadrícula es irrelevante.</span><span class="sxs-lookup"><span data-stu-id="02730-120">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="02730-121">Las filas y columnas ocultas, según la implementación del proveedor, se pueden cargar en el árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] y, por tanto, se reflejarán en las propiedades <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> y <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="02730-121">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="02730-122">Si las filas y columnas ocultas todavía no se han cargado, no deben contarse.</span><span class="sxs-lookup"><span data-stu-id="02730-122">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="02730-123"><xref:System.Windows.Automation.Provider.IGridProvider> no permite la manipulación activa de una cuadrícula; <xref:System.Windows.Automation.Provider.ITransformProvider> debe implementarse para habilitar esta funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="02730-123"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="02730-124">Use un elemento <xref:System.Windows.Automation.StructureChangedEventHandler> para permanecer a la escucha de cambios estructurales o de diseño en la cuadrícula, como por ejemplo, celdas que se hayan agregado, quitado o combinado.</span><span class="sxs-lookup"><span data-stu-id="02730-124">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="02730-125">Use un elemento <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> para realizar un seguimiento del recorrido a través de los elementos o las celdas de una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="02730-125">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>

## <a name="required-members-for-igridprovider"></a><span data-ttu-id="02730-126">Miembros requeridos para IGridProvider</span><span class="sxs-lookup"><span data-stu-id="02730-126">Required Members for IGridProvider</span></span>  

 <span data-ttu-id="02730-127">Se requieren los métodos y propiedades siguientes para implementar la interfaz de IGridProvider.</span><span class="sxs-lookup"><span data-stu-id="02730-127">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="02730-128">Miembros requeridos</span><span class="sxs-lookup"><span data-stu-id="02730-128">Required members</span></span>|<span data-ttu-id="02730-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="02730-129">Type</span></span>|<span data-ttu-id="02730-130">Notas</span><span class="sxs-lookup"><span data-stu-id="02730-130">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="02730-131">Propiedad</span><span class="sxs-lookup"><span data-stu-id="02730-131">Property</span></span>|<span data-ttu-id="02730-132">None</span><span class="sxs-lookup"><span data-stu-id="02730-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="02730-133">Propiedad</span><span class="sxs-lookup"><span data-stu-id="02730-133">Property</span></span>|<span data-ttu-id="02730-134">None</span><span class="sxs-lookup"><span data-stu-id="02730-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="02730-135">Método</span><span class="sxs-lookup"><span data-stu-id="02730-135">Method</span></span>|<span data-ttu-id="02730-136">None</span><span class="sxs-lookup"><span data-stu-id="02730-136">None</span></span>|  
  
 <span data-ttu-id="02730-137">Este patrón de control no tiene eventos asociados.</span><span class="sxs-lookup"><span data-stu-id="02730-137">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="02730-138">Excepciones</span><span class="sxs-lookup"><span data-stu-id="02730-138">Exceptions</span></span>  

 <span data-ttu-id="02730-139">Los proveedores deben producir las siguientes excepciones.</span><span class="sxs-lookup"><span data-stu-id="02730-139">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="02730-140">Tipo de excepción</span><span class="sxs-lookup"><span data-stu-id="02730-140">Exception type</span></span>|<span data-ttu-id="02730-141">Condición</span><span class="sxs-lookup"><span data-stu-id="02730-141">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="02730-142">: Si la coordenada de la fila solicitada es mayor que <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> o la coordenada de columna es mayor que <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .</span><span class="sxs-lookup"><span data-stu-id="02730-142">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="02730-143">: Si alguna de las coordenadas de columna o fila solicitada es menor que cero.</span><span class="sxs-lookup"><span data-stu-id="02730-143">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02730-144">Vea también</span><span class="sxs-lookup"><span data-stu-id="02730-144">See also</span></span>

- [<span data-ttu-id="02730-145">Información general acerca de los patrones de control de UI Automation</span><span class="sxs-lookup"><span data-stu-id="02730-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="02730-146">Patrones de control compatibles en un proveedor de UI Automation</span><span class="sxs-lookup"><span data-stu-id="02730-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="02730-147">Patrones de controles de UI Automation para clientes</span><span class="sxs-lookup"><span data-stu-id="02730-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="02730-148">Implementar el patrón de control GridItem de UI Automation</span><span class="sxs-lookup"><span data-stu-id="02730-148">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="02730-149">Información general sobre el árbol de la UI Automation</span><span class="sxs-lookup"><span data-stu-id="02730-149">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="02730-150">Utilizar el almacenamiento en caché en la UI Automation</span><span class="sxs-lookup"><span data-stu-id="02730-150">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
