---
title: 'Funciones locales: Guía de programación de C#'
description: En C#, las funciones locales son métodos privados que están anidados en otro miembro y se pueden llamar desde su miembro contenedor.
ms.date: 10/09/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: a2d389c8b1c687dc4885004fcdc33e0ed7ada977
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955686"
---
# <a name="local-functions-c-programming-guide"></a>Funciones locales (Guía de programación de C#)

A partir de C# 7.0, C# admite *funciones locales*. Las funciones locales son métodos privados de un tipo que están anidados en otro miembro. Solo se pueden llamar desde su miembro contenedor. Las funciones locales se pueden declarar en y llamar desde:

- Métodos, especialmente los métodos de iterador y asincrónicos
- Constructores
- Descriptores de acceso de propiedad
- Descriptores de acceso de un evento
- Métodos anónimos
- Expresiones lambda
- Finalizadores
- Otras funciones locales

En cambio, las funciones locales no se pueden declarar dentro de un miembro con forma de expresión.

> [!NOTE]
> En algunos casos, puede usar una expresión lambda para implementar funcionalidad compatible también con una función local. Para ver una comparación, consulte [Funciones locales frente a expresiones lambda](#local-functions-vs-lambda-expressions).

Las funciones locales aclaran la intención del código. Cualquiera que lea el código puede ver que solo el método que lo contiene puede llamar al método. Para los proyectos de equipo, también hacen que sea imposible que otro desarrollador llame erróneamente al método de forma directa desde cualquier otro punto de la clase o estructura.

## <a name="local-function-syntax"></a>Sintaxis de función local

Una función local se define como un método anidado dentro de un miembro contenedor. Su definición tiene la siguiente sintaxis:

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

Puede usar los siguientes modificadores con una función local:

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- [`static`](../../language-reference/keywords/static.md) (en C# 8.0 y posterior). Una función local estática no puede capturar variables locales o el estado de la instancia.
- [`extern`](../../language-reference/keywords/extern.md) (en C# 9.0 y posterior). Una función local externa debe ser `static`.

Todas las variables locales que se definen en el miembro contenedor, incluidos sus parámetros de método, son accesibles en la función local no estática.

A diferencia de una definición de método, una definición de función local no puede incluir el modificador de acceso de los miembros. Dado que todas las funciones locales son privadas, incluido un modificador de acceso, como la palabra clave `private`, se genera el error del compilador CS0106, "El modificador 'private' no es válido para este elemento".

En el ejemplo siguiente, se define una función local denominada `AppendPathSeparator` que es privada a un método denominado `GetText`:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

A partir de C# 9.0, puede aplicar atributos a una función local, sus parámetros y parámetros de tipo, como se muestra en el ejemplo siguiente:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

En el ejemplo anterior se usa un [atributo especial](../../language-reference/attributes/nullable-analysis.md) para ayudar al compilador en el análisis estático en un contexto que acepta valores NULL.

## <a name="local-functions-and-exceptions"></a>Excepciones y funciones locales

Una de las características útiles de las funciones locales es que pueden permitir que las excepciones aparezcan inmediatamente. Para los iteradores de método, las excepciones aparecen solo cuando la secuencia devuelta se enumera y no cuando se recupera el iterador. Para los métodos asincrónicos, las excepciones producidas en un método asincrónico se observan cuando se espera la tarea devuelta.

En el ejemplo siguiente se define un método `OddSequence` que enumera los números impares de un intervalo especificado. Dado que pasa un número mayor de 100 al método de enumerador `OddSequence`, el método produce una excepción <xref:System.ArgumentOutOfRangeException>. Como se muestra en el resultado del ejemplo, la excepción aparece solo cuando itera los números, y no al recuperar el enumerador.

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

Si coloca la lógica de iterador en una función local, se iniciarán excepciones de validación de argumentos al recuperar el enumerador, como se muestra en el ejemplo siguiente:

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

Puede usar funciones locales de una manera similar con las operaciones asincrónicas. Las excepciones iniciadas en un método asincrónico aparecen cuando se espera por la tarea correspondiente. Las funciones locales permiten que el código genere un error inmediato y permiten que la excepción se produzca y observe de forma sincrónica.

En el ejemplo siguiente, se usa un método asincrónico denominado `GetMultipleAsync` para pausar durante un número especificado de segundos y se devuelve un valor que es un múltiplo aleatorio de ese número de segundos. El retraso máximo es de 5 segundos; se produce una excepción <xref:System.ArgumentOutOfRangeException> si el valor es mayor que 5. Como se muestra en el ejemplo siguiente, la excepción que se inicia cuando se pasa un valor de 6 al método `GetMultipleAsync` solo se observa cuando se espera por la tarea.

:::code language="csharp" source="snippets/local-functions/AsyncWithoutLocal.cs" :::

Como sucede con el método de iterador, puede refactorizar el ejemplo anterior y colocar el código de la operación asincrónica en una función local. Como se muestra en la salida del ejemplo siguiente, al llamar al método `GetMultiple` se inicia la excepción <xref:System.ArgumentOutOfRangeException>.

:::code language="csharp" source="snippets/local-functions/AsyncWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a>Funciones locales frente a expresiones lambda

A primera vista, las funciones locales y las [expresiones lambda](../../language-reference/operators/lambda-expressions.md) son muy similares. En muchos casos, la elección entre usar expresiones lambda y funciones locales es una cuestión de estilo y de preferencia personal, aunque hay diferencias que debe tener en cuenta acerca de dónde puede usar una u otra.

Vamos a examinar las diferencias entre las implementaciones de la función local y la expresión lambda del algoritmo factorial. Primero la versión que usa una función local:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

Compare esa implementación con una versión que use expresiones lambda:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

Las funciones locales tienen nombres, mientras que las expresiones lambda son métodos anónimos que se asignan a variables que son tipos `Func` o `Action`. Cuando se declara una función local, los tipos de argumento y el tipo de valor devuelto forman parte de la declaración de función. En lugar de formar parte del cuerpo de la expresión lambda, los tipos de argumento y el tipo de valor devuelto forman parte de la declaración de tipo de variable de la expresión lambda. Estas dos diferencias pueden hacer que el código sea más claro.

Las funciones locales tienen reglas diferentes de las expresiones lambda para la asignación definitiva. Se puede hacer referencia a una declaración de función local desde cualquier ubicación del código que esté dentro del ámbito. Las expresiones lambda se deben asignar a una variable de delegado para poder acceder a ellas (o para poder llamarlas mediante el delegado que hace referencia a ellas). Observe que la versión con la expresión lambda debe declarar e inicializar la expresión lambda, `nthFactorial`, antes de definirla. De no hacerlo, se produce un error en tiempo de compilación por hacer referencia a `nthFactorial` antes de asignarlo. Estas diferencias implican que los algoritmos recursivos son más fáciles de crear usando funciones locales. Puede declarar y definir una función local que se llama a sí misma. Las expresiones lambda se deben declarar y se les debe asignar un valor predeterminado para que se les pueda volver a asignar un cuerpo que haga referencia a la misma expresión lambda.

Las reglas de asignación definitiva también afectan a las variables que se capturan con la función local o la expresión lambda. Tanto las funciones locales como las reglas de expresiones lambda exigen que las variables capturadas se asignen definitivamente en el momento en que la función local o la expresión lambda se convierta en un delegado. La diferencia está en que las expresiones lambda se convierten en delegados en el momento en que se declaran, mientras que las funciones locales se convierten en delegados solo cuando se usan como delegados. Si se declara una función local y solo se hace referencia a ella llamándola como un método, no se convertirá en un delegado. Esta regla le permite declarar una función local en cualquier ubicación adecuada de su ámbito de inclusión. Es habitual declarar funciones locales al final del método principal, después de cualquier instrucción "return".

En tercer lugar, el compilador puede efectuar un análisis estático que permita que las funciones locales asignen definitivamente variables capturadas en el ámbito de inclusión. Considere este ejemplo:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

El compilador puede determinar que `LocalFunction` asigna `y` definitivamente cuando se le llama. Como se llama a `LocalFunction` antes de la instrucción `return`, `y` se asigna definitivamente en la instrucción `return`.

El análisis que proporciona el análisis de ejemplo posibilita la cuarta diferencia. Dependiendo de su uso, las funciones locales pueden evitar las asignaciones de montón que siempre son necesarias para las expresiones lambda. Si una función local no se convierte nunca en un delegado y ninguna de las variables capturadas con la función local se captura con otras expresiones lambda o funciones locales que se han convertido en delegados, el compilador puede evitar las asignaciones de montón.

Considere este ejemplo asincrónico:

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

La clausura de esta expresión lambda contiene las variables `address`, `index` y `name`. En el caso de las funciones locales, el objeto que implementa el cierre puede ser un tipo `struct`. Luego, ese tipo de estructura se pasaría por referencia a la función local. Esta diferencia de implementación supondría un ahorro en una asignación.

La creación de instancias necesaria para las expresiones lambda significa asignaciones de memoria adicionales, lo que puede ser un factor de rendimiento en rutas de acceso de código crítico en el tiempo. Las funciones locales no suponen esta sobrecarga. En el ejemplo anterior, la versión de las funciones locales tiene dos asignaciones menos que la versión de la expresión lambda.

> [!NOTE]
> La función local equivalente de este método también usa una clase para el cierre. Si el cierre de una función local se implementa como `class` o `struct` es un detalle de implementación. Una función local puede usar `struct` mientras una expresión lambda siempre usará `class`.

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

Una ventaja final que no se muestra en este ejemplo es que las funciones locales pueden implementarse como iteradores, con la sintaxis `yield return` para producir una secuencia de valores. La instrucción `yield return` no está permitida en las expresiones lambda.

Aunque las funciones locales pueden parecer redundantes con respecto a las expresiones lambda, en realidad tienen finalidades y usos diferentes. Las funciones locales son más eficaces si se quiere escribir una función a la que solo se llame desde el contexto de otro método.

## <a name="see-also"></a>Vea también

- [Métodos](methods.md)
