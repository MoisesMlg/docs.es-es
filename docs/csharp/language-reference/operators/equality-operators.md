---
title: 'Operadores de igualdad: referencia de C#'
description: Obtenga más información sobre los operadores de comparación de igualdad de C# y el tipo de igualdad de C#.
ms.date: 10/30/2020
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 39461157c33fea0effb5c8808ded1c9981900e17
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063220"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="42d91-103">Operadores de igualdad (referencia de C#)</span><span class="sxs-lookup"><span data-stu-id="42d91-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="42d91-104">Los operadores [`==` (igualdad)](#equality-operator-) y [`!=` (desigualdad)](#inequality-operator-) comprueban si los operandos son iguales.</span><span class="sxs-lookup"><span data-stu-id="42d91-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="42d91-105">Operador de igualdad ==</span><span class="sxs-lookup"><span data-stu-id="42d91-105">Equality operator ==</span></span>

<span data-ttu-id="42d91-106">El operador de igualdad `==` devuelve `true` si sus operandos son iguales; en caso contrario, devuelve `false`.</span><span class="sxs-lookup"><span data-stu-id="42d91-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="42d91-107">Igualdad entre tipos de valor</span><span class="sxs-lookup"><span data-stu-id="42d91-107">Value types equality</span></span>

<span data-ttu-id="42d91-108">Los operandos de los [tipos de valor integrados](../builtin-types/value-types.md#built-in-value-types) son iguales si sus valores son iguales:</span><span class="sxs-lookup"><span data-stu-id="42d91-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="42d91-109">Para los operadores `==`, [`<`, `>`, `<=` y `>=`](comparison-operators.md), si cualquier operando no es un número (<xref:System.Double.NaN?displayProperty=nameWithType> o <xref:System.Single.NaN?displayProperty=nameWithType>), el resultado del operador será `false`.</span><span class="sxs-lookup"><span data-stu-id="42d91-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="42d91-110">Esto significa que el valor `NaN` no es mayor, inferior ni igual que cualquier otro valor `double` o `float`, incluido `NaN`.</span><span class="sxs-lookup"><span data-stu-id="42d91-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="42d91-111">Para obtener más información y ejemplos, vea el artículo de referencia <xref:System.Double.NaN?displayProperty=nameWithType> o <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42d91-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="42d91-112">Dos operandos del mismo tipo [enum](../builtin-types/enum.md) son iguales si los valores correspondientes del tipo entero subyacente son iguales.</span><span class="sxs-lookup"><span data-stu-id="42d91-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="42d91-113">Los tipos [struct](../builtin-types/struct.md) definidos por el usuario no son compatibles con el operador `==` de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="42d91-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="42d91-114">Para admitir el operador `==`, un elemento struct definido por el usuario debe [sobrecargarlo](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="42d91-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="42d91-115">A partir de C# 7.3, los operadores `==` y `!=` son compatibles con las [tuplas](../builtin-types/value-tuples.md) de C#.</span><span class="sxs-lookup"><span data-stu-id="42d91-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="42d91-116">Si desea más información, consulte la sección [Igualdad de tupla](../builtin-types/value-tuples.md#tuple-equality) del artículo [Tipos de tupla](../builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="42d91-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="42d91-117">Igualdad entre tipos de referencia</span><span class="sxs-lookup"><span data-stu-id="42d91-117">Reference types equality</span></span>

<span data-ttu-id="42d91-118">De forma predeterminada, dos operandos de tipo de referencia que no son registros son iguales si hacen referencia al mismo objeto:</span><span class="sxs-lookup"><span data-stu-id="42d91-118">By default, two non-record reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="42d91-119">Como se muestra en el ejemplo, el operador `==` es compatible de forma predeterminada con los tipos de referencia definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="42d91-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="42d91-120">Sin embargo, un tipo de referencia puede sobrecargar el operador `==`.</span><span class="sxs-lookup"><span data-stu-id="42d91-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="42d91-121">Si un tipo de referencia sobrecarga el operador `==`, use el método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para comprobar si dos referencias de ese tipo hacen referencia al mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="42d91-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="record-types-equality"></a><span data-ttu-id="42d91-122">Igualdad entre tipos de registro</span><span class="sxs-lookup"><span data-stu-id="42d91-122">Record types equality</span></span>

<span data-ttu-id="42d91-123">Disponibles en C# 9.0 y versiones posteriores, los [tipos de registro](../../whats-new/csharp-9.md#record-types) admiten los operadores `==` y `!=` que, de forma predeterminada, proporcionan semántica de igualdad de valores.</span><span class="sxs-lookup"><span data-stu-id="42d91-123">Available in C# 9.0 and later, [record types](../../whats-new/csharp-9.md#record-types) support the `==` and `!=` operators that by default provide value equality semantics.</span></span> <span data-ttu-id="42d91-124">Es decir, dos operandos de registro son iguales cuando ambos son `null` o los valores correspondientes de todos los campos y las propiedades implementadas de forma automática son iguales.</span><span class="sxs-lookup"><span data-stu-id="42d91-124">That is, two record operands are equal when both of them are `null` or corresponding values of all fields and auto-implemented properties are equal.</span></span>

:::code language="csharp" source="snippets/shared/EqualityOperators.cs" id="RecordTypesEquality":::

<span data-ttu-id="42d91-125">Como se muestra en el ejemplo anterior, en el caso de los miembros de tipo de referencia que no son de registro, se comparan sus valores de referencia, no las instancias a las que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="42d91-125">As the preceding example shows, in case of non-record reference-type members their reference values are compared, not the referenced instances.</span></span>

### <a name="string-equality"></a><span data-ttu-id="42d91-126">Igualdad entre cadenas</span><span class="sxs-lookup"><span data-stu-id="42d91-126">String equality</span></span>

<span data-ttu-id="42d91-127">Dos operandos [string](../builtin-types/reference-types.md#the-string-type) son iguales si ambos son `null`, o bien si las instancias de ambas cadenas tienen la misma longitud y los mismos caracteres en cada posición de caracteres:</span><span class="sxs-lookup"><span data-stu-id="42d91-127">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="42d91-128">Es la comparación de ordinales que distingue entre mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="42d91-128">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="42d91-129">Para obtener más información sobre la comparación de cadenas, vea [Cómo comparar cadenas en C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="42d91-129">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="42d91-130">Igualdad entre delegados</span><span class="sxs-lookup"><span data-stu-id="42d91-130">Delegate equality</span></span>

<span data-ttu-id="42d91-131">Dos operandos de [delegado](../../programming-guide/delegates/index.md) con el mismo tipo de entorno de ejecución son iguales cuando ambos son `null`, o bien cuando sus listas de invocación tienen la misma longitud y las mismas entradas en cada posición:</span><span class="sxs-lookup"><span data-stu-id="42d91-131">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="42d91-132">Para obtener más información, vea la sección sobre los [operadores de igualdad entre delegados](~/_csharplang/spec/expressions.md#delegate-equality-operators) de la [Especificación del lenguaje C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="42d91-132">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="42d91-133">Los delegados que se producen mediante la evaluación de [expresiones lambda](lambda-expressions.md) semánticamente idénticas no son iguales, tal como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="42d91-133">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="42d91-134">Operador de desigualdad !=</span><span class="sxs-lookup"><span data-stu-id="42d91-134">Inequality operator !=</span></span>

<span data-ttu-id="42d91-135">El operador de desigualdad (`!=`) devuelve `true` si sus operandos son iguales; en caso contrario, devuelve `false`.</span><span class="sxs-lookup"><span data-stu-id="42d91-135">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="42d91-136">Para los operandos de los [tipos integrados](../builtin-types/built-in-types.md), la expresión `x != y` genera el mismo resultado que la expresión `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="42d91-136">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="42d91-137">Para obtener más información sobre la igualdad de tipos, vea la sección [Operador de igualdad](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="42d91-137">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="42d91-138">En el siguiente ejemplo se muestra el uso del operador `!=`:</span><span class="sxs-lookup"><span data-stu-id="42d91-138">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="42d91-139">Posibilidad de sobrecarga del operador</span><span class="sxs-lookup"><span data-stu-id="42d91-139">Operator overloadability</span></span>

<span data-ttu-id="42d91-140">Un tipo definido por el usuario puede [sobrecargar](operator-overloading.md) los operadores `==` y `!=`.</span><span class="sxs-lookup"><span data-stu-id="42d91-140">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="42d91-141">Si un tipo sobrecarga uno de los dos operadores, también debe sobrecargar el otro.</span><span class="sxs-lookup"><span data-stu-id="42d91-141">If a type overloads one of the two operators, it must also overload the other one.</span></span>

<span data-ttu-id="42d91-142">Un tipo de registro no puede sobrecargar de forma explícita los operadores `==` y `!=`.</span><span class="sxs-lookup"><span data-stu-id="42d91-142">A record type cannot explicitly overload the `==` and `!=` operators.</span></span> <span data-ttu-id="42d91-143">Si tiene que cambiar el comportamiento de los operadores `==` y `!=` para el tipo de registro `T`, implemente el método <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> con la signatura siguiente:</span><span class="sxs-lookup"><span data-stu-id="42d91-143">If you need to change the behavior of the `==` and `!=` operators for record type `T`, implement the <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> method with the following signature:</span></span>

```csharp
public virtual bool Equals(T? other);
```

## <a name="c-language-specification"></a><span data-ttu-id="42d91-144">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="42d91-144">C# language specification</span></span>

<span data-ttu-id="42d91-145">Para obtener más información, vea la sección [Operadores de comprobación de tipos y relacionales](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [Especificación del lenguaje de C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="42d91-145">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="42d91-146">Para obtener más información sobre la igualdad de los tipos de registro, vea la sección [Miembros de igualdad](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) de la [nota de propuesta de características de registros](~/_csharplang/proposals/csharp-9.0/records.md).</span><span class="sxs-lookup"><span data-stu-id="42d91-146">For more information about equality of record types, see the [Equality members](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) section of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42d91-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="42d91-147">See also</span></span>

- [<span data-ttu-id="42d91-148">Referencia de C#</span><span class="sxs-lookup"><span data-stu-id="42d91-148">C# reference</span></span>](../index.md)
- [<span data-ttu-id="42d91-149">Operadores y expresiones de C#</span><span class="sxs-lookup"><span data-stu-id="42d91-149">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="42d91-150">Comparaciones de igualdad</span><span class="sxs-lookup"><span data-stu-id="42d91-150">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="42d91-151">Operadores de comparación</span><span class="sxs-lookup"><span data-stu-id="42d91-151">Comparison operators</span></span>](comparison-operators.md)
