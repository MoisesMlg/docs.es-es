---
title: Definición de constantes en C#
description: Aprenda a definir constantes de C#, que son campos cuyos valores se establecen en tiempo de compilación. Use constantes para proporcionar nombres descriptivos a los valores especiales.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 42ea67e9012fd55fbceb8a7bad4c8df8bf6bf6da
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099392"
---
# <a name="how-to-define-constants-in-c"></a>Definición de constantes en C\#

Las constantes son campos cuyos valores se establecen en tiempo de compilación y nunca se pueden cambiar. Use constantes para proporcionar nombres descriptivos en lugar de literales numéricos ("números mágicos") para valores especiales.  
  
> [!NOTE]
> En C#, la directiva del preprocesador [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) no puede usarse para definir constantes en la manera que se usa normalmente en C y C++.  
  
 Para definir valores constantes de tipos enteros (`int`, `byte` y así sucesivamente) use un tipo enumerado. Para más información, vea [enum](../../language-reference/builtin-types/enum.md).  
  
 Para definir constantes no enteras, un enfoque es agruparlas en una única clase estática denominada `Constants`. Esto necesitará que todas las referencias a las constantes vayan precedidas por el nombre de clase, como se muestra en el ejemplo siguiente.  
  
## <a name="example"></a>Ejemplo  

 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 El uso del calificador de nombre de clase ayuda a garantizar que usted y otros usuarios que usan la constante comprenden que es una constante y que no puede modificarse.  
  
## <a name="see-also"></a>Consulte también

- [Clases y structs](./index.md)
