---
title: ISymUnmanagedReader::GetDocumentVersion (Método)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: fc38c167b47ea72c7bc7ad81074f9cb1a0d217d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707573"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="5f719-102">ISymUnmanagedReader::GetDocumentVersion (Método)</span><span class="sxs-lookup"><span data-stu-id="5f719-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>

<span data-ttu-id="5f719-103">Obtiene la versión especificada del documento especificado.</span><span class="sxs-lookup"><span data-stu-id="5f719-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="5f719-104">La versión del documento comienza en 1 y se incrementa cada vez que se actualiza el documento mediante el método [UpdateSymbolStore (](isymunmanagedreader-updatesymbolstore-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5f719-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="5f719-105">Si el `pbCurrent` parámetro es `true` , esta es la versión más reciente del documento.</span><span class="sxs-lookup"><span data-stu-id="5f719-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f719-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="5f719-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f719-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5f719-107">Parameters</span></span>  

 `pDoc`  
 <span data-ttu-id="5f719-108">de Documento especificado.</span><span class="sxs-lookup"><span data-stu-id="5f719-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="5f719-109">enuncia Puntero a una variable que recibe la versión del documento especificado.</span><span class="sxs-lookup"><span data-stu-id="5f719-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="5f719-110">enuncia Un puntero a una variable que recibe `true` si se trata de la versión más reciente del documento, o `false` si no es la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="5f719-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f719-111">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="5f719-111">Return Value</span></span>  

 <span data-ttu-id="5f719-112">S_OK si el método se ejecuta correctamente; de lo contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="5f719-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f719-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f719-113">Requirements</span></span>  

 <span data-ttu-id="5f719-114">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5f719-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f719-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5f719-115">See also</span></span>

- [<span data-ttu-id="5f719-116">ISymUnmanagedReader (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="5f719-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
