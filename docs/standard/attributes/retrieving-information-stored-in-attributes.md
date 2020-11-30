---
title: Recuperar información almacenada en atributos
description: Aprenda a recuperar información almacenada en atributos, como en el caso de una instancia de atributo, muchas instancias para el mismo ámbito y muchas instancias para distintos ámbitos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
ms.openlocfilehash: 6ba01fcd23e626354e5f9a2baa914815b61c8332
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701567"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="fba60-103">Recuperar información almacenada en atributos</span><span class="sxs-lookup"><span data-stu-id="fba60-103">Retrieving Information Stored in Attributes</span></span>

<span data-ttu-id="fba60-104">La recuperación de un atributo personalizado es un proceso sencillo.</span><span class="sxs-lookup"><span data-stu-id="fba60-104">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="fba60-105">En primer lugar, declare una instancia del atributo que desea recuperar.</span><span class="sxs-lookup"><span data-stu-id="fba60-105">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="fba60-106">A continuación, utilice el método <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> para inicializar el atributo nuevo en el valor del atributo que desea recuperar.</span><span class="sxs-lookup"><span data-stu-id="fba60-106">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="fba60-107">Una vez inicializado el nuevo atributo, basta con usar sus propiedades para obtener los valores.</span><span class="sxs-lookup"><span data-stu-id="fba60-107">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fba60-108">En este tema se describe cómo recuperar los atributos personalizados del código que se carga en el contexto de ejecución.</span><span class="sxs-lookup"><span data-stu-id="fba60-108">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="fba60-109">Para recuperar los atributos del código que se carga en el contexto de solo reflexión, se debe usar la clase <xref:System.Reflection.CustomAttributeData>, como se muestra en [Cómo: Cargar ensamblados en el contexto de solo reflexión](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="fba60-109">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="fba60-110">En esta sección se describen los siguientes métodos para recuperar atributos:</span><span class="sxs-lookup"><span data-stu-id="fba60-110">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="fba60-111">Recuperar una sola instancia de un atributo</span><span class="sxs-lookup"><span data-stu-id="fba60-111">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="fba60-112">Recuperar varias instancias de un atributo aplicadas al mismo ámbito</span><span class="sxs-lookup"><span data-stu-id="fba60-112">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="fba60-113">Recuperar varias instancias de un atributo aplicadas a diferentes ámbitos</span><span class="sxs-lookup"><span data-stu-id="fba60-113">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>

## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="fba60-114">Recuperar una sola instancia de un atributo</span><span class="sxs-lookup"><span data-stu-id="fba60-114">Retrieving a Single Instance of an Attribute</span></span>  

 <span data-ttu-id="fba60-115">En el ejemplo siguiente, el atributo `DeveloperAttribute` (descrito en la sección anterior) se aplica a la clase `MainApp` en el nivel de clase.</span><span class="sxs-lookup"><span data-stu-id="fba60-115">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="fba60-116">El método `GetAttribute` usa **GetCustomAttribute** para recuperar los valores almacenados en `DeveloperAttribute` en el nivel de clase antes de mostrarlos en la consola.</span><span class="sxs-lookup"><span data-stu-id="fba60-116">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="fba60-117">Este programa muestra el texto siguiente cuando se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="fba60-117">This program displays the following text when executed.</span></span>  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="fba60-118">Si no se encuentra el atributo, el método **GetCustomAttribute** inicializa `MyAttribute` con un valor null.</span><span class="sxs-lookup"><span data-stu-id="fba60-118">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="fba60-119">En este ejemplo se comprueba si en `MyAttribute` se encuentra dicha instancia y notifica al usuario si no se encuentra ningún atributo.</span><span class="sxs-lookup"><span data-stu-id="fba60-119">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="fba60-120">Si `DeveloperAttribute` no se encuentra en el ámbito de clase, aparece el mensaje siguiente en la consola.</span><span class="sxs-lookup"><span data-stu-id="fba60-120">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```console  
The attribute was not found.
```  
  
 <span data-ttu-id="fba60-121">En este ejemplo se da por supuesto que la definición de atributo está en el espacio de nombres actual.</span><span class="sxs-lookup"><span data-stu-id="fba60-121">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="fba60-122">No olvide importar el espacio de nombres en el que reside la definición de atributo si no está en el espacio de nombres actual.</span><span class="sxs-lookup"><span data-stu-id="fba60-122">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>

## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="fba60-123">Recuperar varias instancias de un atributo aplicadas al mismo ámbito</span><span class="sxs-lookup"><span data-stu-id="fba60-123">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  

 <span data-ttu-id="fba60-124">En el ejemplo anterior, la clase para inspeccionar y el atributo específico para buscar se pasan a <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="fba60-124">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="fba60-125">Ese código funciona bien si solo una instancia de un atributo se aplica en el nivel de clase.</span><span class="sxs-lookup"><span data-stu-id="fba60-125">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="fba60-126">Sin embargo, si se aplican varias instancias de un atributo en el mismo nivel de clase, el método **GetCustomAttribute** no recupera toda la información.</span><span class="sxs-lookup"><span data-stu-id="fba60-126">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="fba60-127">En casos donde se aplican varias instancias del mismo atributo al mismo ámbito, puede usar <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> para colocar todas las instancias de un atributo en una matriz.</span><span class="sxs-lookup"><span data-stu-id="fba60-127">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="fba60-128">Por ejemplo, si dos instancias de `DeveloperAttribute` se aplican en el nivel de clase de la misma clase, el método `GetAttribute` se puede modificar para mostrar la información encontrada en ambos atributos.</span><span class="sxs-lookup"><span data-stu-id="fba60-128">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="fba60-129">Recuerde que, para aplicar varios atributos en el mismo nivel, el atributo debe definirse con la propiedad **AllowMultiple** establecida en **true** en <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fba60-129">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="fba60-130">En el ejemplo de código siguiente, se muestra cómo utilizar el método **GetCustomAttributes** para crear una matriz que haga referencia a todas las instancias de `DeveloperAttribute` en cualquier clase específica.</span><span class="sxs-lookup"><span data-stu-id="fba60-130">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="fba60-131">Los valores de todos los atributos, a continuación, se muestran en la consola.</span><span class="sxs-lookup"><span data-stu-id="fba60-131">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="fba60-132">Si no se encuentra ningún atributo, este código avisa al usuario.</span><span class="sxs-lookup"><span data-stu-id="fba60-132">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="fba60-133">En caso contrario, se muestra la información contenida en ambas instancias de `DeveloperAttribute`.</span><span class="sxs-lookup"><span data-stu-id="fba60-133">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>

## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="fba60-134">Recuperar varias instancias de un atributo aplicadas a diferentes ámbitos</span><span class="sxs-lookup"><span data-stu-id="fba60-134">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  

 <span data-ttu-id="fba60-135">Los métodos <xref:System.Attribute.GetCustomAttributes%2A> y <xref:System.Attribute.GetCustomAttribute%2A> no buscan una clase completa y devuelven todas las instancias de un atributo de esa clase.</span><span class="sxs-lookup"><span data-stu-id="fba60-135">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="fba60-136">En su lugar, buscan solo un método especificado o un miembro a la vez.</span><span class="sxs-lookup"><span data-stu-id="fba60-136">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="fba60-137">Si tiene una clase con el mismo atributo aplicado a todos los miembros y desea recuperar los valores de todos los atributos aplicados a dichos miembros, debe proporcionar cada método o miembro individualmente a **GetCustomAttributes** y **GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="fba60-137">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="fba60-138">En el ejemplo de código siguiente se toma una clase como parámetro y busca `DeveloperAttribute` (definido previamente) en el nivel de clase y en todos los métodos individuales de esa clase.</span><span class="sxs-lookup"><span data-stu-id="fba60-138">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="fba60-139">Si no se encuentran instancias de `DeveloperAttribute` en el nivel de método o en el nivel de clase, el método `GetAttribute` notifica al usuario que no se encontraron atributos y muestra el nombre del método o de la clase que no contiene el atributo.</span><span class="sxs-lookup"><span data-stu-id="fba60-139">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="fba60-140">Si se encuentra algún atributo, los campos `Name`, `Level` y `Reviewed` se muestran en la consola.</span><span class="sxs-lookup"><span data-stu-id="fba60-140">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="fba60-141">Puede utilizar los miembros de la clase <xref:System.Type> para obtener los miembros y métodos individuales de la clase pasada.</span><span class="sxs-lookup"><span data-stu-id="fba60-141">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="fba60-142">En este ejemplo primero se consulta el objeto **Type** para obtener información del atributo para el nivel de clase.</span><span class="sxs-lookup"><span data-stu-id="fba60-142">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="fba60-143">A continuación, se utiliza <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> para colocar instancias de todos los métodos en una matriz de objetos <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> para recuperar información del atributo para el nivel del método.</span><span class="sxs-lookup"><span data-stu-id="fba60-143">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="fba60-144">También puede usar el método <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> para comprobar los atributos en el nivel de propiedad o <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> para comprobar los atributos en el nivel de constructor.</span><span class="sxs-lookup"><span data-stu-id="fba60-144">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba60-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="fba60-145">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fba60-146">Atributos</span><span class="sxs-lookup"><span data-stu-id="fba60-146">Attributes</span></span>](index.md)
