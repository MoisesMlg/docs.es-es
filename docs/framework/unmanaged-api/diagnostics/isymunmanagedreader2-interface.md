---
title: ISymUnmanagedReader2 (Interfaz)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709081"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="d12d7-102">ISymUnmanagedReader2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="d12d7-102">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="d12d7-103">Representa un lector de símbolos que proporciona acceso a los documentos, métodos y variables de un almacén de símbolos.</span><span class="sxs-lookup"><span data-stu-id="d12d7-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="d12d7-104">Esta interfaz extiende la interfaz [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d12d7-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d12d7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d12d7-105">Methods</span></span>  
  
|<span data-ttu-id="d12d7-106">Método</span><span class="sxs-lookup"><span data-stu-id="d12d7-106">Method</span></span>|<span data-ttu-id="d12d7-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="d12d7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d12d7-108">Método GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="d12d7-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="d12d7-109">Obtiene un método del lector de símbolos, dado un token de método y un número de versión de edición y continuación.</span><span class="sxs-lookup"><span data-stu-id="d12d7-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="d12d7-110">Método GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="d12d7-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="d12d7-111">Obtiene todos los métodos que tienen información de línea en el documento proporcionado.</span><span class="sxs-lookup"><span data-stu-id="d12d7-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="d12d7-112">Método GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="d12d7-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="d12d7-113">Obtiene un atributo personalizado basado en su nombre.</span><span class="sxs-lookup"><span data-stu-id="d12d7-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d12d7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d12d7-114">Requirements</span></span>  

 <span data-ttu-id="d12d7-115">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d12d7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d12d7-116">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d12d7-116">See also</span></span>

- [<span data-ttu-id="d12d7-117">Interfaces de almacén de símbolos de diagnósticos</span><span class="sxs-lookup"><span data-stu-id="d12d7-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d12d7-118">ISymUnmanagedReader (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="d12d7-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
