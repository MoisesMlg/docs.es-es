---
description: -nowin32manifest (Opciones del compilador de C#)
title: -nowin32manifest (Opciones del compilador de C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 13bbee66901149d54632d9b164431f8898cdf52e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194003"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (Opciones del compilador de C#)

Use la opción **-nowin32manifest** para indicar al compilador que no inserte ningún manifiesto de aplicación en el archivo ejecutable.  
  
## <a name="syntax"></a>Sintaxis  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Comentarios  

 Cuando se use esta opción, la aplicación estará sujeta a la virtualización en Windows Vista a menos que proporcione un manifiesto de aplicación en un archivo de recursos Win32 o durante un paso de compilación posterior.  
  
 En Visual Studio, defina esta opción en la página de **propiedades de la aplicación** seleccionando la opción **Crear aplicación sin manifiesto** en la lista desplegable **Manifiesto**. Para más información, vea [Página de aplicación, Diseñador de proyectos (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Para más información sobre la creación de manifiestos, vea [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md) (-win32manifest [Opciones del compilador de C#]).  
  
## <a name="see-also"></a>Vea también

- [Opciones del compilador de C#](./index.md)
- [Administrar propiedades de soluciones y proyectos](/visualstudio/ide/managing-project-and-solution-properties)
