---
title: ICeeGen::GetSectionBlock (Método)
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: 9ce3afded5f914ecf970d8db738becc7f5cfff84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723147"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="80175-102">ICeeGen::GetSectionBlock (Método)</span><span class="sxs-lookup"><span data-stu-id="80175-102">ICeeGen::GetSectionBlock Method</span></span>

<span data-ttu-id="80175-103">Obtiene un bloque de sección del código base.</span><span class="sxs-lookup"><span data-stu-id="80175-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="80175-104">Este método está obsoleto y no debe usarse.</span><span class="sxs-lookup"><span data-stu-id="80175-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80175-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="80175-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="80175-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="80175-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="80175-107">de La sección de la que se va a recuperar un bloque del código base.</span><span class="sxs-lookup"><span data-stu-id="80175-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="80175-108">de Longitud del bloque que se va a recuperar.</span><span class="sxs-lookup"><span data-stu-id="80175-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="80175-109">de Byte, con respecto al principio de la sección, con el que se va a alinear el primer byte del bloque.</span><span class="sxs-lookup"><span data-stu-id="80175-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="80175-110">Esta es la posición del bloque dentro de la sección.</span><span class="sxs-lookup"><span data-stu-id="80175-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="80175-111">enuncia Puntero a una ubicación que recibe la dirección del bloque recuperado.</span><span class="sxs-lookup"><span data-stu-id="80175-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80175-112">Comentarios</span><span class="sxs-lookup"><span data-stu-id="80175-112">Remarks</span></span>  

 <span data-ttu-id="80175-113">Llame `GetSectionBlock` solo si tiene requisitos de sección especiales que no se controlan mediante otros métodos.</span><span class="sxs-lookup"><span data-stu-id="80175-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80175-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80175-114">Requirements</span></span>  

 <span data-ttu-id="80175-115">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80175-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80175-116">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="80175-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80175-117">**Biblioteca:** Se usa como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80175-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80175-118">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80175-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80175-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="80175-119">See also</span></span>

- [<span data-ttu-id="80175-120">ICeeGen (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="80175-120">ICeeGen Interface</span></span>](iceegen-interface.md)
