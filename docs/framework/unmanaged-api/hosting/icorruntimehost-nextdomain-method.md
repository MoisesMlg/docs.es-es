---
title: ICorRuntimeHost::NextDomain (Método)
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 598c46d50d7b4a67c1b2c0d844c9b12deb12a428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671374"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="db2e5-102">ICorRuntimeHost::NextDomain (Método)</span><span class="sxs-lookup"><span data-stu-id="db2e5-102">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="db2e5-103">Obtiene un puntero de interfaz al siguiente dominio en la enumeración.</span><span class="sxs-lookup"><span data-stu-id="db2e5-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db2e5-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="db2e5-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db2e5-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="db2e5-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="db2e5-106">de Enumerador que se obtuvo a través de una llamada a [EnumDomains (](icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="db2e5-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="db2e5-107">enuncia Puntero de interfaz al <xref:System._AppDomain?displayProperty=nameWithType> tipo que representa el siguiente dominio en la enumeración, o null, si no existen más dominios.</span><span class="sxs-lookup"><span data-stu-id="db2e5-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db2e5-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="db2e5-108">Return Value</span></span>  
  
|<span data-ttu-id="db2e5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db2e5-109">HRESULT</span></span>|<span data-ttu-id="db2e5-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="db2e5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db2e5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="db2e5-111">S_OK</span></span>|<span data-ttu-id="db2e5-112">La operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="db2e5-112">The operation was successful.</span></span>|  
|<span data-ttu-id="db2e5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="db2e5-113">S_FALSE</span></span>|<span data-ttu-id="db2e5-114">No se pudo completar la operación o no hay más dominios en la enumeración.</span><span class="sxs-lookup"><span data-stu-id="db2e5-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="db2e5-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db2e5-115">E_FAIL</span></span>|<span data-ttu-id="db2e5-116">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="db2e5-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="db2e5-117">Si un método devuelve E_FAIL, el Common Language Runtime (CLR) ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="db2e5-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="db2e5-118">Las llamadas subsiguientes a cualquier API de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db2e5-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db2e5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db2e5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db2e5-120">CLR no se ha cargado en un proceso o CLR está en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="db2e5-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db2e5-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db2e5-121">Requirements</span></span>  

 <span data-ttu-id="db2e5-122">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db2e5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db2e5-123">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db2e5-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db2e5-124">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db2e5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db2e5-125">**.NET Framework versiones:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="db2e5-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2e5-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="db2e5-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="db2e5-127">ICorRuntimeHost (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="db2e5-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
