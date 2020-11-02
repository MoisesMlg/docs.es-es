---
title: Revisión de adaptabilidad
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET], localization
- localizability [.NET]
- international applications [.NET], localizability
- globalization [.NET], localizability
- culture, localizability
- localization [.NET], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
ms.openlocfilehash: 6aa0588ea4baa00be476a05c335cf2abaa22aab4
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064163"
---
# <a name="localizability-review"></a><span data-ttu-id="fee67-102">Revisión de localizabilidad</span><span class="sxs-lookup"><span data-stu-id="fee67-102">Localizability review</span></span>

<span data-ttu-id="fee67-103">La revisión de localización es un paso intermedio en el desarrollo de una aplicación de uso internacional.</span><span class="sxs-lookup"><span data-stu-id="fee67-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="fee67-104">Comprueba que una aplicación globalizada está preparada para la localización e identifica cualquier código o los aspectos de la interfaz de usuario que requieren un tratamiento especial.</span><span class="sxs-lookup"><span data-stu-id="fee67-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="fee67-105">Este paso también ayuda a asegurarse de que el proceso de localización no introducirá defectos funcionales en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fee67-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="fee67-106">Una vez solucionados todos los problemas que planteó la revisión de localización, la aplicación estará lista para la localización.</span><span class="sxs-lookup"><span data-stu-id="fee67-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="fee67-107">Si la revisión de localización es exhaustiva, no tiene que modificar ningún código fuente durante el proceso de localización.</span><span class="sxs-lookup"><span data-stu-id="fee67-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="fee67-108">La revisión de localización consta de las tres comprobaciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="fee67-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="fee67-109">¿Se han implementado las recomendaciones de globalización?</span><span class="sxs-lookup"><span data-stu-id="fee67-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="fee67-110">¿Las características que tienen en cuenta las referencias culturales se han controlado correctamente?</span><span class="sxs-lookup"><span data-stu-id="fee67-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="fee67-111">¿Ha probado la aplicación con datos internacionales?</span><span class="sxs-lookup"><span data-stu-id="fee67-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="fee67-112">Implementación de recomendaciones de globalización</span><span class="sxs-lookup"><span data-stu-id="fee67-112">Implement globalization recommendations</span></span>

<span data-ttu-id="fee67-113">Si ha diseñado y desarrollado la aplicación con la localización en mente y, además, si ha seguido las recomendaciones indicadas en el artículo [Globalización](globalization.md), la revisión de localización, en gran medida, será un paso para el control de calidad.</span><span class="sxs-lookup"><span data-stu-id="fee67-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="fee67-114">Sin embargo, durante esta fase, debe revisar e implementar las recomendaciones de [globalización](globalization.md) y corregir los errores del código fuente que impiden la localización.</span><span class="sxs-lookup"><span data-stu-id="fee67-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="fee67-115">Control de características que tienen en cuenta la referencia cultural</span><span class="sxs-lookup"><span data-stu-id="fee67-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="fee67-116">.NET no proporciona soporte técnico de programación en un número de áreas que varían enormemente según la referencia cultural.</span><span class="sxs-lookup"><span data-stu-id="fee67-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="fee67-117">En la mayoría de los casos, tendrá que escribir código personalizado para controlar áreas de características como las siguientes:</span><span class="sxs-lookup"><span data-stu-id="fee67-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="fee67-118">Direcciones</span><span class="sxs-lookup"><span data-stu-id="fee67-118">Addresses</span></span>

- <span data-ttu-id="fee67-119">Números de teléfono</span><span class="sxs-lookup"><span data-stu-id="fee67-119">Telephone numbers</span></span>

- <span data-ttu-id="fee67-120">Tamaños de papel</span><span class="sxs-lookup"><span data-stu-id="fee67-120">Paper sizes</span></span>

- <span data-ttu-id="fee67-121">Unidades de medida usadas para longitud, peso, área, volumen y temperatura</span><span class="sxs-lookup"><span data-stu-id="fee67-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="fee67-122">Aunque .NET no ofrece compatibilidad integrada para la conversión entre unidades de medida, puede utilizar la propiedad <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> para determinar si un determinado país o región utiliza el sistema métrico, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="fee67-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="fee67-123">Probar la aplicación</span><span class="sxs-lookup"><span data-stu-id="fee67-123">Test your application</span></span>

<span data-ttu-id="fee67-124">Para localizar la aplicación, debe probarla mediante el uso de datos internacionales en versiones internacionales del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="fee67-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="fee67-125">Aunque la mayor parte de la interfaz de usuario no se localizará en este momento, podrá detectar problemas como los siguientes:</span><span class="sxs-lookup"><span data-stu-id="fee67-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="fee67-126">Datos serializados que no se deserializan correctamente en las versiones del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="fee67-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="fee67-127">Datos numéricos que no reflejan las convenciones de la referencia cultural actual.</span><span class="sxs-lookup"><span data-stu-id="fee67-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="fee67-128">Por ejemplo, pueden mostrarse números con separadores de grupos, separadores decimales o símbolos de moneda inexactos.</span><span class="sxs-lookup"><span data-stu-id="fee67-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="fee67-129">Los datos de fecha y hora no reflejan las convenciones de la referencia cultural actual.</span><span class="sxs-lookup"><span data-stu-id="fee67-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="fee67-130">Por ejemplo, los números que representan el mes y día pueden aparecer en el orden equivocado, los separadores de fecha pueden ser incorrectos o la información de zona horaria puede ser incorrecta.</span><span class="sxs-lookup"><span data-stu-id="fee67-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="fee67-131">Los recursos que no se pueden encontrar porque no se ha identificado una referencia cultural predeterminada para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fee67-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="fee67-132">Las cadenas que se muestran en un orden inusual para la referencia cultural específica.</span><span class="sxs-lookup"><span data-stu-id="fee67-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="fee67-133">Las comparaciones de cadenas o las comparaciones de igualdad que devuelven resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="fee67-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="fee67-134">Si ha seguido las recomendaciones de globalización al desarrollar la aplicación, ha controlado correctamente las características que tienen en cuenta la referencia cultural y ha identificado y solucionado los problemas de localización planteados durante las pruebas, puede continuar con el paso siguiente, [Localización](localization.md).</span><span class="sxs-lookup"><span data-stu-id="fee67-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fee67-135">Vea también</span><span class="sxs-lookup"><span data-stu-id="fee67-135">See also</span></span>

- [<span data-ttu-id="fee67-136">Globalización y localización</span><span class="sxs-lookup"><span data-stu-id="fee67-136">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="fee67-137">Localización</span><span class="sxs-lookup"><span data-stu-id="fee67-137">Localization</span></span>](localization.md)
- [<span data-ttu-id="fee67-138">Globalización</span><span class="sxs-lookup"><span data-stu-id="fee67-138">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="fee67-139">Recursos de aplicaciones de escritorio</span><span class="sxs-lookup"><span data-stu-id="fee67-139">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
