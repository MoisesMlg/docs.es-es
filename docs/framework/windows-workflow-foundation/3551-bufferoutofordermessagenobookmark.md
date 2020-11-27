---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 5e6a5f9d21435fee8309bd222443407e50ec2cee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263612"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="34952-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="34952-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="34952-103">Propiedades</span><span class="sxs-lookup"><span data-stu-id="34952-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34952-104">ID</span><span class="sxs-lookup"><span data-stu-id="34952-104">ID</span></span>|<span data-ttu-id="34952-105">3551</span><span class="sxs-lookup"><span data-stu-id="34952-105">3551</span></span>|  
|<span data-ttu-id="34952-106">Palabras clave</span><span class="sxs-lookup"><span data-stu-id="34952-106">Keywords</span></span>|<span data-ttu-id="34952-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="34952-107">WFServices</span></span>|  
|<span data-ttu-id="34952-108">Nivel</span><span class="sxs-lookup"><span data-stu-id="34952-108">Level</span></span>|<span data-ttu-id="34952-109">Información</span><span class="sxs-lookup"><span data-stu-id="34952-109">Information</span></span>|  
|<span data-ttu-id="34952-110">Canal</span><span class="sxs-lookup"><span data-stu-id="34952-110">Channel</span></span>|<span data-ttu-id="34952-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="34952-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="34952-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="34952-112">Description</span></span>  

 <span data-ttu-id="34952-113">Indica que se ha producido un error en la reanudación de marcador.</span><span class="sxs-lookup"><span data-stu-id="34952-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="34952-114">La operación de recepción almacenada en búfer se intentará de nuevo cuando la instancia del servicio esté lista para procesar esta operación en particular.</span><span class="sxs-lookup"><span data-stu-id="34952-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="34952-115">Message</span><span class="sxs-lookup"><span data-stu-id="34952-115">Message</span></span>  

 <span data-ttu-id="34952-116">La operación '%2' en la instancia del servicio '%1' no se puede realizar en este momento.</span><span class="sxs-lookup"><span data-stu-id="34952-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="34952-117">Se intentará de nuevo cuando la instancia del servicio esté lista para procesar esta operación en particular.</span><span class="sxs-lookup"><span data-stu-id="34952-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="34952-118">Detalles</span><span class="sxs-lookup"><span data-stu-id="34952-118">Details</span></span>  
  
|<span data-ttu-id="34952-119">Nombre del elemento de datos</span><span class="sxs-lookup"><span data-stu-id="34952-119">Data Item Name</span></span>|<span data-ttu-id="34952-120">Tipo del elemento de datos</span><span class="sxs-lookup"><span data-stu-id="34952-120">Data Item Type</span></span>|<span data-ttu-id="34952-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="34952-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="34952-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="34952-122">OperationName</span></span>|<span data-ttu-id="34952-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="34952-123">xs:string</span></span>|<span data-ttu-id="34952-124">Nombre de la operación.</span><span class="sxs-lookup"><span data-stu-id="34952-124">The name of the operation.</span></span>|  
|<span data-ttu-id="34952-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="34952-125">ServiceInstanceId</span></span>|<span data-ttu-id="34952-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="34952-126">xs:string</span></span>|<span data-ttu-id="34952-127">Identificador de la instancia del servicio.</span><span class="sxs-lookup"><span data-stu-id="34952-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="34952-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="34952-128">AppDomain</span></span>|<span data-ttu-id="34952-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="34952-129">xs:string</span></span>|<span data-ttu-id="34952-130">La cadena devuelta por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="34952-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
