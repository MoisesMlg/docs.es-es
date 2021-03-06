---
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 27fc993ca0b94d406261d5e6275de8cd619eb6a8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303457"
---
# <a name="protected-friend-visual-basic"></a>Friend protegido (Visual Basic)

La combinación de palabras claves `Protected Friend` es un modificador de acceso de miembro. Confiere acceso de [confianza](friend.md) y acceso [protegido](protected.md) en los elementos declarados, por lo que son accesibles desde cualquier lugar del mismo ensamblado, desde su propia clase y desde las clases derivadas. Solo se puede especificar `Protected Friend` en miembros de clases; no se puede aplicar `Protected Friend` a los miembros de una estructura porque las estructuras no se pueden heredar.

> [!NOTE]
> En Visual Studio, al seleccionar la ayuda F1 en se `protected friend` proporciona ayuda para [Protected](protected.md) o [Friend](friend.md). El IDE elige el token único bajo el cursor en lugar de la palabra compuesta.

## <a name="rules"></a>Reglas

**Contexto de declaración.** Solo se puede usar `Protected Friend` en el nivel de clase. Esto significa que el contexto de la declaración de un `Protected` elemento debe ser una clase y no puede ser un archivo de código fuente, un espacio de nombres, una interfaz, un módulo, una estructura o un procedimiento.

## <a name="see-also"></a>Consulte también

- [Pública](public.md)
- [Contra](protected.md)
- [Respecto](friend.md)
- [Privada](private.md)
- [Privado protegido](./private-protected.md)
- [Niveles de acceso en Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimientos](../../programming-guide/language-features/procedures/index.md)
- [Estructuras](../../programming-guide/language-features/data-types/structures.md)
- [Objetos y clases](../../programming-guide/language-features/objects-and-classes/index.md)
