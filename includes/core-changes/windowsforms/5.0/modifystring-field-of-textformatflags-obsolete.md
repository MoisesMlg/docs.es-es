---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400640"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="06ea7-101">TextFormatFlags.ModifyString está obsoleto</span><span class="sxs-lookup"><span data-stu-id="06ea7-101">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="06ea7-102">El campo <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> está obsoleto, como advertencia, y es posible que se quite en una versión futura de .NET.</span><span class="sxs-lookup"><span data-stu-id="06ea7-102">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="06ea7-103">Descripción del cambio</span><span class="sxs-lookup"><span data-stu-id="06ea7-103">Change description</span></span>

<span data-ttu-id="06ea7-104">En versiones anteriores de .NET, el campo de enumeración <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> no está marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="06ea7-104">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="06ea7-105">En .NET 5.0 y versiones posteriores, está marcado como obsoleto como advertencia.</span><span class="sxs-lookup"><span data-stu-id="06ea7-105">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="06ea7-106">Es posible que este campo se quite en una versión futura de .NET.</span><span class="sxs-lookup"><span data-stu-id="06ea7-106">This field may be removed in a future .NET version.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="06ea7-107">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="06ea7-107">Reason for change</span></span>

<span data-ttu-id="06ea7-108">Pasar una cadena a <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> con <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> modifica la cadena en algunas situaciones.</span><span class="sxs-lookup"><span data-stu-id="06ea7-108">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="06ea7-109">Este comportamiento incumple la promesa de inmutabilidad de la cadena y puede provocar daños graves en el estado del entorno de ejecución de .NET.</span><span class="sxs-lookup"><span data-stu-id="06ea7-109">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="06ea7-110">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="06ea7-110">Version introduced</span></span>

<span data-ttu-id="06ea7-111">.NET 5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="06ea7-111">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="06ea7-112">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="06ea7-112">Recommended action</span></span>

<span data-ttu-id="06ea7-113">Actualice cualquier código que se base en <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06ea7-113">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="06ea7-114">Categoría</span><span class="sxs-lookup"><span data-stu-id="06ea7-114">Category</span></span>

<span data-ttu-id="06ea7-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="06ea7-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06ea7-116">API afectadas</span><span class="sxs-lookup"><span data-stu-id="06ea7-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->