---
title: Mutexes
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET], Mutex class
- Mutex class, about Mutex class
- threading [.NET], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
ms.openlocfilehash: ba31fff03cfffda7cf2a40a3a82b2222e8951035
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188996"
---
# <a name="mutexes"></a>Mutexes

Puede usar un objeto <xref:System.Threading.Mutex> para proporcionar acceso exclusivo a un recurso. La clase <xref:System.Threading.Mutex> usa más recursos del sistema que la clase <xref:System.Threading.Monitor>, pero se pueden calcular sus referencias a través de los límites de dominio de aplicación, se puede usar con varias esperas y se puede usar para sincronizar subprocesos en distintos procesos. Para ver una comparación de los mecanismos de sincronización administrados, consulte [Información general sobre los primitivos de sincronización](overview-of-synchronization-primitives.md).  
  
 Para ver ejemplos de código, consulte la documentación de referencia para los constructores <xref:System.Threading.Mutex.%23ctor%2A>.  
  
## <a name="using-mutexes"></a>Uso de las exclusiones mutuas  
 Un subproceso llama al método <xref:System.Threading.WaitHandle.WaitOne%2A> de una exclusión mutua que solicite la propiedad. La llamada se bloquea hasta que está disponible la exclusión mutua o hasta que transcurre el intervalo de tiempo de espera opcional. El estado de una exclusión mutua se señala si no es propiedad de ningún subproceso.  
  
 Un subproceso libera una exclusión mutua mediante una llamada a su método <xref:System.Threading.Mutex.ReleaseMutex%2A>. Las exclusiones mutuas tienen afinidad de subprocesos, es decir, solo el subproceso propietario de la exclusión mutua puede liberarla. Si un subproceso libera una exclusión mutua que no es de su propiedad, se genera <xref:System.ApplicationException> en el subproceso.  
  
 Dado que la clase <xref:System.Threading.Mutex> se deriva de <xref:System.Threading.WaitHandle>, también puede llamar el método estático <xref:System.Threading.WaitHandle.WaitAll%2A> o <xref:System.Threading.WaitHandle.WaitAny%2A> de <xref:System.Threading.WaitHandle> para solicitar la propiedad de <xref:System.Threading.Mutex> en combinación con otros indicadores de espera.  
  
 Si un subproceso es propietario de <xref:System.Threading.Mutex>, puede especificar la misma <xref:System.Threading.Mutex> en llamadas repetidas de solicitud de espera sin bloquear su ejecución; sin embargo, debe liberar <xref:System.Threading.Mutex> la misma cantidad de veces para liberar la propiedad.  
  
## <a name="abandoned-mutexes"></a>Exclusiones mutuas abandonadas  
 Si un subproceso finaliza sin liberar <xref:System.Threading.Mutex>, la exclusión mutua se considera abandonada. A menudo, esto indica un grave error de programación porque el recurso al que protege la exclusión mutua podría quedar con un estado no coherente. Se inicia una excepción <xref:System.Threading.AbandonedMutexException> en el siguiente subproceso que adquiere la exclusión mutua.
  
 En el caso de una exclusión mutua en todo el sistema, una exclusión mutua abandonada podría indicar que una aplicación finalizó inesperadamente (por ejemplo, con el Administrador de tareas de Windows).  
  
## <a name="local-and-system-mutexes"></a>Exclusiones mutuas locales y del sistema  
 Hay dos tipos de exclusiones mutuas: exclusiones mutuas locales y exclusiones mutuas del sistema con nombre. Si crea un objeto <xref:System.Threading.Mutex> con un constructor que acepta un nombre, se asocia con un objeto del sistema operativo con ese nombre. Las exclusiones mutuas del sistema con nombre son visibles en todo el sistema operativo y se pueden usar para sincronizar las actividades de los procesos. Puede crear varios objetos <xref:System.Threading.Mutex> que representen la misma exclusión mutua del sistema con nombre y puede usar el método <xref:System.Threading.Mutex.OpenExisting%2A> para abrir una exclusión mutua del sistema con nombre existente.  
  
 Una exclusión mutua local solo existe dentro del proceso. La puede usar cualquier subproceso del proceso que tenga una referencia al objeto <xref:System.Threading.Mutex> local. Cada objeto <xref:System.Threading.Mutex> es una exclusión mutua local independiente.  
  
### <a name="access-control-security-for-system-mutexes"></a>Seguridad de control de acceso para exclusiones mutuas del sistema  

.NET proporciona la capacidad de consultar y establecer la seguridad de control de acceso de Windows para los objetos del sistema con nombre. Se recomienda proteger las exclusiones mutuas del sistema desde el momento en que se crean, porque los objetos de sistema son globales y, por lo tanto, puede bloquearlos un código distinto del suyo.  
  
 Para obtener información sobre la seguridad de control de acceso para las exclusiones mutuas, vea las clases <xref:System.Security.AccessControl.MutexSecurity> y <xref:System.Security.AccessControl.MutexAccessRule>, la enumeración <xref:System.Security.AccessControl.MutexRights>, los métodos <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A> y <xref:System.Threading.Mutex.OpenExisting%2A> de la clase <xref:System.Threading.Mutex> y el constructor <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>.  
  
## <a name="see-also"></a>Vea también

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Objetos y características de subprocesos](threading-objects-and-features.md)
- [Subprocesos y subprocesamiento](threads-and-threading.md)
- [Subprocesamiento](index.md)
