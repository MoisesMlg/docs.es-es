---
title: <dateTimeSerialization> (Elemento)
description: En este artículo se describe el elemento <dateTimeSerialization>, que determina el modo de serialización de los objetos DateTime.
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 1623517e66955c14b7e738c860ec16086fe30429
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678979"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> (Elemento)

Determina el modo de serialización XML de los objetos <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  

 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributos|Descripción|  
|----------------|-----------------|  
|`mode`|Opcional. Especifica el modo de serialización. Establece uno de los valores de <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> . El valor predeterminado es **RoundTrip**.|  
  
### <a name="child-elements"></a>Elementos secundarios  

 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|system.xml.serialization|El elemento de nivel superior para controlar la serialización XML.|  
  
## <a name="remarks"></a>Comentarios  

Cuando esta propiedad se establece en **Local**, los objetos <xref:System.DateTime> siempre tienen el formato de hora local. Es decir, la información de zona horaria local siempre se incluye con los datos serializados.
  
Cuando esta propiedad se establece en **Roundtrip**, los objetos <xref:System.DateTime> se examinan para determinar si se encuentran en la zona horaria local, UTC o una zona horaria no especificada. Los objetos <xref:System.DateTime> se serializan a continuación de este tipo de manera que esta información se conserva. Éste es el comportamiento predeterminado y el que se recomienda para todas las aplicaciones nuevas que no funcionan con versiones anteriores de .Net Framework.  
  
## <a name="see-also"></a>Vea también

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Esquema de los archivos de configuración](../../framework/configure-apps/file-schema/index.md)
- [Elemento \<schemaImporterExtensions>](schemaimporterextensions-element.md)
- [\<add> Elemento para \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [Elemento \<system.xml.serialization>](system-xml-serialization-element.md)
