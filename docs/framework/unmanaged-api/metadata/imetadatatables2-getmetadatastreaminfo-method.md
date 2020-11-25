---
title: IMetaDataTables2::GetMetaDataStreamInfo (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 21fc79f62dba4b16a7a067dff8fb9dcc795c9d35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708730"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a>IMetaDataTables2::GetMetaDataStreamInfo (Método)

Obtiene el nombre, el tamaño y el contenido de la secuencia de metadatos en el índice especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `ix`  
 de Índice de la secuencia de metadatos solicitada.  
  
 `ppchName`  
 enuncia Puntero al nombre de la secuencia.  
  
 `ppv`  
 enuncia Puntero a la secuencia de metadatos.  
  
 `pcb`  
 enuncia Tamaño, en bytes, de `ppv` .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** Cor. h  
  
 **Biblioteca:** Se usa como un recurso en MsCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [IMetaDataTables2 (Interfaz)](imetadatatables2-interface.md)
- [IMetaDataTables (Interfaz)](imetadatatables-interface.md)
