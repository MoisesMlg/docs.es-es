---
title: Instalación de F#
description: 'Obtenga información sobre cómo instalar F # de varias maneras diferentes.'
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224287"
---
# <a name="install-f"></a>Instalar F\#

Puede instalar F # de varias maneras, en función de su entorno.

## <a name="install-f-with-visual-studio"></a>Instalación de F # con Visual Studio

1. Si está descargando [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) por primera vez, primero instalará instalador de Visual Studio. Instale la edición adecuada de Visual Studio desde el instalador.

   Si ya tiene instalado Visual Studio, elija **modificar** junto a la edición a la que desea agregar F #.

2. En la página cargas de trabajo, seleccione la carga de trabajo **desarrollo de ASP.net y Web** , que incluye compatibilidad con F # y .net Core para proyectos de ASP.net Core.

3. Elija **modificar** en la esquina inferior derecha para instalar todo lo que ha seleccionado.

   Después, puede abrir Visual Studio con F # eligiendo **iniciar** en instalador de Visual Studio.

## <a name="install-f-with-visual-studio-code"></a>Instalar F # con Visual Studio Code

1. Asegúrese de que tiene [git](https://git-scm.com/download) instalado y disponible en su ruta de acceso. Para comprobar que se ha instalado correctamente, escriba `git --version` en un símbolo del sistema y presione **entrar**.

2. Instale el [SDK de .net Core](https://dotnet.microsoft.com/download) y [Visual Studio Code](https://code.visualstudio.com).

3. Seleccione el icono de extensiones y busque "Ionide":

   El único complemento necesario para la compatibilidad con F # en Visual Studio Code es [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Sin embargo, también puede instalar [Ionide-falsificación](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) para obtener compatibilidad [falsa](https://fake.build/) y [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) para obtener soporte técnico de [Paket](https://fsprojects.github.io/Paket/) . FALSAS y Paket son herramientas de la comunidad de F # adicionales para compilar proyectos y administrar dependencias, respectivamente.

## <a name="install-f-with-visual-studio-for-mac"></a>Instalar F # con Visual Studio para Mac

F # está instalado de forma predeterminada en [Visual Studio para Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), independientemente de la configuración que elija.

Una vez finalizada la instalación, elija **iniciar Visual Studio**. También puede abrir Visual Studio a través de Finder en macOS.

## <a name="install-f-on-a-build-server"></a>Instalar F # en un servidor de compilación

Si usa .NET Core o .NET Framework a través del SDK de .NET, solo tiene que instalar el SDK de .NET en el servidor de compilación. Tiene todo lo que necesita.

Si usa .NET Framework y **no** usa el SDK de .net, deberá instalar la [SKU de Visual Studio build tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) en el servidor de Windows. En el instalador, seleccione **herramientas de compilación de escritorio de .net**y, a continuación, seleccione el componente de **compilador de F #** en el lado derecho del menú del instalador.
