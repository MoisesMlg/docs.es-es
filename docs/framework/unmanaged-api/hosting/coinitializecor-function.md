---
title: CoInitializeCor (Función)
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: 9d077d5c5a414568b5643cad0171e101d7bb06f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731714"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="cd772-102">CoInitializeCor (Función)</span><span class="sxs-lookup"><span data-stu-id="cd772-102">CoInitializeCor Function</span></span>

<span data-ttu-id="cd772-103">`CoInitializeCor` está obsoleto.</span><span class="sxs-lookup"><span data-stu-id="cd772-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd772-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cd772-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd772-105">Comentarios</span><span class="sxs-lookup"><span data-stu-id="cd772-105">Remarks</span></span>  

 <span data-ttu-id="cd772-106">Para inicializar el Common Language Runtime, use [CorBindToRuntimeEx](corbindtoruntimeex-function.md) o [CorBindToCurrentRuntime (](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="cd772-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd772-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd772-107">Requirements</span></span>  

 <span data-ttu-id="cd772-108">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cd772-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd772-109">Consulte también</span><span class="sxs-lookup"><span data-stu-id="cd772-109">See also</span></span>

- [<span data-ttu-id="cd772-110">Funciones estáticas globales para metadatos</span><span class="sxs-lookup"><span data-stu-id="cd772-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
