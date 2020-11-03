---
title: Procedimiento para usar canalizaciones con nombre para la comunicación de red entre procesos
description: Vea dos ejemplos de uso de canalizaciones con nombre para la comunicación entre procesos entre un servidor de canalización y uno o varios clientes de canalización en una red.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET], named pipes
- named pipes [.NET]
- pipes [.NET]
- multiple connections via named pipes
- network communications [.NET], named pipes
- impersonation [.NET], named pipes
- full duplex communication [.NET], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: 8657597bee5855061bb5529d80d2fa5f0318e817
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189321"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Procedimiento para usar canalizaciones con nombre para la comunicación de red entre procesos

Las canalizaciones con nombre permiten la comunicación entre procesos entre un servidor de canalización y uno o varios clientes de canalización. Proporcionan más funcionalidad que las canalizaciones anónimas, que permiten la comunicación entre procesos en un equipo local. Las canalizaciones con nombre admiten la comunicación dúplex completa a través de una red y varias instancias de servidor, la comunicación mediante mensajes y la suplantación de clientes, que permite a los procesos que se conectan utilizar su propio conjunto de permisos en servidores remotos.  
  
 Para implementar canalizaciones con nombre, use las clases <xref:System.IO.Pipes.NamedPipeServerStream> y <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo crear una canalización con nombre mediante la clase <xref:System.IO.Pipes.NamedPipeServerStream>. En este ejemplo, el proceso de servidor crea cuatro subprocesos. Cada subproceso puede aceptar una conexión de cliente. A continuación, el proceso de cliente conectado proporciona un nombre de archivo al servidor. Si el cliente tiene los permisos necesarios, el proceso de servidor abre el archivo y envía su contenido de vuelta al cliente.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el proceso de cliente, que utiliza la clase <xref:System.IO.Pipes.NamedPipeClientStream>. El cliente se conecta al proceso de servidor y envía un nombre de archivo al servidor. En el ejemplo, se utiliza la suplantación, por lo que la identidad que ejecuta la aplicación cliente debe tener permiso de acceso al archivo. A continuación, el servidor devuelve el contenido del archivo al cliente. El contenido del archivo se muestra en la consola.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Los procesos de servidor y cliente de este ejemplo están diseñados para ejecutarse en el mismo equipo, por lo que el nombre del servidor proporcionado al objeto <xref:System.IO.Pipes.NamedPipeClientStream> es `"."`. Si los procesos de servidor y cliente estuvieran en equipos independientes, `"."` se reemplazaría por el nombre de red del equipo que ejecuta el proceso de servidor.  
  
## <a name="see-also"></a>Vea también

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [Pipes](pipe-operations.md) (Operaciones de canalización de .NET Framework)
- [Cómo: Usar canalizaciones anónimas para la comunicación local entre procesos](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
