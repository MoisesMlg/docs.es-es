---
title: IAssemblyCache::CreateAssemblyCacheItem (Método)
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: b417377ea1d0746e563490d87cc9a988e857d943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697045"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="b0465-102">IAssemblyCache::CreateAssemblyCacheItem (Método)</span><span class="sxs-lookup"><span data-stu-id="b0465-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="b0465-103">Obtiene una referencia a un nuevo objeto [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b0465-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0465-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b0465-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0465-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b0465-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="b0465-106">de Marcas definidas en Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="b0465-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="b0465-107">Se admiten los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="b0465-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="b0465-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="b0465-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="b0465-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="b0465-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="b0465-110">[in] Reservado para extensibilidad futura.</span><span class="sxs-lookup"><span data-stu-id="b0465-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b0465-111">`pvReserved` debe ser una referencia nula.</span><span class="sxs-lookup"><span data-stu-id="b0465-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="b0465-112">enuncia Puntero devuelto `IAssemblyCacheItem` .</span><span class="sxs-lookup"><span data-stu-id="b0465-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="b0465-113">[in, Optional] Pares no canónicos separados por comas `name=value` .</span><span class="sxs-lookup"><span data-stu-id="b0465-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0465-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0465-114">Requirements</span></span>  

 <span data-ttu-id="b0465-115">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0465-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0465-116">**Encabezado:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b0465-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b0465-117">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0465-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0465-118">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b0465-118">See also</span></span>

- [<span data-ttu-id="b0465-119">IAssemblyCache (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="b0465-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="b0465-120">IAssemblyCacheItem (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="b0465-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
