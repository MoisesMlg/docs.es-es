---
title: ICorDebugSymbolProvider::GetCodeRange (método)
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: f61a98dbd5a65207a46e033d54f9d5f60adac201
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709133"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="925ac-102">ICorDebugSymbolProvider::GetCodeRange (método)</span><span class="sxs-lookup"><span data-stu-id="925ac-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="925ac-103">Obtiene el tamaño y la dirección de inicio del método a partir de una dirección virtual relativa (RVA) en un método.</span><span class="sxs-lookup"><span data-stu-id="925ac-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925ac-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="925ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="925ac-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="925ac-105">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="925ac-106">[in] Dirección virtual relativa (RVA) en un método.</span><span class="sxs-lookup"><span data-stu-id="925ac-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="925ac-107">[out] Puntero a la dirección de inicio del método.</span><span class="sxs-lookup"><span data-stu-id="925ac-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="925ac-108">Puntero al tamaño del código del método (número de bytes del código del método).</span><span class="sxs-lookup"><span data-stu-id="925ac-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="925ac-109">Comentarios</span><span class="sxs-lookup"><span data-stu-id="925ac-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="925ac-110">Este método solo está disponible con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="925ac-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="925ac-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="925ac-111">Requirements</span></span>  

 <span data-ttu-id="925ac-112">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="925ac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="925ac-113">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="925ac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="925ac-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="925ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="925ac-115">**.NET Framework versiones:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="925ac-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925ac-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="925ac-116">See also</span></span>

- [<span data-ttu-id="925ac-117">Interfaz ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="925ac-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="925ac-118">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="925ac-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
