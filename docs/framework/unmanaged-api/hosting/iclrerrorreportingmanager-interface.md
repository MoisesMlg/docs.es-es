---
title: ICLRErrorReportingManager (Interfaz)
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677854"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="152ae-102">ICLRErrorReportingManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="152ae-102">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="152ae-103">Proporciona métodos que permiten al host configurar volcados de pila personalizados para el informe de errores.</span><span class="sxs-lookup"><span data-stu-id="152ae-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="152ae-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="152ae-104">Methods</span></span>  
  
|<span data-ttu-id="152ae-105">Método</span><span class="sxs-lookup"><span data-stu-id="152ae-105">Method</span></span>|<span data-ttu-id="152ae-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="152ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="152ae-107">Método BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="152ae-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="152ae-108">Especifica la configuración de los volcados de pila personalizados para el informe de errores.</span><span class="sxs-lookup"><span data-stu-id="152ae-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="152ae-109">Método EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="152ae-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="152ae-110">Borra la configuración de volcado de la pila personalizada establecida por una llamada anterior a `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="152ae-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="152ae-111">Método GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="152ae-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="152ae-112">Obtiene el depósito de Watson para la excepción actual en el subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="152ae-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="152ae-113">Comentarios</span><span class="sxs-lookup"><span data-stu-id="152ae-113">Remarks</span></span>  

 <span data-ttu-id="152ae-114">El `BeginCustomDump` método establece la configuración personalizada del volcado de la pila.</span><span class="sxs-lookup"><span data-stu-id="152ae-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="152ae-115">El `EndCustomDump` método borra la configuración de volcado de la pila personalizada y libera cualquier estado asociado.</span><span class="sxs-lookup"><span data-stu-id="152ae-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="152ae-116">Se debe llamar después de completar el volcado de memoria personalizado.</span><span class="sxs-lookup"><span data-stu-id="152ae-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="152ae-117">Si no se llama a `EndCustomDump` , se produce una pérdida de memoria.</span><span class="sxs-lookup"><span data-stu-id="152ae-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152ae-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="152ae-118">Requirements</span></span>  

 <span data-ttu-id="152ae-119">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="152ae-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152ae-120">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="152ae-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="152ae-121">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="152ae-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="152ae-122">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="152ae-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152ae-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="152ae-123">See also</span></span>

- [<span data-ttu-id="152ae-124">ECustomDumpItemKind (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="152ae-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="152ae-125">Interfaces de hospedaje</span><span class="sxs-lookup"><span data-stu-id="152ae-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
