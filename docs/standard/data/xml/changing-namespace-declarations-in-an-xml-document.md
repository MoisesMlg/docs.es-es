---
title: Cambiar declaraciones de espacio de nombres en un documento XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: f4f081e1db2ccacf4714ad3009eefdfc290b2ed4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821832"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Cambiar declaraciones de espacio de nombres en un documento XML
**XmlDocument** expone declaraciones de espacios de nombres y atributos **xmlns** como parte del modelo de objetos de documento. Estos se almacenan en **XmlDocument**, de modo que, al guardar el documento, puede conservar la ubicación de dichos atributos. Si se cambian estos atributos, no se produce ningún efecto en las propiedades **Name**, **NamespaceURI** y **Prefix** de otros nodos que ya estén en el árbol. Por ejemplo, si carga el documento siguiente, el elemento `test` tiene **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Si quita el atributo `xmlns` como sigue, entonces el elemento `test` tiene todavía **NamespaceURI** de `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Del mismo modo, si añade otro atributo `xmlns` al elemento `doc` como se muestra a continuación, el elemento `test` todavía tiene **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Por tanto, si se cambian los atributos `xmlns` no se produce ningún efecto hasta que se guarde y se recargue el objeto **XmlDocument**.  
  
## <a name="see-also"></a>Vea también

- [Document Object Model (DOM) para XML](xml-document-object-model-dom.md)
