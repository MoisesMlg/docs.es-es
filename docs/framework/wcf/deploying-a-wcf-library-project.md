---
title: Implementación de un proyecto de biblioteca de WFC
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: e3a90f03639a888b4528a1962a24b7adc5d43c58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260895"
---
# <a name="deploying-a-wcf-library-project"></a>Implementación de un proyecto de biblioteca de WFC

En este tema se describe cómo se puede implementar un proyecto de biblioteca de servicios de Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Implementación de una biblioteca de servicios de WFC  

 Una biblioteca de servicios WCF es una biblioteca de vínculos dinámicos (DLL). Como tal, no se puede ejecutar por sí misma. Se ha de implementar en un entorno de hospedaje. Para obtener más información acerca de este proceso, vea [hospedaje y consumo de servicios WCF](/previous-versions/dotnet/articles/bb332338(v=msdn.10)).  
  
 Una biblioteca de servicios WCF se puede implementar como cualquier otro servicio WCF. Sin embargo, tenga en cuenta que .NET Framework no admite la configuración de archivos dll. <xref:System.Configuration> admite un archivo de configuración por dominio de aplicación. El proyecto de biblioteca de servicios WCF alivia esta limitación proporcionando un archivo de App.config para la biblioteca durante el desarrollo. Sin embargo, el archivo App.config no se reconoce después de la implementación.  
  
 Tiene que pasar su código de configuración al archivo de configuración reconocido por su entorno de hospedaje. Para el autohospedaje, debería copiar el contenido del archivo App.config en el archivo App.config del hospedaje ejecutable. Si utiliza IIS para hospedar su servicio, debería copiar el contenido del archivo App.config en el archivo Web.config del directorio virtual.
