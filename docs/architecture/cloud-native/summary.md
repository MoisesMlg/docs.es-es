---
title: Resumen
description: Un resumen de las conclusiones principales del libro electrónico guía de arquitectura de aplicaciones .NET nativas en la nube para Azure.
ms.date: 04/29/2020
ms.openlocfilehash: 8cad8df1f69e159caf88d3ee119278dff8726385
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395316"
---
# <a name="summary"></a><span data-ttu-id="de2ce-103">Resumen</span><span class="sxs-lookup"><span data-stu-id="de2ce-103">Summary</span></span>

<span data-ttu-id="de2ce-104">En Resumen, estas son algunas conclusiones importantes de esta guía:</span><span class="sxs-lookup"><span data-stu-id="de2ce-104">In summary, here are important conclusions from this guide:</span></span>

- <span data-ttu-id="de2ce-105">**Cloud-Native es el** diseño de aplicaciones modernas que adoptan un cambio rápido, gran escala y resistencia, en entornos modernos y dinámicos como nubes públicas, privadas y híbridas.</span><span class="sxs-lookup"><span data-stu-id="de2ce-105">**Cloud-native** is about designing modern applications that embrace rapid change, large scale, and resilience, in modern, dynamic environments such as public, private, and hybrid clouds.</span></span>

- <span data-ttu-id="de2ce-106">\*\* [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF)\*\* es un consorcio de código abierto influyente de más de 300 grandes corporaciones.</span><span class="sxs-lookup"><span data-stu-id="de2ce-106">The **[Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF)** is an influential open-source consortium of over 300 major corporations.</span></span> <span data-ttu-id="de2ce-107">Es responsable de impulsar la adopción de la informática nativa en la nube a través de pilas de tecnología y en la nube.</span><span class="sxs-lookup"><span data-stu-id="de2ce-107">It's responsible for driving the adoption of cloud-native computing across technology and cloud stacks.</span></span>

- <span data-ttu-id="de2ce-108">Las **instrucciones de CNCF** recomiendan que las aplicaciones nativas de la nube adopten seis pilares importantes, como se muestra en la figura 11-1:</span><span class="sxs-lookup"><span data-stu-id="de2ce-108">**CNCF guidelines** recommend that that cloud-native applications embrace six important pillars as shown in Figure 11-1:</span></span>

  ![Pilares básicos de la nube nativos](./media/cloud-native-foundational-pillars.png)

  <span data-ttu-id="de2ce-110">**Figura 11-1**.</span><span class="sxs-lookup"><span data-stu-id="de2ce-110">**Figure 11-1**.</span></span> <span data-ttu-id="de2ce-111">Pilares básicos de la nube nativos</span><span class="sxs-lookup"><span data-stu-id="de2ce-111">Cloud-native foundational pillars</span></span>

- <span data-ttu-id="de2ce-112">Estos pilares nativos de la nube incluyen:</span><span class="sxs-lookup"><span data-stu-id="de2ce-112">These cloud-native pillars include:</span></span>
  - <span data-ttu-id="de2ce-113">La nube y su modelo de servicio subyacente</span><span class="sxs-lookup"><span data-stu-id="de2ce-113">The cloud and its underlying service model</span></span>
  - <span data-ttu-id="de2ce-114">Principios de diseño modernos</span><span class="sxs-lookup"><span data-stu-id="de2ce-114">Modern design principles</span></span>
  - <span data-ttu-id="de2ce-115">Microservicios</span><span class="sxs-lookup"><span data-stu-id="de2ce-115">Microservices</span></span>
  - <span data-ttu-id="de2ce-116">Contenedores y orquestación de contenedores</span><span class="sxs-lookup"><span data-stu-id="de2ce-116">Containerization and container orchestration</span></span>
  - <span data-ttu-id="de2ce-117">Servicios de respaldo basados en la nube, como bases de datos y agentes de mensajes</span><span class="sxs-lookup"><span data-stu-id="de2ce-117">Cloud-based backing services, such as databases and message brokers</span></span>
  - <span data-ttu-id="de2ce-118">Automatización, incluida la infraestructura como código y la implementación de código</span><span class="sxs-lookup"><span data-stu-id="de2ce-118">Automation, including Infrastructure as Code and code deployment</span></span>

