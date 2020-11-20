---
title: Controlar valores Null
description: Obtenga información sobre cómo el proveedor de datos de .NET Framework para SQL Server controla NULL y cómo obtener información sobre NULL y SqlBoolean, la lógica de tres valores y la asignación de valores NULL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2dda65f605ea9de616f01d6e52eb4e0e5def4db7
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982523"
---
# <a name="handling-null-values"></a><span data-ttu-id="7a726-103">Controlar valores Null</span><span class="sxs-lookup"><span data-stu-id="7a726-103">Handling Null Values</span></span>

<span data-ttu-id="7a726-104">Se utiliza un valor NULL en una base de datos relacional cuando el valor de una columna es desconocido o falta.</span><span class="sxs-lookup"><span data-stu-id="7a726-104">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="7a726-105">Un valor NULL no es una cadena vacía (para tipos de datos de caracteres o de fecha y hora) ni un valor cero (para tipos de datos numéricos).</span><span class="sxs-lookup"><span data-stu-id="7a726-105">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="7a726-106">La especificación ANSI SQL-92 indica que un valor NULL debe ser el mismo para todos los tipos de datos, de modo que todos los valores NULL se traten de manera uniforme.</span><span class="sxs-lookup"><span data-stu-id="7a726-106">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="7a726-107">El espacio de nombres <xref:System.Data.SqlTypes> proporciona la semántica de NULL implementando la interfaz <xref:System.Data.SqlTypes.INullable>.</span><span class="sxs-lookup"><span data-stu-id="7a726-107">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="7a726-108">Cada uno de los tipos de datos de <xref:System.Data.SqlTypes> tiene su propia propiedad `IsNull` y un valor `Null` que se puede asignar a una instancia de ese tipo de datos.</span><span class="sxs-lookup"><span data-stu-id="7a726-108">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a726-109">La versión 2,0 de .NET Framework incorporó compatibilidad con tipos de valor que aceptan valores NULL, que permiten a los programadores extender un tipo de valor para representar todos los valores del tipo subyacente.</span><span class="sxs-lookup"><span data-stu-id="7a726-109">The .NET Framework version 2.0 introduced support for nullable value types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="7a726-110">Estos tipos de valor que aceptan valores NULL de CLR representan una instancia de la <xref:System.Nullable> estructura.</span><span class="sxs-lookup"><span data-stu-id="7a726-110">These CLR nullable value types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="7a726-111">Esta funcionalidad es especialmente útil cuando se aplica la conversión boxing y la conversión unboxing de tipos de valor, lo que proporciona compatibilidad mejorada con los tipos de objeto.</span><span class="sxs-lookup"><span data-stu-id="7a726-111">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="7a726-112">Los tipos de valor que aceptan valores NULL de CLR no están diseñados para el almacenamiento de valores NULL de base de datos porque un valor null de ANSI SQL no se comporta de la misma manera que una `null` referencia (o `Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7a726-112">CLR nullable value types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="7a726-113">Para trabajar con valores NULL de ANSI SQL de la base de datos, utilice valores NULL de tipo <xref:System.Data.SqlTypes> en lugar de <xref:System.Nullable>.</span><span class="sxs-lookup"><span data-stu-id="7a726-113">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="7a726-114">Para obtener más información sobre cómo trabajar con tipos que aceptan valores NULL de CLR en Visual Basic Vea [tipos de valor que aceptan valores NULL](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)y para C#, vea [tipos de valor que aceptan valores NULL](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a726-114">For more information on working with CLR value nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="7a726-115">Valores NULL y la lógica de tres valores</span><span class="sxs-lookup"><span data-stu-id="7a726-115">Nulls and Three-Valued Logic</span></span>  

 <span data-ttu-id="7a726-116">Al permitir valores NULL en definiciones de columna, se introduce la lógica de tres valores en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7a726-116">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="7a726-117">Una comparación puede evaluarse en una de estas tres condiciones:</span><span class="sxs-lookup"><span data-stu-id="7a726-117">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="7a726-118">True</span><span class="sxs-lookup"><span data-stu-id="7a726-118">True</span></span>  
  
- <span data-ttu-id="7a726-119">False</span><span class="sxs-lookup"><span data-stu-id="7a726-119">False</span></span>  
  
