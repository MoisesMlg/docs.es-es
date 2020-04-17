---
title: Consideraciones de seguridad sobre XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2020
ms.locfileid: "81432921"
---
# <a name="xaml-security-considerations"></a><span data-ttu-id="381d9-102">Consideraciones de seguridad XAML</span><span class="sxs-lookup"><span data-stu-id="381d9-102">XAML security considerations</span></span>

<span data-ttu-id="381d9-103">En este artículo se describen los procedimientos recomendados para la seguridad en las aplicaciones cuando se usa XAML y la API de servicios XAML de .NET.</span><span class="sxs-lookup"><span data-stu-id="381d9-103">This article describes best practices for security in applications when you use XAML and .NET XAML Services API.</span></span>

## <a name="untrusted-xaml-in-applications"></a><span data-ttu-id="381d9-104">XAML que no es de confianza en aplicaciones</span><span class="sxs-lookup"><span data-stu-id="381d9-104">Untrusted XAML in Applications</span></span>

<span data-ttu-id="381d9-105">En el sentido más general, XAML que no es de confianza es cualquier origen XAML que la aplicación no incluyó o emitió específicamente.</span><span class="sxs-lookup"><span data-stu-id="381d9-105">In the most general sense, untrusted XAML is any XAML source that your application did not specifically include or emit.</span></span>

<span data-ttu-id="381d9-106">XAML que se compila o `resx`almacena como un recurso de tipo dentro de un ensamblado de confianza y firmado no es inherentemente de confianza.</span><span class="sxs-lookup"><span data-stu-id="381d9-106">XAML that is compiled into or stored as a `resx`-type resource within a trusted and signed assembly is not inherently untrusted.</span></span> <span data-ttu-id="381d9-107">Puede confiar en el XAML tanto como confíe en el ensamblado en su conjunto.</span><span class="sxs-lookup"><span data-stu-id="381d9-107">You can trust the XAML as much as you trust the assembly as a whole.</span></span> <span data-ttu-id="381d9-108">En la mayoría de los casos, solo te preocupan los aspectos de confianza de XAML suelto, que es un origen XAML que se carga desde una secuencia u otra E/S.</span><span class="sxs-lookup"><span data-stu-id="381d9-108">In most cases, you are only concerned with the trust aspects of loose XAML, which is a XAML source that you load from a stream or other I/O.</span></span> <span data-ttu-id="381d9-109">XAML suelto no es un componente específico o característica de un modelo de aplicación con una infraestructura de implementación y empaquetado.</span><span class="sxs-lookup"><span data-stu-id="381d9-109">Loose XAML is not a specific component or feature of an application model with a deployment and packaging infrastructure.</span></span> <span data-ttu-id="381d9-110">Sin embargo, un ensamblado podría implementar un comportamiento que implica cargar XAML suelto.</span><span class="sxs-lookup"><span data-stu-id="381d9-110">However, an assembly might implement a behavior that involves loading loose XAML.</span></span>

<span data-ttu-id="381d9-111">Para XAML que no es de confianza, debe tratarlo generalmente igual que si fuera código que no es de confianza.</span><span class="sxs-lookup"><span data-stu-id="381d9-111">For untrusted XAML, you should treat it generally the same as if it were untrusted code.</span></span> <span data-ttu-id="381d9-112">Usa el espacio aislado u otras metáforas para evitar que XAML posiblemente no sea de confianza tenga acceso al código de confianza.</span><span class="sxs-lookup"><span data-stu-id="381d9-112">Use sandboxing or other metaphors to prevent possibly untrusted XAML from accessing your trusted code.</span></span>

<span data-ttu-id="381d9-113">La naturaleza de las capacidades XAML da al XAML el derecho de construir objetos y establecer sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="381d9-113">The nature of XAML capabilities gives the XAML the right to construct objects and set their properties.</span></span> <span data-ttu-id="381d9-114">Estas capacidades también incluyen el acceso a convertidores de tipos, `x:Code` la asignación y el acceso a ensamblados en el dominio de aplicación, mediante extensiones de marcado, bloques, etc.</span><span class="sxs-lookup"><span data-stu-id="381d9-114">These capabilities also include accessing type converters, mapping and accessing assemblies in the application domain, using markup extensions, `x:Code` blocks, and so on.</span></span>

