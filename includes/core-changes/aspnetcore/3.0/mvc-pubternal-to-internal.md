---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032834"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="d5ee9-101">MVC: los tipos "pubternal" se han cambiado a internal</span><span class="sxs-lookup"><span data-stu-id="d5ee9-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="d5ee9-102">En ASP.NET Core 3.0, todos los tipos "pubternal" de MVC se actualizaron para ser `public` en un espacio de nombres compatible o `internal`, según correspondiera.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d5ee9-103">Descripción del cambio</span><span class="sxs-lookup"><span data-stu-id="d5ee9-103">Change description</span></span>

<span data-ttu-id="d5ee9-104">In ASP.NET Core, los tipos "pubternal" se declaran como `public` pero residen en un espacio de nombres con un sufijo `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="d5ee9-105">Aunque estos tipos son `public`, no tienen ninguna directiva compatible y están sujetos a cambios importantes.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="d5ee9-106">Desafortunadamente, el uso accidental de estos tipos es habitual, lo que da lugar a cambios importantes en estos proyectos y limita la capacidad de mantener el marco.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d5ee9-107">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="d5ee9-107">Version introduced</span></span>

<span data-ttu-id="d5ee9-108">3.0</span><span class="sxs-lookup"><span data-stu-id="d5ee9-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d5ee9-109">Comportamiento anterior</span><span class="sxs-lookup"><span data-stu-id="d5ee9-109">Old behavior</span></span>

<span data-ttu-id="d5ee9-110">Algunos tipos de MVC eran `public` pero en un espacio de nombres `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="d5ee9-111">Estos tipos no tenían ninguna directiva compatible y estaban sujetos a cambios importantes.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d5ee9-112">Comportamiento nuevo</span><span class="sxs-lookup"><span data-stu-id="d5ee9-112">New behavior</span></span>

<span data-ttu-id="d5ee9-113">Todos estos tipos se actualizan para ser `public` en un espacio de nombres compatible o que se marquen como `internal`.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d5ee9-114">Motivo del cambio</span><span class="sxs-lookup"><span data-stu-id="d5ee9-114">Reason for change</span></span>

<span data-ttu-id="d5ee9-115">El uso accidental de los tipos "pubternal" es habitual, lo que da lugar a cambios importantes en estos proyectos y limita la capacidad de mantener el marco.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d5ee9-116">Acción recomendada</span><span class="sxs-lookup"><span data-stu-id="d5ee9-116">Recommended action</span></span>

<span data-ttu-id="d5ee9-117">Si usa tipos que se han convertido realmente en `public` y se han movido a un nuevo espacio de nombres compatible, actualice las referencias para que coincidan con los espacios de nombres nuevos.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="d5ee9-118">Si utiliza tipos que se han marcado como `internal`, deberá buscar una alternativa.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="d5ee9-119">Los tipos "pubternal" anteriores nunca se admitieron para uso público.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="d5ee9-120">Si hay tipos específicos en estos espacios de nombres que son fundamentales para las aplicaciones, registre una incidencia en [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="d5ee9-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="d5ee9-121">Se pueden pensar ideas para hacer los tipos solicitados `public`.</span><span class="sxs-lookup"><span data-stu-id="d5ee9-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="d5ee9-122">Categoría</span><span class="sxs-lookup"><span data-stu-id="d5ee9-122">Category</span></span>

<span data-ttu-id="d5ee9-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d5ee9-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d5ee9-124">API afectadas</span><span class="sxs-lookup"><span data-stu-id="d5ee9-124">Affected APIs</span></span>

<span data-ttu-id="d5ee9-125">Este cambio incluye tipos en los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="d5ee9-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
