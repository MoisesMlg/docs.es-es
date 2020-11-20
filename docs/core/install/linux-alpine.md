---
title: 'Instalación de .NET en Alpine: .NET'
description: Se muestran las diversas maneras de instalar el SDK y el entorno de ejecución de .NET en Alpine.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506834"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a>Instalación del SDK y el entorno de ejecución de .NET en Alpine

En este artículo se describe cómo instalar .NET en Alpine. Cuando una versión de Alpine no es compatible, .NET deja de ser compatible con esa versión. Pero estas instrucciones pueden ayudarle a conseguir que .NET se ejecute en esas versiones, aunque no se admita.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

No hay instaladores para Alpine. Debe usar el [script de instalación](#scripted-install) o seguir las instrucciones de [instalación manual](#manual-install).

## <a name="supported-distributions"></a>Distribuciones admitidas

En la tabla siguiente se muestra una lista de versiones de .NET actualmente compatibles y las versiones de Alpine en las que se admiten. Estas versiones siguen siendo compatibles hasta que la versión de [.NET llega al fin del soporte técnico](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) o la versión de [Alpine llega al final del ciclo de vida](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- El símbolo ✔️ indica que todavía se admite la versión de Alpine o de .NET.
- El símbolo ❌ indica que la versión de Alpine o de .NET no se admite en esa versión de Alpine.
- Si una versión de Alpine y una versión de .NET tienen un símbolo ✔️, esa combinación de sistema operativo y .NET se admite.

| Alpine  | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-------- |---------------|---------------|----------------|
| ✔️ 3.12 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.11 | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 |
| ✔️ 3.10 | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.9  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |
| ❌ 3.8  | ✔️ 2.1        | ✔️ 3.1        | ❌ 5.0 |

Las versiones siguientes de .NET ya no se admiten. aunque sus descargas siguen estando publicadas:

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>Dependencias

Para .NET en Alpine Linux es necesario que estén instaladas las dependencias siguientes:

- icu-libs
- krb5-libs
- libgcc
- libintl
- libssl1.1 (Alpine 3.9 o superior)
- libssl1.0 (Alpine 3.8 o inferior)
- libstdc++
- zlib

## <a name="scripted-install"></a>Instalación con script

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalación manual

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Pasos siguientes

- [Tutorial: Creación de una aplicación de consola con el SDK de .NET mediante Visual Studio Code](../tutorials/with-visual-studio-code.md)
