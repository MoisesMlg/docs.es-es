---
title: Exposición de los componentes de .NET Core a COM
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 33574eeac5b1f7aa2067b1974f3f2e68fb22e8ff
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577177"
---
# <a name="exposing-net-core-components-to-com"></a>Exposición de los componentes de .NET Core a COM

En .NET Core, el proceso de exposición de los objetos .NET a COM se ha simplificado significativamente en comparación con .NET Framework. El siguiente proceso le guiará a través de la exposición de una clase a COM. En este tutorial se le enseñará a hacer lo siguiente:

- Exponer una clase a COM desde .NET Core.
- Generar un servidor COM como parte de la creación de la biblioteca de .NET Core.
- Generar automáticamente un manifiesto de servidor en paralelo para COM sin registro.

## <a name="prerequisites"></a>Requisitos previos

- Instale el [SDK de la versión preliminar 7 de .NET Core 3.0](https://www.microsoft.com/net/core) o una versión más reciente.

## <a name="create-the-library"></a>Crear la biblioteca

El primer paso consiste en crear la biblioteca.

1. Cree una carpeta y, en ella, ejecute `dotnet new classlib`.
2. Abra `Class1.cs`.
3. Agregue `using System.Runtime.InteropServices;` a la parte superior del archivo.
4. Cree una interfaz denominada `IServer`. Por ejemplo: [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]
5. Agregue el atributo `[Guid("<IID>")]` a la interfaz con el GUID de la interfaz para la interfaz COM que está implementando. Por ejemplo: `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Tenga en cuenta que este GUID debe ser único, ya que es el único identificador de esta interfaz para COM. En Visual Studio, puede generar un GUID desde Herramientas > Crear GUID para abrir la herramienta de creación de GUID.
6. Agregue el atributo `[InterfaceType]` a la interfaz y especifique qué interfaces COM base debe implementar la interfaz.
7. Cree una clase denominada `Server` que implemente `IServer`.
8. Agregue el atributo `[Guid("<CLSID>")]` a la clase, con el identificador de clase GUID para la clase COM que está implementando. Por ejemplo: `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Igual que sucede con la interfaz GUID, este GUID debe ser único, ya que es el único identificador de esta interfaz para COM.
9. Agregue el atributo `[ComVisible(true)]` a la interfaz y a la clase.

> [!IMPORTANT]
> A diferencia de lo que ocurre en .NET Framework, en .NET Core debe especificar el CLSID de cualquier clase que le interese que se pueda activar mediante COM.

## <a name="generate-the-com-host"></a>Generar el host de COM

1. Abra el archivo de proyecto `.csproj` y agregue `<EnableComHosting>true</EnableComHosting>` en una etiqueta `<PropertyGroup></PropertyGroup>`.
2. Compile el proyecto.

El resultado contendrá un archivo `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` y `ProjectName.comhost.dll`.

## <a name="register-the-com-host-for-com"></a>Registrar el host COM para COM

Abra un símbolo del sistema con privilegios elevados y ejecute `regsvr32 ProjectName.comhost.dll`. Esto registrará todos los objetos .NET expuestos con COM.

## <a name="enabling-regfree-com"></a>Habilitar RegFree COM

1. Abra el archivo de proyecto `.csproj` y agregue `<EnableRegFreeCom>true</EnableRegFreeCom>` en una etiqueta `<PropertyGroup></PropertyGroup>`.
2. Compile el proyecto.

Ahora el resultado también contendrá un archivo `ProjectName.X.manifest`. Este archivo es el manifiesto en paralelo que se podrá usar con COM sin registro.

## <a name="sample"></a>Ejemplo

Puede encontrar un [ejemplo de servidor COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) totalmente funcional en el repositorio dotnet/samples de GitHub.

## <a name="additional-notes"></a>Notas adicionales

A diferencia de lo que ocurre en .NET Framework, .NET Core no admite la generación de una biblioteca de tipos COM (TLB) a partir de un ensamblado de .NET Core. Tendrá que escribir manualmente un archivo IDL o un encabezado C++ para las declaraciones nativas de las interfaces.

Además, no se admite la carga de .NET Framework y .NET Core en el mismo proceso. Por lo tanto, no se admite la carga de un servidor COM de .NET Core en un proceso de cliente COM de .NET Framework o viceversa.