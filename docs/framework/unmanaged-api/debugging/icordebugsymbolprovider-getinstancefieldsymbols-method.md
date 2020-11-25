---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols (método)
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 1a74b355b695f65166d0fe63bbdd41d789db5cfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730869"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="c42b2-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols (método)</span><span class="sxs-lookup"><span data-stu-id="c42b2-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>

<span data-ttu-id="c42b2-103">Obtiene los símbolos de campo de instancia que corresponden a una firma Typespec.</span><span class="sxs-lookup"><span data-stu-id="c42b2-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42b2-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c42b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c42b2-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c42b2-105">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="c42b2-106">[in] Número de bytes en la matriz `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="c42b2-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="c42b2-107">[in] Matriz de bytes que contiene la firma `typespec`.</span><span class="sxs-lookup"><span data-stu-id="c42b2-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="c42b2-108">[in] Número de símbolos solicitado.</span><span class="sxs-lookup"><span data-stu-id="c42b2-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="c42b2-109">[out] Puntero al número de símbolos recuperados por el método.</span><span class="sxs-lookup"><span data-stu-id="c42b2-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="c42b2-110">enuncia Puntero a una matriz [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) que contiene los símbolos de campo de instancia solicitados.</span><span class="sxs-lookup"><span data-stu-id="c42b2-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c42b2-111">Comentarios</span><span class="sxs-lookup"><span data-stu-id="c42b2-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c42b2-112">Este método solo está disponible con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c42b2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42b2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c42b2-113">Requirements</span></span>  

 <span data-ttu-id="c42b2-114">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c42b2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42b2-115">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c42b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c42b2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c42b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c42b2-117">**.NET Framework versiones:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c42b2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42b2-118">Consulte también</span><span class="sxs-lookup"><span data-stu-id="c42b2-118">See also</span></span>

- [<span data-ttu-id="c42b2-119">Método GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="c42b2-119">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="c42b2-120">Interfaz ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="c42b2-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c42b2-121">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="c42b2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
