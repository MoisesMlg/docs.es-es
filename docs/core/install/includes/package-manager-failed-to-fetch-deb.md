---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920661"
---

<span data-ttu-id="3eabe-101">Al instalar el paquete de .NET Core, puede ver un error similar a `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span><span class="sxs-lookup"><span data-stu-id="3eabe-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="3eabe-102">En términos generales, este error significa que la fuente de paquetes para .NET Core se está actualizando con versiones de paquetes más recientes y que debe volver a intentarlo más tarde.</span><span class="sxs-lookup"><span data-stu-id="3eabe-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="3eabe-103">Durante una actualización, la fuente de paquetes no debe estar disponible durante más de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="3eabe-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="3eabe-104">Si recibe este error continuamente durante más de 30 minutos, abra una incidencia en <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="3eabe-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>