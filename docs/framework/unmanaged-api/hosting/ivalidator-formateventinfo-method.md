---
title: IValidator::FormatEventInfo (Método)
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: c5c89e0eda6e93e34775c00d5ec8fb4ff0940707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701021"
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo (Método)

Obtiene el mensaje de error correspondiente al error de validación especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `hVECode`  
 de Valor HRESULT que se pasó al controlador de errores de validación.  
  
 `Context`  
 de `VEContext` Instancia de que contiene información de contexto sobre el error de validación.  
  
 `msg`  
 [in, out] Cadena que contiene el mensaje de error devuelto.  
  
 `ulMaxLength`  
 de La longitud máxima del mensaje de error.  
  
 `psa`  
 de Matriz segura que contiene los parámetros adicionales que describen el error.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** IValidator. idl, IValidator. h  
  
 **Biblioteca:** Se incluye como un recurso en MSCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
