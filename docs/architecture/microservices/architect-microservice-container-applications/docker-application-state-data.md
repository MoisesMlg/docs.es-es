---
title: Estado y datos en aplicaciones de Docker
description: Administración de estado y datos en aplicaciones de Docker. Las instancias de microservicios son prescindibles, pero LOS DATOS NO, aquí se explica cómo controlarlos con microservicios.
ms.date: 09/20/2018
ms.openlocfilehash: 9d7b0ff0e73267c6b80be2f1c956c3b4eae140e2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673132"
---
# <a name="state-and-data-in-docker-applications"></a><span data-ttu-id="26190-104">Estado y datos en aplicaciones de Docker</span><span class="sxs-lookup"><span data-stu-id="26190-104">State and data in Docker applications</span></span>

<span data-ttu-id="26190-105">En la mayoría de los casos, un contenedor se puede considerar como una instancia de un proceso.</span><span class="sxs-lookup"><span data-stu-id="26190-105">In most cases, you can think of a container as an instance of a process.</span></span> <span data-ttu-id="26190-106">Un proceso no mantiene un estado persistente.</span><span class="sxs-lookup"><span data-stu-id="26190-106">A process doesn't maintain persistent state.</span></span> <span data-ttu-id="26190-107">Si bien un contenedor puede escribir en su almacenamiento local, suponer que una instancia permanecerá indefinidamente sería como suponer que una sola ubicación en memoria será duradera.</span><span class="sxs-lookup"><span data-stu-id="26190-107">While a container can write to its local storage, assuming that an instance will be around indefinitely would be like assuming that a single location in memory will be durable.</span></span> <span data-ttu-id="26190-108">Debe suponer que las imágenes de contenedor, como los procesos, tienen varias instancias o finalmente se terminarán.</span><span class="sxs-lookup"><span data-stu-id="26190-108">You should assume that container images, like processes, have multiple instances or will eventually be killed.</span></span> <span data-ttu-id="26190-109">Si se administran con un orquestador de contenedores, debe suponer que podrían desplazarse de un nodo o máquina virtual a otro.</span><span class="sxs-lookup"><span data-stu-id="26190-109">If they're managed with a container orchestrator, you should assume that they might get moved from one node or VM to another.</span></span>

<span data-ttu-id="26190-110">Las soluciones siguientes se usan para administrar datos persistentes en aplicaciones de Docker:</span><span class="sxs-lookup"><span data-stu-id="26190-110">The following solutions are used to manage persistent data in Docker applications:</span></span>