<span data-ttu-id="381d9-115">Además de sus capacidades de nivel de lenguaje, XAML se usa para la definición de interfaz de usuario en muchas tecnologías.</span><span class="sxs-lookup"><span data-stu-id="381d9-115">In addition to its language-level capabilities, XAML is used for UI definition in many technologies.</span></span> <span data-ttu-id="381d9-116">Cargar XAML que no es de confianza puede significar cargar una interfaz de usuario de suplantación malintencionada.</span><span class="sxs-lookup"><span data-stu-id="381d9-116">Loading untrusted XAML might mean loading a malicious spoofing UI.</span></span>

## <a name="sharing-context-between-readers-and-writers"></a><span data-ttu-id="381d9-117">Compartir contexto entre lectores y escritores</span><span class="sxs-lookup"><span data-stu-id="381d9-117">Sharing Context Between Readers and Writers</span></span>

<span data-ttu-id="381d9-118">La arquitectura de servicios XAML de .NET para lectores XAML y escritores XAML a menudo requiere compartir un lector XAML en un escritor XAML o en un contexto de esquema XAML compartido.</span><span class="sxs-lookup"><span data-stu-id="381d9-118">.NET XAML Services architecture for XAML readers and XAML writers often requires sharing a XAML reader to a XAML writer, or a shared XAML schema context.</span></span> <span data-ttu-id="381d9-119">Es posible que sea necesario compartir objetos o contextos si escribes lógica de bucle de nodo XAML o proporcionas una ruta de acceso de guardado personalizada.</span><span class="sxs-lookup"><span data-stu-id="381d9-119">Sharing objects or contexts might be required if you are writing XAML node loop logic, or providing a custom save path.</span></span> <span data-ttu-id="381d9-120">No compartas instancias de lector XAML, contexto de esquema XAML no predeterminado ni configuración para clases de lector/escritor XAML entre código de confianza y código que no es de confianza.</span><span class="sxs-lookup"><span data-stu-id="381d9-120">Don't share XAML reader instances, nondefault XAML schema context, or settings for XAML reader/writer classes between trusted and untrusted code.</span></span>

<span data-ttu-id="381d9-121">La mayoría de los escenarios y operaciones que implican la escritura de objetos XAML para una copia de seguridad de tipos basada en CLR solo pueden usar el contexto de esquema XAML predeterminado.</span><span class="sxs-lookup"><span data-stu-id="381d9-121">Most scenarios and operations involving XAML object writing for a CLR-based type backing can just use default XAML schema context.</span></span> <span data-ttu-id="381d9-122">El contexto de esquema XAML predeterminado no incluye explícitamente la configuración que podría poner en peligro la plena confianza.</span><span class="sxs-lookup"><span data-stu-id="381d9-122">The default XAML schema context does not explicitly include settings that could compromise full trust.</span></span> <span data-ttu-id="381d9-123">Por lo tanto, es seguro compartir el contexto entre componentes de lector/escritor XAML de confianza y que no son de confianza.</span><span class="sxs-lookup"><span data-stu-id="381d9-123">It is thus safe to share context between trusted and untrusted XAML reader/writer components.</span></span> <span data-ttu-id="381d9-124">Sin embargo, si lo hace, sigue siendo una práctica recomendada <xref:System.AppDomain> mantener a dichos lectores y escritores en ámbitos separados, con uno de ellos específicamente pensado/sandboxed para la confianza parcial.</span><span class="sxs-lookup"><span data-stu-id="381d9-124">However, if you do this, it is still a best practice to keep such readers and writers in separate <xref:System.AppDomain> scopes, with one of them specifically intended/sandboxed for partial trust.</span></span>

## <a name="xaml-namespaces-and-assembly-trust"></a><span data-ttu-id="381d9-125">Espacios de nombres XAML y confianza de ensamblado</span><span class="sxs-lookup"><span data-stu-id="381d9-125">XAML Namespaces and Assembly Trust</span></span>

