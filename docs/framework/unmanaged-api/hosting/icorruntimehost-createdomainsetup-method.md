---
title: ICorRuntimeHost::CreateDomainSetup (Método)
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: 1be7eee5c2591f26c33572446080a4fa4b3b929d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723901"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="e32be-102">ICorRuntimeHost::CreateDomainSetup (Método)</span><span class="sxs-lookup"><span data-stu-id="e32be-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="e32be-103">Obtiene un puntero de interfaz de tipo IAppDomainSetup a una <xref:System.AppDomainSetup?displayProperty=nameWithType> instancia de.</span><span class="sxs-lookup"><span data-stu-id="e32be-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="e32be-104">`IAppDomainSetup` proporciona métodos para configurar aspectos de un dominio de aplicación antes de que se cree.</span><span class="sxs-lookup"><span data-stu-id="e32be-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32be-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e32be-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e32be-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e32be-106">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="e32be-107">enuncia Puntero de interfaz a una <xref:System.AppDomainSetup?displayProperty=nameWithType> instancia de.</span><span class="sxs-lookup"><span data-stu-id="e32be-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="e32be-108">Este parámetro tiene el tipo `IUnknown` , por lo que los llamadores generalmente deben llamar a `QueryInterface` en este puntero para obtener un puntero de interfaz de tipo `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="e32be-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e32be-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="e32be-109">Return Value</span></span>  
  
|<span data-ttu-id="e32be-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e32be-110">HRESULT</span></span>|<span data-ttu-id="e32be-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="e32be-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e32be-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e32be-112">S_OK</span></span>|<span data-ttu-id="e32be-113">La operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="e32be-113">The operation was successful.</span></span>|  
|<span data-ttu-id="e32be-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e32be-114">S_FALSE</span></span>|<span data-ttu-id="e32be-115">No se pudo completar la operación.</span><span class="sxs-lookup"><span data-stu-id="e32be-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e32be-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e32be-116">E_FAIL</span></span>|<span data-ttu-id="e32be-117">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="e32be-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e32be-118">Si un método devuelve E_FAIL, el Common Language Runtime (CLR) ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="e32be-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e32be-119">Las llamadas subsiguientes a cualquier API de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e32be-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e32be-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e32be-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e32be-121">CLR no se ha cargado en un proceso o CLR está en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="e32be-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e32be-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="e32be-122">Remarks</span></span>  

 <span data-ttu-id="e32be-123">Normalmente, el puntero devuelto por este método se pasa como un parámetro al método [createdomainex (](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e32be-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e32be-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e32be-124">Requirements</span></span>  

 <span data-ttu-id="e32be-125">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e32be-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e32be-126">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e32be-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e32be-127">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e32be-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e32be-128">**Versión de .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e32be-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32be-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e32be-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="e32be-130">ICorRuntimeHost (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="e32be-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