- <span data-ttu-id="de2ce-119">**Kubernetes** es el entorno de hospedaje que se elige para la mayoría de las aplicaciones nativas de la nube.</span><span class="sxs-lookup"><span data-stu-id="de2ce-119">**Kubernetes** is the hosting environment of choice for most cloud-native applications.</span></span> <span data-ttu-id="de2ce-120">Los servicios simples más pequeños se hospedan a veces en plataformas sin servidor, como Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="de2ce-120">Smaller, simple services are sometimes hosted in serverless platforms, such as Azure Functions.</span></span> <span data-ttu-id="de2ce-121">Entre muchas características clave de automatización, ambos entornos proporcionan escalado automático para controlar los volúmenes de carga de trabajo fluctuantes.</span><span class="sxs-lookup"><span data-stu-id="de2ce-121">Among many key automation features, both environments provide automatic scaling to handle fluctuating workload volumes.</span></span>

- <span data-ttu-id="de2ce-122">La **comunicación del servicio** se convierte en una decisión de diseño importante al construir una aplicación nativa en la nube.</span><span class="sxs-lookup"><span data-stu-id="de2ce-122">**Service communication** becomes a significant design decision when constructing a cloud-native application.</span></span> <span data-ttu-id="de2ce-123">Normalmente, las aplicaciones exponen una puerta de enlace de API para administrar la comunicación de cliente front-end.</span><span class="sxs-lookup"><span data-stu-id="de2ce-123">Applications typically expose an API gateway to manage front-end client communication.</span></span> <span data-ttu-id="de2ce-124">A continuación, los microservicios de back-end esfuerzan a comunicarse entre sí que implementan patrones de comunicación asincrónica, siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="de2ce-124">Then backend microservices strive to communicate with each other implementing asynchronous communication patterns, when possible.</span></span>

- <span data-ttu-id="de2ce-125">**gRPC** es un marco de trabajo moderno y de alto rendimiento que evoluciona el protocolo de llamada a procedimiento remoto (RPC) de edad antiguo.</span><span class="sxs-lookup"><span data-stu-id="de2ce-125">**gRPC** is a modern, high-performance framework that evolves the age-old remote procedure call (RPC) protocol.</span></span> <span data-ttu-id="de2ce-126">Las aplicaciones nativas de la nube a menudo adoptan gRPC para simplificar la mensajería entre los servicios back-end.</span><span class="sxs-lookup"><span data-stu-id="de2ce-126">Cloud-native applications often embrace gRPC to streamline messaging between back-end services.</span></span> <span data-ttu-id="de2ce-127">gRPC usa HTTP/2 para su Protocolo de transporte.</span><span class="sxs-lookup"><span data-stu-id="de2ce-127">gRPC uses HTTP/2 for its transport protocol.</span></span> <span data-ttu-id="de2ce-128">Puede ser hasta 8X más rápido que la serialización de JSON con tamaños de mensaje 60-80% más pequeños.</span><span class="sxs-lookup"><span data-stu-id="de2ce-128">It can be up to 8x faster than JSON serialization with message sizes 60-80% smaller.</span></span> <span data-ttu-id="de2ce-129">gRPC es de código abierto y está administrado por Cloud Native Computing Foundation (CNCF).</span><span class="sxs-lookup"><span data-stu-id="de2ce-129">gRPC is open source and managed by the Cloud Native Computing Foundation (CNCF).</span></span>

- <span data-ttu-id="de2ce-130">Los **datos distribuidos** son un modelo a menudo implementado por aplicaciones nativas de la nube.</span><span class="sxs-lookup"><span data-stu-id="de2ce-130">**Distributed data** is a model often implemented by cloud-native applications.</span></span> <span data-ttu-id="de2ce-131">Las aplicaciones segregan la funcionalidad empresarial en microservicios pequeños e independientes.</span><span class="sxs-lookup"><span data-stu-id="de2ce-131">Applications segregate business functionality into small, independent microservices.</span></span> <span data-ttu-id="de2ce-132">Cada microservicio encapsula sus propias dependencias, datos y estado.</span><span class="sxs-lookup"><span data-stu-id="de2ce-132">Each microservice encapsulates its own dependencies, data, and state.</span></span> <span data-ttu-id="de2ce-133">El modelo de base de datos compartido clásico evoluciona en una de muchas bases de datos más pequeñas, cada una de las cuales se alinea con un microservicio.</span><span class="sxs-lookup"><span data-stu-id="de2ce-133">The classic shared database model evolves into one of many smaller databases, each aligning with a microservice.</span></span> <span data-ttu-id="de2ce-134">Cuando el humo se borra, surge un diseño que expone un `database-per-microservice` modelo.</span><span class="sxs-lookup"><span data-stu-id="de2ce-134">When the smoke clears, we emerge with a design that exposes a `database-per-microservice` model.</span></span>

