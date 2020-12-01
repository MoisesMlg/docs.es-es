---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032770"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="93c2f-101">HTTP: se ha quitado la extensibilidad de DefaultHttpContext</span><span class="sxs-lookup"><span data-stu-id="93c2f-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="93c2f-102">Como parte de las mejoras de rendimiento de ASP.NET Core 3.0, se ha quitado la extensibilidad de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="93c2f-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="93c2f-103">La clase ahora es `sealed`.</span><span class="sxs-lookup"><span data-stu-id="93c2f-103">The class is now `sealed`.</span></span> <span data-ttu-id="93c2f-104">Para obtener más información, consulte [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="93c2f-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="93c2f-105">Si en las pruebas unitarias se usa `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` o `new DefaultHttpContext()` en su lugar.</span><span class="sxs-lookup"><span data-stu-id="93c2f-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="93c2f-106">Para obtener información, vea [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="93c2f-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="93c2f-107">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="93c2f-107">Version introduced</span></span>

<span data-ttu-id="93c2f-108">3.0</span><span class="sxs-lookup"><span data-stu-id="93c2f-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="93c2f-109">Comportamiento anterior</span><span class="sxs-lookup"><span data-stu-id="93c2f-109">Old behavior</span></span>

<span data-ttu-id="93c2f-110">Las clases se pueden derivar de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="93c2f-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="93c2f-111">Comportamiento nuevo</span><span class="sxs-lookup"><span data-stu-id="93c2f-111">New behavior</span></span>

<span data-ttu-id="93c2f-112">Las clases se pueden derivar de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="93c2f-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="93c2f-113">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="93c2f-113">Reason for change</span></span>

<span data-ttu-id="93c2f-114">La extensibilidad se proporcionó inicialmente para permitir la agrupación de `HttpContext`, pero incorporaba una complejidad innecesaria e impedía otras optimizaciones.</span><span class="sxs-lookup"><span data-stu-id="93c2f-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="93c2f-115">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="93c2f-115">Recommended action</span></span>

<span data-ttu-id="93c2f-116">Si usa `Mock<DefaultHttpContext>` en las pruebas unitarias, empiece a usar `Mock<HttpContext>` en su lugar.</span><span class="sxs-lookup"><span data-stu-id="93c2f-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="93c2f-117">Categoría</span><span class="sxs-lookup"><span data-stu-id="93c2f-117">Category</span></span>

<span data-ttu-id="93c2f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="93c2f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="93c2f-119">API afectadas</span><span class="sxs-lookup"><span data-stu-id="93c2f-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
