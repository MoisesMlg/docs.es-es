---
title: Procedimiento para transformar un fragmento de nodo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 5c69a35497feced92a05e124307d3be584ab86b7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829445"
---
# <a name="how-to-transform-a-node-fragment"></a>Procedimiento para transformar un fragmento de nodo
Cuando se transforman los datos contenidos en un objeto <xref:System.Xml.XmlDocument> o <xref:System.Xml.XPath.XPathDocument>, las transformaciones XSLT se aplican a un documento completo. En otras palabras, si se pasa un nodo distinto del nodo raíz del documento, esto no evita que el proceso de transformación pueda obtener acceso a todos los nodos del documento cargado. Para transformar un fragmento del nodo, debe crear un objeto diferente que contenga el fragmento del nodo y pasar ese objeto al método <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-transform-a-node-fragment"></a>Para transformar un fragmento de nodo  
  
1. Cree un objeto que contenga el documento de origen.  
  
2. Localice el fragmento del nodo que desee transformar.  
  
3. Cree un objeto diferente solo con el fragmento del nodo.  
  
4. Pase el fragmento del nodo al método <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se transforma un fragmento de nodo y los resultados se envían a la consola.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Entrada  
  
##### <a name="booksxml"></a>books.xml  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Salida  
 El título del libro es The Confidence Man.  
  
## <a name="see-also"></a>Vea también

- [Uso de la clase XslCompiledTransform](using-the-xslcompiledtransform-class.md)
