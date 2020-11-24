---
title: CorExitProcess (Función)
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: f6d8114732a3b7c15d0a0258a28a362d661b030a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673649"
---
# <a name="corexitprocess-function"></a>CorExitProcess (Función)

Cierra el proceso no administrado actual.  
  
 Esta función está en desuso en el .NET Framework 4. Use en su lugar el método [ICLRMetaHost:: ExitProcess](iclrmetahost-exitprocess-method.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>Parámetros  

 `exitCode`  
 Un entero que especifica el código de salida del proceso.  
  
## <a name="remarks"></a>Comentarios  
  
> [!NOTE]
> A partir de la .NET Framework 4, `CorExitProcess` sale de cada tiempo de ejecución iniciado en el proceso, no solo el Runtime al que se han enlazado las API heredadas.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [Funciones de hospedaje de CLR en desuso](deprecated-clr-hosting-functions.md)
