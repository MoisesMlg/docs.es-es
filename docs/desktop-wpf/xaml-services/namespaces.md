---
title: Espacios de nombres XAML para servicios XAML de .NET
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2020
ms.locfileid: "81433065"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a><span data-ttu-id="efa49-102">Espacios de nombres XAML para servicios XAML de .NET</span><span class="sxs-lookup"><span data-stu-id="efa49-102">XAML Namespaces for .NET XAML Services</span></span>
<span data-ttu-id="efa49-103">Un espacio de nombres XAML es un concepto que se expande en la definición de un espacio de nombres XML.</span><span class="sxs-lookup"><span data-stu-id="efa49-103">A XAML namespace is a concept that expands on the definition of an XML namespace.</span></span> <span data-ttu-id="efa49-104">De forma similar a un espacio de `xmlns` nombres XML, puede definir un espacio de nombres XAML mediante un atributo en el marcado.</span><span class="sxs-lookup"><span data-stu-id="efa49-104">Similar to an XML namespace, you can define a XAML namespace using an `xmlns` attribute in markup.</span></span> <span data-ttu-id="efa49-105">Los espacios de nombres XAML también se representan en el flujo de nodo XAML y otras API de servicios XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-105">XAML namespaces are also represented in the XAML node stream and other XAML Services APIs.</span></span> <span data-ttu-id="efa49-106">En este tema se define el concepto de espacio de nombres XAML y se describe cómo se pueden definir los espacios de nombres XAML y los usan los contextos de esquema XAML y otros aspectos de los servicios XAML de .NET.</span><span class="sxs-lookup"><span data-stu-id="efa49-106">This topic defines the XAML namespace concept, and describes how XAML namespaces can be defined and are used by XAML schema contexts and other aspects of .NET XAML Services.</span></span>  
  
## <a name="xml-namespace-and-xaml-namespace"></a><span data-ttu-id="efa49-107">Espacio de nombres XML y espacio de nombres XAML</span><span class="sxs-lookup"><span data-stu-id="efa49-107">XML Namespace and XAML Namespace</span></span>  
 <span data-ttu-id="efa49-108">Un espacio de nombres XAML es un espacio de nombres XML especializado, al igual que XAML es una forma especializada de XML y usa el formulario XML básico para su marcado.</span><span class="sxs-lookup"><span data-stu-id="efa49-108">A XAML namespace is a specialized XML namespace, just as XAML is a specialized form of XML and uses the basic XML form for its markup.</span></span> <span data-ttu-id="efa49-109">En el marcado, se declara un `xmlns` espacio de nombres XAML y su asignación a través de un atributo aplicado a un elemento.</span><span class="sxs-lookup"><span data-stu-id="efa49-109">In markup, you declare a XAML namespace and its mapping through an `xmlns` attribute applied to an element.</span></span> <span data-ttu-id="efa49-110">La `xmlns` declaración se puede realizar en el mismo elemento en el que se declara el espacio de nombres XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-110">The `xmlns` declaration can be made to the same element that the XAML namespace is declared in.</span></span> <span data-ttu-id="efa49-111">Una declaración de espacio de nombres XAML realizada a un elemento es válida para ese elemento, todos los atributos de ese elemento y todos los elementos secundarios de ese elemento.</span><span class="sxs-lookup"><span data-stu-id="efa49-111">A XAML namespace declaration made to an element is valid for that element, all attributes of that element, and all children of that element.</span></span> <span data-ttu-id="efa49-112">Los atributos pueden usar un espacio de nombres XAML que no es el mismo que el elemento que contiene el atributo, siempre y cuando el propio nombre del atributo haga referencia al prefijo como parte de su nombre de atributo en el marcado.</span><span class="sxs-lookup"><span data-stu-id="efa49-112">Attributes can use a XAML namespace that is not the same as the element that contains the attribute, so long as the attribute name itself references the prefix as part of its attribute name in markup.</span></span>  
  
 <span data-ttu-id="efa49-113">La distinción de un espacio de nombres XAML frente a un espacio de nombres XML es que un espacio de nombres XML se puede usar para hacer referencia a un esquema o simplemente para diferenciar entidades.</span><span class="sxs-lookup"><span data-stu-id="efa49-113">The distinction of a XAML namespace versus an XML namespace is that an XML namespace might be used to reference a schema or simply to differentiate entities.</span></span> <span data-ttu-id="efa49-114">Para XAML, los tipos y miembros tal como se usan en XAML deben resolverse en última instancia en tipos de respaldo y los conceptos de esquema XML no se aplican bien a esta capacidad.</span><span class="sxs-lookup"><span data-stu-id="efa49-114">For XAML, the types and members as used in XAML must ultimately be resolved to backing types, and XML schema concepts do not apply well to this capability.</span></span> <span data-ttu-id="efa49-115">El espacio de nombres XAML contiene información que el contexto de esquema XAML debe tener disponible para realizar esta asignación de tipos.</span><span class="sxs-lookup"><span data-stu-id="efa49-115">The XAML namespace contains information that the XAML schema context must have available in order to perform this type mapping.</span></span>  
  
