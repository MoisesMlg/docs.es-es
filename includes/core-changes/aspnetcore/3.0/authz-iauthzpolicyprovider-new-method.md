---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032698"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorización: las implementaciones de IAuthorizationPolicyProvider requieren un método nuevo

En ASP.NET Core 3.0, se ha agregado un nuevo método `GetFallbackPolicyAsync` a `IAuthorizationPolicyProvider`. El middleware de autorización usa esta directiva de reserva cuando no se especifica ninguna directiva.

Para obtener más información, consulte [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Versión introducida

3.0

#### <a name="old-behavior"></a>Comportamiento anterior

Las implementaciones de `IAuthorizationPolicyProvider` no requerían un método `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Comportamiento nuevo

Las implementaciones de `IAuthorizationPolicyProvider` requieren un método `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Motivo del cambio

Se necesitaba un nuevo método para que el nuevo `AuthorizationMiddleware` lo usara cuando no se especificara ninguna directiva.

#### <a name="recommended-action"></a>Acción recomendada

Agregue el método `GetFallbackPolicyAsync` a las implementaciones de `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Categoría

ASP.NET Core

#### <a name="affected-apis"></a>API afectadas

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
