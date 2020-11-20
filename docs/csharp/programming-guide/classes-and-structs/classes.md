---
title: 'Clases: Guía de programación de C#'
description: Obtenga información sobre los tipos de clases y cómo crearlas
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 8fa8d33ce9ece20a18c5c1542bc44cf569e9fa2e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440411"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="64c90-103">Clases (Guía de programación de C#)</span><span class="sxs-lookup"><span data-stu-id="64c90-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="64c90-104">Tipos de referencia</span><span class="sxs-lookup"><span data-stu-id="64c90-104">Reference types</span></span>  

<span data-ttu-id="64c90-105">Un tipo que se define como una [clase](../../language-reference/keywords/class.md), es un *tipo de referencia*.</span><span class="sxs-lookup"><span data-stu-id="64c90-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="64c90-106">Al declarar una variable de un tipo de referencia en tiempo de ejecución, esta contendrá el valor [null](../../language-reference/keywords/null.md) hasta que se cree expresamente una instancia de la clase mediante el operador [new](../../language-reference/operators/new-operator.md) o se le asigne un objeto de un tipo compatible que se ha creado en otro lugar, tal y como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="64c90-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="64c90-107">Cuando se crea el objeto, se asigna suficiente memoria en el montón administrado para ese objeto específico y la variable solo contiene una referencia a la ubicación de dicho objeto.</span><span class="sxs-lookup"><span data-stu-id="64c90-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="64c90-108">Los tipos del montón administrado producen sobrecarga cuando se asignan y cuando los reclama la función de administración de memoria automática de CLR, conocida como *recolección de elementos no utilizados*.</span><span class="sxs-lookup"><span data-stu-id="64c90-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="64c90-109">En cambio, la recolección de elementos no utilizados también está muy optimizada y no crea problemas de rendimiento en la mayoría de los escenarios.</span><span class="sxs-lookup"><span data-stu-id="64c90-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="64c90-110">Para obtener más información sobre la recolección de elementos no utilizados, vea [Administración automática de la memoria y recolección de elementos no utilizados](../../../standard/garbage-collection/fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/fundamentals.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="64c90-111">Declarar clases</span><span class="sxs-lookup"><span data-stu-id="64c90-111">Declaring Classes</span></span>

 <span data-ttu-id="64c90-112">Las clases se declaran mediante la palabra clave [class](../../language-reference/keywords/class.md) seguida por un identificador único, como se muestra en el siguiente ejemplo:</span><span class="sxs-lookup"><span data-stu-id="64c90-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="64c90-113">La palabra clave `class` va precedida del nivel de acceso.</span><span class="sxs-lookup"><span data-stu-id="64c90-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="64c90-114">Como en este caso se usa [public](../../language-reference/keywords/public.md), cualquier usuario puede crear instancias de esta clase.</span><span class="sxs-lookup"><span data-stu-id="64c90-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="64c90-115">El nombre de la clase sigue a la palabra clave `class`.</span><span class="sxs-lookup"><span data-stu-id="64c90-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="64c90-116">El nombre de la clase debe ser un [nombre de identificador](../inside-a-program/identifier-names.md) de C# válido.</span><span class="sxs-lookup"><span data-stu-id="64c90-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="64c90-117">El resto de la definición es el cuerpo de la clase, donde se definen los datos y el comportamiento.</span><span class="sxs-lookup"><span data-stu-id="64c90-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="64c90-118">Los campos, las propiedades, los métodos y los eventos de una clase se denominan de manera colectiva *miembros de clase*.</span><span class="sxs-lookup"><span data-stu-id="64c90-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="64c90-119">Creación de objetos</span><span class="sxs-lookup"><span data-stu-id="64c90-119">Creating objects</span></span>

<span data-ttu-id="64c90-120">Aunque a veces se usan indistintamente, una clase y un objeto son cosas diferentes.</span><span class="sxs-lookup"><span data-stu-id="64c90-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="64c90-121">Una clase define un tipo de objeto, pero no es un objeto en sí.</span><span class="sxs-lookup"><span data-stu-id="64c90-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="64c90-122">Un objeto es una entidad concreta basada en una clase y, a veces, se conoce como una instancia de una clase.</span><span class="sxs-lookup"><span data-stu-id="64c90-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="64c90-123">Los objetos se pueden crear usando la palabra clave [new](../../language-reference/operators/new-operator.md), seguida del nombre de la clase en la que se basará el objeto, como en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="64c90-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="64c90-124">Cuando se crea una instancia de una clase, se vuelve a pasar al programador una referencia al objeto.</span><span class="sxs-lookup"><span data-stu-id="64c90-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="64c90-125">En el ejemplo anterior, `object1` es una referencia a un objeto que se basa en `Customer`.</span><span class="sxs-lookup"><span data-stu-id="64c90-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="64c90-126">Esta referencia apunta al objeto nuevo, pero no contiene los datos del objeto.</span><span class="sxs-lookup"><span data-stu-id="64c90-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="64c90-127">De hecho, puede crear una referencia de objeto sin tener que crear ningún objeto:</span><span class="sxs-lookup"><span data-stu-id="64c90-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="64c90-128">No se recomienda crear referencias de objeto como esta, que no hace referencia a ningún objeto, ya que, si se intenta obtener acceso a un objeto a través de este tipo de referencia, se producirá un error en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="64c90-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="64c90-129">Pero este tipo de referencia se puede haber creado para hacer referencia a un objeto, ya sea creando uno o asignándola a un objeto existente, como en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="64c90-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="64c90-130">Este código crea dos referencias de objeto que hacen referencia al mismo objeto.</span><span class="sxs-lookup"><span data-stu-id="64c90-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="64c90-131">Por lo tanto, los cambios efectuados en el objeto mediante `object3` se reflejan en los usos posteriores de `object4`.</span><span class="sxs-lookup"><span data-stu-id="64c90-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="64c90-132">Dado que los objetos basados en clases se tratan por referencia, las clases se denominan "tipos de referencia".</span><span class="sxs-lookup"><span data-stu-id="64c90-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="64c90-133">Herencia de clases</span><span class="sxs-lookup"><span data-stu-id="64c90-133">Class inheritance</span></span>  

