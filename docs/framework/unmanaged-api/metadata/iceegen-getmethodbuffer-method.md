---
title: ICeeGen::GetMethodBuffer (Método)
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: e9c2dab9f30be6e5eea8f6570b297f8df11b6fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715338"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="17307-102">ICeeGen::GetMethodBuffer (Método)</span><span class="sxs-lookup"><span data-stu-id="17307-102">ICeeGen::GetMethodBuffer Method</span></span>

<span data-ttu-id="17307-103">Obtiene un búfer del tamaño adecuado para el método en la dirección virtual relativa especificada.</span><span class="sxs-lookup"><span data-stu-id="17307-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="17307-104">Este método está obsoleto y no debe usarse.</span><span class="sxs-lookup"><span data-stu-id="17307-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17307-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="17307-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17307-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17307-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="17307-107">de Dirección virtual relativa del método para el que se va a devolver un búfer.</span><span class="sxs-lookup"><span data-stu-id="17307-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="17307-108">enuncia Puntero al búfer devuelto.</span><span class="sxs-lookup"><span data-stu-id="17307-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17307-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17307-109">Requirements</span></span>  

 <span data-ttu-id="17307-110">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17307-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17307-111">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="17307-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17307-112">**Biblioteca:** Se usa como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17307-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17307-113">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17307-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17307-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="17307-114">See also</span></span>

- [<span data-ttu-id="17307-115">ICeeGen (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="17307-115">ICeeGen Interface</span></span>](iceegen-interface.md)
