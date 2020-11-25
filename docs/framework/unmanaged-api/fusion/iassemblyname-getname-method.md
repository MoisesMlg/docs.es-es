---
title: IAssemblyName::GetName (Método)
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 58b8b83ce1db9338612cbaa01a0db0862cf1054e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727905"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="3f0b0-102">IAssemblyName::GetName (Método)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-102">IAssemblyName::GetName Method</span></span>

<span data-ttu-id="3f0b0-103">Obtiene el nombre simple y sin cifrar del ensamblado al que hace referencia este objeto de [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3f0b0-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f0b0-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3f0b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f0b0-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3f0b0-105">Parameters</span></span>  

 `lpcwBuffer`  
 <span data-ttu-id="3f0b0-106">[in, out] Tamaño de `pwzName` en caracteres anchos, incluido el carácter de terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="3f0b0-107">enuncia Búfer que contiene el nombre del ensamblado al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="3f0b0-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f0b0-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f0b0-108">Requirements</span></span>  

 <span data-ttu-id="3f0b0-109">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f0b0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f0b0-110">**Encabezado:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="3f0b0-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3f0b0-111">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f0b0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0b0-112">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3f0b0-112">See also</span></span>

- [<span data-ttu-id="3f0b0-113">IAssemblyName (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="3f0b0-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
