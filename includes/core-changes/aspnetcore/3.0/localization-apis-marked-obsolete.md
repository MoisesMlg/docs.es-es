---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032818"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localización: ResourceManagerWithCultureStringLocalizer y WithCulture se han marcado como obsoletos

La clase [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) y el miembro de interfaz [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) suelen ser fuentes de confusión para los usuarios de localización, en particular al crear su propia implementación de `IStringLocalizer`. Estos elementos proporcionan al usuario la impresión de que una instancia de `IStringLocalizer` es "por lenguaje y por recurso". En realidad, las instancias solo deben ser "por recurso". El lenguaje que se busca lo determina el `CultureInfo.CurrentUICulture` en tiempo de ejecución. Para eliminar el origen de la confusión, las API se han marcado como obsoletas en ASP.NET Core 3.0, versión preliminar 3. Las API se quitarán en una versión futura.

Para obtener el contexto, consulte [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324). Para obtener información, vea [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Versión introducida

3.0

#### <a name="old-behavior"></a>Comportamiento anterior

Los métodos no se marcaban como `Obsolete`.

#### <a name="new-behavior"></a>Comportamiento nuevo

Los métodos se marcan como `Obsolete`.

#### <a name="reason-for-change"></a>Motivo del cambio

Las API representan un caso de uso que no se recomienda. Ha habido confusión sobre el diseño de la localización.

#### <a name="recommended-action"></a>Acción recomendada

La recomendación es usar `ResourceManagerStringLocalizer` en su lugar. Permita que `CurrentCulture` establezca la referencia cultural. Si no es una opción, cree y use una copia de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Categoría

ASP.NET Core

#### <a name="affected-apis"></a>API afectadas

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
