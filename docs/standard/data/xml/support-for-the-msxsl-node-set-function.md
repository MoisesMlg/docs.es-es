---
title: Compatibilidad con la función msxsl:node-set()
ms.date: 03/30/2017
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 26ae3014af93377dc106b5638ba194bd38e3dc9e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818549"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="ea386-102">Compatibilidad con la función msxsl:node-set()</span><span class="sxs-lookup"><span data-stu-id="ea386-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="ea386-103">La función `msxsl:node-set` permite convertir un fragmento del árbol de resultados en un conjunto de nodos.</span><span class="sxs-lookup"><span data-stu-id="ea386-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="ea386-104">El conjunto de nodos resultante siempre contiene un único nodo, que es el nodo raíz del árbol.</span><span class="sxs-lookup"><span data-stu-id="ea386-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea386-105">La clase <xref:System.Xml.Xsl.XslTransform> está obsoleta en .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ea386-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="ea386-106">Puede llevar a cabo Extensible Stylesheet Language for Transformations (XSLT) mediante la clase <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="ea386-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ea386-107">Consulte [Uso de la clase XslCompiledTransform](using-the-xslcompiledtransform-class.md) y [Migración desde la clase XslTransform](migrating-from-the-xsltransform-class.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="ea386-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="ea386-108">La función `msxsl:node-set` permite convertir un fragmento del árbol de resultados en un conjunto de nodos.</span><span class="sxs-lookup"><span data-stu-id="ea386-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="ea386-109">El conjunto de nodos resultante siempre contiene un único nodo, que es el nodo raíz del árbol.</span><span class="sxs-lookup"><span data-stu-id="ea386-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea386-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ea386-110">Example</span></span>  
 <span data-ttu-id="ea386-111">En el ejemplo siguiente, `$books` es una variable que es un árbol de nodos en la hoja de estilos.</span><span class="sxs-lookup"><span data-stu-id="ea386-111">In the following example, `$books` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="ea386-112">La instrucción for-each, combinada con la función `node-set`, permite que el usuario itere por este árbol como un conjunto de nodos.</span><span class="sxs-lookup"><span data-stu-id="ea386-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="ea386-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="ea386-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="ea386-114">Salida</span><span class="sxs-lookup"><span data-stu-id="ea386-114">Output</span></span>  
 <span data-ttu-id="ea386-115">El resultado de la transformación es</span><span class="sxs-lookup"><span data-stu-id="ea386-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea386-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea386-116">See also</span></span>

- [<span data-ttu-id="ea386-117">La clase XslTransform implementa el procesador XSLT</span><span class="sxs-lookup"><span data-stu-id="ea386-117">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
