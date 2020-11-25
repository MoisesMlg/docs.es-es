---
title: ICorDebugFunction2::GetVersionNumber (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 88fb205235cfaf3566fbd74b05a4e9833058f4a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696107"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="5f06f-102">ICorDebugFunction2::GetVersionNumber (Método)</span><span class="sxs-lookup"><span data-stu-id="5f06f-102">ICorDebugFunction2::GetVersionNumber Method</span></span>

<span data-ttu-id="5f06f-103">Obtiene la versión de edición y continuación de esta función.</span><span class="sxs-lookup"><span data-stu-id="5f06f-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f06f-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5f06f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f06f-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5f06f-105">Parameters</span></span>  

 `pnVersion`  
 <span data-ttu-id="5f06f-106">enuncia Un puntero a un entero que es el número de versión de la función representada por este objeto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="5f06f-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f06f-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="5f06f-107">Remarks</span></span>  

 <span data-ttu-id="5f06f-108">El tiempo de ejecución realiza un seguimiento del número de modificaciones que se han producido en cada módulo durante una sesión de depuración.</span><span class="sxs-lookup"><span data-stu-id="5f06f-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="5f06f-109">El número de versión de una función es uno más que el número de la edición que presentó la función.</span><span class="sxs-lookup"><span data-stu-id="5f06f-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="5f06f-110">La versión original de la función es la versión 1.</span><span class="sxs-lookup"><span data-stu-id="5f06f-110">The function's original version is version 1.</span></span> <span data-ttu-id="5f06f-111">El número se incrementa para un módulo cada vez que se llama a [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md) en ese módulo.</span><span class="sxs-lookup"><span data-stu-id="5f06f-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="5f06f-112">Por lo tanto, si el cuerpo de una función se ha reemplazado en la primera y la tercera llamada a `ICorDebugModule2::ApplyChanges` , `GetVersionNumber` puede devolver la versión 1, 2 o 4 para esa función, pero no la versión 3.</span><span class="sxs-lookup"><span data-stu-id="5f06f-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="5f06f-113">(Esa función no tendría la versión 3).</span><span class="sxs-lookup"><span data-stu-id="5f06f-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="5f06f-114">Se realiza un seguimiento del número de versión por separado para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="5f06f-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="5f06f-115">Por lo tanto, si realiza cuatro ediciones en el módulo 1 y ninguna en el módulo 2, la siguiente edición del módulo 1 asignará un número de versión de 6 a todas las funciones editadas en el módulo 1.</span><span class="sxs-lookup"><span data-stu-id="5f06f-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="5f06f-116">Si la misma edición toca el módulo 2, las funciones del módulo 2 obtendrán un número de versión de 2.</span><span class="sxs-lookup"><span data-stu-id="5f06f-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="5f06f-117">El número de versión obtenido por el `GetVersionNumber` método puede ser menor que el obtenido por [ICorDebugFunction:: GetCurrentVersionNumber (](icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="5f06f-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="5f06f-118">El método [ICorDebugCode:: GetVersionNumber (](icordebugcode-getversionnumber-method.md) realiza la misma operación que `ICorDebugFunction2::GetVersionNumber` .</span><span class="sxs-lookup"><span data-stu-id="5f06f-118">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f06f-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f06f-119">Requirements</span></span>  

 <span data-ttu-id="5f06f-120">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f06f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f06f-121">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f06f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f06f-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f06f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f06f-123">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f06f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
