---
title: Exponer el contenido de una tabla mediante UI Automation
description: Vea cómo exponer el contenido de una tabla mediante la automatización de la interfaz de usuario. Se exponen el contenido y las propiedades intrínsecas de cada celda de un control tabular.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
ms.openlocfilehash: e089f1371dba476b1f75f9fffe7d224c840f8d80
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276521"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a><span data-ttu-id="702f2-104">Exponer el contenido de una tabla mediante UI Automation</span><span class="sxs-lookup"><span data-stu-id="702f2-104">Expose the Content of a Table Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="702f2-105">Esta documentación está dirigida a los desarrolladores de .NET Framework que quieran usar las clases [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] administradas definidas en el espacio de nombres <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="702f2-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="702f2-106">Para ver la información más reciente acerca de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: automatización de la interfaz de usuario](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="702f2-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="702f2-107">En este tema se muestra cómo [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] se puede usar para exponer el contenido y las propiedades intrínsecas de cada celda de un control tabular.</span><span class="sxs-lookup"><span data-stu-id="702f2-107">This topic shows how [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] can be used to expose the content and intrinsic properties of each cell within a tabular control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="702f2-108">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="702f2-108">Example</span></span>  

 <span data-ttu-id="702f2-109">En el ejemplo de código siguiente se muestra cómo obtener un <xref:System.Windows.Automation.AutomationElement> que representa el contenido de una celda de tabla; también se obtienen las propiedades de celda, como índices de fila y columna, intervalos de filas y columnas, y la información de encabezado de fila y de columna.</span><span class="sxs-lookup"><span data-stu-id="702f2-109">The following code example demonstrates how to obtain a <xref:System.Windows.Automation.AutomationElement> that represents the content of a table cell; cell properties such as row and column indices, row and column spans, and row and column header information are also obtained.</span></span> <span data-ttu-id="702f2-110">En este ejemplo se usa un controlador de eventos de cambio de foco para simular el recorrido del teclado de un control tabular que implementa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="702f2-110">This example uses a focus change event handler to simulate keyboard traversal of a tabular control that implements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="702f2-111">La información de cada elemento de la tabla se expone en un evento de cambio de foco.</span><span class="sxs-lookup"><span data-stu-id="702f2-111">Information for each table item is exposed on a focus change event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="702f2-112">Dado que los cambios de foco son eventos de escritorio globales, se deben filtrar los eventos de cambio de foco fuera de la tabla.</span><span class="sxs-lookup"><span data-stu-id="702f2-112">Since focus changes are global desktop events, focus change events outside the table should be filtered.</span></span> <span data-ttu-id="702f2-113">Vea el [ejemplo TrackFocus](/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90)) para obtener una implementación relacionada.</span><span class="sxs-lookup"><span data-stu-id="702f2-113">See the [TrackFocus Sample](/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90)) for a related implementation.</span></span>  
  
 [!code-csharp[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#starttarget)]
 [!code-vb[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#starttarget)]  
[!code-csharp[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#gettableelement)]
[!code-vb[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#gettableelement)]  
[!code-csharp[UIATableItemPattern_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#101)]
[!code-vb[UIATableItemPattern_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#101)]  
[!code-csharp[UIATableItemPattern_snip#1015](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#1015)]
[!code-vb[UIATableItemPattern_snip#1015](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#1015)]  
[!code-csharp[UIATableItemPattern_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#102)]
[!code-vb[UIATableItemPattern_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#102)]  
[!code-csharp[UIATableItemPattern_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#103)]
[!code-vb[UIATableItemPattern_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="702f2-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="702f2-114">See also</span></span>

- [<span data-ttu-id="702f2-115">Información general acerca de los patrones de control de UI Automation</span><span class="sxs-lookup"><span data-stu-id="702f2-115">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="702f2-116">Patrones de controles de UI Automation para clientes</span><span class="sxs-lookup"><span data-stu-id="702f2-116">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="702f2-117">Implementar el patrón de control Table de UI Automation</span><span class="sxs-lookup"><span data-stu-id="702f2-117">Implementing the UI Automation Table Control Pattern</span></span>](implementing-the-ui-automation-table-control-pattern.md)
- [<span data-ttu-id="702f2-118">Implementar el patrón de control TableItem de UI Automation</span><span class="sxs-lookup"><span data-stu-id="702f2-118">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="702f2-119">Implementar el patrón de control Grid de UI Automation</span><span class="sxs-lookup"><span data-stu-id="702f2-119">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="702f2-120">Implementar el patrón de control GridItem de UI Automation</span><span class="sxs-lookup"><span data-stu-id="702f2-120">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
