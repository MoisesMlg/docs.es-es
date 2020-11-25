---
title: Nombres de miembros de tipos
description: Obtenga información sobre las directrices para asignar nombres a los miembros de tipos en .NET como, por ejemplo, métodos, propiedades, eventos y campos.
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 409e881198a359fa28356e22ea73d5b724742a0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706481"
---
# <a name="names-of-type-members"></a>Nombres de miembros de tipos

Los tipos están conformados por miembros: métodos, propiedades, eventos, constructores y campos. En las siguientes secciones se detallan las instrucciones para asignar un nombre a los miembros de tipos.

## <a name="names-of-methods"></a>Nombres de métodos

 Dado que los métodos son medios para emprender una acción, las instrucciones de diseño requieren que los nombres sean verbos o enunciados verbales. Esto también permite distinguir los nombres de métodos de los de propiedades y tipos, que emplean sintagmas nominales o adjetivales.

 ✔️ proporcionan nombres de métodos que son verbos o frases verbales.

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>Nombres de propiedades

 A diferencia de otros miembros, las propiedades deben tener nombres en forma de sintagmas nominales o adjetivales. El motivo es que las propiedades hacen referencia a datos, y el nombre de estas deben reflejarlo adecuadamente. Los nombres de propiedades siempre se escriben con el formato PascalCase, es decir, las palabras se escriben unidas y se diferencian las unas de las otras por el uso de la mayúscula inicial. Este formato también es conocido como CamelCase.

 ✔️ las propiedades de nombre mediante un nombre, una frase o un adjetivo.

 ❌ NO tenga propiedades que coincidan con el nombre de los métodos "Get" como en el ejemplo siguiente:

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 Este patrón suele indicar que la propiedad en realidad debería ser un método.

 ✔️ las propiedades de la colección de nombres con una frase plural que describe los elementos de la colección en lugar de usar una frase singular seguida de "list" o "Collection".

 ✔️ denominar propiedades booleanas con una frase afirmativa ( `CanSeek` en lugar de `CantSeek` ). Opcionalmente, también puede prefijar las propiedades booleanas con "es", "puede" o "tiene", pero solo cuando agrega valor.

 ✔️ considere la posibilidad de asignar a una propiedad el mismo nombre que su tipo.

 Por ejemplo, la propiedad siguiente permite obtener y establecer un valor de enumeración denominado `Color`, de modo que el nombre de la propiedad es `Color`:

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>Nombres de eventos

 Los eventos siempre hacen referencia a algún tipo de acción, ya sea una acción en curso o una ya finalizada. Así pues, como en el caso de los métodos, para los nombres de los eventos se utilizan verbos, y el tiempo verbal permite indicar el momento de la acción.

 ✔️ REALIZAR eventos de nombre con un verbo o una frase verbal.

 Por ejemplo, `Clicked`, `Painting`, `DroppedDown`,etc.

 ✔️ proporcionan nombres de eventos con un concepto de antes y después, con los últimos tiempos actuales y anteriores.

 Por ejemplo, un evento de cierre que tuviera lugar antes de cerrar una ventana se llamaría `Closing`, mientras que uno que lo hiciera después se llamaría `Closed`.

 ❌ No use prefijos "Before" o "after" o posteriores para indicar eventos anteriores y posteriores. Utilice tiempos verbales que indiquen presente y futuro, como se ha explicado.

 ✔️ los controladores de eventos de nombre (delegados usados como tipos de eventos) con el sufijo "EventHandler", como se muestra en el ejemplo siguiente:

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️ utilizan dos parámetros denominados `sender` y `e` en los controladores de eventos.

 El parámetro de envío corresponde al objeto que genera el evento. Este suele ser del tipo `object`, incluso aunque sea posible utilizar un tipo que sea más específico.

 ✔️ las clases de argumento de evento de nombre con el sufijo "EventArgs".

## <a name="names-of-fields"></a>Nombres de campos

 Las instrucciones relativas a la nomenclatura de los campos son aplicables a los campos estáticos públicos y protegidos. En las instrucciones no se abordan los campos internos y privados. Asimismo, las [instrucciones de diseño de miembros](member.md) no permiten los campos de instancias públicas o protegidas.

 ✔️ usar PascalCasing en nombres de campo.

 ✔️ asignar nombres a los campos con un nombre, una frase o un adjetivo.

 ❌ No use un prefijo para los nombres de campo.

 Por ejemplo, no utilice "g_" ni "s_" para indicar campos estáticos.

 *Partes © 2005, 2009 Microsoft Corporation. Todos los derechos reservados.*

 *Material reimpreso con el consentimiento de Pearson Education, Inc. y extraído de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) (Instrucciones de diseño de .NET Framework: convenciones, expresiones y patrones para bibliotecas .NET reutilizables, 2.ª edición), de Krzysztof Cwalina y Brad Abrams, publicado el 22 de octubre de 2008 por Addison-Wesley Professional como parte de la serie Microsoft Windows Development.*

## <a name="see-also"></a>Consulte también

- [Directrices de diseño de marco](index.md)
- [Instrucciones de nomenclatura](naming-guidelines.md)