## <a name="xaml-namespace-components"></a><span data-ttu-id="efa49-116">Componentes de espacio de nombres XAML</span><span class="sxs-lookup"><span data-stu-id="efa49-116">XAML Namespace Components</span></span>  
 <span data-ttu-id="efa49-117">La definición de espacio de nombres XAML tiene dos componentes: un prefijo y un identificador.</span><span class="sxs-lookup"><span data-stu-id="efa49-117">The XAML namespace definition has two components: a prefix, and an identifier.</span></span> <span data-ttu-id="efa49-118">Cada uno de estos componentes está presente cuando se declara un espacio de nombres XAML en el marcado o se define en el sistema de tipos XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-118">Each of these components is present when a XAML namespace is declared in markup, or defined in the XAML type system.</span></span>  
  
 <span data-ttu-id="efa49-119">El prefijo puede ser cualquier cadena según lo permitido por los espacios de nombres [W3C en la especificación XML 1.0.](https://www.w3.org/TR/REC-xml-names/)</span><span class="sxs-lookup"><span data-stu-id="efa49-119">The prefix can be any string as allowed by the [W3C Namespaces in XML 1.0 specification](https://www.w3.org/TR/REC-xml-names/).</span></span> <span data-ttu-id="efa49-120">Por convención, los prefijos suelen ser cadenas cortas, porque el prefijo se repite muchas veces en un archivo de marcado típico.</span><span class="sxs-lookup"><span data-stu-id="efa49-120">By convention, the prefixes are typically short strings, because the prefix is repeated many times in a typical markup file.</span></span> <span data-ttu-id="efa49-121">Ciertos espacios de nombres XAML que están diseñados para usarse en varias implementaciones XAML usan prefijos convencionales concretos.</span><span class="sxs-lookup"><span data-stu-id="efa49-121">Certain XAML namespaces that are intended to be used in multiple XAML implementations use particular conventional prefixes.</span></span> <span data-ttu-id="efa49-122">Por ejemplo, el espacio de nombres XAML `x`del lenguaje XAML normalmente se asigna con el prefijo .</span><span class="sxs-lookup"><span data-stu-id="efa49-122">For example, the XAML language XAML namespace is typically mapped using the prefix `x`.</span></span> <span data-ttu-id="efa49-123">Puede definir un espacio de nombres XAML predeterminado, donde el prefijo no se proporciona en la definición, pero se representa como una cadena vacía si se define o se consulta by.NET API de servicios XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-123">You can define a default XAML namespace, where the prefix is not given in the definition but is represented as an empty string if defined or queried by.NET XAML Services API.</span></span> <span data-ttu-id="efa49-124">Normalmente, el espacio de nombres XAML predeterminado se elige deliberadamente para promover una cantidad maximizada de marcado de omisión de prefijos mediante una tecnología de implementación XAML y sus escenarios y vocabularios.</span><span class="sxs-lookup"><span data-stu-id="efa49-124">Typically, the default XAML namespace is deliberately chosen in order to promote a maximized amount of prefix-omitting markup by a XAML-implementing technology and its scenarios and vocabularies.</span></span>  
  
 <span data-ttu-id="efa49-125">El identificador puede ser cualquier cadena según lo permitido por los espacios de nombres [W3C en la especificación XML 1.0](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="efa49-125">The identifier can be any string as allowed by the [W3C Namespaces in XML 1.0 specification](https://www.w3.org/TR/REC-xml-names/).</span></span> <span data-ttu-id="efa49-126">Por convención, los identificadores de espacios de nombres XML o espacios de nombres XAML a menudo se dan en forma de URI, normalmente como un URI absoluto calificado por protocolo.</span><span class="sxs-lookup"><span data-stu-id="efa49-126">By convention, identifiers for either XML namespaces or XAML namespaces are often given in URI form, typically as a protocol-qualified absolute URI.</span></span> <span data-ttu-id="efa49-127">A menudo, la información de versión que define un vocabulario XAML determinado está implícita como parte de la cadena de ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="efa49-127">Often, version information that defines a particular XAML vocabulary is implied as part of the path string.</span></span> <span data-ttu-id="efa49-128">Los espacios de nombres XAML agregan una convención de identificador adicional más allá de la convención URI XML.</span><span class="sxs-lookup"><span data-stu-id="efa49-128">XAML namespaces add an additional identifier convention beyond the XML URI convention.</span></span> <span data-ttu-id="efa49-129">Para los espacios de nombres XAML, el identificador comunica la información que necesita un contexto de esquema XAML para resolver los tipos que se especifican como elementos en ese espacio de nombres XAML o para resolver atributos a los miembros.</span><span class="sxs-lookup"><span data-stu-id="efa49-129">For XAML namespaces, the identifier communicates information that is needed by a XAML schema context in order to resolve the types that are specified as elements under that XAML namespace, or to resolve attributes to members.</span></span>  
  
 <span data-ttu-id="efa49-130">Para comunicar información a un contexto de esquema XAML, el identificador de un espacio de nombres XAML puede seguir en forma de URI.</span><span class="sxs-lookup"><span data-stu-id="efa49-130">For purposes of communicating information to a XAML schema context, the identifier for a XAML namespace might still be in URI form.</span></span> <span data-ttu-id="efa49-131">Sin embargo, en este caso, el URI también se declara como un identificador coincidente en un ensamblado o lista de ensamblados determinado.</span><span class="sxs-lookup"><span data-stu-id="efa49-131">However, in this case the URI is also declared as a matching identifier in a particular assembly or list of assemblies.</span></span> <span data-ttu-id="efa49-132">Esto se hace en ensamblados mediante <xref:System.Windows.Markup.XmlnsDefinitionAttribute>la atribución del ensamblado con .</span><span class="sxs-lookup"><span data-stu-id="efa49-132">This is done in assemblies by attributing the assembly with <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span> <span data-ttu-id="efa49-133">Este método para identificar el espacio de nombres XAML y admitir un comportamiento de resolución de tipos basado en CLR en el ensamblado con atributos es compatible con el contexto de esquema XAML predeterminado en los servicios XAML de .NET.</span><span class="sxs-lookup"><span data-stu-id="efa49-133">This method of identifying the XAML namespace and supporting a CLR-based type resolution behavior in the attributed assembly is supported by the default XAML schema context in .NET XAML Services.</span></span> <span data-ttu-id="efa49-134">De forma más general, esta convención se puede usar para los casos en los que el contexto de esquema XAML incorpora CLR o se basa en el contexto de esquema XAML predeterminado, que es necesario para leer los atributos CLR de ensamblados CLR.</span><span class="sxs-lookup"><span data-stu-id="efa49-134">More generally, this convention can be used for cases where the XAML schema context incorporates the CLR or is based on the default XAML schema context, which is necessary in order to read CLR attributes from CLR assemblies.</span></span>  
  
 <span data-ttu-id="efa49-135">Los espacios de nombres XAML también se pueden identificar mediante una convención que comunica un espacio de nombres CLR y un ensamblado de definición de tipos.</span><span class="sxs-lookup"><span data-stu-id="efa49-135">XAML namespaces also can be identified by a convention that communicates a CLR namespace and a type-defining assembly.</span></span> <span data-ttu-id="efa49-136">Esta convención se utiliza <xref:System.Windows.Markup.XmlnsDefinitionAttribute> en casos en los que no existe ninguna atribución en los ensamblados que contienen tipos.</span><span class="sxs-lookup"><span data-stu-id="efa49-136">This convention is used in cases where no <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attribution exists in the assemblies that contain types.</span></span> <span data-ttu-id="efa49-137">Esta convención es potencialmente más compleja que la convención URI y también tiene el potencial de ambiguedad y duplicación, porque hay varias maneras de hacer referencia a un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="efa49-137">This convention is potentially more complex than the URI convention, and also has the potential for ambiguity and duplication, because there are multiple ways of referring to an assembly.</span></span>  
  
 <span data-ttu-id="efa49-138">La forma más básica de un identificador que usa el espacio de nombres CLR y la convención de ensamblado es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="efa49-138">The most basic form of an identifier that uses the CLR namespace and assembly convention is as follows:</span></span>  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 <span data-ttu-id="efa49-139">`clr-namespace:`y `; assembly=` son componentes literales de la sintaxis.</span><span class="sxs-lookup"><span data-stu-id="efa49-139">`clr-namespace:` and `; assembly=` are literal components of the syntax.</span></span>  
  
 <span data-ttu-id="efa49-140">*clrnsName* es el nombre de cadena que identifica un espacio de nombres CLR.</span><span class="sxs-lookup"><span data-stu-id="efa49-140">*clrnsName* is the string name that identifies a CLR namespace.</span></span> <span data-ttu-id="efa49-141">Este nombre de cadena incluye cualquier carácter de punto interno (.) que proporcione sugerencias sobre el espacio de nombres CLR y su relación con otros espacios de nombres CLR.</span><span class="sxs-lookup"><span data-stu-id="efa49-141">This string name includes any internal dot characters (.) that provide hints about the CLR namespace and its relation to other CLR namespaces.</span></span>
  
 <span data-ttu-id="efa49-142">*assemblyShortName* es el nombre de cadena de un ensamblado que define tipos que son útiles en XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-142">*assemblyShortName* is the string name of an assembly that defines types that are useful in XAML.</span></span> <span data-ttu-id="efa49-143">Se espera que el ensamblado defina los tipos a los que se va a tener acceso a través del espacio de nombres XAML declarado y que se declaren dentro del espacio de nombres CLR especificado por *clrnsName*.</span><span class="sxs-lookup"><span data-stu-id="efa49-143">The types to be accessed through the declared XAML namespace are expected to be defined by the assembly and to be declared within the CLR namespace specified by *clrnsName*.</span></span> <span data-ttu-id="efa49-144">Este nombre de cadena normalmente es <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>paralelo a la información según lo informado por .</span><span class="sxs-lookup"><span data-stu-id="efa49-144">This string name typically parallels the information as reported by <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="efa49-145">Una definición más completa del espacio de nombres CLR y la convención de ensamblado es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="efa49-145">A more complete definition of the CLR namespace and assembly convention is as follows:</span></span>  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 <span data-ttu-id="efa49-146">*assemblyName* representa cualquier cadena que <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> sea legal como entrada.</span><span class="sxs-lookup"><span data-stu-id="efa49-146">*assemblyName* represents any string that is legal as an <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> input.</span></span> <span data-ttu-id="efa49-147">Esta cadena puede incluir información de referencia cultural, clave pública o versión <xref:System.Reflection.Assembly>(las definiciones de estos conceptos se definen en el tema de referencia para ).</span><span class="sxs-lookup"><span data-stu-id="efa49-147">This string can include culture, public key, or version information (definitions of these concepts are defined in the reference topic for <xref:System.Reflection.Assembly>).</span></span> <span data-ttu-id="efa49-148">El formato COFF y las pruebas <xref:System.Reflection.Assembly.Load%2A>(como se usan en otras sobrecargas de ) no son relevantes para los propósitos de carga de ensamblados XAML; toda la información de carga debe presentarse como una cadena.</span><span class="sxs-lookup"><span data-stu-id="efa49-148">COFF format and evidence (as used by other overloads of <xref:System.Reflection.Assembly.Load%2A>) are not relevant for XAML assembly loading purposes; all load information must be presented as a string.</span></span>  
  
 <span data-ttu-id="efa49-149">Especificar una clave pública para el ensamblado es una técnica útil para la seguridad XAML o para quitar la posible ambiguedad que puede existir si los ensamblados se cargan por nombre simple o preexistentes en una memoria caché o dominio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="efa49-149">Specifying a public key for the assembly is a useful technique for XAML security, or for removing possible ambiguity that can exist if assemblies are loaded by simple name, or pre-exist in a cache or application domain.</span></span> <span data-ttu-id="efa49-150">Para obtener más información, vea [Consideraciones](security-considerations.md)de seguridad XAML .</span><span class="sxs-lookup"><span data-stu-id="efa49-150">For more information, see [XAML Security Considerations](security-considerations.md).</span></span>  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a><span data-ttu-id="efa49-151">Declaraciones de espacio de nombres XAML en la API de servicios XAML</span><span class="sxs-lookup"><span data-stu-id="efa49-151">XAML Namespace Declarations in the XAML Services API</span></span>  
 <span data-ttu-id="efa49-152">En la API de servicios XAML, una <xref:System.Xaml.NamespaceDeclaration> declaración de espacio de nombres XAML se representa mediante un objeto.</span><span class="sxs-lookup"><span data-stu-id="efa49-152">In the XAML Services API, a XAML namespace declaration is represented by a <xref:System.Xaml.NamespaceDeclaration> object.</span></span> <span data-ttu-id="efa49-153">Si declara un espacio de nombres XAML <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> en el código, llame al constructor.</span><span class="sxs-lookup"><span data-stu-id="efa49-153">If you are declaring a XAML namespace in code, you call the <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> constructor.</span></span> <span data-ttu-id="efa49-154">Los `ns` `prefix` parámetros y se especifican como cadenas y la entrada para proporcionar estos parámetros corresponde a la definición de identificador de espacio de nombres XAML y prefijo de espacio de nombres XAML como se proporciona anteriormente en este tema.</span><span class="sxs-lookup"><span data-stu-id="efa49-154">The `ns` and `prefix` parameters are specified as strings, and the input to provide for these parameters corresponds to the definition of XAML namespace identifier and XAML namespace prefix as provided previously in this topic.</span></span>  
  
 <span data-ttu-id="efa49-155">Si está examinando la información del espacio de nombres XAML como parte de <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> un flujo de <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> nodo XAML o a través de otro acceso al sistema de tipos XAML, notifica el identificador de espacio de nombres XAML e informa del prefijo de espacio de nombres XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-155">If you are examining XAML namespace information as part of a XAML node stream or through other access to the XAML type system, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> reports the XAML namespace identifier, and <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> reports the XAML namespace prefix.</span></span>  
  
 <span data-ttu-id="efa49-156">En un flujo de nodo XAML, la información del espacio de nombres XAML puede aparecer como un nodo XAML que precede a la entidad a la que se aplica.</span><span class="sxs-lookup"><span data-stu-id="efa49-156">In a XAML node stream, the XAML namespace information can appear as a XAML node that precedes the entity to which it applies.</span></span> <span data-ttu-id="efa49-157">Esto incluye los casos en los `StartObject` que la información del espacio de nombres XAML precede al elemento raíz XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-157">This includes cases where the XAML namespace information precedes the `StartObject` of the XAML root element.</span></span> <span data-ttu-id="efa49-158">Para obtener más información, consulta [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="efa49-158">For more information, see [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md).</span></span>  
  
 <span data-ttu-id="efa49-159">Para muchos escenarios que usan la API de servicios XAML de .NET, se espera que exista al menos una declaración de espacio de nombres XAML y la declaración debe contener o hacer referencia a la información que requiere un contexto de esquema XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-159">For many scenarios that use .NET XAML Services API, at least one XAML namespace declaration is expected to exist, and the declaration must either contain or refer to information that is required by a XAML schema context.</span></span> <span data-ttu-id="efa49-160">Los espacios de nombres XAML deben especificar los ensamblados que se van a cargar o ayudar a resolver tipos específicos dentro de espacios de nombres y ensamblados que ya están cargados o conocidos por el contexto de esquema XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-160">The XAML namespaces must either specify assemblies to be loaded, or assist in resolving specific types within namespaces and assemblies that are already loaded or known by the XAML schema context.</span></span>  
  
 <span data-ttu-id="efa49-161">Para generar un flujo de nodo XAML, la información de tipo XAML debe estar disponible, a través del contexto de esquema XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-161">In order to generate a XAML node stream, XAML type information must be available, through the XAML schema context.</span></span> <span data-ttu-id="efa49-162">La información de tipo XAML no se puede determinar sin determinar primero el espacio de nombres XAML relevante para cada nodo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="efa49-162">The XAML type information cannot be determined without first determining the relevant XAML namespace for each node to create.</span></span> <span data-ttu-id="efa49-163">En este momento, todavía no se ha creado ninguna instancia de tipos, pero es posible que el contexto del esquema XAML deba buscar información del ensamblado de definición y el tipo de respaldo.</span><span class="sxs-lookup"><span data-stu-id="efa49-163">At this point, no instances of types are created yet, but the XAML schema context may need to look up information from the defining assembly and backing type.</span></span> <span data-ttu-id="efa49-164">Por ejemplo, para procesar `<Party><PartyFavor/></Party>`el marcado , el contexto de esquema XAML `ContentProperty` debe `Party`ser capaz de determinar el `Party` nombre `PartyFavor`y el tipo de la de , y por lo tanto también debe conocer la información de espacio de nombres XAML para y .</span><span class="sxs-lookup"><span data-stu-id="efa49-164">For example, in order to process the markup `<Party><PartyFavor/></Party>`, the XAML schema context must be able to determine the name and type of the `ContentProperty` of `Party`, and thus also must know the XAML namespace information for `Party` and `PartyFavor`.</span></span> <span data-ttu-id="efa49-165">En el caso del contexto de esquema XAML predeterminado, la reflexión estática notifica gran parte de la información del sistema de tipos XAML necesaria para generar nodos de tipo XAML en el flujo de nodo.</span><span class="sxs-lookup"><span data-stu-id="efa49-165">In the case of the default XAML schema context, static reflection reports much of the XAML type system information that is needed to generate XAML type nodes in the node stream.</span></span>  
  
 <span data-ttu-id="efa49-166">Para generar un gráfico de objetos a partir de un flujo de nodo XAML, deben existir declaraciones de espacio de nombres XAML para cada prefijo XAML utilizado en el marcado original y registrado en el flujo de nodo XAML.</span><span class="sxs-lookup"><span data-stu-id="efa49-166">In order to generate an object graph from a XAML node stream, XAML namespace declarations must exist for each XAML prefix used in the original markup and recorded in the XAML node stream.</span></span> <span data-ttu-id="efa49-167">En este punto, se están creando instancias y se produce un comportamiento de asignación de tipos verdadero.</span><span class="sxs-lookup"><span data-stu-id="efa49-167">At this point, instances are being created, and true type-mapping behavior occurs.</span></span>  
  
 <span data-ttu-id="efa49-168">Si necesita rellenar previamente la información del espacio de nombres XAML, en los casos en los que el espacio de nombres XAML <xref:System.Xml.XmlParserContext> que <xref:System.Xml.XmlReader>desea usar el contexto de esquema XAML no está definido en el marcado, una técnica que puede usar es declarar declaraciones de espacio de nombres XML en el for an .</span><span class="sxs-lookup"><span data-stu-id="efa49-168">If you need to prepopulate XAML namespace information, in cases where the XAML namespace you intend the XAML schema context to use is not defined in the markup, one technique you can use is to declare XML namespace declarations in the <xref:System.Xml.XmlParserContext> for an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="efa49-169">A continuación, úselo <xref:System.Xml.XmlReader> como entrada <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>para un constructor de lector XAML o .</span><span class="sxs-lookup"><span data-stu-id="efa49-169">Then use that <xref:System.Xml.XmlReader> as input for a XAML reader constructor, or <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="efa49-170">Otras dos API que son relevantes para el control <xref:System.Windows.Markup.XmlnsDefinitionAttribute> de <xref:System.Windows.Markup.XmlnsPrefixAttribute>espacios de nombres XAML en .NET XAML Services son los atributos y .</span><span class="sxs-lookup"><span data-stu-id="efa49-170">Two other APIs that are relevant for XAML namespace handling in .NET XAML Services are the attributes <xref:System.Windows.Markup.XmlnsDefinitionAttribute> and <xref:System.Windows.Markup.XmlnsPrefixAttribute>.</span></span> <span data-ttu-id="efa49-171">Estos atributos se aplican a los ensamblados.</span><span class="sxs-lookup"><span data-stu-id="efa49-171">These attributes apply to assemblies.</span></span> <span data-ttu-id="efa49-172"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>un contexto de esquema XAML lo usa para interpretar cualquier declaración de espacio de nombres XAML que incluya un URI.</span><span class="sxs-lookup"><span data-stu-id="efa49-172"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> is used by a XAML schema context to interpret any XAML namespace declaration that includes a URI.</span></span> <span data-ttu-id="efa49-173"><xref:System.Windows.Markup.XmlnsPrefixAttribute>las herramientas que emiten XAML para que un espacio de nombres XAML determinado se pueda serializar con un prefijo de predicción.</span><span class="sxs-lookup"><span data-stu-id="efa49-173"><xref:System.Windows.Markup.XmlnsPrefixAttribute> is used by tools that emit XAML so that a particular XAML namespace can be serialized with a predictable prefix.</span></span> <span data-ttu-id="efa49-174">Para obtener más información, vea [Atributos CLR relacionados con XAML para bibliotecas y tipos personalizados.](clr-attributes-with-custom-types-and-libraries.md)</span><span class="sxs-lookup"><span data-stu-id="efa49-174">For more information, see [XAML-Related CLR Attributes for Custom Types and Libraries](clr-attributes-with-custom-types-and-libraries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa49-175">Consulte también</span><span class="sxs-lookup"><span data-stu-id="efa49-175">See also</span></span>

- [<span data-ttu-id="efa49-176">Introducción a las estructuras y conceptos de secuencias de nodo XAML</span><span class="sxs-lookup"><span data-stu-id="efa49-176">Understanding XAML Node Stream Structures and Concepts</span></span>](understanding-xaml-node-stream-structures-and-concepts.md)