<span data-ttu-id="381d9-126">La sintaxis y definición básicas no calificadas para saber cómo XAML interpreta una asignación de espacio de nombres XAML personalizada a un ensamblado no distingue entre un ensamblado de confianza y no confiable como cargado en el dominio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="381d9-126">The basic unqualified syntax and definition for how XAML interprets a custom XAML namespace mapping to an assembly does not distinguish between a trusted and untrusted assembly as loaded into the application domain.</span></span> <span data-ttu-id="381d9-127">Por lo tanto, es técnicamente posible que un ensamblado que no es de confianza suplantar la asignación de espacio de nombres XAML prevista de un ensamblado de confianza y capturar la información de objeto y propiedad declarada de un origen XAML.</span><span class="sxs-lookup"><span data-stu-id="381d9-127">Thus, it is technically possible for an untrusted assembly to spoof a trusted assembly's intended XAML namespace mapping and capture a XAML source's declared object and property information.</span></span> <span data-ttu-id="381d9-128">Si tiene requisitos de seguridad para evitar esta situación, la asignación de espacio de nombres XAML prevista debe realizarse mediante una de las siguientes técnicas:</span><span class="sxs-lookup"><span data-stu-id="381d9-128">If you have security requirements to avoid this situation, your intended XAML namespace mapping should be made using one of the following techniques:</span></span>

- <span data-ttu-id="381d9-129">Usa un nombre de ensamblado completo con nombre seguro en cualquier asignación de espacio de nombres XAML realizada por XAML de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="381d9-129">Use a fully qualified assembly name with strong name in any XAML namespace mapping made by your application's XAML.</span></span>

- <span data-ttu-id="381d9-130">Restringir la asignación de ensamblados a un conjunto <xref:System.Xaml.XamlSchemaContext> fijo de ensamblados de referencia, mediante la construcción de un específico para los lectores XAML y escritores de objetos XAML.</span><span class="sxs-lookup"><span data-stu-id="381d9-130">Restrict assembly mapping to a fixed set of reference assemblies, by constructing a specific <xref:System.Xaml.XamlSchemaContext> for your XAML readers and XAML object writers.</span></span> <span data-ttu-id="381d9-131">Vea <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="381d9-131">See <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.</span></span>

## <a name="xaml-type-mapping-and-type-system-access"></a><span data-ttu-id="381d9-132">Asignación de tipos XAML y acceso al sistema de tipos</span><span class="sxs-lookup"><span data-stu-id="381d9-132">XAML Type Mapping and Type System Access</span></span>

<span data-ttu-id="381d9-133">XAML admite su propio sistema de tipos, que en muchos sentidos es un elemento del mismo nivel para cómo CLR implementa el sistema de tipos CLR básico.</span><span class="sxs-lookup"><span data-stu-id="381d9-133">XAML supports its own type system, which in many ways is a peer to how CLR implements the basic CLR type system.</span></span> <span data-ttu-id="381d9-134">Sin embargo, para ciertos aspectos de la conciencia de tipo donde está tomando decisiones de confianza sobre un tipo basado en su información de tipo, debe aplazar la información de tipo en los tipos de respaldo de CLR.</span><span class="sxs-lookup"><span data-stu-id="381d9-134">However, for certain aspects of type awareness where you are making trust decisions about a type based on its type information, you should defer to the type information in the CLR backing types.</span></span> <span data-ttu-id="381d9-135">Esto se debe a que algunas de las capacidades de informes específicas del sistema de tipos XAML se dejan abiertas como métodos virtuales y, por lo tanto, no están totalmente bajo el control de las implementaciones originales de servicios XAML de .NET.</span><span class="sxs-lookup"><span data-stu-id="381d9-135">This is because some of the specific reporting capabilities of the XAML type system are left open as virtual methods and are therefore, not fully under the control of the original .NET XAML Services implementations.</span></span> <span data-ttu-id="381d9-136">Estos puntos de extensibilidad existen porque el sistema de tipos XAML es extensible, para que coincida con la extensibilidad del propio XAML y sus posibles estrategias alternativas de asignación de tipos frente a la implementación respaldada por CLR predeterminada y el contexto de esquema XAML predeterminado.</span><span class="sxs-lookup"><span data-stu-id="381d9-136">These extensibility points exist because the XAML type system is extensible, to match the extensibility of XAML itself and its possible alternative type-mapping strategies versus the default CLR-backed implementation and default XAML schema context.</span></span> <span data-ttu-id="381d9-137">Para obtener más información, consulte las notas <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>específicas sobre varias de las propiedades de y .</span><span class="sxs-lookup"><span data-stu-id="381d9-137">For more information, see the specific notes on several of the properties of <xref:System.Xaml.XamlType> and <xref:System.Xaml.XamlMember>.</span></span>

## <a name="see-also"></a><span data-ttu-id="381d9-138">Consulte también</span><span class="sxs-lookup"><span data-stu-id="381d9-138">See also</span></span>

- <xref:System.Xaml.Permissions.XamlAccessLevel>