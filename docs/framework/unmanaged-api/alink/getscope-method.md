---
title: Método GetScope
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: fd5ae6ef40cb171c33132df0f640acbef96d69b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684684"
---
# <a name="getscope-method"></a><span data-ttu-id="6db7e-102">Método GetScope</span><span class="sxs-lookup"><span data-stu-id="6db7e-102">GetScope Method</span></span>

<span data-ttu-id="6db7e-103">Obtiene un ámbito de importación.</span><span class="sxs-lookup"><span data-stu-id="6db7e-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db7e-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6db7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6db7e-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6db7e-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="6db7e-106">IDENTIFICADOR único del ensamblado en el que se va a importar.</span><span class="sxs-lookup"><span data-stu-id="6db7e-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6db7e-107">IDENTIFICADOR único del archivo desde el que se va a importar.</span><span class="sxs-lookup"><span data-stu-id="6db7e-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="6db7e-108">Ámbito de base cero que se va a importar.</span><span class="sxs-lookup"><span data-stu-id="6db7e-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="6db7e-109">Recibe la interfaz de [interfaz IMetaDataImport](../metadata/imetadataimport-interface.md) para el ámbito.</span><span class="sxs-lookup"><span data-stu-id="6db7e-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6db7e-110">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="6db7e-110">Return Value</span></span>  

 <span data-ttu-id="6db7e-111">Devuelve S_OK si el método se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="6db7e-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6db7e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6db7e-112">Requirements</span></span>  

 <span data-ttu-id="6db7e-113">Requiere ALink. h</span><span class="sxs-lookup"><span data-stu-id="6db7e-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db7e-114">Consulte también</span><span class="sxs-lookup"><span data-stu-id="6db7e-114">See also</span></span>

- [<span data-ttu-id="6db7e-115">IALink (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="6db7e-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6db7e-116">IALink2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="6db7e-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6db7e-117">API de ALink</span><span class="sxs-lookup"><span data-stu-id="6db7e-117">ALink API</span></span>](index.md)
