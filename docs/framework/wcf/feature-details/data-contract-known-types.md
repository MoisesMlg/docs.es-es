---
title: Tipos conocidos de contratos de datos
description: Obtenga información sobre cómo el modelo de contrato de datos usa la clase KnownTypeAttribute para especificar los tipos que se van a incluir durante la deserialización en WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: 124083d86c220451c55a9290c2edf996b50d8d28
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286687"
---
# <a name="data-contract-known-types"></a><span data-ttu-id="547b1-103">Tipos conocidos de contratos de datos</span><span class="sxs-lookup"><span data-stu-id="547b1-103">Data Contract Known Types</span></span>

<span data-ttu-id="547b1-104">La clase <xref:System.Runtime.Serialization.KnownTypeAttribute> le permite especificar, de antemano, los tipos que deberían tenerse en cuenta durante la deserialización.</span><span class="sxs-lookup"><span data-stu-id="547b1-104">The <xref:System.Runtime.Serialization.KnownTypeAttribute> class allows you to specify, in advance, the types that should be included for consideration during deserialization.</span></span> <span data-ttu-id="547b1-105">Para ver un ejemplo ilustrativo, consulte el ejemplo [Known Types](../samples/known-types.md) .</span><span class="sxs-lookup"><span data-stu-id="547b1-105">For a working example, see the [Known Types](../samples/known-types.md) example.</span></span>  
  
 <span data-ttu-id="547b1-106">Normalmente, al pasar parámetros y valores devueltos entre un cliente y un servicio, ambos extremos comparten todos los contratos de datos de los datos que se van a transmitir.</span><span class="sxs-lookup"><span data-stu-id="547b1-106">Normally, when passing parameters and return values between a client and a service, both endpoints share all of the data contracts of the data to be transmitted.</span></span> <span data-ttu-id="547b1-107">Sin embargo, éste no es el caso en las siguientes circunstancias:</span><span class="sxs-lookup"><span data-stu-id="547b1-107">However, this is not the case in the following circumstances:</span></span>  
  
- <span data-ttu-id="547b1-108">El contrato de datos enviados se deriva del contrato de datos esperados.</span><span class="sxs-lookup"><span data-stu-id="547b1-108">The sent data contract is derived from the expected data contract.</span></span> <span data-ttu-id="547b1-109">Para obtener más información, vea la sección acerca de la herencia en la [equivalencia del contrato de datos](data-contract-equivalence.md).</span><span class="sxs-lookup"><span data-stu-id="547b1-109">For more information, see the section about inheritance in [Data Contract Equivalence](data-contract-equivalence.md)).</span></span> <span data-ttu-id="547b1-110">En ese caso, los datos transmitidos no tienen el mismo contrato de datos que espera el extremo receptor.</span><span class="sxs-lookup"><span data-stu-id="547b1-110">In that case, the transmitted data does not have the same data contract as expected by the receiving endpoint.</span></span>  
  
- <span data-ttu-id="547b1-111">El tipo declarado de la información que se va a transmitir es una interfaz, en lugar de una clase, estructura o enumeración.</span><span class="sxs-lookup"><span data-stu-id="547b1-111">The declared type for the information to be transmitted is an interface, as opposed to a class, structure, or enumeration.</span></span> <span data-ttu-id="547b1-112">En consecuencia, no se puede saber por adelantado qué tipo que implementa la interfaz se envía realmente y, por consiguiente, el extremo receptor no puede determinar de antemano el contrato de datos para los datos transmitidos.</span><span class="sxs-lookup"><span data-stu-id="547b1-112">Therefore, it cannot be known in advance which type that implements the interface is actually sent and therefore, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span>  
  
