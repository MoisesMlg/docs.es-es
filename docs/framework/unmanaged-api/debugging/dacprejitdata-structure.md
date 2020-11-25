---
title: Estructura DacpReJitData
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 46708acc77dad00727ee35e7d06e4228eacbd502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723043"
---
# <a name="dacprejitdata-structure"></a>Estructura DacpReJitData

Define la información básica sobre un método instrumentado del generador de perfiles determinado.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxis

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>Miembros

| Miembro           | Descripción                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | El número de revisión de ReJit para un método.                                                          |
| `flags`          | Marca que indica el estado actual de la instrumentación ReJit del método para la versión especificada. |
| `NativeCodeAddr` | Dirección base de la implementación de rejitted del método.                                         |

## <a name="remarks"></a>Comentarios

Esta estructura reside dentro del tiempo de ejecución y no se expone a través de los encabezados o archivos de biblioteca. Para usarlo, defina la estructura tal y como se especificó anteriormente. La estructura también debe definirse mediante `ms_struct` Packing si no se usan los compiladores de Microsoft.

## <a name="requirements"></a>Requisitos

**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
**Encabezado:** Ninguna  
**Biblioteca:** Ninguna  
**.NET Framework versiones:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte también

- [Depuración](index.md)
- [Estructuras de depuración](debugging-structures.md)
