---
description: -highentropyva (Opciones del compilador de C#)
title: -highentropyva (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: f3cdeb5e63d632fecbbd94501558cc53c28a918a
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173209"
---
# <a name="-highentropyva-c-compiler-options"></a>-highentropyva (Opciones del compilador de C#)

La opción del compilador **-highentropyva** indica al kernel de Windows si un archivo ejecutable determinado admite la selección aleatoria del diseño del espacio de direcciones (ASLR) de alta entropía.  
  
## <a name="syntax"></a>Sintaxis  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Argumentos  

 `+` &#124; `-`  
 Esta opción especifica que un archivo ejecutable de 64 bits o un archivo ejecutable que está marcado con la opción del compilador [-platform:anycpu](./platform-compiler-option.md) admite un espacio de direcciones virtuales de alta entropía. La opción está deshabilitada de forma predeterminada. Para habilitarla, use **-highentropyva+** o **-highentropyva**.  
  
## <a name="remarks"></a>Comentarios  

 La opción **-highentropyva** habilita las versiones compatibles del kernel de Windows para usar niveles superiores de entropía al aleatorizar el diseño del espacio de direcciones de un proceso como parte de ASLR. El uso de niveles superiores de entropía significa que un mayor número de direcciones se puede asignar a las regiones de memoria como pilas y montones. Como resultado, la ubicación de un área de memoria específica es más difícil de adivinar.  
  
 Cuando se especifica la opción del compilador **-highentropyva**, el archivo ejecutable de destino y todos los módulos de los que depende deben ser capaces de controlar los valores de puntero que son superiores a 4 gigas (GB), cuando se ejecutan como un proceso de 64 bits.