- <span data-ttu-id="547b1-113">El tipo declarado de la información que se va a transmitir es <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="547b1-113">The declared type for the information to be transmitted is <xref:System.Object>.</span></span> <span data-ttu-id="547b1-114">Puesto que cada tipo hereda de <xref:System.Object>, y no se puede conocer de antemano qué tipo se envía realmente, el extremo receptor no puede determinar de antemano el contrato de datos para los datos transmitidos.</span><span class="sxs-lookup"><span data-stu-id="547b1-114">Because every type inherits from <xref:System.Object>, and it cannot be known in advance which type is actually sent, the receiving endpoint cannot determine in advance the data contract for the transmitted data.</span></span> <span data-ttu-id="547b1-115">Éste es un caso especial del primer elemento: cada contrato de datos se deriva del valor predeterminado, un contrato de datos en blanco que se genera para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="547b1-115">This is a special case of the first item: Every data contract derives from the default, a blank data contract that is generated for <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="547b1-116">Algunos tipos, entre los que se incluyen tipos .NET Framework, tienen miembros que se encuentran en una de las tres categorías anteriores.</span><span class="sxs-lookup"><span data-stu-id="547b1-116">Some types, which include .NET Framework types, have members that are in one of the preceding three categories.</span></span> <span data-ttu-id="547b1-117">Por ejemplo, <xref:System.Collections.Hashtable> utiliza <xref:System.Object> para almacenar los objetos reales en la tabla hash.</span><span class="sxs-lookup"><span data-stu-id="547b1-117">For example, <xref:System.Collections.Hashtable> uses <xref:System.Object> to store the actual objects in the hash table.</span></span> <span data-ttu-id="547b1-118">Al serializar estos tipos, el lado receptor no puede determinar de antemano el contrato de datos de estos miembros.</span><span class="sxs-lookup"><span data-stu-id="547b1-118">When serializing these types, the receiving side cannot determine in advance the data contract for these members.</span></span>  
  
## <a name="the-knowntypeattribute-class"></a><span data-ttu-id="547b1-119">La clase KnownTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="547b1-119">The KnownTypeAttribute Class</span></span>  

 <span data-ttu-id="547b1-120">Cuando los datos llegan a un extremo receptor, el tiempo de ejecución de WCF intenta deserializar los datos en una instancia de un tipo Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="547b1-120">When data arrives at a receiving endpoint, the WCF runtime attempts to deserialize the data into an instance of a common language runtime (CLR) type.</span></span> <span data-ttu-id="547b1-121">El tipo del que se crea una instancia para la deserialización se elige inspeccionando primero el mensaje entrante para determinar el contrato de datos al que se ajusta el contenido del mensaje.</span><span class="sxs-lookup"><span data-stu-id="547b1-121">The type that is instantiated for deserialization is chosen by first inspecting the incoming message to determine the data contract to which the contents of the message conform.</span></span> <span data-ttu-id="547b1-122">El motor de deserialización intenta a continuación encontrar un tipo CLR que implemente un contrato de datos compatible con el contenido del mensaje.</span><span class="sxs-lookup"><span data-stu-id="547b1-122">The deserialization engine then attempts to find a CLR type that implements a data contract compatible with the message contents.</span></span> <span data-ttu-id="547b1-123">El conjunto de tipos de candidatos que admite el motor de deserialización durante este proceso se conoce como el conjunto del deserializador de "tipos conocidos."</span><span class="sxs-lookup"><span data-stu-id="547b1-123">The set of candidate types that the deserialization engine allows for during this process is referred to as the deserializer's set of "known types."</span></span>  
  
 <span data-ttu-id="547b1-124">Una manera de permitir al motor de deserialización saber sobre un tipo consiste en utilizar el <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="547b1-124">One way to let the deserialization engine know about a type is by using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="547b1-125">El atributo no se puede aplicar a miembros de datos individuales, solo a tipos de contrato de datos enteros.</span><span class="sxs-lookup"><span data-stu-id="547b1-125">The attribute cannot be applied to individual data members, only to whole data contract types.</span></span> <span data-ttu-id="547b1-126">El atributo se aplica a un *tipo exterior* que puede ser una clase o una estructura.</span><span class="sxs-lookup"><span data-stu-id="547b1-126">The attribute is applied to an *outer type* that can be a class or a structure.</span></span> <span data-ttu-id="547b1-127">En su uso más básico, al aplicar el atributo, se especifica un tipo como "tipo conocido".</span><span class="sxs-lookup"><span data-stu-id="547b1-127">In its most basic usage, applying the attribute specifies a type as a "known type."</span></span> <span data-ttu-id="547b1-128">Esto hace que el tipo conocido forme parte del conjunto de tipos conocidos siempre que se deserialice un objeto del tipo exterior o cualquier objeto al que se hace referencia a través de sus miembros.</span><span class="sxs-lookup"><span data-stu-id="547b1-128">This causes the known type to be a part of the set of known types whenever an object of the outer type or any object referred to through its members is being deserialized.</span></span> <span data-ttu-id="547b1-129">Se puede aplicar más de un atributo <xref:System.Runtime.Serialization.KnownTypeAttribute> al mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="547b1-129">More than one <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute can be applied to the same type.</span></span>  
  
