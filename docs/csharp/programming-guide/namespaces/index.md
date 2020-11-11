---
title: 'Espacios de nombres: Guía de programación de C#'
description: Obtenga información sobre el uso de los espacios de nombres en la programación de C#. Vea información general sobre las propiedades de espacio de nombres y otros recursos.
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 41a666fd5f368e6990e08a36700e18f648939213
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440346"
---
# <a name="namespaces-c-programming-guide"></a>Espacios de nombres (Guía de programación de C#)

Los espacios de nombres se usan mucho en programación de C# de dos maneras. En primer lugar, .NET usa espacios de nombres para organizar sus clases de la siguiente manera:  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<xref:System> es un espacio de nombres y <xref:System.Console> es una clase de ese espacio de nombres. La palabra clave `using` se puede usar para que no se necesite el nombre completo, como en el ejemplo siguiente:

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

Para más información, vea [using (Directiva)](../../language-reference/keywords/using-directive.md).

En segundo lugar, declarar sus propios espacios de nombres puede ayudarle a controlar el ámbito de nombres de clase y método en proyectos de programación grandes. Use la palabra clave [namespace](../../language-reference/keywords/namespace.md) para declarar un espacio de nombres, como en el ejemplo siguiente:

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

El nombre del espacio de nombres debe ser un [nombre de identificador](../inside-a-program/identifier-names.md) de C# válido.

## <a name="namespaces-overview"></a>Información general sobre los espacios de nombres

Los espacios de nombres tienen las propiedades siguientes:

- Organizan proyectos de código de gran tamaño.
- Se delimitan mediante el operador `.`.
- La directiva `using` obvia la necesidad de especificar el nombre del espacio de nombres para cada clase.
- El espacio de nombres `global` es el espacio de nombres "raíz": `global::System` siempre hará referencia al espacio de nombres <xref:System> de .NET.

## <a name="c-language-specification"></a>Especificación del lenguaje C#

Para más información, vea la sección [Espacio de nombres](~/_csharplang/spec/namespaces.md) de la [Especificación del lenguaje C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Vea también

- [Guía de programación de C#](../index.md)
- [Utilizar espacios de nombres](using-namespaces.md)
- [Procedimiento para usar el espacio de nombres My](how-to-use-the-my-namespace.md)
- [Nombres de identificador](../inside-a-program/identifier-names.md)
- [using (directiva)](../../language-reference/keywords/using-directive.md)
- [:: !](../../language-reference/operators/namespace-alias-qualifier.md)
