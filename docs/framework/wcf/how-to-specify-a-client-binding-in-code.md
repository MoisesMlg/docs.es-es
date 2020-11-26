---
title: Procedimiento para especificar un enlace de cliente en el código
description: Obtenga información sobre cómo especificar el enlace de un cliente WCF de forma imperativa en el código. El cliente tiene acceso a un servicio en este ejemplo.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: f9a56c631d841fe60923c05a19bdec9db989ac60
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236577"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Procedimiento para especificar un enlace de cliente en el código

En este ejemplo, se crea un cliente para utilizar un servicio de la calculadora y el enlace para ese cliente se especifica en código de manera imperativa. El cliente obtiene acceso al `CalculatorService`, que implementa la interfaz `ICalculator`, y el servicio y el cliente utilizan la clase <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Este procedimiento asume que el servicio de la calculadora se está ejecutando. Para obtener información sobre cómo crear el servicio, vea [Cómo: especificar un enlace de servicio en la configuración](how-to-specify-a-service-binding-in-configuration.md). También usa la [herramienta de utilidad de metadatos de ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) proporciona para generar automáticamente los componentes de cliente. La herramienta genera el código de cliente para tener acceso al servicio.  
  
 El cliente se crea en dos partes. Svcutil.exe genera la `ClientCalculator` que implementa la interfaz `ICalculator`. Esta aplicación de cliente se construye mediante la creación de una instancia de `ClientCalculator` y especificando, a continuación, el enlace y la dirección del servicio mediante código.  
  
 Para la copia de origen de este ejemplo, consulte el ejemplo [BasicBinding](./samples/basicbinding.md) .  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Para especificar un enlace personalizado mediante código  
  
1. Utilice Svcutil.exe desde la línea de comandos para generar el código a partir de los metadatos del servicio.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. El cliente que se genera contiene la interfaz `ICalculator` que define el contrato de servicios que la implementación del cliente debe cumplir.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. El cliente generado también contiene la implementación de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Cree una instancia de `ClientCalculator` que utiliza la clase <xref:System.ServiceModel.BasicHttpBinding> en una aplicación cliente y, a continuación, llame a las operaciones del servicio en la dirección especificada.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Compile y ejecute el cliente.  
  
## <a name="see-also"></a>Vea también

- [Utilización de enlaces para configurar servicios y clientes](using-bindings-to-configure-services-and-clients.md)
