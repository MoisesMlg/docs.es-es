---
title: ISymUnmanagedMethod::GetSequencePointCount (Método)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: 44472c7beff72d24853b7fb9865071a9b15ef0e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699435"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="1e16c-102">ISymUnmanagedMethod::GetSequencePointCount (Método)</span><span class="sxs-lookup"><span data-stu-id="1e16c-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>

<span data-ttu-id="1e16c-103">Obtiene el recuento de puntos de secuencia dentro de este método.</span><span class="sxs-lookup"><span data-stu-id="1e16c-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e16c-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1e16c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e16c-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1e16c-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1e16c-106">enuncia Un puntero a un `ULONG32` que recibe el tamaño del búfer necesario para contener los puntos de secuencia.</span><span class="sxs-lookup"><span data-stu-id="1e16c-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e16c-107">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1e16c-107">Return Value</span></span>  

 <span data-ttu-id="1e16c-108">S_OK si el método se ejecuta correctamente; de lo contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="1e16c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e16c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e16c-109">Requirements</span></span>  

 <span data-ttu-id="1e16c-110">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1e16c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e16c-111">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1e16c-111">See also</span></span>

- [<span data-ttu-id="1e16c-112">ISymUnmanagedMethod (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="1e16c-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