<span data-ttu-id="64c90-134">Las clases admiten completamente la *herencia*, una característica fundamental de la programación orientada a objetos.</span><span class="sxs-lookup"><span data-stu-id="64c90-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="64c90-135">Al crear una clase, puede heredar de cualquier otra que no esté definida como [sellada](../../language-reference/keywords/sealed.md), y otras clases pueden heredar de esa e invalidar sus métodos virtuales.</span><span class="sxs-lookup"><span data-stu-id="64c90-135">When you create a class, you can inherit from any other class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span> <span data-ttu-id="64c90-136">Además, puede implementar una o varias interfaces.</span><span class="sxs-lookup"><span data-stu-id="64c90-136">Furthermore, you can implement one or more interfaces.</span></span>

<span data-ttu-id="64c90-137">La herencia se consigue mediante una *derivación*, en la que se declara una clase mediante una *clase base*, desde la que hereda los datos y el comportamiento.</span><span class="sxs-lookup"><span data-stu-id="64c90-137">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="64c90-138">Una clase base se especifica anexando dos puntos y el nombre de la clase base seguido del nombre de la clase derivada, como en el siguiente ejemplo:</span><span class="sxs-lookup"><span data-stu-id="64c90-138">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="64c90-139">Cuando una clase declara una clase base, hereda todos los miembros de la clase base excepto los constructores.</span><span class="sxs-lookup"><span data-stu-id="64c90-139">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="64c90-140">Para obtener más información, vea [Herencia](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-140">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="64c90-141">A diferencia de C++, una clase de C# solo puede heredar directamente de una clase base.</span><span class="sxs-lookup"><span data-stu-id="64c90-141">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="64c90-142">En cambio, dado que una clase base puede heredar de otra clase, una clase podría heredar indirectamente varias clases base.</span><span class="sxs-lookup"><span data-stu-id="64c90-142">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="64c90-143">Además, una clase puede implementar directamente una o varias interfaces.</span><span class="sxs-lookup"><span data-stu-id="64c90-143">Furthermore, a class can directly implement one or more interfaces.</span></span> <span data-ttu-id="64c90-144">Para obtener más información, vea [Interfaces](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-144">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="64c90-145">Una clase puede declararse [abstracta](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-145">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="64c90-146">Una clase abstracta contiene métodos abstractos que tienen una definición de firma, pero no tienen ninguna implementación.</span><span class="sxs-lookup"><span data-stu-id="64c90-146">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="64c90-147">No se pueden crear instancias de las clases abstractas.</span><span class="sxs-lookup"><span data-stu-id="64c90-147">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="64c90-148">Solo se pueden usar a través de las clases derivadas que implementan los métodos abstractos.</span><span class="sxs-lookup"><span data-stu-id="64c90-148">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="64c90-149">Por el contrario, la clase [sealed](../../language-reference/keywords/sealed.md) no permite que otras clases se deriven de ella.</span><span class="sxs-lookup"><span data-stu-id="64c90-149">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="64c90-150">Para más información, vea [Clases y miembros de clase abstractos y sellados](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-150">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="64c90-151">Las definiciones de clase se pueden dividir entre distintos archivos de código fuente.</span><span class="sxs-lookup"><span data-stu-id="64c90-151">Class definitions can be split between different source files.</span></span> <span data-ttu-id="64c90-152">Para más información, vea [Clases y métodos parciales](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-152">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64c90-153">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="64c90-153">Example</span></span>

<span data-ttu-id="64c90-154">En el ejemplo siguiente se define una clase pública que contiene una [propiedad implementada automáticamente](auto-implemented-properties.md), un método y un método especial denominado constructor.</span><span class="sxs-lookup"><span data-stu-id="64c90-154">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="64c90-155">Para obtener más información, consulta los temas [Propiedades](properties.md), [Métodos](methods.md) y [Constructores](constructors.md).</span><span class="sxs-lookup"><span data-stu-id="64c90-155">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="64c90-156">Luego, se crea una instancia de las instancias de la clase con la palabra clave `new`.</span><span class="sxs-lookup"><span data-stu-id="64c90-156">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="64c90-157">Especificación del lenguaje C#</span><span class="sxs-lookup"><span data-stu-id="64c90-157">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64c90-158">Vea también</span><span class="sxs-lookup"><span data-stu-id="64c90-158">See also</span></span>

- [<span data-ttu-id="64c90-159">Guía de programación de C#</span><span class="sxs-lookup"><span data-stu-id="64c90-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="64c90-160">Programación orientada a objetos</span><span class="sxs-lookup"><span data-stu-id="64c90-160">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="64c90-161">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="64c90-161">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="64c90-162">Nombres de identificador</span><span class="sxs-lookup"><span data-stu-id="64c90-162">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="64c90-163">Miembros</span><span class="sxs-lookup"><span data-stu-id="64c90-163">Members</span></span>](members.md)
- [<span data-ttu-id="64c90-164">Métodos</span><span class="sxs-lookup"><span data-stu-id="64c90-164">Methods</span></span>](methods.md)
- [<span data-ttu-id="64c90-165">Constructores</span><span class="sxs-lookup"><span data-stu-id="64c90-165">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="64c90-166">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="64c90-166">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="64c90-167">Objects</span><span class="sxs-lookup"><span data-stu-id="64c90-167">Objects</span></span>](objects.md)
