---
description: yield (Palabra clave contextual, Referencia de C#)
title: yield (Palabra clave contextual, Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c8caf7e34397faf9f7085d6634287cffcb37eb08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141886"
---
# <a name="yield-c-reference"></a>yield (Referencia de C#)

Cuando se usa la [palabra clave contextual](index.md#contextual-keywords) `yield` en una instrucción, se indica que el método, el operador o el descriptor de acceso `get` en el que aparece es un iterador. Al usar `yield` para definir un iterador ya no es necesaria una clase adicional explícita (la clase que retiene el estado para una enumeración, consulte <xref:System.Collections.Generic.IEnumerator%601> para ver un ejemplo) al implementar los patrones <xref:System.Collections.IEnumerable> y <xref:System.Collections.IEnumerator> para un tipo de colección personalizado.

En el ejemplo siguiente se muestran las dos formas de la instrucción `yield`.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Comentarios

Utilice una instrucción `yield return` para devolver cada elemento de uno en uno.

La secuencia devuelta desde un método iterador se puede consumir mediante la instrucción [foreach](foreach-in.md) o una consulta LINQ. Cada iteración del bucle `foreach` llama al método iterador. Cuando se alcanza una instrucción `yield return` en el método iterador, se devuelve `expression` y se conserva la ubicación actual en el código. La ejecución se reinicia desde esa ubicación la próxima vez que se llama a la función del iterador.

Puede usar una instrucción `yield break` para finalizar la iteración.

Para obtener más información sobre los iteradores, vea [Iteradores](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Métodos de iterador y descriptores de acceso get

La declaración de un iterador debe cumplir los requisitos siguientes:

- El tipo de valor devuelto debe ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> o <xref:System.Collections.Generic.IEnumerator%601>.

- La declaración no puede tener ningún parámetro [in](in-parameter-modifier.md) [ref](ref.md) o [out](out-parameter-modifier.md).

El tipo `yield` de un iterador que devuelve <xref:System.Collections.IEnumerable> o <xref:System.Collections.IEnumerator> es `object`.  Si el iterador devuelve <xref:System.Collections.Generic.IEnumerable%601> o <xref:System.Collections.Generic.IEnumerator%601>, debe haber una conversión implícita del tipo de la expresión en la instrucción `yield return` al parámetro de tipo genérico.

No puede incluir una instrucción `yield return` ni `yield break` en:

- [Expresiones lambda](../operators/lambda-expressions.md) y [métodos anónimos](../operators/delegate-operator.md).

- Métodos que contienen bloques inseguros. Para obtener más información, vea [unsafe](unsafe.md).

## <a name="exception-handling"></a>Control de excepciones

Una instrucción `yield return` no puede encontrarse en un bloque try-catch. Una instrucción `yield return` puede encontrarse en el bloque try de una instrucción try-finally.

Una instrucción `yield break` puede encontrarse en un bloque try o un bloque catch, pero no en un bloque finally.

Si el cuerpo `foreach` (fuera del método iterador) produce una excepción, se ejecuta un bloque `finally` en el método iterador.

## <a name="technical-implementation"></a>Implementación técnica

El código siguiente devuelve un valor `IEnumerable<string>` desde un método iterador y, a continuación, recorre sus elementos en iteración.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

La llamada a `MyIteratorMethod` no ejecuta el cuerpo del método. En su lugar, la llamada devuelve un valor `IEnumerable<string>` en la variable `elements`.

En una iteración del bucle `foreach`, se llama al método <xref:System.Collections.IEnumerator.MoveNext%2A> para `elements`. Esta llamada ejecuta el cuerpo de `MyIteratorMethod` hasta que se alcanza la siguiente instrucción `yield return`. La expresión devuelta por la instrucción `yield return` determina no solo el valor de la variable `element` para que la utilice el cuerpo del bucle, sino también la propiedad <xref:System.Collections.Generic.IEnumerator%601.Current%2A> de `elements`, que es un valor `IEnumerable<string>`.

En cada iteración subsiguiente del bucle `foreach`, la ejecución del cuerpo del iterador continúa desde donde se dejó, deteniéndose de nuevo al alcanzar una instrucción `yield return`. El bucle `foreach` se completa al alcanzar el fin del método iterador o una instrucción `yield break`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente tiene una instrucción `yield return` que está dentro de un bucle `for`. Cada iteración del cuerpo de instrucción `foreach` en el método `Main` crea una llamada a la función de iterador `Power`. Cada llamada a la función de iterador prosigue con la siguiente ejecución de la instrucción `yield return`, que se produce durante la siguiente iteración del bucle `for`.

El tipo de valor devuelto del método iterador es <xref:System.Collections.IEnumerable>, que es un tipo de interfaz de iteradores. Cuando se llama al método iterador, este devuelve un objeto enumerable que contiene las potencias de un número.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un descriptor de acceso `get` que es un iterador. En el ejemplo, cada una de las instrucciones `yield return` devuelve una instancia de una clase definida por el usuario.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>Especificación del lenguaje C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Vea también

- [Referencia de C#](../index.md)
- [Guía de programación de C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iteradores](../../iterators.md)
