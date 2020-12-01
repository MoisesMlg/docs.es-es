---
title: Procedimiento para compilar un ensamblado de un solo archivo de .NET Framework
description: Explore cómo compilar un ensamblado de un solo archivo en .NET. Un ensamblado de un solo archivo puede ser una biblioteca (.dll) destinada a .NET o puede ser un archivo ejecutable (.exe).
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: bdffa9417a7d52e9c825ca6455997b9bfa7408e4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271530"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Procedimiento para compilar un ensamblado de un solo archivo de .NET Framework

Un ensamblado de único archivo, que es el tipo de ensamblado más sencillo, contiene información y la implementación del tipo, así como el [manifiesto del ensamblado](../../standard/assembly/manifest.md). Puede usar los compiladores de la línea de comandos o Visual Studio para crear un ensamblado de un solo archivo que tenga como destino .NET Framework. De forma predeterminada, el compilador crea un archivo de ensamblado con la extensión *.exe*.

> [!NOTE]
> Visual Studio para C# y Visual Basic solo se pueden usar para crear ensamblados de único archivo. Si desea crear ensamblados de múltiples archivos, debe usar compiladores de la línea de comandos o Visual C++.

En los procedimientos siguientes se muestra cómo crear ensamblados de único archivo mediante los compiladores de la línea de comandos.

## <a name="create-an-assembly-with-an-exe-extension"></a>Creación de un ensamblado con una extensión .exe

En el símbolo del sistema, escriba el siguiente comando:

\<*compiler command*> \<*module name*>

En este comando, *comando de compilador* es el comando del compilador del lenguaje usado en el módulo del código, mientras que *nombre del módulo* es el nombre del módulo del código al compilarlo en el ensamblado.

En el ejemplo siguiente se crea un ensamblado llamado *myCode.exe* desde un módulo de código denominado `myCode`.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Creación de un ensamblado con la extensión .exe y especificar el nombre del archivo de salida

En el símbolo del sistema, escriba el siguiente comando:

\<*compiler command*> **/out:** \<*file name*> \<*module name*>

En este comando, *comando del compilador* es el comando del compilador del lenguaje usado en el módulo del código, *nombre del archivo* es el nombre del archivo de salida y *nombre del módulo* es el nombre del módulo del código al compilarlo en el ensamblado.

En el ejemplo siguiente se crea un ensamblado llamado *myAssembly.exe* desde un módulo de código denominado `myCode`.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Creación de ensamblados de biblioteca

 Los ensamblados de biblioteca se parecen a las bibliotecas de clases. Contiene tipos a los que harán referencia otros ensamblados, pero no tiene ningún punto de entrada para comenzar la ejecución.

En el símbolo del sistema, escriba este comando para crear un ensamblado de biblioteca:

\<*compiler command*> **-t:library** \<*module name*>

En este comando, *comando de compilador* es el comando del compilador del lenguaje usado en el módulo del código, mientras que *nombre del módulo* es el nombre del módulo del código al compilarlo en el ensamblado. También puede usar otras opciones del compilador, como la opción **-out:** .

En el ejemplo siguiente se crea un ensamblado de biblioteca llamado *myCodeAssembly.dll* desde un módulo de código denominado `myCode`.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Vea también

- [Creación de ensamblados](../../standard/assembly/create.md)
- [Ensamblados de varios archivos](multifile-assemblies.md)
- [Cómo: Compilar un ensamblado de varios archivos](build-multifile-assembly.md)
- [Programación con ensamblados](../../standard/assembly/index.md)
