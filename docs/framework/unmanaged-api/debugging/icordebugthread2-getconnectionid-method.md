---
title: ICorDebugThread2::GetConnectionID (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: 1507715e80761c871dfdb0b8d25dc708a2130678
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678693"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="ef4cd-102">ICorDebugThread2::GetConnectionID (Método)</span><span class="sxs-lookup"><span data-stu-id="ef4cd-102">ICorDebugThread2::GetConnectionID Method</span></span>

<span data-ttu-id="ef4cd-103">Obtiene el identificador de conexión de este objeto ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="ef4cd-103">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef4cd-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ef4cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef4cd-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ef4cd-105">Parameters</span></span>  

 `pdwConnectionId`  
 <span data-ttu-id="ef4cd-106">enuncia `CONNID` Que representa el identificador de conexión.</span><span class="sxs-lookup"><span data-stu-id="ef4cd-106">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef4cd-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="ef4cd-107">Remarks</span></span>  

 <span data-ttu-id="ef4cd-108">El `GetConnectionID` método devuelve cero en el `pdwConnectionId` parámetro, si este subproceso no forma parte de una conexión.</span><span class="sxs-lookup"><span data-stu-id="ef4cd-108">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="ef4cd-109">Si este subproceso está conectado a una instancia de Microsoft SQL Server 2005 Analysis Services (SSAS), se `CONNID` asigna a un identificador de proceso de servidor (SPID).</span><span class="sxs-lookup"><span data-stu-id="ef4cd-109">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef4cd-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef4cd-110">Requirements</span></span>  

 <span data-ttu-id="ef4cd-111">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef4cd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef4cd-112">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef4cd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef4cd-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef4cd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef4cd-114">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef4cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
