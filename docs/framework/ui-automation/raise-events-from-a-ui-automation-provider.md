---
title: Provocar eventos desde un proveedor de UI Automation
description: Vea un ejemplo en el que se muestra cómo generar un evento desde un proveedor de automatización de la interfaz de usuario. Genera un evento de automatización de la interfaz de usuario en la implementación de un control de botón personalizado.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 73be7fd92f3fde90255326c51bed03427fd68e8d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250494"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>Provocar eventos desde un proveedor de UI Automation

> [!NOTE]
> Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>. Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).  
  
 Este tema contiene código de ejemplo que muestra cómo desencadenar un evento desde un proveedor de Automatización de la interfaz de usuario.  
  
## <a name="example"></a>Ejemplo  

 En el ejemplo siguiente, un evento de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se genera en la implementación de un control de botón personalizado. La implementación permite a una aplicación cliente de Automatización de la interfaz de usuario simular un clic de botón.  
  
 Para evitar un procesamiento innecesario, el ejemplo comprueba <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> para ver si se deben generar eventos.  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>Vea también

- [Información general sobre proveedores de UI Automation](ui-automation-providers-overview.md)
