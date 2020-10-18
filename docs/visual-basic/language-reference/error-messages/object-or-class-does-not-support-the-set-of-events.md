---
title: El objeto o la clase no admite el conjunto de eventos
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: c5e8b8de3477147fc3174cdbee401c89753004ad
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159955"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="2d029-102">El objeto o la clase no admite el conjunto de eventos</span><span class="sxs-lookup"><span data-stu-id="2d029-102">Object or class does not support the set of events</span></span>

<span data-ttu-id="2d029-103">Ha intentado usar una `WithEvents` variable con un componente que no puede funcionar como un origen de eventos para el conjunto de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="2d029-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="2d029-104">Por ejemplo, desea recibir los eventos de un objeto y, a continuación, crear otro objeto que sea `Implements` el primer objeto.</span><span class="sxs-lookup"><span data-stu-id="2d029-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="2d029-105">Aunque podría pensar que podría recibir los eventos del objeto implementado, este no es siempre el caso.</span><span class="sxs-lookup"><span data-stu-id="2d029-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="2d029-106">`Implements` solo implementa una interfaz para los métodos y las propiedades.</span><span class="sxs-lookup"><span data-stu-id="2d029-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="2d029-107">`WithEvents` no se admite para Private `UserControls` , porque la información de tipo necesaria para generar `ObjectEvent` no está disponible en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2d029-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2d029-108">Para corregir este error</span><span class="sxs-lookup"><span data-stu-id="2d029-108">To correct this error</span></span>

- <span data-ttu-id="2d029-109">No se pueden recibir eventos para un componente que no tiene eventos de origen.</span><span class="sxs-lookup"><span data-stu-id="2d029-109">You cannot sink events for a component that does not source events.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d029-110">Vea también</span><span class="sxs-lookup"><span data-stu-id="2d029-110">See also</span></span>

- [<span data-ttu-id="2d029-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="2d029-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="2d029-112">Implements (Instrucción)</span><span class="sxs-lookup"><span data-stu-id="2d029-112">Implements Statement</span></span>](../statements/implements-statement.md)
