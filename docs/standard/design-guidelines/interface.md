---
title: Diseño de interfaces
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 6f8cbb757ffb42f63903b212fee33cdcbba7ecb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727684"
---
# <a name="interface-design"></a><span data-ttu-id="567fe-102">Diseño de interfaces</span><span class="sxs-lookup"><span data-stu-id="567fe-102">Interface Design</span></span>

<span data-ttu-id="567fe-103">Aunque la mayoría de las API se modelan mejor mediante clases y Structs, hay casos en los que las interfaces son más adecuadas o son la única opción.</span><span class="sxs-lookup"><span data-stu-id="567fe-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="567fe-104">CLR no admite la herencia múltiple (es decir, las clases CLR no pueden heredar de más de una clase base), pero permite que los tipos implementen una o varias interfaces además de heredar de una clase base.</span><span class="sxs-lookup"><span data-stu-id="567fe-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="567fe-105">Por lo tanto, las interfaces se usan a menudo para lograr el efecto de la herencia múltiple.</span><span class="sxs-lookup"><span data-stu-id="567fe-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="567fe-106">Por ejemplo, <xref:System.IDisposable> es una interfaz que permite que los tipos admitan la eliminación independientemente de cualquier otra jerarquía de herencia en la que deseen participar.</span><span class="sxs-lookup"><span data-stu-id="567fe-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="567fe-107">La otra situación en la que la definición de una interfaz es adecuada es crear una interfaz común que pueda ser compatible con varios tipos, incluidos algunos tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="567fe-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="567fe-108">Los tipos de valor no pueden heredar de tipos distintos de <xref:System.ValueType> , pero pueden implementar interfaces, por lo que el uso de una interfaz es la única opción para proporcionar un tipo base común.</span><span class="sxs-lookup"><span data-stu-id="567fe-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="567fe-109">✔️ definir una interfaz si necesita que una API común sea compatible con un conjunto de tipos que incluye tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="567fe-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="567fe-110">✔️ considere la posibilidad de definir una interfaz si necesita admitir su funcionalidad en tipos que ya heredan de algún otro tipo.</span><span class="sxs-lookup"><span data-stu-id="567fe-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="567fe-111">❌ Evite el uso de interfaces de marcador (interfaces sin miembros).</span><span class="sxs-lookup"><span data-stu-id="567fe-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="567fe-112">Si necesita marcar una clase como una característica específica (marcador), en general, use un atributo personalizado en lugar de una interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="567fe-113">✔️ proporcionan al menos un tipo que es una implementación de una interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="567fe-114">Esto ayuda a validar el diseño de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="567fe-115">Por ejemplo, <xref:System.Collections.Generic.List%601> es una implementación de la <xref:System.Collections.Generic.IList%601> interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="567fe-116">✔️ proporcionan al menos una API que consume cada interfaz que defina (un método que toma la interfaz como un parámetro o una propiedad con el tipo de interfaz).</span><span class="sxs-lookup"><span data-stu-id="567fe-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="567fe-117">Esto ayuda a validar el diseño de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="567fe-118">Por ejemplo, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consume la <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="567fe-119">❌ NO agregue miembros a una interfaz que se haya enviado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="567fe-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="567fe-120">Si lo hace, se interrumpirán las implementaciones de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="567fe-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="567fe-121">Debe crear una nueva interfaz con el fin de evitar problemas de control de versiones.</span><span class="sxs-lookup"><span data-stu-id="567fe-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="567fe-122">A excepción de las situaciones descritas en estas instrucciones, debe, en general, elegir clases en lugar de interfaces al diseñar bibliotecas reutilizables de código administrado.</span><span class="sxs-lookup"><span data-stu-id="567fe-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="567fe-123">*Partes © 2005, 2009 Microsoft Corporation. Todos los derechos reservados.*</span><span class="sxs-lookup"><span data-stu-id="567fe-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="567fe-124">*Material reimpreso con el consentimiento de Pearson Education, Inc. y extraído de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) (Instrucciones de diseño de .NET Framework: convenciones, expresiones y patrones para bibliotecas .NET reutilizables, 2.ª edición), de Krzysztof Cwalina y Brad Abrams, publicado el 22 de octubre de 2008 por Addison-Wesley Professional como parte de la serie Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="567fe-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="567fe-125">Consulte también</span><span class="sxs-lookup"><span data-stu-id="567fe-125">See also</span></span>

- [<span data-ttu-id="567fe-126">Instrucciones de diseño de tipos</span><span class="sxs-lookup"><span data-stu-id="567fe-126">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="567fe-127">Directrices de diseño de marco</span><span class="sxs-lookup"><span data-stu-id="567fe-127">Framework Design Guidelines</span></span>](index.md)
