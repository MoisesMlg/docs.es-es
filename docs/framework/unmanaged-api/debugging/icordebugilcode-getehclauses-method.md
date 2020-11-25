---
title: ICorDebugILCode::GetEHClauses (Método)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: 38936a57944e9a0920c374f473c4cbe8e8d70abb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728672"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="da179-102">ICorDebugILCode::GetEHClauses (Método)</span><span class="sxs-lookup"><span data-stu-id="da179-102">ICorDebugILCode::GetEHClauses Method</span></span>

<span data-ttu-id="da179-103">[Compatible con .NET Framework 4.5.2 y versiones posteriores]</span><span class="sxs-lookup"><span data-stu-id="da179-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="da179-104">Devuelve un puntero a una lista de cláusulas de control de excepciones (EH) definidas para este lenguaje intermedio (IL).</span><span class="sxs-lookup"><span data-stu-id="da179-104">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da179-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="da179-105">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da179-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="da179-106">Parameters</span></span>  

 `cClauses`  
 <span data-ttu-id="da179-107">[in] Capacidad de almacenamiento de la matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="da179-107">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="da179-108">Vea la sección Comentarios para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="da179-108">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="da179-109">[out] Número de cláusulas para las cuales se escribe información en la matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="da179-109">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="da179-110">cláusulas</span><span class="sxs-lookup"><span data-stu-id="da179-110">clauses</span></span>  
 <span data-ttu-id="da179-111">enuncia Matriz de objetos [cordebugehclause (](cordebugehclause-structure.md) que contienen información sobre las cláusulas de control de excepciones definidas para este Il.</span><span class="sxs-lookup"><span data-stu-id="da179-111">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da179-112">Comentarios</span><span class="sxs-lookup"><span data-stu-id="da179-112">Remarks</span></span>  

 <span data-ttu-id="da179-113">Si `cClauses` es 0 y `pcClauses` no es **null**, `pcClauses` se establece en el número de cláusulas de control de excepciones disponibles.</span><span class="sxs-lookup"><span data-stu-id="da179-113">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="da179-114">Si `cClauses` no es cero, representa la capacidad de almacenamiento de la matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="da179-114">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="da179-115">Cuando el método vuelve, `clauses` contiene un máximo de elementos `cClauses` y `pcClauses` se establece en el número de cláusulas escritas realmente en la matriz `clauses`.</span><span class="sxs-lookup"><span data-stu-id="da179-115">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da179-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da179-116">Requirements</span></span>  

 <span data-ttu-id="da179-117">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da179-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da179-118">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da179-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da179-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da179-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da179-120">**.NET Framework versiones:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da179-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da179-121">Consulte también</span><span class="sxs-lookup"><span data-stu-id="da179-121">See also</span></span>

- [<span data-ttu-id="da179-122">ICorDebugILCode (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="da179-122">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="da179-123">CorDebugEHClause (Estructura)</span><span class="sxs-lookup"><span data-stu-id="da179-123">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="da179-124">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="da179-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
