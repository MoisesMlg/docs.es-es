---
title: IMetaDataAssemblyEmit::DefineFile (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 1dd71dbe0ddb894cb5ed05c32e50429d27c66aa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689334"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile (Método)

Crea una estructura de metadatos `File` que contiene los metadatos para el ensamblado al que se refiere este ensamblado y devuelve el token de metadatos asociado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `szName`  
 de Nombre del archivo que se va a consumir.  
  
 `pbHashValue`  
 de Puntero a los datos hash asociados al ensamblado.  
  
 `cbHashValue`  
 de Tamaño en bytes de `pbHashValue` .  
  
 `dwFileFlags`  
 de Combinación bit a bit de `FileFlags` valores que especifican la configuración de propiedades.  
  
 `pmdf`  
 enuncia Puntero al token devuelto `File` .  
  
## <a name="remarks"></a>Comentarios  

 Se `File` debe definir una estructura de metadatos para cada archivo que formaba parte de este ensamblado en el momento en que se compiló este ensamblado, excluyendo el archivo que contiene los metadatos.  
  
## <a name="requirements"></a>Requisitos  

 **Plataforma:** Consulte [requisitos del sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** Cor. h  
  
 **Biblioteca:** Se usa como un recurso en MsCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [IMetaDataAssemblyEmit (Interfaz)](imetadataassemblyemit-interface.md)
