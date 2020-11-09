---
title: Operaciones básicas de cadenas en .NET
description: Obtenga información sobre las operaciones básicas que puede realizar en las cadenas.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 4ab087435880c6a5357bc161899cd585982622f4
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342610"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="b87f1-103">Operaciones básicas de cadenas en .NET</span><span class="sxs-lookup"><span data-stu-id="b87f1-103">Basic string operations in .NET</span></span>

<span data-ttu-id="b87f1-104">A menudo, las aplicaciones responden a los usuarios mediante la construcción de mensajes basados en los datos proporcionados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b87f1-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="b87f1-105">Por ejemplo, no es raro que los sitios web respondan a un usuario que acaba de iniciar sesión con un saludo especializado que incluye el nombre del usuario.</span><span class="sxs-lookup"><span data-stu-id="b87f1-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="b87f1-106">Varios métodos de las clases <xref:System.String?displayProperty=nameWithType> y <xref:System.Text.StringBuilder?displayProperty=nameWithType> le permiten construir cadenas personalizadas de forma dinámica para mostrarlas en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="b87f1-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="b87f1-107">Estos métodos también le ayudan a realizar una serie de operaciones básicas de cadenas, como crear cadenas nuevas a partir de matrices de bytes, comparar los valores de cadenas y modificar cadenas existentes.</span><span class="sxs-lookup"><span data-stu-id="b87f1-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b87f1-108">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="b87f1-108">Related sections</span></span>

<span data-ttu-id="b87f1-109">[Conversión de tipos en .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="b87f1-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="b87f1-110">Se describe cómo convertir un tipo en otro.</span><span class="sxs-lookup"><span data-stu-id="b87f1-110">Describes how to convert one type into another type.</span></span>

<span data-ttu-id="b87f1-111">[Aplicar formato a tipos](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="b87f1-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="b87f1-112">Se describe cómo dar formato a cadenas mediante los especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="b87f1-112">Describes how to format strings using format specifiers.</span></span>
