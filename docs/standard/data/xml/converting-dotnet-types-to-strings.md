---
title: Conversión de tipos de .NET en cadenas
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: ca35af17a402dc901c02edf94099af1377e1160f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687634"
---
# <a name="convert-net-types-to-strings"></a><span data-ttu-id="26143-102">Conversión de tipos de .NET en cadenas</span><span class="sxs-lookup"><span data-stu-id="26143-102">Convert .NET types to strings</span></span>

<span data-ttu-id="26143-103">Si quiere convertir un tipo de .NET en una cadena, use el método **ToString**.</span><span class="sxs-lookup"><span data-stu-id="26143-103">If you want to convert a .NET type to a string, use the **ToString** method.</span></span> <span data-ttu-id="26143-104">El método **ToString** devuelve una representación de cadena del tipo que se le pasa.</span><span class="sxs-lookup"><span data-stu-id="26143-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="26143-105">En la tabla siguiente se enumeran los tipos de .NET que devuelven una cadena en un formato que se asigna a las especificaciones de los esquemas XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="26143-105">The following table lists the .NET types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="26143-106">Tipo de .NET</span><span class="sxs-lookup"><span data-stu-id="26143-106">.NET type</span></span>|<span data-ttu-id="26143-107">Tipo de cadena devuelta</span><span class="sxs-lookup"><span data-stu-id="26143-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="26143-108">Booleano</span><span class="sxs-lookup"><span data-stu-id="26143-108">Boolean</span></span>|<span data-ttu-id="26143-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="26143-109">"true", "false"</span></span>|  
|<span data-ttu-id="26143-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="26143-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="26143-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="26143-111">"INF"</span></span>|  
|<span data-ttu-id="26143-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="26143-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="26143-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="26143-113">"-INF"</span></span>|  
|<span data-ttu-id="26143-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="26143-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="26143-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="26143-115">"INF"</span></span>|  
|<span data-ttu-id="26143-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="26143-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="26143-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="26143-117">"-INF"</span></span>|  
|<span data-ttu-id="26143-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="26143-118">DateTime</span></span>|<span data-ttu-id="26143-119">El formato es aaaa-MM-ddTHH:mm:sszzzzzz y sus subconjuntos.</span><span class="sxs-lookup"><span data-stu-id="26143-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="26143-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="26143-120">Timespan</span></span>|<span data-ttu-id="26143-121">El formato es PnYnMnTnHnMnS, por ejemplo, `P2Y10M15DT10H30M20S` corresponde a una duración de 2 años, 10 meses, 15 días, 10 horas, 30 minutos y 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="26143-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26143-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="26143-122">See also</span></span>

- [<span data-ttu-id="26143-123">Conversión de tipos de datos XML</span><span class="sxs-lookup"><span data-stu-id="26143-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="26143-124">Conversión de cadenas en tipos de datos de .NET</span><span class="sxs-lookup"><span data-stu-id="26143-124">Converting Strings to .NET Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
