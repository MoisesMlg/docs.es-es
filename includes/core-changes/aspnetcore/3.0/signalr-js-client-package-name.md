---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032883"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="6216c-101">SignalR: se ha cambiado el nombre del paquete de cliente de JavaScript</span><span class="sxs-lookup"><span data-stu-id="6216c-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="6216c-102">En ASP.NET Core 3.0, versión preliminar 7, el nombre del paquete de cliente de JavaScript de SignalR ha cambiado de `@aspnet/signalr` a `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="6216c-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="6216c-103">El cambio de nombre refleja el hecho de que SignalR es útil más allá de las aplicaciones de ASP.NET Core, gracias a Azure SignalR Service.</span><span class="sxs-lookup"><span data-stu-id="6216c-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="6216c-104">Para reaccionar a este cambio, cambie las referencias en los archivos *package.json*, las instrucciones `require` y las instrucciones `import` de ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="6216c-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="6216c-105">No se cambiará ninguna API como parte de este cambio de nombre.</span><span class="sxs-lookup"><span data-stu-id="6216c-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="6216c-106">Para obtener información, vea [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="6216c-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6216c-107">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="6216c-107">Version introduced</span></span>

<span data-ttu-id="6216c-108">3.0</span><span class="sxs-lookup"><span data-stu-id="6216c-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6216c-109">Comportamiento anterior</span><span class="sxs-lookup"><span data-stu-id="6216c-109">Old behavior</span></span>

<span data-ttu-id="6216c-110">El paquete de cliente se llamaba `@aspnet/signalr`.</span><span class="sxs-lookup"><span data-stu-id="6216c-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6216c-111">Comportamiento nuevo</span><span class="sxs-lookup"><span data-stu-id="6216c-111">New behavior</span></span>

<span data-ttu-id="6216c-112">El paquete de cliente se llama `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="6216c-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6216c-113">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="6216c-113">Reason for change</span></span>

<span data-ttu-id="6216c-114">El cambio de nombre clarifica que SignalR es útil más allá de las aplicaciones de ASP.NET Core, gracias a Azure SignalR Service.</span><span class="sxs-lookup"><span data-stu-id="6216c-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6216c-115">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="6216c-115">Recommended action</span></span>

<span data-ttu-id="6216c-116">Cambie al paquete `@microsoft/signalr` nuevo.</span><span class="sxs-lookup"><span data-stu-id="6216c-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="6216c-117">Categoría</span><span class="sxs-lookup"><span data-stu-id="6216c-117">Category</span></span>

<span data-ttu-id="6216c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6216c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6216c-119">API afectadas</span><span class="sxs-lookup"><span data-stu-id="6216c-119">Affected APIs</span></span>

<span data-ttu-id="6216c-120">None</span><span class="sxs-lookup"><span data-stu-id="6216c-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
