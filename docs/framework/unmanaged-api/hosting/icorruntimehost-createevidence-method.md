---
title: ICorRuntimeHost::CreateEvidence (Método)
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 6627fce519934177aefd26a612e5b00ca1941d02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715672"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="24a55-102">ICorRuntimeHost::CreateEvidence (Método)</span><span class="sxs-lookup"><span data-stu-id="24a55-102">ICorRuntimeHost::CreateEvidence Method</span></span>

<span data-ttu-id="24a55-103">Obtiene un puntero de interfaz de tipo <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , que permite al host crear la evidencia de seguridad que se va a pasar al método [CreateDomain](icorruntimehost-createdomain-method.md) o [createdomainex (](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="24a55-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24a55-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="24a55-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24a55-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="24a55-105">Parameters</span></span>  

 `pEvidence`  
 <span data-ttu-id="24a55-106">enuncia Puntero de interfaz a una <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instancia de utilizada para crear la evidencia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="24a55-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="24a55-107">Este puntero tiene tipo `IUnknown` , por lo que los llamadores normalmente deben llamar a `QueryInterface` en esta interfaz para obtener un puntero a <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="24a55-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24a55-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="24a55-108">Return Value</span></span>  
  
|<span data-ttu-id="24a55-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24a55-109">HRESULT</span></span>|<span data-ttu-id="24a55-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="24a55-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24a55-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="24a55-111">S_OK</span></span>|<span data-ttu-id="24a55-112">La operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="24a55-112">The operation was successful.</span></span>|  
|<span data-ttu-id="24a55-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="24a55-113">S_FALSE</span></span>|<span data-ttu-id="24a55-114">No se pudo completar la operación.</span><span class="sxs-lookup"><span data-stu-id="24a55-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="24a55-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24a55-115">E_FAIL</span></span>|<span data-ttu-id="24a55-116">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="24a55-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="24a55-117">Si un método devuelve E_FAIL, el Common Language Runtime (CLR) ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="24a55-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="24a55-118">Las llamadas subsiguientes a cualquier API de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="24a55-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="24a55-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24a55-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24a55-120">CLR no se ha cargado en un proceso o CLR está en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="24a55-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24a55-121">Comentarios</span><span class="sxs-lookup"><span data-stu-id="24a55-121">Remarks</span></span>  

 <span data-ttu-id="24a55-122">Este método devuelve una colección vacía que no se puede rellenar desde código nativo.</span><span class="sxs-lookup"><span data-stu-id="24a55-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="24a55-123">En su lugar, debe utilizar el <xref:System.Security.Policy.Evidence> método.</span><span class="sxs-lookup"><span data-stu-id="24a55-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24a55-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24a55-124">Requirements</span></span>  

 <span data-ttu-id="24a55-125">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24a55-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24a55-126">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="24a55-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24a55-127">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24a55-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24a55-128">**Versión de .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="24a55-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a55-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="24a55-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="24a55-130">ICorRuntimeHost (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="24a55-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
