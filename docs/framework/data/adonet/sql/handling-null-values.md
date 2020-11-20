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
# <a name="handling-null-values"></a>Controlar valores Null

Se utiliza un valor NULL en una base de datos relacional cuando el valor de una columna es desconocido o falta. Un valor NULL no es una cadena vacía (para tipos de datos de caracteres o de fecha y hora) ni un valor cero (para tipos de datos numéricos). La especificación ANSI SQL-92 indica que un valor NULL debe ser el mismo para todos los tipos de datos, de modo que todos los valores NULL se traten de manera uniforme. El espacio de nombres <xref:System.Data.SqlTypes> proporciona la semántica de NULL implementando la interfaz <xref:System.Data.SqlTypes.INullable>. Cada uno de los tipos de datos de <xref:System.Data.SqlTypes> tiene su propia propiedad `IsNull` y un valor `Null` que se puede asignar a una instancia de ese tipo de datos.  
  
> [!NOTE]
> La versión 2,0 de .NET Framework incorporó compatibilidad con tipos de valor que aceptan valores NULL, que permiten a los programadores extender un tipo de valor para representar todos los valores del tipo subyacente. Estos tipos de valor que aceptan valores NULL de CLR representan una instancia de la <xref:System.Nullable> estructura. Esta funcionalidad es especialmente útil cuando se aplica la conversión boxing y la conversión unboxing de tipos de valor, lo que proporciona compatibilidad mejorada con los tipos de objeto. Los tipos de valor que aceptan valores NULL de CLR no están diseñados para el almacenamiento de valores NULL de base de datos porque un valor null de ANSI SQL no se comporta de la misma manera que una `null` referencia (o `Nothing` en Visual Basic). Para trabajar con valores NULL de ANSI SQL de la base de datos, utilice valores NULL de tipo <xref:System.Data.SqlTypes> en lugar de <xref:System.Nullable>. Para obtener más información sobre cómo trabajar con tipos que aceptan valores NULL de CLR en Visual Basic Vea [tipos de valor que aceptan valores NULL](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)y para C#, vea [tipos de valor que aceptan valores NULL](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Valores NULL y la lógica de tres valores  

 Al permitir valores NULL en definiciones de columna, se introduce la lógica de tres valores en la aplicación. Una comparación puede evaluarse en una de estas tres condiciones:  
  
- True  
  
- False  
  
- Desconocido  
  
 Dado que se considera que NULL es desconocido, dos valores NULL comparados entre sí no se consideran iguales. En las expresiones que usan operadores aritméticos, si alguno de los operandos es NULL, el resultado es NULL también.  
  
