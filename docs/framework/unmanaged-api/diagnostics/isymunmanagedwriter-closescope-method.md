---
title: ISymUnmanagedWriter::CloseScope (Método)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: 561a6348b9976789b02961fadb37d9127f5a6a13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713046"
---
# <a name="isymunmanagedwriterclosescope-method"></a>ISymUnmanagedWriter::CloseScope (Método)

Cierra el ámbito léxico actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a>Parámetros  

 `endOffset`  
 de Desplazamiento desde el principio del método del punto al final de la última instrucción del ámbito léxico, en bytes.  
  
## <a name="return-value"></a>Valor devuelto  

 S_OK si el método se ejecuta correctamente; de lo contrario, E_FAIL u otro código de error.  
  
## <a name="remarks"></a>Comentarios  

 Una vez que se cierra un ámbito, no se pueden definir más variables en él.  
  
 [ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) devuelve un identificador de ámbito opaco que se puede usar con [ISymUnmanagedWriter:: SetScopeRange (](isymunmanagedwriter-setscoperange-method.md) para definir más adelante el desplazamiento inicial y final de un ámbito. En este caso, se omiten los desplazamientos pasados a `ISymUnmanagedWriter::OpenScope` y `ISymUnmanagedWriter::CloseScope`. Los identificadores de ámbito solo son válidos en el método actual.  
  
## <a name="requirements"></a>Requisitos  

 **Encabezado:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte también

- [ISymUnmanagedWriter (Interfaz)](isymunmanagedwriter-interface.md)
