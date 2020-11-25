---
title: ICorDebugChainEnum::Next (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 0f42020821ec71d1e59ae8097f22ee530e16a576
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706182"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="8ee9d-102">ICorDebugChainEnum::Next (Método)</span><span class="sxs-lookup"><span data-stu-id="8ee9d-102">ICorDebugChainEnum::Next Method</span></span>

<span data-ttu-id="8ee9d-103">Obtiene el número especificado de instancias de ICorDebugChain de la enumeración, comenzando en la posición actual.</span><span class="sxs-lookup"><span data-stu-id="8ee9d-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee9d-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="8ee9d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ee9d-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="8ee9d-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="8ee9d-106">de El número de `ICorDebugChain` instancias que se van a recuperar.</span><span class="sxs-lookup"><span data-stu-id="8ee9d-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="8ee9d-107">enuncia Matriz de punteros, cada uno de los cuales apunta a un `ICorDebugChain` objeto que representa una cadena.</span><span class="sxs-lookup"><span data-stu-id="8ee9d-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8ee9d-108">enuncia Puntero al número de `ICorDebugChain` instancias devueltas realmente.</span><span class="sxs-lookup"><span data-stu-id="8ee9d-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="8ee9d-109">Este valor puede ser null si `celt` es uno.</span><span class="sxs-lookup"><span data-stu-id="8ee9d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ee9d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ee9d-110">Requirements</span></span>  

 <span data-ttu-id="8ee9d-111">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ee9d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ee9d-112">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ee9d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ee9d-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ee9d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ee9d-114">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ee9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