- <span data-ttu-id="de2ce-135">**Las bases de datos no-SQL** hacen referencia a almacenes de datos no relacionales de alto rendimiento.</span><span class="sxs-lookup"><span data-stu-id="de2ce-135">**No-SQL databases** refer to high-performance, non-relational data stores.</span></span> <span data-ttu-id="de2ce-136">Excel en sus características de facilidad de uso, escalabilidad, resistencia y disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="de2ce-136">They excel in their ease-of-use, scalability, resilience, and availability characteristics.</span></span> <span data-ttu-id="de2ce-137">Los servicios de gran volumen que requieren un tiempo de respuesta de subsegundo favorecen los almacenes de los mismos.</span><span class="sxs-lookup"><span data-stu-id="de2ce-137">High volume services that require sub second response time favor NoSQL datastores.</span></span> <span data-ttu-id="de2ce-138">La proliferación de tecnologías NoSQL para sistemas nativos en la nube distribuida no puede ser inestable.</span><span class="sxs-lookup"><span data-stu-id="de2ce-138">The proliferation of NoSQL technologies for distributed cloud-native systems can't be overstated.</span></span>

- <span data-ttu-id="de2ce-139">**NewSQL** es una tecnología de base de datos emergente que combina la escalabilidad distribuida de NoSQL y las garantías acid de una base de datos relacional.</span><span class="sxs-lookup"><span data-stu-id="de2ce-139">**NewSQL** is an emerging database technology that combines the distributed scalability of NoSQL and the ACID guarantees of a relational database.</span></span> <span data-ttu-id="de2ce-140">Las bases de datos de NewSQL se dirigen a sistemas empresariales que deben procesar grandes volúmenes de datos, en entornos distribuidos, con compatibilidad total con la transacción o el ácido.</span><span class="sxs-lookup"><span data-stu-id="de2ce-140">NewSQL databases target business systems that must process high-volumes of data, across distributed environments, with full transactional/ACID compliance.</span></span> <span data-ttu-id="de2ce-141">Cloud Native Computing Foundation (CNCF) incluye varios proyectos de base de datos NewSQL.</span><span class="sxs-lookup"><span data-stu-id="de2ce-141">The Cloud Native Computing Foundation (CNCF) features several NewSQL database projects.</span></span>

- <span data-ttu-id="de2ce-142">La **resistencia** es la capacidad del sistema de reaccionar ante errores y seguir siendo funcional.</span><span class="sxs-lookup"><span data-stu-id="de2ce-142">**Resiliency** is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="de2ce-143">Los sistemas nativos en la nube adoptan una arquitectura distribuida en la que el error es inevitable.</span><span class="sxs-lookup"><span data-stu-id="de2ce-143">Cloud-native systems embrace distributed architecture where failure is inevitable.</span></span> <span data-ttu-id="de2ce-144">Las aplicaciones deben construirse para responder a los errores de forma elegante y volver rápidamente a un estado totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="de2ce-144">Applications must be constructed to respond elegantly to failure and quickly return to a fully functioning state.</span></span>

