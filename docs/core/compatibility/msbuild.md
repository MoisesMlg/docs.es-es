---
title: Cambios importantes de MSBuild
description: Se enumeran los cambios importantes de MSBuild en .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159498"
---
# <a name="msbuild-breaking-changes"></a>Cambios importantes de MSBuild

En esta página se documentan los siguientes cambios importantes:

| Cambio importante | Versión introducida |
| - | - |
| [Cambio de TargetFramework de netcoreapp a net](#targetframework-change-from-netcoreapp-to-net) | 5.0 |
| [Símbolo de preprocesador de NETCOREAPP3_1 no definido al establecer .NET 5 como destino](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | 5.0 |
| [Cambio de comportamiento de PublishDepsFilePath](#publishdepsfilepath-behavior-change) | 5.0 |
| [Los archivos Directory.Packages.props se importan de forma predeterminada](#directorypackagesprops-files-is-imported-by-default) | 5.0 |
| [Cambio de nombre de archivo de manifiesto del recurso](#resource-manifest-file-name-change) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
