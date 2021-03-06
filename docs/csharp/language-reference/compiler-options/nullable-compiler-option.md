---
description: -nullable (opciones del compilador de C#)
title: -nullable (opciones del compilador de C#)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: 68857d0cb4d0cd1177506e0b7ce897d2cfc3aa5b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099229"
---
# <a name="-nullable-c-compiler-options"></a>-nullable (opciones del compilador de C#)

La opción **-nullable** le permite especificar el contexto que admite un valor NULL.

## <a name="syntax"></a>Sintaxis

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Argumentos

`+` &#124; `-`  
Si se especifica `+`, o bien **-nullable**, el compilador habilita el contexto que admite un valor NULL. Si se especifica `-`, que se aplica si no se especifica **-nullable**, se deshabilita el contexto que admite un valor NULL.

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
Especifica la opción de contexto que admite un valor NULL. Es similar a `+` o `-` en cuanto a habilitación y deshabilitación, pero permite una mayor granularidad de la especificidad del contexto que admite un valor NULL. El argumento `enable`, que se aplica del mismo modo que al especificar **-nullable**, habilita el contexto que admite un valor NULL. Si se especifica `disable`, se deshabilitará el contexto que admite un valor NULL. Al proporcionar el argumento `warnings`, **-nullable:warnings**, se habilita el contexto de advertencia que admite un valor NULL. Al especificar el argumento `annotations`, **-nullable:warnings**, se habilita el contexto de anotación que admite un valor NULL.

## <a name="remarks"></a>Comentarios

El análisis de flujo se utiliza para inferir la nulabilidad de las variables del código ejecutable. La nulabilidad inferida de una variable es independiente de la nulabilidad declarada de dicha variable. Las llamadas de método se analizan incluso cuando se omiten de forma condicional. Es el caso de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> en modo de versión.

La invocación de métodos anotados con los siguientes atributos también afectará al análisis de flujo:

- Condiciones previas simples: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> y <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Condiciones posteriores simples: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> y <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Condiciones posteriores condicionales: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> y <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (por ejemplo, `DoesNotReturnIf(false)` para <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) y <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Condiciones posteriores de miembros: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> y <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

> [!IMPORTANT]
> El contexto global que admite un valor NULL no se aplica a los archivos de código generado. Con independencia de este valor, el contexto que admite un valor NULL está *deshabilitado* para cualquier archivo de código fuente marcado como generado. Hay cuatro maneras de marcar un archivo como generado:
>
> 1. En el archivo .editorconfig, especifique `generated_code = true` en una sección que se aplique a ese archivo.
> 1. Coloque `<auto-generated>` o `<auto-generated/>` en un comentario en la parte superior del archivo. Puede estar en cualquier línea de ese comentario, pero el bloque de comentario debe ser el primer elemento del archivo.
> 1. Inicie el nombre de archivo con *TemporaryGeneratedFile_*
> 1. Finalice el nombre de archivo con *.designer.cs*, *.generated.cs*, *.g.cs* o *.g.i.cs*.
>
> Los generadores pueden optar por usar la directiva de preprocesador [`#nullable`](../preprocessor-directives/preprocessor-nullable.md).

### <a name="to-set-this-compiler-option-in-a-project"></a>Cómo establecer esta opción del compilador en un proyecto

Edite el archivo *.csproj* para agregar la etiqueta `<Nullable>` dentro de una jerarquía `Project/PropertyGroup`:

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Vea también

- [Opciones del compilador de C#](./index.md)
- [Directiva de preprocesador `#nullable`](../preprocessor-directives/preprocessor-nullable.md)
- [Tipos de referencia que aceptan valores null](../../nullable-references.md)
