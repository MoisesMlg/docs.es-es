---
title: Control de espacios en blanco y de espacios en blanco significativos al cargar DOM
ms.date: 03/30/2017
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 6282b47e8a63143e32df39db02e79e7b44d38275
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675560"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a>Control de espacios en blanco y de espacios en blanco significativos al cargar DOM

Al cargar el documento, se puede establecer la opción de conservar los espacios en blanco y crear nodos **XmlWhitespace** en el árbol del documento. Para crear nodos de espacio en blanco, debe establecerse la propiedad **PreserveWhitespace** como true. Si se establece como **false**, que es el valor predeterminado, no se crean nodos de espacio en blanco. Siempre se conservan los nodos de espacio en blanco significativos y se crean nodos **XmlSignificantWhitespace** en la memoria para representar estos datos, independientemente de la configuración de la marca **PreserveWhitespace**.  
  
 Si el documento se carga desde un sistema de lectura, la configuración de la propiedad de la marca **PreserveWhitespace** en la clase **XmlDocument** afecta a la creación de nodos **XmlWhitespace** solo cuando la propiedad **WhitespaceHandling** en **XmlTextReader** no se establece en **WhitespaceHandling.None**. Es el valor de la propiedad **WhitespaceHandling** en el sistema de lectura la que tiene prioridad sobre la configuración de dicha marca en **XmlDocument**. Para obtener más información sobre **XmlSignificantWhitespace**, vea <xref:System.Xml.XmlSignificantWhitespace>.  
  
## <a name="see-also"></a>Vea también

- [Document Object Model (DOM) para XML](xml-document-object-model-dom.md)
