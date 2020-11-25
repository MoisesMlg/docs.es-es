---
title: IMetaDataImport::EnumCustomAttributes (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 3b12200dae23a7b6a2f6e1654e46fdf74dc90968
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700540"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes (Método)

Enumera los tokens de definición de atributos personalizados asociados al tipo o miembro especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `phEnum`  
 [in, out] Puntero al enumerador devuelto.  
  
 `tk`  
 de Un token para el ámbito de la enumeración o cero para todos los atributos personalizados.  
  
 `tkType`  
 de Token para el constructor del tipo de los atributos que se van a enumerar o `null` para todos los tipos.  
  
 `rCustomAttributes`  
 enuncia Matriz de tokens de atributos personalizados.  
  
 `cMax`  
 [in] Tamaño máximo de la matriz `rCustomAttributes`.  
  
 `pcCustomAttributes`  
 [out, opcional] Número real de valores de token devueltos en `rCustomAttributes` .  
  
## <a name="return-value"></a>Valor devuelto  
  
|HRESULT|Descripción|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes` se devolvió correctamente.|  
|`S_FALSE`|No hay atributos personalizados para enumerar. En ese caso, `pcCustomAttributes` es cero.|  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** Cor. h  
  
 **Biblioteca:** Se incluye como un recurso en MsCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [IMetaDataImport (Interfaz)](imetadataimport-interface.md)
- [IMetaDataImport2 (Interfaz)](imetadataimport2-interface.md)
