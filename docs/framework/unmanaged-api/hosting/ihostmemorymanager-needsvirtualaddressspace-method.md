---
title: IHostMemoryManager::NeedsVirtualAddressSpace (Método)
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: 74fbb2f162fbb68871f1bb4e1a1de32f5f913cd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731324"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="ce9bc-102">IHostMemoryManager::NeedsVirtualAddressSpace (Método)</span><span class="sxs-lookup"><span data-stu-id="ce9bc-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>

<span data-ttu-id="ce9bc-103">Notifica al host que el Common Language Runtime (CLR) intentará usar la memoria especificada.</span><span class="sxs-lookup"><span data-stu-id="ce9bc-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9bc-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ce9bc-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce9bc-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ce9bc-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="ce9bc-106">de Dirección inicial de la memoria.</span><span class="sxs-lookup"><span data-stu-id="ce9bc-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="ce9bc-107">de Tamaño, en bytes, de la memoria.</span><span class="sxs-lookup"><span data-stu-id="ce9bc-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce9bc-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="ce9bc-108">Remarks</span></span>  

 <span data-ttu-id="ce9bc-109">El `NeedsVirtualAddressSpace` método es un método de devolución de llamada y debe ser implementado por el escritor de la aplicación de hospedaje.</span><span class="sxs-lookup"><span data-stu-id="ce9bc-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="ce9bc-110">Lo llama el CLR.</span><span class="sxs-lookup"><span data-stu-id="ce9bc-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="ce9bc-111">Si el host no desea que CLR use la memoria especificada, puede devolver una E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ce9bc-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9bc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce9bc-112">Requirements</span></span>  

 <span data-ttu-id="ce9bc-113">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9bc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9bc-114">**Encabezado:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ce9bc-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce9bc-115">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce9bc-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce9bc-116">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9bc-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ce9bc-117">See also</span></span>

- [<span data-ttu-id="ce9bc-118">IHostMemoryManager (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="ce9bc-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