## <a name="known-types-and-primitives"></a><span data-ttu-id="547b1-130">Tipos conocidos y primitivos</span><span class="sxs-lookup"><span data-stu-id="547b1-130">Known Types and Primitives</span></span>  

 <span data-ttu-id="547b1-131">Los tipos primitivos, así como ciertos tipos tratados como primitivos (como, por ejemplo, <xref:System.DateTime> y <xref:System.Xml.XmlElement>) son siempre “conocidos” y nunca tienen que agregarse mediante este mecanismo.</span><span class="sxs-lookup"><span data-stu-id="547b1-131">Primitive types, as well as certain types treated as primitives (for example, <xref:System.DateTime> and <xref:System.Xml.XmlElement>) are always "known" and never have to be added through this mechanism.</span></span> <span data-ttu-id="547b1-132">Sin embargo, las matrices de tipos primitivos tienen que agregarse explícitamente.</span><span class="sxs-lookup"><span data-stu-id="547b1-132">However, arrays of primitive types have to be added explicitly.</span></span> <span data-ttu-id="547b1-133">La mayoría de las colecciones se consideran equivalentes a las matrices.</span><span class="sxs-lookup"><span data-stu-id="547b1-133">Most collections are considered equivalent to arrays.</span></span> <span data-ttu-id="547b1-134">(Las colecciones no genéricas se consideran equivalentes a las matrices de <xref:System.Object>).</span><span class="sxs-lookup"><span data-stu-id="547b1-134">(Non-generic collections are considered equivalent to arrays of <xref:System.Object>).</span></span> <span data-ttu-id="547b1-135">Para obtener un ejemplo del uso de primitivos, matrices de primitivos y colecciones de primitivos, vea el Ejemplo 4.</span><span class="sxs-lookup"><span data-stu-id="547b1-135">For an example of the using primitives, primitive arrays, and primitive collections, see Example 4.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="547b1-136">A diferencia de otros tipos primitivos, la estructura <xref:System.DateTimeOffset> no es un tipo conocido de forma predeterminada, por lo que debe agregarse manualmente a la lista de tipos conocidos.</span><span class="sxs-lookup"><span data-stu-id="547b1-136">Unlike other primitive types, the <xref:System.DateTimeOffset> structure is not a known type by default, so it must be manually added to the list of known types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="547b1-137">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="547b1-137">Examples</span></span>  

 <span data-ttu-id="547b1-138">En los siguientes ejemplos se muestra la clase <xref:System.Runtime.Serialization.KnownTypeAttribute> en uso.</span><span class="sxs-lookup"><span data-stu-id="547b1-138">The following examples show the <xref:System.Runtime.Serialization.KnownTypeAttribute> class in use.</span></span>  
  