<span data-ttu-id="26190-111">Desde el host de Docker, como [volúmenes de Docker](https://docs.docker.com/engine/admin/volumes/):</span><span class="sxs-lookup"><span data-stu-id="26190-111">From the Docker host, as [Docker Volumes](https://docs.docker.com/engine/admin/volumes/):</span></span>

- <span data-ttu-id="26190-112">Los **volúmenes** se almacenan en un área del sistema de archivos de host administrado por Docker.</span><span class="sxs-lookup"><span data-stu-id="26190-112">**Volumes** are stored in an area of the host filesystem that's managed by Docker.</span></span>

- <span data-ttu-id="26190-113">Los **montajes de enlace** pueden asignar cualquier carpeta en el sistema de archivos de host, por lo que el acceso no se puede controlar desde el proceso de Docker y puede suponer un riesgo de seguridad ya que un contenedor podría acceder a carpetas del sistema operativo confidenciales.</span><span class="sxs-lookup"><span data-stu-id="26190-113">**Bind mounts** can map to any folder in the host filesystem, so access can't be controlled from Docker process and can pose a security risk as a container could access sensitive OS folders.</span></span>

- <span data-ttu-id="26190-114">Los **montajes tmpfs** son como carpetas virtuales que solo existen en la memoria del host y nunca se escriben en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="26190-114">**tmpfs mounts** are like virtual folders that only exist in the host's memory and are never written to the filesystem.</span></span>

<span data-ttu-id="26190-115">Desde el almacenamiento remoto:</span><span class="sxs-lookup"><span data-stu-id="26190-115">From remote storage:</span></span>

- <span data-ttu-id="26190-116">[Azure Storage](https://azure.microsoft.com/documentation/services/storage/), que proporciona almacenamiento con distribución geográfica y representa una buena solución de persistencia a largo plazo para los contenedores.</span><span class="sxs-lookup"><span data-stu-id="26190-116">[Azure Storage](https://azure.microsoft.com/documentation/services/storage/), which provides geo-distributable storage, providing a good long-term persistence solution for containers.</span></span>

- <span data-ttu-id="26190-117">Bases de datos relacionales remotas como [Azure SQL Database](https://azure.microsoft.com/services/sql-database/), bases de datos NoSQL como [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) o servicios de caché como [Redis](https://redis.io/).</span><span class="sxs-lookup"><span data-stu-id="26190-117">Remote relational databases like [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) or NoSQL databases like [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), or cache services like [Redis](https://redis.io/).</span></span>

<span data-ttu-id="26190-118">Desde el contenedor de Docker:</span><span class="sxs-lookup"><span data-stu-id="26190-118">From the Docker container:</span></span>

> <span data-ttu-id="26190-119">Docker ofrece una característica denominada el *sistema de archivos de superposición*.</span><span class="sxs-lookup"><span data-stu-id="26190-119">Docker provides a feature named the *overlay file system*.</span></span> <span data-ttu-id="26190-120">Esto implementa una tarea de copia en escritura que almacena información actualizada en el sistema de archivos raíz del contenedor.</span><span class="sxs-lookup"><span data-stu-id="26190-120">This implements a copy-on-write task that stores updated information to the root file system of the container.</span></span> <span data-ttu-id="26190-121">Esa información se combina con la imagen original en la que se basa el contenedor.</span><span class="sxs-lookup"><span data-stu-id="26190-121">That information is in addition to the original image on which the container is based.</span></span> <span data-ttu-id="26190-122">Si se elimina el contenedor del sistema, estos cambios se pierden.</span><span class="sxs-lookup"><span data-stu-id="26190-122">If the container is deleted from the system, those changes are lost.</span></span> <span data-ttu-id="26190-123">Por tanto, si bien es posible guardar el estado de un contenedor dentro de su almacenamiento local, diseñar un sistema sobre esta base entraría en conflicto con la idea del diseño del contenedor, que de manera predeterminada es sin estado.</span><span class="sxs-lookup"><span data-stu-id="26190-123">Therefore, while it's possible to save the state of a container within its local storage, designing a system around this would conflict with the premise of container design, which by default is stateless.</span></span>
>
> <span data-ttu-id="26190-124">Pero los volúmenes de Docker introducidos previamente ahora son la mejor manera de controlar los datos locales de Docker.</span><span class="sxs-lookup"><span data-stu-id="26190-124">However, the previously introduced Docker Volumes is now the preferred way to handling local data Docker.</span></span> <span data-ttu-id="26190-125">Si necesita obtener más información sobre el almacenamiento en contenedores, consulte [Docker storage drivers](https://docs.docker.com/storage/storagedriver/select-storage-driver/) (Controladores de almacenamiento de Docker) y [About storage drivers](https://docs.docker.com/storage/storagedriver/) (Sobre los controladores de almacenamiento).</span><span class="sxs-lookup"><span data-stu-id="26190-125">If you need more information about storage in containers check on [Docker storage drivers](https://docs.docker.com/storage/storagedriver/select-storage-driver/) and [About storage drivers](https://docs.docker.com/storage/storagedriver/).</span></span>

<span data-ttu-id="26190-126">Los siguientes puntos proporcionan más información sobre estas opciones:</span><span class="sxs-lookup"><span data-stu-id="26190-126">The following provides more detail about these options:</span></span>

<span data-ttu-id="26190-127">Los **volúmenes** son directorios asignados desde el sistema operativo del host a directorios en contenedores.</span><span class="sxs-lookup"><span data-stu-id="26190-127">**Volumes** are directories mapped from the host OS to directories in containers.</span></span> <span data-ttu-id="26190-128">Cuando el código en el contenedor tiene acceso al directorio, ese acceso es realmente a un directorio en el sistema operativo del host.</span><span class="sxs-lookup"><span data-stu-id="26190-128">When code in the container has access to the directory, that access is actually to a directory on the host OS.</span></span> <span data-ttu-id="26190-129">Este directorio no está asociado a la duración del contenedor y Docker lo administra y aísla de la funcionalidad básica de la máquina host.</span><span class="sxs-lookup"><span data-stu-id="26190-129">This directory is not tied to the lifetime of the container itself, and the directory is managed by Docker and isolated from the core functionality of the host machine.</span></span> <span data-ttu-id="26190-130">Por tanto, los volúmenes de datos están diseñados para conservar los datos independientemente de la vida del contenedor.</span><span class="sxs-lookup"><span data-stu-id="26190-130">Thus, data volumes are designed to persist data independently of the life of the container.</span></span> <span data-ttu-id="26190-131">Si elimina un contenedor o una imagen del host de Docker, los datos que se conservan en el volumen de datos no se eliminan.</span><span class="sxs-lookup"><span data-stu-id="26190-131">If you delete a container or an image from the Docker host, the data persisted in the data volume isn't deleted.</span></span>

<span data-ttu-id="26190-132">Los volúmenes pueden tener nombre o ser anónimos (predeterminado).</span><span class="sxs-lookup"><span data-stu-id="26190-132">Volumes can be named or anonymous (the default).</span></span> <span data-ttu-id="26190-133">Los volúmenes con nombre son la evolución de los **Contenedores de volúmenes de datos** y facilitan el uso compartido de datos entre contenedores.</span><span class="sxs-lookup"><span data-stu-id="26190-133">Named volumes are the evolution of **Data Volume Containers** and make it easy to share data between containers.</span></span> <span data-ttu-id="26190-134">Los volúmenes también admiten controladores de volumen, que le permiten almacenar datos en hosts remotos, entre otras opciones.</span><span class="sxs-lookup"><span data-stu-id="26190-134">Volumes also support volume drivers, that allow you to store data on remote hosts, among other options.</span></span>

<span data-ttu-id="26190-135">Los **montajes de enlace** están disponibles desde hace mucho tiempo y permiten la asignación de cualquier carpeta a un punto de montaje en un contenedor.</span><span class="sxs-lookup"><span data-stu-id="26190-135">**Bind mounts** are available since a long time ago and allow the mapping of any folder to a mount point in a container.</span></span> <span data-ttu-id="26190-136">Los montajes de enlace tienen más limitaciones que los volúmenes y algunos problemas de seguridad importantes, por lo que los volúmenes son la opción recomendada.</span><span class="sxs-lookup"><span data-stu-id="26190-136">Bind mounts have more limitations than volumes and some important security issues, so volumes are the recommended option.</span></span>

<span data-ttu-id="26190-137">Los **montajes tmpfs** son básicamente carpetas virtuales que solo existen en la memoria del host y nunca se escriben en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="26190-137">**tmpfs mounts** are basically virtual folders that live only in the host's memory and are never written to the filesystem.</span></span> <span data-ttu-id="26190-138">Son rápidos y seguros, pero usan memoria y solo están diseñados para datos no persistentes.</span><span class="sxs-lookup"><span data-stu-id="26190-138">They are fast and secure but use memory and are only meant for non-persistent data.</span></span>

<span data-ttu-id="26190-139">Tal como se muestra en la figura 4-5, los volúmenes de Docker normales pueden almacenarse fuera de los propios contenedores, pero dentro de los límites físicos del servidor de host o de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="26190-139">As shown in Figure 4-5, regular Docker volumes can be stored outside of the containers themselves but within the physical boundaries of the host server or VM.</span></span> <span data-ttu-id="26190-140">Pero los contenedores de Docker no pueden acceder a un volumen desde un servidor de host o máquina virtual a otro.</span><span class="sxs-lookup"><span data-stu-id="26190-140">However, Docker containers can't access a volume from one host server or VM to another.</span></span> <span data-ttu-id="26190-141">En otras palabras, con estos volúmenes, no es posible administrar los datos que se comparten entre contenedores que se ejecutan en otros hosts de Docker, aunque se podría lograr con un controlador de volumen que sea compatible con los hosts remotos.</span><span class="sxs-lookup"><span data-stu-id="26190-141">In other words, with these volumes, it isn't possible to manage data shared between containers that run on different Docker hosts, although it could be achieved with a volume driver that supports remote hosts.</span></span>

![<span data-ttu-id="26190-142">Los volúmenes se pueden compartir entre contenedores, pero solo en el mismo host, a menos que use un controlador remoto compatible con hosts remotos.</span><span class="sxs-lookup"><span data-stu-id="26190-142">Volumes can be shared between containers, but only in the same host, unless you use a remote driver that supports remote hosts.</span></span> ](./media/image5.png)

<span data-ttu-id="26190-143">**Figura 4-5**.</span><span class="sxs-lookup"><span data-stu-id="26190-143">**Figure 4-5**.</span></span> <span data-ttu-id="26190-144">Volúmenes y orígenes de datos externos para aplicaciones basadas en contenedor</span><span class="sxs-lookup"><span data-stu-id="26190-144">Volumes and external data sources for container-based applications</span></span>

<span data-ttu-id="26190-145">Además, cuando un orquestador administra los contenedores de Docker, estos podrían "moverse" entre hosts, según las optimizaciones que el clúster realice.</span><span class="sxs-lookup"><span data-stu-id="26190-145">In addition, when Docker containers are managed by an orchestrator, containers might "move" between hosts, depending on the optimizations performed by the cluster.</span></span> <span data-ttu-id="26190-146">Por tanto, no se recomienda usar volúmenes de datos para los datos empresariales.</span><span class="sxs-lookup"><span data-stu-id="26190-146">Therefore, it isn't recommended that you use data volumes for business data.</span></span> <span data-ttu-id="26190-147">Pero son un buen mecanismo para trabajar con archivos de seguimiento, archivos temporales o similares que no afectarán a la coherencia de los datos empresariales.</span><span class="sxs-lookup"><span data-stu-id="26190-147">But they're a good mechanism to work with trace files, temporal files, or similar that will not impact business data consistency.</span></span>

<span data-ttu-id="26190-148">Las herramientas de **orígenes de datos remotos y caché** como Azure SQL Database, Azure Cosmos DB o una caché remota como Redis pueden usarse en aplicaciones en contenedores del mismo modo que se usan al desarrollar sin contenedores.</span><span class="sxs-lookup"><span data-stu-id="26190-148">**Remote data sources and cache** tools like Azure SQL Database, Azure Cosmos DB, or a remote cache like Redis can be used in containerized applications the same way they are used when developing without containers.</span></span> <span data-ttu-id="26190-149">Se trata de una manera comprobada para almacenar datos de aplicaciones empresariales.</span><span class="sxs-lookup"><span data-stu-id="26190-149">This is a proven way to store business application data.</span></span>

<span data-ttu-id="26190-150">**Azure Storage.**</span><span class="sxs-lookup"><span data-stu-id="26190-150">**Azure Storage.**</span></span> <span data-ttu-id="26190-151">Normalmente, los datos empresariales deben colocarse en recursos o bases de datos externos, como Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="26190-151">Business data usually will need to be placed in external resources or databases, like Azure Storage.</span></span> <span data-ttu-id="26190-152">Azure Storage, en concreto, proporciona los siguientes servicios en la nube:</span><span class="sxs-lookup"><span data-stu-id="26190-152">Azure Storage, in concrete, provides the following services in the cloud:</span></span>

- <span data-ttu-id="26190-153">El almacenamiento de blobs almacena datos de objetos no estructurados.</span><span class="sxs-lookup"><span data-stu-id="26190-153">Blob storage stores unstructured object data.</span></span> <span data-ttu-id="26190-154">Un blob puede ser cualquier tipo de texto o datos binarios, como documentos o archivos multimedia (archivos de imagen, audio y vídeo).</span><span class="sxs-lookup"><span data-stu-id="26190-154">A blob can be any type of text or binary data, such as document or media files (images, audio, and video files).</span></span> <span data-ttu-id="26190-155">El almacenamiento de blobs también se conoce como "almacenamiento de objetos".</span><span class="sxs-lookup"><span data-stu-id="26190-155">Blob storage is also referred to as Object storage.</span></span>

- <span data-ttu-id="26190-156">El almacenamiento de archivos ofrece almacenamiento compartido para aplicaciones heredadas mediante el protocolo SMB estándar.</span><span class="sxs-lookup"><span data-stu-id="26190-156">File storage offers shared storage for legacy applications using standard SMB protocol.</span></span> <span data-ttu-id="26190-157">Las máquinas virtuales de Azure y los servicios en la nube pueden compartir datos de archivos en los componentes de la aplicación a través de recursos compartidos montados.</span><span class="sxs-lookup"><span data-stu-id="26190-157">Azure virtual machines and cloud services can share file data across application components via mounted shares.</span></span> <span data-ttu-id="26190-158">Las aplicaciones locales pueden tener acceso a datos de archivos en un recurso compartido a través de la API de REST de servicio de archivos.</span><span class="sxs-lookup"><span data-stu-id="26190-158">On-premises applications can access file data in a share via the File service REST API.</span></span>

- <span data-ttu-id="26190-159">El almacenamiento de tabla almacena conjuntos de datos estructurados.</span><span class="sxs-lookup"><span data-stu-id="26190-159">Table storage stores structured datasets.</span></span> <span data-ttu-id="26190-160">El almacenamiento de tabla es un almacén de datos del atributo de clave NoSQL, lo que permite desarrollar y acceder rápidamente a grandes cantidades de datos.</span><span class="sxs-lookup"><span data-stu-id="26190-160">Table storage is a NoSQL key-attribute data store, which allows rapid development and fast access to large quantities of data.</span></span>

<span data-ttu-id="26190-161">**Bases de datos relacionales y bases de datos NoSQL.**</span><span class="sxs-lookup"><span data-stu-id="26190-161">**Relational databases and NoSQL databases.**</span></span> <span data-ttu-id="26190-162">Existen muchas opciones de bases de datos externas, desde las bases de datos relacionales como SQL Server, PostgreSQL u Oracle, o las bases de datos NoSQL como Azure Cosmos DB, MongoDB, etc. En esta guía no se explicarán estas bases de datos puesto que eso se hace en un tema completamente diferente.</span><span class="sxs-lookup"><span data-stu-id="26190-162">There are many choices for external databases, from relational databases like SQL Server, PostgreSQL, Oracle, or NoSQL databases like Azure Cosmos DB, MongoDB, etc. These databases are not going to be explained as part of this guide since they are in a completely different subject.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="26190-163">[Anterior](containerize-monolithic-applications.md)
>[Siguiente](service-oriented-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="26190-163">[Previous](containerize-monolithic-applications.md)
[Next](service-oriented-architecture.md)</span></span>