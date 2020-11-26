---
title: Información general acerca de las propiedades de UI Automation
description: Vea una amplia introducción a las propiedades de automatización de la interfaz de usuario de Microsoft. Obtenga información sobre los identificadores de propiedad, las propiedades por categoría, localización, propiedades y eventos.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 95729c1d26a9ae7fdec4fa4215f9478251612242
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240399"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="1cc95-104">Información general acerca de las propiedades de UI Automation</span><span class="sxs-lookup"><span data-stu-id="1cc95-104">UI Automation Properties Overview</span></span>

> [!NOTE]
> <span data-ttu-id="1cc95-105">Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="1cc95-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1cc95-106">Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="1cc95-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="1cc95-107">Los proveedores de Automatización de la interfaz de usuario exponen propiedades en los elementos [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1cc95-107">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="1cc95-108">Estas propiedades permiten que las aplicaciones de cliente de Automatización de la interfaz de usuario detecten información sobre partes de la [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especialmente los controles, e incluidos los datos estáticos y dinámicos.</span><span class="sxs-lookup"><span data-stu-id="1cc95-108">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="1cc95-109">En esta sección se ofrece información general sobre las propiedades de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1cc95-109">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="1cc95-110">En los temas siguientes se proporciona información más específica:</span><span class="sxs-lookup"><span data-stu-id="1cc95-110">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="1cc95-111">Propiedades de UI Automation para clientes</span><span class="sxs-lookup"><span data-stu-id="1cc95-111">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="1cc95-112">Implementación del proveedor de UI Automation en el servidor</span><span class="sxs-lookup"><span data-stu-id="1cc95-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>

## <a name="property-identifiers"></a><span data-ttu-id="1cc95-113">Identificadores de propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-113">Property Identifiers</span></span>  

 <span data-ttu-id="1cc95-114">Cada propiedad se identifica mediante un número y un nombre.</span><span class="sxs-lookup"><span data-stu-id="1cc95-114">Every property is identified by a number and a name.</span></span> <span data-ttu-id="1cc95-115">Los nombres de las propiedades se utilizan únicamente para la depuración y el diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="1cc95-115">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="1cc95-116">Los proveedores usan los identificadores numéricos para identificar las solicitudes de propiedad entrantes.</span><span class="sxs-lookup"><span data-stu-id="1cc95-116">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="1cc95-117">Las aplicaciones cliente, sin embargo, solo utilizan <xref:System.Windows.Automation.AutomationProperty>, que encapsula el número y el nombre, para identificar las propiedades que quieren recuperar.</span><span class="sxs-lookup"><span data-stu-id="1cc95-117">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="1cc95-118">Los objetos<xref:System.Windows.Automation.AutomationProperty> que representan propiedades determinadas están disponibles como campos en diversas clases.</span><span class="sxs-lookup"><span data-stu-id="1cc95-118"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="1cc95-119">Por motivos de seguridad, los proveedores de Automatización de la interfaz de usuario obtienen estos objetos de un conjunto independiente de clases que están incluidas en Uiautomationtypes.dll.</span><span class="sxs-lookup"><span data-stu-id="1cc95-119">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="1cc95-120">En la tabla siguiente se clasifican las propiedades por las clases que contienen los <xref:System.Windows.Automation.AutomationProperty> identificadores.</span><span class="sxs-lookup"><span data-stu-id="1cc95-120">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="1cc95-121">Tipos de propiedades</span><span class="sxs-lookup"><span data-stu-id="1cc95-121">Kinds of properties</span></span>|<span data-ttu-id="1cc95-122">Los clientes obtienen los identificadores de</span><span class="sxs-lookup"><span data-stu-id="1cc95-122">Clients get IDs from</span></span>|<span data-ttu-id="1cc95-123">Los proveedores obtienen los identificadores de</span><span class="sxs-lookup"><span data-stu-id="1cc95-123">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="1cc95-124">Propiedades comunes a todos los elementos (consulte las tablas siguientes)</span><span class="sxs-lookup"><span data-stu-id="1cc95-124">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="1cc95-125">Posición de una ventana de acoplamiento</span><span class="sxs-lookup"><span data-stu-id="1cc95-125">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="1cc95-126">Estado de un elemento que se puede expandir y contraer</span><span class="sxs-lookup"><span data-stu-id="1cc95-126">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="1cc95-127">Propiedades de un elemento en una cuadrícula</span><span class="sxs-lookup"><span data-stu-id="1cc95-127">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="1cc95-128">Propiedades de una cuadrícula</span><span class="sxs-lookup"><span data-stu-id="1cc95-128">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="1cc95-129">Vista actual y admitida de un elemento que tiene varias vistas</span><span class="sxs-lookup"><span data-stu-id="1cc95-129">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="1cc95-130">Propiedades de un elemento que se desplaza en un intervalo de valores, como un control deslizante</span><span class="sxs-lookup"><span data-stu-id="1cc95-130">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="1cc95-131">Propiedades de una ventana desplazable</span><span class="sxs-lookup"><span data-stu-id="1cc95-131">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="1cc95-132">Estado y contenedor de un elemento que se puede seleccionar, como en una lista</span><span class="sxs-lookup"><span data-stu-id="1cc95-132">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="1cc95-133">Propiedades de un control que contiene elementos de selección</span><span class="sxs-lookup"><span data-stu-id="1cc95-133">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="1cc95-134">Encabezados de fila y columna de un elemento en una tabla</span><span class="sxs-lookup"><span data-stu-id="1cc95-134">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="1cc95-135">Encabezados de fila y columna, y orientación, de una tabla</span><span class="sxs-lookup"><span data-stu-id="1cc95-135">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="1cc95-136">Estado de un control de alternancia</span><span class="sxs-lookup"><span data-stu-id="1cc95-136">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="1cc95-137">Capacidades de un elemento que se pueden mover, girar o cambiar de tamaño</span><span class="sxs-lookup"><span data-stu-id="1cc95-137">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="1cc95-138">Capacidades de lectura y escritura y valor de un elemento que tiene un valor</span><span class="sxs-lookup"><span data-stu-id="1cc95-138">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="1cc95-139">Capacidades y estado de una ventana</span><span class="sxs-lookup"><span data-stu-id="1cc95-139">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>

## <a name="properties-by-category"></a><span data-ttu-id="1cc95-140">Propiedades por categoría</span><span class="sxs-lookup"><span data-stu-id="1cc95-140">Properties by Category</span></span>  

 <span data-ttu-id="1cc95-141">En las siguientes tablas se clasifican las propiedades cuyos identificadores se encuentran en <xref:System.Windows.Automation.AutomationElement> y <xref:System.Windows.Automation.AutomationElementIdentifiers> .</span><span class="sxs-lookup"><span data-stu-id="1cc95-141">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="1cc95-142">Estas propiedades son comunes para todos los controles.</span><span class="sxs-lookup"><span data-stu-id="1cc95-142">These properties are common to all controls.</span></span> <span data-ttu-id="1cc95-143">Salvo algunas de ellas, todas suelen ser estáticas a lo largo de la duración de la aplicación de proveedor; la mayoría de propiedades dinámicas están asociadas con patrones de control.</span><span class="sxs-lookup"><span data-stu-id="1cc95-143">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="1cc95-144">En la columna **Property Access** se enumeran los otros descriptores de acceso de cada propiedad, además de <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> y <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="1cc95-144">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="1cc95-145">Para más información sobre la obtención de propiedades en una aplicación cliente, consulte [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1cc95-145">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cc95-146">Para obtener información específica sobre cada propiedad, siga el vínculo de la columna **Property Access** .</span><span class="sxs-lookup"><span data-stu-id="1cc95-146">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="1cc95-147">Características de presentación</span><span class="sxs-lookup"><span data-stu-id="1cc95-147">Display Characteristics</span></span>  
  
|<span data-ttu-id="1cc95-148">Identificador de la propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-148">Property identifier</span></span>|<span data-ttu-id="1cc95-149">Property Access</span><span class="sxs-lookup"><span data-stu-id="1cc95-149">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="1cc95-150">N/D</span><span class="sxs-lookup"><span data-stu-id="1cc95-150">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="1cc95-151">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="1cc95-151">Element Type</span></span>  
  
|<span data-ttu-id="1cc95-152">Identificador de la propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-152">Property identifier</span></span>|<span data-ttu-id="1cc95-153">Property Access</span><span class="sxs-lookup"><span data-stu-id="1cc95-153">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="1cc95-154">Identificación</span><span class="sxs-lookup"><span data-stu-id="1cc95-154">Identification</span></span>  
  
|<span data-ttu-id="1cc95-155">Identificador de la propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-155">Property identifier</span></span>|<span data-ttu-id="1cc95-156">Property Access</span><span class="sxs-lookup"><span data-stu-id="1cc95-156">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="1cc95-157">Interacción</span><span class="sxs-lookup"><span data-stu-id="1cc95-157">Interaction</span></span>  
  
|<span data-ttu-id="1cc95-158">Identificador de la propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-158">Property identifier</span></span>|<span data-ttu-id="1cc95-159">Property Access</span><span class="sxs-lookup"><span data-stu-id="1cc95-159">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="1cc95-160">Compatibilidad con patrones</span><span class="sxs-lookup"><span data-stu-id="1cc95-160">Support for Patterns</span></span>  
  
|<span data-ttu-id="1cc95-161">Identificador de la propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-161">Property identifier</span></span>|<span data-ttu-id="1cc95-162">Property Access</span><span class="sxs-lookup"><span data-stu-id="1cc95-162">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="1cc95-163">Varios</span><span class="sxs-lookup"><span data-stu-id="1cc95-163">Miscellaneous</span></span>  
  
|<span data-ttu-id="1cc95-164">Identificador de la propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-164">Property identifier</span></span>|<span data-ttu-id="1cc95-165">Property Access</span><span class="sxs-lookup"><span data-stu-id="1cc95-165">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>

## <a name="localization"></a><span data-ttu-id="1cc95-166">Localización</span><span class="sxs-lookup"><span data-stu-id="1cc95-166">Localization</span></span>  

 <span data-ttu-id="1cc95-167">Los proveedores[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] deben presentar las siguientes propiedades en el idioma del sistema operativo:</span><span class="sxs-lookup"><span data-stu-id="1cc95-167">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>

## <a name="properties-and-events"></a><span data-ttu-id="1cc95-168">Propiedades y eventos</span><span class="sxs-lookup"><span data-stu-id="1cc95-168">Properties and Events</span></span>  

 <span data-ttu-id="1cc95-169">El concepto de eventos de cambio de propiedad está estrechamente relacionado con las propiedades de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1cc95-169">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="1cc95-170">Para las propiedades dinámicas, la aplicación cliente necesita una manera de saber que un valor de propiedad ha cambiado, por lo que puede actualizar su caché de información o reaccionar a la nueva información de alguna otra manera.</span><span class="sxs-lookup"><span data-stu-id="1cc95-170">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="1cc95-171">Los proveedores generan eventos cuando cambia algo en la [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1cc95-171">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="1cc95-172">Por ejemplo, si se selecciona o se desactiva una casilla, la implementación del proveedor del patrón Toggle genera un evento de cambio de propiedad.</span><span class="sxs-lookup"><span data-stu-id="1cc95-172">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="1cc95-173">Los proveedores pueden generar eventos de forma selectiva, dependiendo de si hay clientes en escucha de eventos o en escucha de eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="1cc95-173">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="1cc95-174">No todos los cambios de propiedades generan eventos; esto depende totalmente de la implementación del proveedor de Automatización de la interfaz de usuario del elemento.</span><span class="sxs-lookup"><span data-stu-id="1cc95-174">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="1cc95-175">Por ejemplo, los proveedores de proxy estándares para cuadros de lista no generan un evento cuando el elemento <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> cambia.</span><span class="sxs-lookup"><span data-stu-id="1cc95-175">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="1cc95-176">En este caso, la aplicación debe estar en su lugar a la escucha de un elemento <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span><span class="sxs-lookup"><span data-stu-id="1cc95-176">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="1cc95-177">Los clientes se ponen a la escucha de eventos suscribiéndose a ellos.</span><span class="sxs-lookup"><span data-stu-id="1cc95-177">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="1cc95-178">La suscripción a eventos supone la creación de métodos delegados que pueden controlar los eventos y, después, pasan los métodos a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] junto con los eventos específicos que se tratarán en esos métodos.</span><span class="sxs-lookup"><span data-stu-id="1cc95-178">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="1cc95-179">Para los eventos de cambio de propiedad en concreto, los clientes deben implementar <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1cc95-179">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc95-180">Vea también</span><span class="sxs-lookup"><span data-stu-id="1cc95-180">See also</span></span>

- [<span data-ttu-id="1cc95-181">Almacenar en caché en los clientes de automatización de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="1cc95-181">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="1cc95-182">Propiedades de UI Automation para clientes</span><span class="sxs-lookup"><span data-stu-id="1cc95-182">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="1cc95-183">Implementación del proveedor de UI Automation en el servidor</span><span class="sxs-lookup"><span data-stu-id="1cc95-183">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="1cc95-184">Buscar un elemento de UI Automation basándose en una condición de propiedad</span><span class="sxs-lookup"><span data-stu-id="1cc95-184">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="1cc95-185">Devolución de propiedades por parte de un proveedor de UI Automation</span><span class="sxs-lookup"><span data-stu-id="1cc95-185">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="1cc95-186">Provocar eventos desde un proveedor de UI Automation</span><span class="sxs-lookup"><span data-stu-id="1cc95-186">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
