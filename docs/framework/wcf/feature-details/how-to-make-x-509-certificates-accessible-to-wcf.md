---
title: Procedimiento para hacer los certificados X.509 accesibles para WCF
description: Obtenga información acerca de cómo hacer que un certificado X. 509 sea accesible para WCF. El código de aplicación debe especificar el nombre y la ubicación del almacén de certificados. Puede haber otros requisitos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 06a6167f0ad352955eb6b764ef8bfdb1394f4ed9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279745"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Procedimiento para hacer los certificados X.509 accesibles para WCF

Para que un certificado X. 509 sea accesible para Windows Communication Foundation (WCF), el código de aplicación debe especificar el nombre y la ubicación del almacén de certificados. En ciertas circunstancias, la identidad del proceso debe tener el acceso al archivo que contiene la clave privada asociada al certificado X.509. Para obtener la clave privada asociada a un certificado X. 509 en un almacén de certificados, WCF debe tener permiso para hacerlo. De forma predeterminada, solo el propietario y la cuenta del sistema pueden tener acceso a la clave privada de un certificado.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Para hacer los certificados X.509 accesibles para WCF  
  
1. Proporcione a la cuenta con la que WCF está ejecutando acceso de lectura al archivo que contiene la clave privada asociada al certificado X. 509.  
  
    1. Determine si WCF requiere acceso de lectura a la clave privada para el certificado X. 509.  
  
         La tabla siguiente detalla si una clave privada debe estar disponible al utilizar un certificado X.509.  
  
        |Uso del certificado X.509|Clave privada|  
        |---------------------------|-----------------|  
        |Firmar digitalmente un mensaje SOAP saliente.|Yes|  
        |Comprobar la firma de un mensaje SOAP entrante.|No|  
        |Cifrar un mensaje SOAP saliente.|No|  
        |Descifrar un mensaje SOAP entrante.|Yes|  
  
    2. Determine la ubicación del almacén de certificados y diga dónde está almacenado el certificado.  
  
         El almacén de certificados en el que el certificado está almacenado se especifica en código de aplicación o en configuración. Por ejemplo, el ejemplo siguiente especifica que el certificado se encuentra en el almacén de certificados `CurrentUser` denominado `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Determine dónde se encuentra la clave privada para el certificado en el equipo mediante la herramienta [FindPrivateKey](../samples/findprivatekey.md) .  
  
         La herramienta [FindPrivateKey](../samples/findprivatekey.md) requiere el nombre del almacén de certificados, la ubicación del almacén de certificados y algo que identifica de forma única el certificado. La herramienta acepta el nombre de sujeto del certificado o su huella digital como identificador único. Para obtener más información sobre cómo determinar la huella digital de un certificado, consulte [Cómo: recuperar la huella digital de un certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         En el ejemplo de código siguiente se usa la herramienta [FindPrivateKey](../samples/findprivatekey.md) para determinar la ubicación de la clave privada de un certificado en el `My` almacén `CurrentUser` con una huella digital de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` .  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Determine la cuenta con la que se ejecuta WCF.  
  
         En la tabla siguiente se detalla la cuenta con la que se ejecuta WCF para un escenario determinado.  
  
        |Escenario|Identidad de proceso|  
        |--------------|----------------------|  
        |Cliente (consola o aplicación WinForms).|Usuario actualmente registrado.|  
        |Servicio que tiene host propio.|Usuario actualmente registrado.|  
        |Servicio hospedado en IIS 6,0 (Windows Server 2003) o IIS 7,0 (Windows Vista).|SERVICIO DE RED|  
        |Servicio que se hospeda en IIS 5. X (Windows XP).|Controlado por el elemento `<processModel>` en el archivo Machine.config. La cuenta predeterminada es ASPNET.|  
  
    5. Conceda acceso de lectura al archivo que contiene la clave privada a la cuenta con la que se está ejecutando WCF mediante una herramienta como icacls.exe.  
  
         En el ejemplo de código siguiente se edita la lista de control de acceso discrecional (DACL) del archivo especificado para conceder a la cuenta de servicio de red acceso de lectura (: R) al archivo.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Vea también

- [FindPrivateKey](../samples/findprivatekey.md)
- [Procedimiento para recuperar la huella digital de un certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Trabajar con certificados](working-with-certificates.md)
