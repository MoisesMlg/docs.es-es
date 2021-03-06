---
title: Procedimiento para instalar y configurar los componentes de activación de WFC
description: Obtenga información acerca de cómo configurar el servicio de activación de procesos de Windows (WAS) en Windows Vista para hospedar servicios WCF que no se comunican a través de HTTP.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 085a69421f0aa7b763bd2222820ced4b4a7e1c81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557871"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Procedimiento para instalar y configurar los componentes de activación de WFC

En este tema se describen los pasos necesarios para configurar el servicio de activación de procesos de Windows (también conocido como WAS) en Windows Vista para hospedar servicios Windows Communication Foundation (WCF) que no se comunican a través de protocolos de red HTTP. Las siguientes secciones describen los pasos para realizar esta configuración:

- Instale (o confirme la instalación de) los componentes de activación de WCF.

- Configure WAS para que admita un protocolo que no sea HTTP. El procedimiento siguiente configura Windows Vista para la activación de TCP.

Después de instalar y configurar WAS, consulte [Cómo: hospedar un servicio WCF en was](how-to-host-a-wcf-service-in-was.md) para los procedimientos para crear un servicio WCF que exponga un punto de conexión que no sea http y que emplee was.

## <a name="to-install-the-wcf-non-http-activation-components"></a>Instalación de los componentes de activación que no son HTTP de WCF

1. Haga clic en el botón **Inicio** y, a continuación, haga clic en **Panel de control**.

2. Haga clic en **Programas** y, a continuación, haga clic en **Programas y características**.

3. En el menú **tareas** , haga clic en **activar o desactivar las características de Windows**.

4. Busque el nodo WinFX, selecciónelo y, a continuación, expándalo.

5. Seleccione el cuadro **componentes de activación no http de WCF** y guarde la configuración.

## <a name="to-configure-the-was-to-support-tcp-activation"></a>Configuración de WAS para admitir la activación TCP

1. Para admitir la activación del net.tcp, el sitio web predeterminado debe enlazarse primero a un puerto net.tcp. Puede hacerlo mediante Appcmd.exe, que se instala con el conjunto de herramientas de administración de IIS 7,0. En una ventana de símbolo de sistema para administradores, ejecute el siguiente comando.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Este comando es una sola línea de texto. Este comando agrega un enlace del sitio net.tcp al sitio web predeterminado que realiza escuchas en el puerto TCP 808 con cualquier nombre de host.

2. Aunque todas las aplicaciones dentro de un sitio comparten un enlace net. tcp común, cada aplicación puede habilitar la compatibilidad net. tcp individualmente. Para habilitar net.tcp para la aplicación, ejecute el siguiente comando desde un símbolo del sistema del nivel del administrador:

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > Este comando es una sola línea de texto. Este comando permite \<*WCF Application*> tener acceso a la aplicación/mediante `http://localhost/<WCF Application>` y `net.tcp://localhost/<WCF Application>` .

     Elimine el enlace del sitio de net.tcp que ha agregado para este ejemplo.

     Para su comodidad, los dos pasos siguientes se implementan en un archivo de información llamado RemoveNetTcpSiteBinding.cmd localizado en el directorio de ejemplo.

    1. Quite el net.tcp de la lista de protocolos habilitados ejecutando el comando siguiente en una ventana de símbolo del sistema del nivel del administrador:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > Este comando es una sola línea de texto.

    2. Quite el enlace del sitio net.tcp ejecutando el siguiente comando desde una ventana de símbolo del sistema elevado:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > Este comando es una sola línea de texto.

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Quitar el net.tcp de la lista de protocolos habilitados

1. Para quitar el net.tcp de la lista de protocolos habilitados, ejecute el siguiente comando en una ventana de símbolo del sistema del nivel del administrador:

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > Este comando es una sola línea de texto.

## <a name="to-remove-the-nettcp-site-binding"></a>Quitar el enlace de sitio de net.tcp

1. Para quitar el enlace del sitio net.tcp ejecute el siguiente comando desde una ventana de símbolo del sistema en el nivel de administrador:

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Este comando es una sola línea de texto.

## <a name="see-also"></a>Vea también

- [Activación de TCP](../samples/tcp-activation.md)
- [Activación MSMQ](../samples/msmq-activation.md)
- [Activación NamedPipe](../samples/namedpipe-activation.md)
- [Características de hospedaje de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))