#### <a name="example-1"></a><span data-ttu-id="547b1-139">Ejemplo 1</span><span class="sxs-lookup"><span data-stu-id="547b1-139">Example 1</span></span>  

 <span data-ttu-id="547b1-140">Hay tres clases con una relación de herencia.</span><span class="sxs-lookup"><span data-stu-id="547b1-140">There are three classes with an inheritance relationship.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 <span data-ttu-id="547b1-141">Se puede serializar la siguiente clase `CompanyLogo` , pero no se puede deserializar si el miembro `ShapeOfLogo` está establecido en un objeto `CircleType` o `TriangleType` , porque el motor de deserialización no reconoce ningún tipo con nombres de contrato de datos "Circle" o "Triangle".</span><span class="sxs-lookup"><span data-stu-id="547b1-141">The following `CompanyLogo` class can be serialized, but cannot be deserialized if the `ShapeOfLogo` member is set to either a `CircleType` or a `TriangleType` object, because the deserialization engine does not recognize any types with data contract names "Circle" or "Triangle."</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 <span data-ttu-id="547b1-142">La forma correcta de escribir el tipo `CompanyLogo` se muestra en el siguiente código.</span><span class="sxs-lookup"><span data-stu-id="547b1-142">The correct way to write the `CompanyLogo` type is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 <span data-ttu-id="547b1-143">Cuando quiera que se deserializa el tipo exterior `CompanyLogo2` , el motor de deserialización sabe de `CircleType` y `TriangleType` y, por consiguiente, puede encontrar tipos coincidentes para los contratos de datos "Circle" y "Triangle".</span><span class="sxs-lookup"><span data-stu-id="547b1-143">Whenever the outer type `CompanyLogo2` is being deserialized, the deserialization engine knows about `CircleType` and `TriangleType` and, therefore, is able to find matching types for the "Circle" and "Triangle" data contracts.</span></span>  
  
#### <a name="example-2"></a><span data-ttu-id="547b1-144">Ejemplo 2</span><span class="sxs-lookup"><span data-stu-id="547b1-144">Example 2</span></span>  

 <span data-ttu-id="547b1-145">En el siguiente ejemplo , aunque `CustomerTypeA` y `CustomerTypeB` tienen el contrato de datos `Customer` , se crea una instancia de `CustomerTypeB` siempre que se deserializa una `PurchaseOrder` , porque el motor de deserialización solo conoce al `CustomerTypeB` .</span><span class="sxs-lookup"><span data-stu-id="547b1-145">In the following example, even though both `CustomerTypeA` and `CustomerTypeB` have the `Customer` data contract, an instance of `CustomerTypeB` is created whenever a `PurchaseOrder` is deserialized, because only `CustomerTypeB` is known to the deserialization engine.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a><span data-ttu-id="547b1-146">Ejemplo 3</span><span class="sxs-lookup"><span data-stu-id="547b1-146">Example 3</span></span>  

 <span data-ttu-id="547b1-147">En el siguiente ejemplo, una <xref:System.Collections.Hashtable> almacena internamente su contenido como <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="547b1-147">In the following example, a <xref:System.Collections.Hashtable> stores its contents internally as <xref:System.Object>.</span></span> <span data-ttu-id="547b1-148">Para deserializar correctamente una tabla hash, el motor de deserialización debe conocer el conjunto de tipos posibles que se pueden dar.</span><span class="sxs-lookup"><span data-stu-id="547b1-148">To successfully deserialize a hash table, the deserialization engine must know the set of possible types that can occur there.</span></span> <span data-ttu-id="547b1-149">En este caso, conocemos de antemano que solo los objetos `Book` y `Magazine` se almacenan en `Catalog`, por lo que aquellos se agregan utilizando el atributo <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="547b1-149">In this case, we know in advance that only `Book` and `Magazine` objects are stored in the `Catalog`, so those are added using the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a><span data-ttu-id="547b1-150">Ejemplo 4</span><span class="sxs-lookup"><span data-stu-id="547b1-150">Example 4</span></span>  

 <span data-ttu-id="547b1-151">En el siguiente ejemplo, un contrato de datos almacena un número y una operación que se va a realizar sobre el número.</span><span class="sxs-lookup"><span data-stu-id="547b1-151">In the following example, a data contract stores a number and an operation to perform on the number.</span></span> <span data-ttu-id="547b1-152">El miembro de datos `Numbers` puede ser un entero, una matriz de enteros, o una <xref:System.Collections.Generic.List%601> que contenga enteros.</span><span class="sxs-lookup"><span data-stu-id="547b1-152">The `Numbers` data member can be an integer, an array of integers, or a <xref:System.Collections.Generic.List%601> that contains integers.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="547b1-153">Esto solo funcionará en el lado del cliente si se usa SVCUTIL.EXE para generar un proxy WCF.</span><span class="sxs-lookup"><span data-stu-id="547b1-153">This will only work on the client side if SVCUTIL.EXE is used to generate a WCF proxy.</span></span> <span data-ttu-id="547b1-154">SVCUTIL.EXE recupera metadatos del servicio, incluyendo los tipos conocidos.</span><span class="sxs-lookup"><span data-stu-id="547b1-154">SVCUTIL.EXE retrieves metadata from the service including any known types.</span></span> <span data-ttu-id="547b1-155">Sin esta información, un cliente no podrá deserializar los tipos.</span><span class="sxs-lookup"><span data-stu-id="547b1-155">Without this information a client will not be able to deserialize the types.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 <span data-ttu-id="547b1-156">Éste es el código de aplicación.</span><span class="sxs-lookup"><span data-stu-id="547b1-156">This is the application code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a><span data-ttu-id="547b1-157">Herencia, interfaces y tipos conocidos</span><span class="sxs-lookup"><span data-stu-id="547b1-157">Known Types, Inheritance, and Interfaces</span></span>  

 <span data-ttu-id="547b1-158">Cuando un tipo conocido está asociado a un tipo determinado mediante el atributo `KnownTypeAttribute` , el tipo conocido también está asociado a todos los tipos derivados de ese tipo.</span><span class="sxs-lookup"><span data-stu-id="547b1-158">When a known type is associated with a particular type using the `KnownTypeAttribute` attribute, the known type is also associated with all of the derived types of that type.</span></span> <span data-ttu-id="547b1-159">Por ejemplo, vea el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="547b1-159">For example, see the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 <span data-ttu-id="547b1-160">La clase `DoubleDrawing` no exige al atributo `KnownTypeAttribute` que utilice `Square` y `Circle` en el campo `AdditionalShape` , porque ya se han aplicado esos atributos a la clase base (`Drawing`).</span><span class="sxs-lookup"><span data-stu-id="547b1-160">The `DoubleDrawing` class does not require the `KnownTypeAttribute` attribute to use `Square` and `Circle` in the `AdditionalShape` field, because the base class (`Drawing`) already has these attributes applied.</span></span>  
  
 <span data-ttu-id="547b1-161">Los tipos conocidos solo pueden estar asociados a clases y estructuras, no a interfaces.</span><span class="sxs-lookup"><span data-stu-id="547b1-161">Known types can be associated only with classes and structures, not interfaces.</span></span>  
  