- <span data-ttu-id="7a726-120">Desconocido</span><span class="sxs-lookup"><span data-stu-id="7a726-120">Unknown</span></span>  
  
 <span data-ttu-id="7a726-121">Dado que se considera que NULL es desconocido, dos valores NULL comparados entre sí no se consideran iguales.</span><span class="sxs-lookup"><span data-stu-id="7a726-121">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="7a726-122">En las expresiones que usan operadores aritméticos, si alguno de los operandos es NULL, el resultado es NULL también.</span><span class="sxs-lookup"><span data-stu-id="7a726-122">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="7a726-123">Valores NULL y SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="7a726-123">Nulls and SqlBoolean</span></span>  

 <span data-ttu-id="7a726-124">La comparación entre cualquier <xref:System.Data.SqlTypes> devolverá un <xref:System.Data.SqlTypes.SqlBoolean>.</span><span class="sxs-lookup"><span data-stu-id="7a726-124">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="7a726-125">La función `IsNull` para cada `SqlType` devuelve un valor <xref:System.Data.SqlTypes.SqlBoolean> y se puede usar para comprobar si hay valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-125">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="7a726-126">Las siguientes tablas truth muestran cómo funcionan los operadores AND, OR y NOT en presencia de un valor NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-126">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="7a726-127">(T = true, F = false y U = Unknown, o NULL).</span><span class="sxs-lookup"><span data-stu-id="7a726-127">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="7a726-128">![Tabla Truth](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="7a726-128">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="7a726-129">Descripción de la opción ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="7a726-129">Understanding the ANSI_NULLS Option</span></span>  

 <span data-ttu-id="7a726-130"><xref:System.Data.SqlTypes> proporciona la misma semántica que cuando se establece la opción ANSI_NULLS en SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7a726-130"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="7a726-131">Todos los operadores aritméticos (+,-, \* ,/,%), los operadores bit a bit (~, &, \| ) y la mayoría de las funciones devuelven NULL si alguno de los operandos o argumentos es null, excepto la propiedad `IsNull` .</span><span class="sxs-lookup"><span data-stu-id="7a726-131">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="7a726-132">El estándar ANSI SQL-92 no admite *columnName* = NULL en una cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="7a726-132">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="7a726-133">En SQL Server, la opción ANSI_NULLS controla la nulabilidad predeterminada en la base de datos y la evaluación de las comparaciones con respecto a los valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-133">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="7a726-134">Si ANSI_NULLS está activado (valor predeterminado), se debe usar el operador IS NULL en expresiones al comprobar si hay valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-134">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="7a726-135">Por ejemplo, la siguiente comparación genera siempre UNKNOWN cuando ANSI_NULLS está activado:</span><span class="sxs-lookup"><span data-stu-id="7a726-135">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="7a726-136">La comparación con una variable que contenga un valor NULL también produce Unknown:</span><span class="sxs-lookup"><span data-stu-id="7a726-136">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="7a726-137">Use el predicado IS NULL o IS NOT NULL para probar un valor NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-137">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="7a726-138">Esto puede hacer más compleja la cláusula WHERE.</span><span class="sxs-lookup"><span data-stu-id="7a726-138">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="7a726-139">Por ejemplo, la columna TerritoryID de la tabla AdventureWorks Customer permite valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-139">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="7a726-140">Si una instrucción SELECT debe comprobar la existencia de valores NULL además de otros, debe incluir un predicado IS NULL:</span><span class="sxs-lookup"><span data-stu-id="7a726-140">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="7a726-141">Si desactiva ANSI_NULLS en SQL Server, puede crear expresiones que usen el operador de igualdad para comparar con NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-141">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="7a726-142">Sin embargo, no puede evitar que diferentes conexiones establezcan opciones NULL para esa conexión.</span><span class="sxs-lookup"><span data-stu-id="7a726-142">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="7a726-143">El uso de IS NULL para probar los valores NULL funciona siempre, independientemente de la configuración de ANSI_NULLS para una conexión.</span><span class="sxs-lookup"><span data-stu-id="7a726-143">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="7a726-144">No se admite la desactivación de ANSI_NULLS en un `DataSet`, que siempre sigue el estándar ANSI SQL-92 para administrar valores NULL en <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="7a726-144">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="7a726-145">Asignación de valores NULL</span><span class="sxs-lookup"><span data-stu-id="7a726-145">Assigning Null Values</span></span>  

 <span data-ttu-id="7a726-146">Los valores NULL son especiales, y su semántica de asignación y almacenamiento difiere en diferentes sistemas de tipos y sistemas de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="7a726-146">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="7a726-147">Un valor `Dataset` está diseñado para usarse con diferentes sistemas de almacenamiento y tipos.</span><span class="sxs-lookup"><span data-stu-id="7a726-147">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="7a726-148">En esta sección se describe la semántica de valores NULL para asignar valores NULL a un parámetro <xref:System.Data.DataColumn> en un parámetro <xref:System.Data.DataRow> en los distintos sistemas de tipos.</span><span class="sxs-lookup"><span data-stu-id="7a726-148">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="7a726-149">Esta asignación es válida para un parámetro `DataColumn` de cualquier tipo.</span><span class="sxs-lookup"><span data-stu-id="7a726-149">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="7a726-150">Si el tipo implementa `INullable`, `DBNull.Value` se convierte en el valor NULL fuertemente tipado adecuado.</span><span class="sxs-lookup"><span data-stu-id="7a726-150">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="7a726-151">Todos los tipos de datos <xref:System.Data.SqlTypes> implementan `INullable`.</span><span class="sxs-lookup"><span data-stu-id="7a726-151">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="7a726-152">Si el valor NULL fuertemente tipado se puede convertir en el tipo de datos de la columna mediante operadores de conversión implícitos, la asignación debería avanzar.</span><span class="sxs-lookup"><span data-stu-id="7a726-152">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="7a726-153">En caso contrario, se produce una excepción de conversión no válida.</span><span class="sxs-lookup"><span data-stu-id="7a726-153">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="7a726-154">Si "null" es un valor válido para el tipo de datos `DataColumn` especificado, se convierte en el parámetro `DbNull.Value` adecuado o el parámetro `Null` asociado al tipo de `INullable` (`SqlType.Null`)</span><span class="sxs-lookup"><span data-stu-id="7a726-154">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="7a726-155">En el caso de las columnas de UDT, los valores NULL se almacenan siempre en función del tipo asociado a `DataColumn`.</span><span class="sxs-lookup"><span data-stu-id="7a726-155">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="7a726-156">Considere el caso de un UDT asociado a un `DataColumn` que no implementa `INullable`, mientras su subclase sí lo hace.</span><span class="sxs-lookup"><span data-stu-id="7a726-156">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="7a726-157">En este caso, si se asigna un valor NULL fuertemente tipado asociado a la clase derivada, se almacena como un `DbNull.Value` sin tipo, ya que el almacenamiento NULL siempre es coherente con el tipo de datos de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="7a726-157">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a726-158">La estructura `Nullable<T>` o <xref:System.Nullable> no se admite actualmente en `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="7a726-158">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="7a726-159">Asignación de varias columnas (filas)</span><span class="sxs-lookup"><span data-stu-id="7a726-159">Multiple Column (Row) Assignment</span></span>  

 <span data-ttu-id="7a726-160">`DataTable.Add`, `DataTable.LoadDataRow` u otras API que aceptan un parámetro <xref:System.Data.DataRow.ItemArray%2A> que se asigna a una fila, asignan "null" al valor predeterminado de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="7a726-160">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="7a726-161">Si un objeto de la matriz contiene `DbNull.Value` o su homólogo fuertemente tipado, se aplican las mismas reglas que se han descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7a726-161">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="7a726-162">Además, las siguientes reglas se aplican a una instancia de asignaciones NULL `DataRow.["columnName"]`:</span><span class="sxs-lookup"><span data-stu-id="7a726-162">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="7a726-163">El valor *predeterminado* es `DbNull.Value` para todas las columnas, excepto las nulas con establecimiento inflexible de tipos, donde es el valor null fuertemente tipado adecuado.</span><span class="sxs-lookup"><span data-stu-id="7a726-163">The *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="7a726-164">Los valores NULL nunca se escriben durante la serialización en archivos XML (como en "xsi: nil").</span><span class="sxs-lookup"><span data-stu-id="7a726-164">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="7a726-165">Todos los valores no NULL, incluidos los valores predeterminados, siempre se escriben durante la serialización a XML.</span><span class="sxs-lookup"><span data-stu-id="7a726-165">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="7a726-166">Esto se diferencia de la semántica de XSD/XML, en la que un valor NULL (xsi:nil) es explícito y el valor predeterminado es implícito (si no está presente en XML, un analizador de validación puede obtenerlo de un esquema XSD asociado).</span><span class="sxs-lookup"><span data-stu-id="7a726-166">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="7a726-167">Lo contrario es true para un parámetro `DataTable`: un valor NULL es implícito y el valor predeterminado es explícito.</span><span class="sxs-lookup"><span data-stu-id="7a726-167">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="7a726-168">Todos los valores de columna que faltan para las filas leídas de la entrada XML se asignan como NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-168">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="7a726-169">A las filas creadas con <xref:System.Data.DataTable.NewRow%2A> o métodos similares se les asigna el valor predeterminado de DataColumn.</span><span class="sxs-lookup"><span data-stu-id="7a726-169">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="7a726-170">El método <xref:System.Data.DataRow.IsNull%2A> devuelve `true` para `DbNull.Value` y `INullable.Null`.</span><span class="sxs-lookup"><span data-stu-id="7a726-170">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="7a726-171">Asignación de valores NULL</span><span class="sxs-lookup"><span data-stu-id="7a726-171">Assigning Null Values</span></span>  

 <span data-ttu-id="7a726-172">El valor predeterminado de cualquier instancia <xref:System.Data.SqlTypes> es NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-172">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="7a726-173">Los valores NULL de <xref:System.Data.SqlTypes> son específicos del tipo y no se pueden representar con un valor único, como `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="7a726-173">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="7a726-174">Use la propiedad `IsNull` para comprobar si hay valores NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-174">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="7a726-175">Los valores NULL se pueden asignar a un parámetro <xref:System.Data.DataColumn> como se muestra en el ejemplo de código siguiente.</span><span class="sxs-lookup"><span data-stu-id="7a726-175">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="7a726-176">Puede asignar directamente valores NULL a variables `SqlTypes` sin desencadenar una excepción.</span><span class="sxs-lookup"><span data-stu-id="7a726-176">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7a726-177">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7a726-177">Example</span></span>  

 <span data-ttu-id="7a726-178">En el ejemplo de código siguiente se crea un parámetro <xref:System.Data.DataTable> con dos columnas definidas como <xref:System.Data.SqlTypes.SqlInt32> y <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="7a726-178">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="7a726-179">El código agrega una fila de valores conocidos y una fila de valores NULL y, a continuación, recorre en iteración <xref:System.Data.DataTable>, asignando los valores a las variables y mostrando el resultado en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="7a726-179">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="7a726-180">Este ejemplo genera los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="7a726-180">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="7a726-181">Comparación de valores NULL con SqlTypes y tipos CLR</span><span class="sxs-lookup"><span data-stu-id="7a726-181">Comparing Null Values with SqlTypes and CLR Types</span></span>  

 <span data-ttu-id="7a726-182">Al comparar valores NULL, es importante comprender la diferencia entre la forma en que el método `Equals` evalúa los valores NULL en <xref:System.Data.SqlTypes> en comparación con el modo en que funciona con tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="7a726-182">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="7a726-183">Todos los métodos <xref:System.Data.SqlTypes> de `Equals`utilizan la semántica de base de datos para evaluar valores NULL: si uno o ambos de los valores son NULL, la comparación da como resultado NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-183">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="7a726-184">Por otro lado, el uso del método `Equals` de CLR en dos <xref:System.Data.SqlTypes> dará como resultado true si ambos son NULL.</span><span class="sxs-lookup"><span data-stu-id="7a726-184">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="7a726-185">Esto refleja la diferencia entre el uso de un método de instancia como el método `String.Equals` de CLR y el uso del método estático o compartido, `SqlString.Equals`.</span><span class="sxs-lookup"><span data-stu-id="7a726-185">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="7a726-186">En el ejemplo siguiente se muestra la diferencia en los resultados entre el método `SqlString.Equals` y el método `String.Equals` cuando cada uno de ellos pasa un par de valores NULL y, a continuación, un par de cadenas vacías.</span><span class="sxs-lookup"><span data-stu-id="7a726-186">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="7a726-187">El código genera el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="7a726-187">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a><span data-ttu-id="7a726-188">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7a726-188">See also</span></span>

- [<span data-ttu-id="7a726-189">Tipos de datos de SQL Server y ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7a726-189">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="7a726-190">Información general de ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7a726-190">ADO.NET Overview</span></span>](../ado-net-overview.md)
