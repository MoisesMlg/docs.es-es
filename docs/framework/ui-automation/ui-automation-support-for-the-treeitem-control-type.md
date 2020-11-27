---
title: Compatibilidad de UI Automation para el tipo de control TreeItem
description: Obtenga información sobre la compatibilidad de UI Automation para el tipo de control TreeItem. Obtenga información sobre la estructura de árbol necesaria, las propiedades, los patrones de control y los eventos.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
ms.openlocfilehash: 4ad53ee63d5e3ebb2cdd845a1258d191fa9fb521
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281279"
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>Compatibilidad de UI Automation para el tipo de control TreeItem

> [!NOTE]
> Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).  
  
 En este tema se ofrece información sobre la compatibilidad de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] con el tipo de control TreeItem. En [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un tipo de control es un conjunto de condiciones que un control debe cumplir para poder usar la propiedad <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . En las condiciones se incluyen instrucciones específicas para la estructura de árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , los patrones de control y los valores de propiedad de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 El tipo de control TreeItem representa un nodo dentro de un contenedor de árbol. Cada nodo puede contener otros nodos, llamados nodos secundarios. Los nodos primarios o los nodos que contienen nodos secundarios se pueden mostrar expandidos o contraídos.  
  
 En las secciones siguientes se definen la estructura del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , las propiedades, los patrones de control y los eventos necesarios para el tipo de control TreeItem. Los [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requisitos de se aplican a todos los controles de elemento de árbol, ya sean [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 o Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Estructura de árbol de Automatización de la interfaz de usuario necesaria  

 En la tabla siguiente se detallan la vista de control y la vista de contenido del árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que pertenece a los controles de elemento de árbol y se describe lo que puede incluirse en cada vista. Para más información sobre el árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , vea [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Vista de control|Vista de contenido|  
|------------------|------------------|  
|TreeItem<br /><br /> -CheckBox (0 o 1)<br />-Image (0 o 1)<br />-Button (0 o 1)<br />-TreeItem (0 o más)|TreeItem<br /><br /> -TreeItem (0 o más)|  
  
 Los controles de elemento de árbol pueden tener cero o más elementos secundarios de elemento de árbol en la vista de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Si el control de elemento de árbol tiene una funcionalidad más allá de lo expuesto en los patrones de control que se muestran a continuación, el control debe basarse en el tipo de control Data Item.  
  
 Los elementos del árbol contraídos no se mostrarán en la vista de control ni en la vista de contenido hasta que estén visibles y expandidos (o se pueden desplazar en la vista).  
  
 La vista de control puede contener detalles adicionales de un control, entre los que se incluyen una imagen asociada o un botón. Por ejemplo, un elemento de una vista Esquema podría contener una imagen, así como un botón para expandir o contraer el esquema. Estos objetos de detalle no aparecen en la vista de contenido porque la información ya está representada por el elemento de árbol primario. Los elementos de árbol que se desplazan fuera de la pantalla aparecerán en las vistas de control y de contenido del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] y deben tener la propiedad <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> establecida en true.  
  
<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Propiedades de Automatización de la interfaz de usuario necesarias  

 En la tabla siguiente se muestran las propiedades [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] cuyo valor o definición es especialmente relevante para los controles de lista. Para obtener más información sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] las propiedades, vea [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Propiedad[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valor|Notas|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Vea las notas.|El valor de esta propiedad debe ser único en todos los controles de una aplicación.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Vea las notas.|El rectángulo exterior que contiene el control completo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Vea las notas.|Esta propiedad debe devolver una ubicación del elemento que hará que el elemento cambie el estado de selección u obtenga el foco.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TreeItem|Este valor es el mismo para todos los marcos de trabajo de la interfaz de usuario.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|El control de lista siempre se incluye en la vista de contenido del árbol [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|El control de lista siempre se incluye en la vista de control del árbol de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Vea las notas.|Esta propiedad se establece para indicar cuando un control de elemento de árbol se desplaza fuera de la pantalla.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Vea las notas.|Si el control puede recibir el foco del teclado, debe admitir esta propiedad.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Vea las notas.|Si el control de elemento de árbol utiliza un icono visual para indicar que es un tipo de objeto determinado, esta propiedad debe admitirse e indicar cuál es el objeto.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Los controles de elemento de árbol se etiquetan automáticamente.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"elemento de árbol"|Cadena localizada que corresponde al tipo de control TreeItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Vea las notas.|Esta propiedad expone el texto que se muestra para cada control de elemento de árbol.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Patrones de control de Automatización de la interfaz de usuario necesarios  

 En la tabla siguiente se muestran los patrones de control [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que deben admitir los controles de lista. Para más información sobre los patrones de control, vea [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Patrón de control/Propiedad de patrón|Soporte técnico/valor|Notas|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Depende|Implemente este patrón de control si el elemento de árbol tiene un comando independiente y accionable.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Yes|Todos los elementos del árbol se pueden expandir o contraer.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Expanded, Collapsed o Leaf Node|Los elementos de árbol serán nodos hoja cuando no se expandan ni contraigan.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Depende|Implemente este patrón de control si el contenedor de árbol admite el patrón de control Scroll.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Depende|Implemente este patrón de control si es posible tener una selección activa que se mantenga cuando el usuario vuelva al contenedor de árbol.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Yes|Esta propiedad expondrá el mismo contenedor para todos los elementos de dentro del contenedor.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Depende|Implemente este patrón de control si el elemento de árbol tiene una casilla asociada.|  
  
<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Eventos de Automatización de la interfaz de usuario necesarios  

 En la siguiente tabla se muestran los eventos de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] que deben admitir todos los controles de elemento de datos. Para más información sobre eventos, vea [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|o[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Soporte técnico|Notas|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatorio|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Requerido|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Requerido|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Requerido|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> .|Depende|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> .|Requerido|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatorio|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> .|Requerido|None|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Depende|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> .|Depende|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Depende|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Depende|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Depende|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> .|Depende|None|  
|Evento cambiado por propiedad<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> .|Depende|None|  
  
## <a name="see-also"></a>Vea también

- <xref:System.Windows.Automation.ControlType.TreeItem>
- [Información general sobre tipos de control de UI Automation](ui-automation-control-types-overview.md)
- [Información general sobre UI Automation](ui-automation-overview.md)