- <span data-ttu-id="de2ce-145">Las **mallas de servicio** son una capa de infraestructura configurable con capacidades integradas para controlar la comunicación del servicio y otros desafíos transversales.</span><span class="sxs-lookup"><span data-stu-id="de2ce-145">**Service meshes** are a configurable infrastructure layer with built-in capabilities to handle service communication and other cross-cutting challenges.</span></span> <span data-ttu-id="de2ce-146">Desacoplan responsabilidades transversales del código de negocio.</span><span class="sxs-lookup"><span data-stu-id="de2ce-146">They decouple cross-cutting responsibilities from your business code.</span></span> <span data-ttu-id="de2ce-147">Estas responsabilidades se trasladan a un proxy de servicio.</span><span class="sxs-lookup"><span data-stu-id="de2ce-147">These responsibilities move into a service proxy.</span></span> <span data-ttu-id="de2ce-148">Al que se hace referencia como `Sidecar pattern` , el proxy se implementa en un proceso independiente para proporcionar aislamiento del código de negocio.</span><span class="sxs-lookup"><span data-stu-id="de2ce-148">Referred to as the `Sidecar pattern`, the proxy is deployed into a separate process to provide isolation from your business code.</span></span>

- <span data-ttu-id="de2ce-149">La **observación** es una consideración de diseño clave para las aplicaciones nativas en la nube.</span><span class="sxs-lookup"><span data-stu-id="de2ce-149">**Observability** is a key design consideration for cloud-native applications.</span></span> <span data-ttu-id="de2ce-150">A medida que los servicios se distribuyen a través de un clúster de nodos, el registro, la supervisión y las alertas centralizados, se convierten en obligatorios.</span><span class="sxs-lookup"><span data-stu-id="de2ce-150">As services are distributed across a cluster of nodes, centralized logging, monitoring, and alerts, become mandatory.</span></span> <span data-ttu-id="de2ce-151">Azure Monitor es una colección de herramientas basadas en la nube diseñadas para proporcionar visibilidad sobre el estado del sistema.</span><span class="sxs-lookup"><span data-stu-id="de2ce-151">Azure Monitor is a collection of cloud-based tools designed to provide visibility into the state of your system.</span></span>

- <span data-ttu-id="de2ce-152">La **infraestructura como código** es una práctica ampliamente aceptada que automatiza el aprovisionamiento de plataforma.</span><span class="sxs-lookup"><span data-stu-id="de2ce-152">**Infrastructure as Code** is a widely accepted practice that automates platform provisioning.</span></span> <span data-ttu-id="de2ce-153">La infraestructura y las implementaciones son automatizadas, coherentes y repetibles.</span><span class="sxs-lookup"><span data-stu-id="de2ce-153">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="de2ce-154">Herramientas como Azure Resource Manager, terraform y el CLI de Azure le permiten crear un script de la infraestructura de la nube que necesita mediante declaración.</span><span class="sxs-lookup"><span data-stu-id="de2ce-154">Tools like Azure Resource Manager, Terraform, and the Azure CLI, enable you to declaratively script the cloud infrastructure you require.</span></span>

- <span data-ttu-id="de2ce-155">La **automatización de código** es un requisito para las aplicaciones nativas de la nube.</span><span class="sxs-lookup"><span data-stu-id="de2ce-155">**Code automation** is a requirement for cloud-native applications.</span></span> <span data-ttu-id="de2ce-156">Los sistemas de CI/CD modernos ayudan a completar este principio.</span><span class="sxs-lookup"><span data-stu-id="de2ce-156">Modern CI/CD systems help fulfill this principle.</span></span> <span data-ttu-id="de2ce-157">Proporcionan pasos de compilación e implementación independientes que ayudan a garantizar un código coherente y de calidad.</span><span class="sxs-lookup"><span data-stu-id="de2ce-157">They provide separate build and deployment steps that help ensure consistent and quality code.</span></span> <span data-ttu-id="de2ce-158">La fase de compilación transforma el código en un artefacto binario.</span><span class="sxs-lookup"><span data-stu-id="de2ce-158">The build stage transforms the code into a binary artifact.</span></span> <span data-ttu-id="de2ce-159">La fase de versión recoge el artefacto binario, aplica la configuración del entorno externo y lo implementa en un entorno especificado.</span><span class="sxs-lookup"><span data-stu-id="de2ce-159">The release stage picks up the binary artifact, applies external environment configuration, and deploys it to a specified environment.</span></span> <span data-ttu-id="de2ce-160">Azure DevOps y GitHub son entornos de DevOps con todas las características.</span><span class="sxs-lookup"><span data-stu-id="de2ce-160">Azure DevOps and GitHub are full-featured DevOps environments.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="de2ce-161">Anterior</span><span class="sxs-lookup"><span data-stu-id="de2ce-161">Previous</span></span>](application-bundles.md)