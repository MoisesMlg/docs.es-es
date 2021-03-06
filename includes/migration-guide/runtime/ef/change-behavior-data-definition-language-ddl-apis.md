---
ms.openlocfilehash: 4416a7c09f2d163961fe2fe3d6dfaa8bd5e66f93
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496394"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Cambio de comportamiento en las API de lenguaje de definición de datos (DDL)

#### <a name="details"></a>Detalles

El comportamiento de las API de DDL cuando se especifica AttachDBFilename ha cambiado tal y como se describe a continuación:<ul><li>Las cadenas de conexión no necesitan especificar un valor Initial Catalog. Anteriormente, se necesitaban los valores AttachDBFilename e Initial Catalog.</li><li>Si se especifican los valores Initial Catalog y AttachDBFilename, y existe el archivo MDF indicado, el método <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> devuelve <code>true</code>. Anteriormente devolvía <code>false</code>.</li><li>Si se especifican los valores Initial Catalog y AttachDBFilename, y existe el archivo MDF indicado, la llamada al método <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> elimina los archivos.</li><li>Si se llama a <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> cuando la cadena de conexión especifica un valor AttachDBFilename con un archivo MDF y un valor Initial Catalog que no existen, el método inicia una excepción <xref:System.InvalidOperationException>. Anteriormente iniciaba una excepción <xref:System.Data.SqlClient.SqlException>.</li></ul>

#### <a name="suggestion"></a>Sugerencia

Estos cambios facilitan la creación de herramientas y aplicaciones que utilizan las API de DDL. Estos cambios pueden afectar a la compatibilidad de las aplicaciones en los escenarios siguientes:<ul><li>El usuario escribe código que ejecuta directamente un comando <code>DROP DATABASE</code> en lugar de llamar al método <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> si el método <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> devuelve <code>true</code>. Esto interrumpe el código existente si la base de datos no está asociada pero el archivo MDF existe.</li><li>El usuario escribe código en el que espera que el método <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> inicie una excepción <xref:System.Data.SqlClient.SqlException> en lugar de una excepción <xref:System.InvalidOperationException> si no existen Initial Catalog ni el archivo MDF.</li></ul>

| NOMBRE    | Valor       |
|:--------|:------------|
| Ámbito   |Secundaria|
|Versión|4.5|
|Tipo|Tiempo de ejecución|

#### <a name="affected-apis"></a>API afectadas

No detectable a través del análisis de la API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
