---
title: ICorProfilerInfo::GetInprocInspectionIThisThread (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 8daa84e3abbbc64c9a48d8957b4ad9c6756d0d8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682086"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread (Método)

Obtiene un objeto que se puede consultar para la interfaz ICorDebugThread. Este método está obsoleto en la .NET Framework versión 2,0.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parámetros  

 `ppicd`  
 objeto [out](/cpp/atl/iunknown) que se puede consultar para la `ICorDebugThread` interfaz.  
  
## <a name="remarks"></a>Comentarios  

 Los servicios de depuración de Common Language Runtime (CLR) admiten la depuración limitada en proceso en la versión 1,0 de .NET Framework. La depuración en proceso ha habilitado un generador de perfiles para usar las partes de inspección de la API de depuración. Como resultado de los comentarios de los clientes, la depuración en proceso se ha quitado del .NET Framework en la versión 2,0 y se ha reemplazado por un conjunto de funcionalidades que está más en línea con la API de generación de perfiles.  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versión de .NET Framework:** 1,0  
  
## <a name="see-also"></a>Consulte también

- [ICorProfilerInfo (Interfaz)](icorprofilerinfo-interface.md)
