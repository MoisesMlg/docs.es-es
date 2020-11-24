---
title: Cómo quitar nodos del DOM
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: ecda49960f51d807730cb44b966aa2dfcada22d7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823711"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="be49b-102">Cómo quitar nodos del DOM</span><span class="sxs-lookup"><span data-stu-id="be49b-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="be49b-103">Para quitar un nodo del Modelo de objetos de documento XML (DOM), utilice el método <xref:System.Xml.XmlNode.RemoveChild%2A> para quitar un nodo específico.</span><span class="sxs-lookup"><span data-stu-id="be49b-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="be49b-104">Cuando se quita un nodo, el método quita el subárbol que pertenece al nodo que se está quitando; es decir, no se trata de un nodo hoja.</span><span class="sxs-lookup"><span data-stu-id="be49b-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="be49b-105">Para quitar varios nodos del DOM, utilice el método <xref:System.Xml.XmlNode.RemoveAll%2A> para quitar todos los atributos y nodos secundarios, si es preciso, del nodo actual.</span><span class="sxs-lookup"><span data-stu-id="be49b-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="be49b-106">Si está trabajando con <xref:System.Xml.XmlNamedNodeMap>, puede quitar un nodo con el método <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="be49b-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="be49b-107">Para quitar atributos, vea [Cómo quitar atributos de un nodo de elementos en el DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="be49b-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be49b-108">Vea también</span><span class="sxs-lookup"><span data-stu-id="be49b-108">See also</span></span>

- [<span data-ttu-id="be49b-109">Document Object Model (DOM) para XML</span><span class="sxs-lookup"><span data-stu-id="be49b-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
