---
title: 'Mitigación: período de bloqueo del grupo'
description: Obtenga información sobre cómo mitigar los problemas causados por la eliminación del período de bloqueo del grupo de conexiones para las conexiones a bases de datos de Azure SQL.
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 270a71790f7a602df003415e9dc6dbf784cffdd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276573"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="27ab8-103">Mitigación: período de bloqueo del grupo</span><span class="sxs-lookup"><span data-stu-id="27ab8-103">Mitigation: Pool Blocking Period</span></span>

<span data-ttu-id="27ab8-104">El período de bloqueo del grupo de conexiones se quito de las conexiones a bases de datos SQL de Azure.</span><span class="sxs-lookup"><span data-stu-id="27ab8-104">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="27ab8-105">Descripción adicional</span><span class="sxs-lookup"><span data-stu-id="27ab8-105">Additional description</span></span>  

 <span data-ttu-id="27ab8-106">En .NET Framework 4.6.1 y versiones anteriores, cuando una aplicación encuentra un error de conexión transitorio al conectarse a una base de datos, no es posible reintentar rápidamente la conexión, porque el grupo de conexiones almacena el error en la caché y vuelve a generarlo entre 5 segundos y 1 minuto. Para obtener más información, consulte [Agrupaciones de conexiones de SQL Server (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="27ab8-106">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="27ab8-107">Este comportamiento causa problemas en las conexiones a bases de datos SQL de Azure, las que habitualmente presentan errores transitorios de los que se recuperan dentro de unos pocos segundos.</span><span class="sxs-lookup"><span data-stu-id="27ab8-107">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="27ab8-108">La característica de bloqueo del grupo de conexiones significa que la aplicación no se puede conectar a la base de datos durante un período prolongado, incluso si la base de datos está disponible.</span><span class="sxs-lookup"><span data-stu-id="27ab8-108">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="27ab8-109">Este comportamiento es problemático especialmente para las aplicaciones web que se conectan a las bases de datos SQL de Azure y que necesitan presentarse dentro de unos segundos.</span><span class="sxs-lookup"><span data-stu-id="27ab8-109">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="27ab8-110">A partir de .NET Framework 4.6.2, para las solicitudes de apertura de conexión a bases de datos SQL de Azure conocidas (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), los errores de apertura de conexión no se almacenan en la caché.</span><span class="sxs-lookup"><span data-stu-id="27ab8-110">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="27ab8-111">Para todos los otros intentos de conexión, se sigue aplicando el período de bloqueo del grupo de conexiones.</span><span class="sxs-lookup"><span data-stu-id="27ab8-111">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="27ab8-112">Impacto</span><span class="sxs-lookup"><span data-stu-id="27ab8-112">Impact</span></span>  

 <span data-ttu-id="27ab8-113">Este cambio permite que el intento de abrir una conexión a las bases de datos SQL de Azure se reintente de inmediato, lo que mejora el rendimiento de las aplicaciones habilitadas para la nube.</span><span class="sxs-lookup"><span data-stu-id="27ab8-113">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="27ab8-114">Mitigación</span><span class="sxs-lookup"><span data-stu-id="27ab8-114">Mitigation</span></span>  

 <span data-ttu-id="27ab8-115">En el caso de las aplicaciones a las que este cambio afecta negativamente, puede configurar el período de bloqueo del grupo de conexiones si establece la nueva propiedad <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27ab8-115">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="27ab8-116">El valor de la propiedad es un miembro de la enumeración <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> que puede tener cualquiera de los tres valores:</span><span class="sxs-lookup"><span data-stu-id="27ab8-116">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="27ab8-117">El comportamiento anterior se puede restaurar al establecer la propiedad <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> en <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27ab8-117">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ab8-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="27ab8-118">See also</span></span>

- [<span data-ttu-id="27ab8-119">Compatibilidad de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="27ab8-119">Application compatibility</span></span>](application-compatibility.md)
