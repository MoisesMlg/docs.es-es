---
title: ISymENCUnmanagedMethod::GetLineFromOffset (Método)
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707365"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="d4bbb-102">ISymENCUnmanagedMethod::GetLineFromOffset (Método)</span><span class="sxs-lookup"><span data-stu-id="d4bbb-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="d4bbb-103">Obtiene la información de línea asociada a un desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="d4bbb-104">Si el parámetro de desplazamiento ( `dwOffset` ) no es un punto de secuencia, este método obtiene la información de línea asociada al desplazamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4bbb-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d4bbb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4bbb-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d4bbb-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="d4bbb-107">de Un `ULONG32` que contiene el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="d4bbb-108">enuncia Un puntero a un `ULONG32` que recibe la línea.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="d4bbb-109">enuncia Un puntero a un `ULONG32` que recibe la columna.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="d4bbb-110">enuncia Un puntero a un `ULONG32` que recibe la línea final.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="d4bbb-111">enuncia Un puntero a un `ULONG32` que recibe la columna final.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="d4bbb-112">enuncia Puntero a un objeto `ULONG32` que recibe el punto de secuencia asociado.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4bbb-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="d4bbb-113">Return Value</span></span>  

 <span data-ttu-id="d4bbb-114">S_OK si el método se ejecuta correctamente; de lo contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="d4bbb-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4bbb-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4bbb-115">Requirements</span></span>  

 <span data-ttu-id="d4bbb-116">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d4bbb-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bbb-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d4bbb-117">See also</span></span>

- [<span data-ttu-id="d4bbb-118">ISymENCUnmanagedMethod (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="d4bbb-118">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