## <a name="known-types-using-open-generic-methods"></a><span data-ttu-id="547b1-162">Tipos conocidos utilizando métodos genéricos abiertos</span><span class="sxs-lookup"><span data-stu-id="547b1-162">Known Types Using Open Generic Methods</span></span>  

 <span data-ttu-id="547b1-163">Puede que sea necesario agregar un tipo genérico como un tipo conocido.</span><span class="sxs-lookup"><span data-stu-id="547b1-163">It may be necessary to add a generic type as a known type.</span></span> <span data-ttu-id="547b1-164">Sin embargo, un tipo genérico abierto no se puede pasar como un parámetro al atributo `KnownTypeAttribute` .</span><span class="sxs-lookup"><span data-stu-id="547b1-164">However, an open generic type cannot be passed as a parameter to the `KnownTypeAttribute` attribute.</span></span>  
  
 <span data-ttu-id="547b1-165">Este problema se puede resolver utilizando un mecanismo alternativo: Escriba un método que devuelva una lista de tipos que se han de agregar a la colección de tipos conocidos.</span><span class="sxs-lookup"><span data-stu-id="547b1-165">This problem can be solved by using an alternative mechanism: Write a method that returns a list of types to add to the known types collection.</span></span> <span data-ttu-id="547b1-166">El nombre del método se especifica a continuación como un argumento de cadena al atributo `KnownTypeAttribute` debido a algunas restricciones.</span><span class="sxs-lookup"><span data-stu-id="547b1-166">The name of the method is then specified as a string argument to the `KnownTypeAttribute` attribute due to some restrictions.</span></span>  
  
 <span data-ttu-id="547b1-167">El método debe existir en el tipo al que se aplica el atributo `KnownTypeAttribute` , debe ser estático, no debe aceptar parámetros y debe devolver un objeto que se pueda asignar a <xref:System.Collections.IEnumerable> de <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="547b1-167">The method must exist on the type to which the `KnownTypeAttribute` attribute is applied, must be static, must accept no parameters, and must return an object that can be assigned to <xref:System.Collections.IEnumerable> of <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="547b1-168">No puede combinar el atributo `KnownTypeAttribute` con un nombre de método y atributos `KnownTypeAttribute` con tipos reales en el mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="547b1-168">You cannot combine the `KnownTypeAttribute` attribute with a method name and `KnownTypeAttribute` attributes with actual types on the same type.</span></span> <span data-ttu-id="547b1-169">Es más, no puede aplicar más de un `KnownTypeAttribute` con un nombre de método al mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="547b1-169">Furthermore, you cannot apply more than one `KnownTypeAttribute` with a method name to the same type.</span></span>  
  
 <span data-ttu-id="547b1-170">Vea la siguiente clase.</span><span class="sxs-lookup"><span data-stu-id="547b1-170">See the following class.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 <span data-ttu-id="547b1-171">El campo `theDrawing` contiene instancias de una clase genérica `ColorDrawing` y una clase genérica `BlackAndWhiteDrawing`, las cuales heredan de una clase genérica `Drawing`.</span><span class="sxs-lookup"><span data-stu-id="547b1-171">The `theDrawing` field contains instances of a generic class `ColorDrawing` and a generic class `BlackAndWhiteDrawing`, both of which inherit from a generic class `Drawing`.</span></span> <span data-ttu-id="547b1-172">Normalmente, ambos se deben agregar a los tipos conocidos, pero la siguiente sintaxis no es una sintaxis válida para atributos.</span><span class="sxs-lookup"><span data-stu-id="547b1-172">Normally, both must be added to known types, but the following is not valid syntax for attributes.</span></span>  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 <span data-ttu-id="547b1-173">De este modo, se debe crear un método para devolver estos tipos.</span><span class="sxs-lookup"><span data-stu-id="547b1-173">Thus, a method must be created to return these types.</span></span> <span data-ttu-id="547b1-174">La forma correcta de escribir este tipo, entonces, se muestra en el siguiente código.</span><span class="sxs-lookup"><span data-stu-id="547b1-174">The correct way to write this type, then, is shown in the following code.</span></span>  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a><span data-ttu-id="547b1-175">Maneras adicionales de agregar tipos conocidos</span><span class="sxs-lookup"><span data-stu-id="547b1-175">Additional Ways to Add Known Types</span></span>  

 <span data-ttu-id="547b1-176">Además, los tipos conocidos se pueden agregar a través de un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="547b1-176">Additionally, known types can be added through a configuration file.</span></span> <span data-ttu-id="547b1-177">Esto resulta útil cuando no se controla el tipo que requiere tipos conocidos para la deserialización correcta, como cuando se usan bibliotecas de tipos de terceros con Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="547b1-177">This is useful when you do not control the type that requires known types for proper deserialization, such as when using third-party type libraries with Windows Communication Foundation (WCF).</span></span>  
  
 <span data-ttu-id="547b1-178">En el archivo de configuración siguiente se observa cómo se especifica un tipo conocido en un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="547b1-178">The following configuration file shows how to specify a known type in a configuration file.</span></span>  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 <span data-ttu-id="547b1-179">En el archivo de configuración anterior, se declara que un tipo de contrato de datos denominado `MyCompany.Library.Shape` tiene `MyCompany.Library.Circle` como tipo conocido.</span><span class="sxs-lookup"><span data-stu-id="547b1-179">In the preceding configuration file a data contract type called `MyCompany.Library.Shape` is declared to have `MyCompany.Library.Circle` as a known type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="547b1-180">Vea también</span><span class="sxs-lookup"><span data-stu-id="547b1-180">See also</span></span>

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [<span data-ttu-id="547b1-181">Tipos conocidos</span><span class="sxs-lookup"><span data-stu-id="547b1-181">Known Types</span></span>](../samples/known-types.md)
- [<span data-ttu-id="547b1-182">Equivalencia del contrato de datos</span><span class="sxs-lookup"><span data-stu-id="547b1-182">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="547b1-183">Diseño de contratos de servicios</span><span class="sxs-lookup"><span data-stu-id="547b1-183">Designing Service Contracts</span></span>](../designing-service-contracts.md)
