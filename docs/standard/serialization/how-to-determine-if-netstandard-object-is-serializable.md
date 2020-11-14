---
title: Procedimiento para determinar si un objeto de .NET Standard es serializable
description: Se explica cómo determinar si un tipo de .NET Standard se puede serializar en tiempo de ejecución.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 9f7ab8a824b9687f68382a5edc342536289c5d09
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282330"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="7af5b-103">Procedimiento para determinar si un objeto de .NET Standard es serializable</span><span class="sxs-lookup"><span data-stu-id="7af5b-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="7af5b-104">.NET Standard es una especificación que define los tipos y miembros que debe haber en implementaciones concretas de .NET que se ajusten a esa versión del estándar.</span><span class="sxs-lookup"><span data-stu-id="7af5b-104">.NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="7af5b-105">Pero .NET Standard no define si un tipo es serializable.</span><span class="sxs-lookup"><span data-stu-id="7af5b-105">However, .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="7af5b-106">Los tipos definidos en la biblioteca de .NET Standard no están marcados con el atributo <xref:System.SerializableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7af5b-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="7af5b-107">En su lugar, son las implementaciones de .NET específicas, como .NET Framework y .NET Core, las que deciden libremente si un tipo determinado es serializable.</span><span class="sxs-lookup"><span data-stu-id="7af5b-107">Instead, specific .NET implementations, such as .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="7af5b-108">Si ha desarrollado una biblioteca que tiene como destino .NET Standard, cualquier implementación de .NET que admita .NET Standard puede usar la biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7af5b-108">If you've developed a library that targets .NET Standard, your library can be consumed by any .NET implementation that supports .NET Standard.</span></span> <span data-ttu-id="7af5b-109">Esto significa que no se puede saber con antelación si un tipo determinado es serializable; solo se sabrá en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="7af5b-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="7af5b-110">Para determinar si un objeto es serializable en tiempo de ejecución, hay que recuperar el valor de la propiedad <xref:System.Type.IsSerializable> de un objeto <xref:System.Type> que representa el tipo de ese objeto.</span><span class="sxs-lookup"><span data-stu-id="7af5b-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="7af5b-111">En el siguiente ejemplo se proporciona una implementación.</span><span class="sxs-lookup"><span data-stu-id="7af5b-111">The following example provides one implementation.</span></span> <span data-ttu-id="7af5b-112">En él se define un método de extensión `IsSerializable(Object)` que indica si cualquier instancia de <xref:System.Object> se puede serializar.</span><span class="sxs-lookup"><span data-stu-id="7af5b-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="7af5b-113">Después, se puede pasar cualquier objeto al método para determinar si se puede serializar y deserializar en la implementación actual de .NET, como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7af5b-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7af5b-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="7af5b-114">See also</span></span>

- [<span data-ttu-id="7af5b-115">Serialización binaria</span><span class="sxs-lookup"><span data-stu-id="7af5b-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
