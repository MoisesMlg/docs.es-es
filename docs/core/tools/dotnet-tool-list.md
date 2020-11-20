---
title: Comando dotnet tool list
description: El comando dotnet tool list enumera las herramientas de .NET que están instaladas en el equipo.
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634290"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Este artículo se aplica a:** ✔️ SDK de .NET Core 2.1 y versiones posteriores

## <a name="name"></a>NOMBRE

`dotnet tool list`: enumera todas las [herramientas de .NET](global-tools.md) del tipo especificado actualmente instalado en el equipo.

## <a name="synopsis"></a>Sinopsis

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a>Descripción

El comando `dotnet tool list` permite enumerar todas las herramientas locales, de ruta de acceso de herramienta y globales de .NET instaladas en el equipo. El comando enumera el nombre del paquete, la versión instalada y el comando de la herramienta.  Para usar el comando, especifique una de las siguientes opciones:

* Para enumerar las herramientas globales instaladas en la ubicación predeterminada, use la opción `--global`.
* Para enumerar las herramientas globales instaladas en la ubicación personalizada, use la opción `--tool-path`.
* Para enumerar las herramientas locales, use la opción `--local` u omita las opciones `--global`, `--tool-path` y `--local`.

**Las herramientas locales están disponibles a partir del SDK de .NET Core 3.0.**

## <a name="options"></a>Opciones

- **`-g|--global`**

  Enumera las herramientas globales de los usuarios. No se puede combinar con la opción `--tool-path`. Al omitir `--global` y `--tool-path`, se muestran las herramientas locales.

- **`-h|--help`**

  Imprime una corta ayuda para el comando.

- **`--local`**

  Enumera las herramientas locales del directorio actual. No se puede combinar con las opciones `--global` o `--tool-path`. Al omitir `--global` y `--tool-path`, se enumeran las herramientas locales, aunque no se haya especificado `--local`.

- **`--tool-path <PATH>`**

  Especifica una ubicación personalizada para las herramientas globales. PATH puede ser una ruta absoluta o relativa. No se puede combinar con la opción `--global`. Al omitir `--global` y `--tool-path`, se muestran las herramientas locales.

## <a name="examples"></a>Ejemplos

- **`dotnet tool list -g`**

  Enumera todas las herramientas globales instaladas para todos los usuarios en su equipo (perfil de usuario actual).

- **`dotnet tool list --tool-path c:\global-tools`**

  Enumera las herramientas globales de un directorio específico de Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Enumera las herramientas globales de un directorio específico de Linux/macOS.

- **`dotnet tool list`** o **`dotnet tool list --local`**

  Enumera todas las herramientas locales disponibles en el directorio actual.

## <a name="see-also"></a>Vea también

- [Herramientas de .NET](global-tools.md)
- [Tutorial: Instalación y uso de una herramienta global de .NET mediante la CLI de .NET](global-tools-how-to-use.md)
- [Tutorial: Instalación y uso de una herramienta local de .NET mediante la CLI de .NET](local-tools-how-to-use.md)
