---
title: Orden de los miembros de datos
description: Obtenga información sobre el orden de los miembros de datos en WCF. Es posible que las aplicaciones necesiten conocer o cambiar el orden en el que los miembros de datos se envían o se esperan.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 1cb63569c1789b1577588caf63fb0a0259e530ff
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262169"
---
# <a name="data-member-order"></a>Orden de los miembros de datos

En algunas aplicaciones, es útil conocer el orden en el que se envían los datos de los distintos miembros de datos o en el que se espera recibir (como el orden en el que los datos aparecen en el XML serializado). A veces puede ser necesario cambiar este orden. En este tema se explican las reglas de la clasificación.  
  
## <a name="basic-rules"></a>Reglas básicas  

 Las reglas básicas sobre el orden de los datos incluyen:  
  
- Si un tipo de contrato de datos forma parte de una jerarquía de herencia, los miembros de datos de sus tipos base siempre aparecerán en primer lugar.  
  
- A continuación, se encontrarán los miembros de datos del tipo actual que no tienen la propiedad <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> del conjunto de atributos <xref:System.Runtime.Serialization.DataMemberAttribute>, en orden alfabético.  
  
- Después se encontrará cualquier miembro de datos que tenga la propiedad <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> del conjunto de atributos <xref:System.Runtime.Serialization.DataMemberAttribute>. Se ordenan por el valor de la propiedad `Order` y después alfabéticamente si hay más de un miembro de un valor `Order` concreto. Los valores de orden pueden omitirse.  
  
 El orden alfabético se establece llamando al método <xref:System.String.CompareOrdinal%2A>.  
  
## <a name="examples"></a>Ejemplos  

 Observe el código siguiente.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 El XML generado es similar a lo siguiente.  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>
</DerivedType>  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Equivalencia del contrato de datos](data-contract-equivalence.md)
- [Utilización de contratos de datos](using-data-contracts.md)
