---
title: Nombres de ensamblados y bibliotecas DLL
description: Obtenga información sobre las directrices para asignar nombres a ensamblados y bibliotecas de vínculos dinámicos (dll). Un ensamblado puede abarcar uno o varios archivos, pero normalmente se asigna uno a uno con un archivo DLL.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: 2d1484889eb7db537de970c31109f26a6d61ad8d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830056"
---
# <a name="names-of-assemblies-and-dlls"></a>Nombres de ensamblados y bibliotecas DLL
Un ensamblado es la unidad de implementación e identidad para los programas de código administrado. Aunque los ensamblados pueden abarcar uno o varios archivos, normalmente un ensamblado se asigna uno a uno con un archivo DLL. Por lo tanto, en esta sección solo se describen las convenciones de nomenclatura de archivos DLL, que se pueden asignar a las convenciones de nomenclatura de ensamblados.

 ✔️ Elija nombres para los archivos dll de ensamblado que sugieran grandes fragmentos de funcionalidad, como System. Data.

 No es necesario que los nombres de ensamblado y DLL se correspondan con los nombres de espacios de nombres, pero es razonable seguir el nombre del espacio de nombres al asignar nombres a los ensamblados. Una buena regla general es asignar un nombre a la DLL basándose en el prefijo común de los espacios de nombres contenidos en el ensamblado. Por ejemplo, `MyCompany.MyTechnology.FirstFeature` `MyCompany.MyTechnology.SecondFeature` se podría llamar a un ensamblado con dos espacios de nombres, y `MyCompany.MyTechnology.dll` .

 ✔️ considere la posibilidad de asignar nombres a los archivos dll según el siguiente patrón:

 `<Company>.<Component>.dll`

 donde `<Component>` contiene una o más cláusulas separadas por puntos. Por ejemplo:

 `Litware.Controls.dll`.

 *Partes © 2005, 2009 Microsoft Corporation. Todos los derechos reservados.*

 *Material reimpreso con el consentimiento de Pearson Education, Inc. y extraído de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) (Instrucciones de diseño de .NET Framework: convenciones, expresiones y patrones para bibliotecas .NET reutilizables, 2.ª edición), de Krzysztof Cwalina y Brad Abrams, publicado el 22 de octubre de 2008 por Addison-Wesley Professional como parte de la serie Microsoft Windows Development.*

## <a name="see-also"></a>Vea también

- [Directrices de diseño de marco](index.md)
- [Instrucciones de nomenclatura](naming-guidelines.md)
