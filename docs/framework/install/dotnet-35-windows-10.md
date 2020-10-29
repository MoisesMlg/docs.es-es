---
title: Instalación de .NET Framework 3.5 en Windows 10, 8.1 y 8
description: Aprenda a instalar .NET Framework 3.5 en Windows 10, Windows 8.1 y Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: a385c46d2b3b384bc0a413d1dfa80e88ba7fb00a
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223803"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalación de .NET Framework 3.5 en Windows 10, Windows 8.1 y Windows 8

Para ejecutar una aplicación en Windows 10, Windows 8.1 y Windows 8, es posible que necesite .NET Framework 3.5. También puede usar estas instrucciones para versiones anteriores de Windows.

## <a name="download-the-offline-installer"></a>Descarga del instalador sin conexión

El instalador sin conexión de .NET Framework 3.5 SP1 está disponible en la [página de descarga de .NET Framework 3.5 SP1](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) y está disponible para las versiones de Windows anteriores a Windows 10.

## <a name="install-the-net-framework-35-on-demand"></a>Instalar .NET Framework 3.5 a petición

Si intenta ejecutar una aplicación que requiere .NET Framework 3.5, es posible que vea el siguiente cuadro de diálogo de configuración. Elija **Instalar esta característica** para habilitar .NET Framework 3.5. Esta opción requiere una conexión a Internet.

![Captura de pantalla del cuadro de diálogo de instalación de .NET Framework.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>¿Por qué recibo este elemento emergente?

Microsoft ha creado .NET Framework y proporciona un entorno para ejecutar aplicaciones. Hay diferentes versiones disponibles. Muchas empresas desarrollan sus aplicaciones para que se ejecuten con .NET Framework, y estas aplicaciones se dirigen a una versión específica. Si ve este elemento emergente, está intentando ejecutar una aplicación que requiere la versión 3.5 de .NET Framework, pero esa versión no está instalada en su sistema.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Habilitar .NET Framework 3.5 en el Panel de control

Puede habilitar .NET Framework 3.5 mediante el Panel de control de Windows. Esta opción requiere una conexión a Internet.

1. Presione la tecla del logotipo de Windows ![Captura de pantalla de la tecla del logotipo de Windows.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) en el teclado, escriba "Características de Windows" y presione Entrar. Aparecerá el cuadro de diálogo **Activar o desactivar las características de Windows** .

2. Active la casilla **.NET Framework 3.5 (incluye .NET 2.0 y 3.0)** , seleccione **Aceptar** y reinicie el equipo si se le solicita.

   ![Captura de pantalla que muestra la instalación de .NET con el panel de control.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   No necesita seleccionar los elementos secundarios para la **activación HTTP de Windows Communication Foundation (WCF)** y la **activación no HTTP de Windows Communication Foundation (WCF)** , a menos que sea un desarrollador o administrador de servidores que requiera esta funcionalidad.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Solución de problemas de instalación de .NET Framework 3.5

Durante la instalación es posible que encuentre el error 0x800f0906, 0x800f0907, 0x800f081f, o 0x800F0922. En ese caso, consulte [Error de instalación de .NET Framework 3.5: 0x800F0906, 0x800F081F, 0x800F0907](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) para ver cómo solucionar estos problemas.

Si todavía no puede resolver el problema de instalación o no dispone de una conexión a Internet, puede intentar instalarlo mediante el soporte de instalación de Windows. Para obtener más información, consulte [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism) (Implementación de .NET Framework 3.5 mediante Administración y mantenimiento de imágenes de implementación). Si usa Windows 7, Windows 8.1 o la versión más reciente de Windows 10 pero no dispone de los soportes de instalación, cree uno actualizado aquí: [Crear medios de instalación de Windows](https://support.microsoft.com/help/15088/windows-create-installation-media). Información adicional sobre las características a petición de Windows 10: [Características a petición](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).

> [!WARNING]
> Si no va a depender de Windows Update como origen para la instalación de .NET Framework 3.5, debe asegurarse de usar estrictamente los orígenes de la misma versión del sistema operativo de Windows correspondiente. El uso de orígenes de otra versión del sistema operativo Windows instala una versión no coincidente de .NET Framework 3.5 o hace que se produzca un error en la instalación, lo que deja al sistema en un estado no compatible y sin posibilidad de mantenimiento.
