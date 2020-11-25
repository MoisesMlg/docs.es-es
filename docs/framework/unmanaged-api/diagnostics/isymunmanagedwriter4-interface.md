---
title: ISymUnmanagedWriter4 (Interfaz)
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: c2b57897e4f0e8b23337302f344065d79677e0c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725812"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="2cbfb-102">ISymUnmanagedWriter4 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2cbfb-102">ISymUnmanagedWriter4 Interface</span></span>

<span data-ttu-id="2cbfb-103">Interfaz Isymunmanagedwriter4 (.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbfb-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2cbfb-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="2cbfb-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2cbfb-105">Methods</span></span>  

 <span data-ttu-id="2cbfb-106">Esta interfaz contiene los siguientes métodos:</span><span class="sxs-lookup"><span data-stu-id="2cbfb-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="2cbfb-107">Método</span><span class="sxs-lookup"><span data-stu-id="2cbfb-107">Method</span></span>|<span data-ttu-id="2cbfb-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="2cbfb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cbfb-109">Método GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="2cbfb-109">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="2cbfb-110">Funciona igual que el [método GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , salvo que la cadena de ruta de acceso se rellena con ceros después del carácter nulo de terminación para convertir los datos de cadena en un tamaño fijo de `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="2cbfb-110">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="2cbfb-111">El relleno solo se proporciona si la longitud de la cadena de ruta de acceso es menor que `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="2cbfb-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="2cbfb-112">Esto facilita la escritura de herramientas que diferencian los archivos PE.</span><span class="sxs-lookup"><span data-stu-id="2cbfb-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cbfb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cbfb-113">Requirements</span></span>  

 <span data-ttu-id="2cbfb-114">**Encabezado:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2cbfb-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbfb-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2cbfb-115">See also</span></span>

- [<span data-ttu-id="2cbfb-116">Interfaces de almacén de símbolos de diagnósticos</span><span class="sxs-lookup"><span data-stu-id="2cbfb-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="2cbfb-117">ISymUnmanagedWriter3 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="2cbfb-117">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
