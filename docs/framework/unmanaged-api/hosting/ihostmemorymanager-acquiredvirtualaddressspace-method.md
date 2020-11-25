---
title: IHostMemoryManager::AcquiredVirtualAddressSpace (Método)
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: 58fce616ae05dcc622369a706f010f91d657389f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700631"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="5087f-102">IHostMemoryManager::AcquiredVirtualAddressSpace (Método)</span><span class="sxs-lookup"><span data-stu-id="5087f-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="5087f-103">Notifica al host que el Common Language Runtime (CLR) ha adquirido la memoria especificada del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="5087f-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5087f-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5087f-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5087f-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5087f-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="5087f-106">de Dirección inicial de la memoria.</span><span class="sxs-lookup"><span data-stu-id="5087f-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="5087f-107">de Tamaño, en bytes, de la memoria.</span><span class="sxs-lookup"><span data-stu-id="5087f-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5087f-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="5087f-108">Remarks</span></span>  

 <span data-ttu-id="5087f-109">El `AcquiredVirtualAddressSpace` método es un método de devolución de llamada y debe ser implementado por el escritor de la aplicación de hospedaje.</span><span class="sxs-lookup"><span data-stu-id="5087f-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="5087f-110">Lo llama el CLR.</span><span class="sxs-lookup"><span data-stu-id="5087f-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5087f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5087f-111">Requirements</span></span>  

 <span data-ttu-id="5087f-112">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5087f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5087f-113">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5087f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5087f-114">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5087f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5087f-115">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5087f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5087f-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5087f-116">See also</span></span>

- [<span data-ttu-id="5087f-117">IHostMemoryManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="5087f-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