## <a name="nulls-and-sqlboolean"></a>Valores NULL y SqlBoolean  

 La comparación entre cualquier <xref:System.Data.SqlTypes> devolverá un <xref:System.Data.SqlTypes.SqlBoolean>. La función `IsNull` para cada `SqlType` devuelve un valor <xref:System.Data.SqlTypes.SqlBoolean> y se puede usar para comprobar si hay valores NULL. Las siguientes tablas truth muestran cómo funcionan los operadores AND, OR y NOT en presencia de un valor NULL. (T = true, F = false y U = Unknown, o NULL).  
  
 ![Tabla Truth](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Descripción de la opción ANSI_NULLS  

 <xref:System.Data.SqlTypes> proporciona la misma semántica que cuando se establece la opción ANSI_NULLS en SQL Server. Todos los operadores aritméticos (+,-, \* ,/,%), los operadores bit a bit (~, &, \| ) y la mayoría de las funciones devuelven NULL si alguno de los operandos o argumentos es null, excepto la propiedad `IsNull` .  
  
 El estándar ANSI SQL-92 no admite *columnName* = NULL en una cláusula WHERE. En SQL Server, la opción ANSI_NULLS controla la nulabilidad predeterminada en la base de datos y la evaluación de las comparaciones con respecto a los valores NULL. Si ANSI_NULLS está activado (valor predeterminado), se debe usar el operador IS NULL en expresiones al comprobar si hay valores NULL. Por ejemplo, la siguiente comparación genera siempre UNKNOWN cuando ANSI_NULLS está activado:  
  
```sql
colname > NULL  
```  
  
 La comparación con una variable que contenga un valor NULL también produce Unknown:  
  
```sql
colname > @MyVariable  
```  
  
 Use el predicado IS NULL o IS NOT NULL para probar un valor NULL. Esto puede hacer más compleja la cláusula WHERE. Por ejemplo, la columna TerritoryID de la tabla AdventureWorks Customer permite valores NULL. Si una instrucción SELECT debe comprobar la existencia de valores NULL además de otros, debe incluir un predicado IS NULL:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Si desactiva ANSI_NULLS en SQL Server, puede crear expresiones que usen el operador de igualdad para comparar con NULL. Sin embargo, no puede evitar que diferentes conexiones establezcan opciones NULL para esa conexión. El uso de IS NULL para probar los valores NULL funciona siempre, independientemente de la configuración de ANSI_NULLS para una conexión.  
  
 No se admite la desactivación de ANSI_NULLS en un `DataSet`, que siempre sigue el estándar ANSI SQL-92 para administrar valores NULL en <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Asignación de valores NULL  

 Los valores NULL son especiales, y su semántica de asignación y almacenamiento difiere en diferentes sistemas de tipos y sistemas de almacenamiento. Un valor `Dataset` está diseñado para usarse con diferentes sistemas de almacenamiento y tipos.  
  
 En esta sección se describe la semántica de valores NULL para asignar valores NULL a un parámetro <xref:System.Data.DataColumn> en un parámetro <xref:System.Data.DataRow> en los distintos sistemas de tipos.  
  
 `DBNull.Value`  
 Esta asignación es válida para un parámetro `DataColumn` de cualquier tipo. Si el tipo implementa `INullable`, `DBNull.Value` se convierte en el valor NULL fuertemente tipado adecuado.  
  
 `SqlType.Null`  
 Todos los tipos de datos <xref:System.Data.SqlTypes> implementan `INullable`. Si el valor NULL fuertemente tipado se puede convertir en el tipo de datos de la columna mediante operadores de conversión implícitos, la asignación debería avanzar. En caso contrario, se produce una excepción de conversión no válida.  
  
 `null`  
 Si "null" es un valor válido para el tipo de datos `DataColumn` especificado, se convierte en el parámetro `DbNull.Value` adecuado o el parámetro `Null` asociado al tipo de `INullable` (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 En el caso de las columnas de UDT, los valores NULL se almacenan siempre en función del tipo asociado a `DataColumn`. Considere el caso de un UDT asociado a un `DataColumn` que no implementa `INullable`, mientras su subclase sí lo hace. En este caso, si se asigna un valor NULL fuertemente tipado asociado a la clase derivada, se almacena como un `DbNull.Value` sin tipo, ya que el almacenamiento NULL siempre es coherente con el tipo de datos de DataColumn.  
  
> [!NOTE]
> La estructura `Nullable<T>` o <xref:System.Nullable> no se admite actualmente en `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Asignación de varias columnas (filas)  

 `DataTable.Add`, `DataTable.LoadDataRow` u otras API que aceptan un parámetro <xref:System.Data.DataRow.ItemArray%2A> que se asigna a una fila, asignan "null" al valor predeterminado de DataColumn. Si un objeto de la matriz contiene `DbNull.Value` o su homólogo fuertemente tipado, se aplican las mismas reglas que se han descrito anteriormente.  
  
 Además, las siguientes reglas se aplican a una instancia de asignaciones NULL `DataRow.["columnName"]`:  
  
1. El valor *predeterminado* es `DbNull.Value` para todas las columnas, excepto las nulas con establecimiento inflexible de tipos, donde es el valor null fuertemente tipado adecuado.  
  
2. Los valores NULL nunca se escriben durante la serialización en archivos XML (como en "xsi: nil").  
  
3. Todos los valores no NULL, incluidos los valores predeterminados, siempre se escriben durante la serialización a XML. Esto se diferencia de la semántica de XSD/XML, en la que un valor NULL (xsi:nil) es explícito y el valor predeterminado es implícito (si no está presente en XML, un analizador de validación puede obtenerlo de un esquema XSD asociado). Lo contrario es true para un parámetro `DataTable`: un valor NULL es implícito y el valor predeterminado es explícito.  
  
4. Todos los valores de columna que faltan para las filas leídas de la entrada XML se asignan como NULL. A las filas creadas con <xref:System.Data.DataTable.NewRow%2A> o métodos similares se les asigna el valor predeterminado de DataColumn.  
  
5. El método <xref:System.Data.DataRow.IsNull%2A> devuelve `true` para `DbNull.Value` y `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Asignación de valores NULL  

 El valor predeterminado de cualquier instancia <xref:System.Data.SqlTypes> es NULL.  
  
 Los valores NULL de <xref:System.Data.SqlTypes> son específicos del tipo y no se pueden representar con un valor único, como `DbNull`. Use la propiedad `IsNull` para comprobar si hay valores NULL.  
  
 Los valores NULL se pueden asignar a un parámetro <xref:System.Data.DataColumn> como se muestra en el ejemplo de código siguiente. Puede asignar directamente valores NULL a variables `SqlTypes` sin desencadenar una excepción.  
  
### <a name="example"></a>Ejemplo  

 En el ejemplo de código siguiente se crea un parámetro <xref:System.Data.DataTable> con dos columnas definidas como <xref:System.Data.SqlTypes.SqlInt32> y <xref:System.Data.SqlTypes.SqlString>. El código agrega una fila de valores conocidos y una fila de valores NULL y, a continuación, recorre en iteración <xref:System.Data.DataTable>, asignando los valores a las variables y mostrando el resultado en la ventana de la consola.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Este ejemplo genera los siguientes resultados:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Comparación de valores NULL con SqlTypes y tipos CLR  

 Al comparar valores NULL, es importante comprender la diferencia entre la forma en que el método `Equals` evalúa los valores NULL en <xref:System.Data.SqlTypes> en comparación con el modo en que funciona con tipos CLR. Todos los métodos <xref:System.Data.SqlTypes> de `Equals`utilizan la semántica de base de datos para evaluar valores NULL: si uno o ambos de los valores son NULL, la comparación da como resultado NULL. Por otro lado, el uso del método `Equals` de CLR en dos <xref:System.Data.SqlTypes> dará como resultado true si ambos son NULL. Esto refleja la diferencia entre el uso de un método de instancia como el método `String.Equals` de CLR y el uso del método estático o compartido, `SqlString.Equals`.  
  
 En el ejemplo siguiente se muestra la diferencia en los resultados entre el método `SqlString.Equals` y el método `String.Equals` cuando cada uno de ellos pasa un par de valores NULL y, a continuación, un par de cadenas vacías.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 El código genera el siguiente resultado:  
  
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
  
## <a name="see-also"></a>Consulte también

- [Tipos de datos de SQL Server y ADO.NET](sql-server-data-types.md)
- [Información general de ADO.NET](../ado-net-overview.md)
