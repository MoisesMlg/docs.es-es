---
title: Implementación de contenedores en Azure
description: Implementación de contenedores en Azure con Azure Container Registry, Azure Kubernetes Service y Azure Dev Spaces.
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/23/2019
ms.locfileid: "73840488"
---
# <a name="deploying-containers-in-azure"></a><span data-ttu-id="fa771-103">Implementación de contenedores en Azure</span><span class="sxs-lookup"><span data-stu-id="fa771-103">Deploying containers in Azure</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fa771-104">Los contenedores ofrecen muchas ventajas, una de las cuales es la portabilidad.</span><span class="sxs-lookup"><span data-stu-id="fa771-104">Containers provide many benefits, one of which is portability.</span></span> <span data-ttu-id="fa771-105">Puede tomar fácilmente el mismo contenedor que ha desarrollado y probado localmente e implementarlo en Azure, donde puede ejecutar la aplicación en entornos de ensayo y de producción.</span><span class="sxs-lookup"><span data-stu-id="fa771-105">You can easily take the same container you've developed and tested locally and deploy it to Azure where it can run your app in staging and production environments.</span></span> <span data-ttu-id="fa771-106">Azure proporciona una serie de opciones para el hospedaje de aplicaciones basadas en contenedores y, de igual forma, admite varios métodos diferentes de implementación.</span><span class="sxs-lookup"><span data-stu-id="fa771-106">Azure provides a number of options for container-based app hosting and likewise supports several different means of deployment.</span></span> <span data-ttu-id="fa771-107">El enfoque más común y más flexible es implementar los contenedores en Azure Container Registry (ACR), donde son accesibles para todos los servicios que desee usar para hospedarlos.</span><span class="sxs-lookup"><span data-stu-id="fa771-107">The most common and most flexible approach is to deploy your containers to Azure Container Registry (ACR), where they're accessible by whatever services you wish to use to host them.</span></span> <span data-ttu-id="fa771-108">Azure Web App for Containers, Azure Kubernetes Services (AKS) y Azure Container Instance (ACI) pueden acceder a las imágenes de contenedor que se han insertado en ACR.</span><span class="sxs-lookup"><span data-stu-id="fa771-108">Azure Web App for Containers, Azure Kubernetes Services (AKS), and Azure Container Instance (ACI) all can access container images that have been pushed to ACR.</span></span>

## <a name="azure-container-registry"></a><span data-ttu-id="fa771-109">Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="fa771-109">Azure Container Registry</span></span>

<span data-ttu-id="fa771-110">Azure Container Registry (ACR) le permite compilar, almacenar y administrar imágenes para todas las implementaciones de contenedores.</span><span class="sxs-lookup"><span data-stu-id="fa771-110">Azure Container Registry (ACR) lets you build, store, and manage images for all of your container deployments.</span></span> <span data-ttu-id="fa771-111">Hay otros registros de contenedor, tanto públicos como privados, en los que puede implementar contenedores.</span><span class="sxs-lookup"><span data-stu-id="fa771-111">There are other container registries, both public and private, to which you can deploy containers.</span></span> <span data-ttu-id="fa771-112">La ventaja de ACR sobre otras opciones es que puede mantener las imágenes cerca de su entorno de producción, lo que mejora los tiempos de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="fa771-112">The benefit of ACR over other options is that you can keep your images close to your production environment, improving build and deployment times.</span></span> <span data-ttu-id="fa771-113">También puede protegerlos con los mismos procedimientos de seguridad que usa para el resto de los recursos de Azure, lo que mejora la seguridad y reduce el esfuerzo de administración de recursos.</span><span class="sxs-lookup"><span data-stu-id="fa771-113">You can also secure them using the same security procedures you use for the rest of your Azure resources, improving security and reducing asset management effort.</span></span>

<span data-ttu-id="fa771-114">Puede [crear un registro de contenedor mediante Azure portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) o [con las herramientas de CLI de Azure](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) o [PowerShell](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell).</span><span class="sxs-lookup"><span data-stu-id="fa771-114">You [create a container registry using the Azure Portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) or [using the Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) or [PowerShell tools](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell).</span></span> <span data-ttu-id="fa771-115">La creación de un nuevo registro de contenedor solo requiere una suscripción de Azure, un grupo de recursos y un nombre único.</span><span class="sxs-lookup"><span data-stu-id="fa771-115">Creating a new container registry just requires an Azure subscription, a resource group, and a unique name.</span></span> <span data-ttu-id="fa771-116">En la figura 3-11 se muestran las opciones básicas para crear un registro, que se hospedará en *nombrederegistro*. azurecr.IO.</span><span class="sxs-lookup"><span data-stu-id="fa771-116">Figure 3-11 shows the basic options for creating a registry, which will be hosted at *registryname*.azurecr.io.</span></span>

<span data-ttu-id="fa771-117">![crear el registro de contenedor](./media/create-container-registry.png)
**figura 3-11**.</span><span class="sxs-lookup"><span data-stu-id="fa771-117">![Create container registry](./media/create-container-registry.png)
**Figure 3-11**.</span></span> <span data-ttu-id="fa771-118">Crear registro de contenedor</span><span class="sxs-lookup"><span data-stu-id="fa771-118">Create container registry</span></span>

<span data-ttu-id="fa771-119">Una vez que haya creado un registro, debe autenticarse con él para poder usarlo.</span><span class="sxs-lookup"><span data-stu-id="fa771-119">Once you've created a registry, you'll need to authenticate with it before you can use it.</span></span> <span data-ttu-id="fa771-120">Normalmente, se iniciará sesión en el registro mediante el comando CLI de Azure:</span><span class="sxs-lookup"><span data-stu-id="fa771-120">Typically, you'll log into the registry using the Azure CLI command:</span></span>

```azurecli
az acr login --name *registryname*
```

<span data-ttu-id="fa771-121">Una vez que haya creado un registro en Azure Container Registry, puede usar los comandos de Docker para insertar imágenes de contenedor en él.</span><span class="sxs-lookup"><span data-stu-id="fa771-121">Once you've created a registry in Azure Container Registry, you can use docker commands to push container images to it.</span></span> <span data-ttu-id="fa771-122">Sin embargo, antes de poder hacerlo, primero debe etiquetar la imagen con el nombre completo (URL) del servidor de inicio de sesión de ACR.</span><span class="sxs-lookup"><span data-stu-id="fa771-122">Before you can do so, however, you must first tag your image with the fully qualified name (URL) of your ACR login server.</span></span> <span data-ttu-id="fa771-123">Tendrá el formato *nombrederegistro*. azurecr.IO.</span><span class="sxs-lookup"><span data-stu-id="fa771-123">This will have the format *registryname*.azurecr.io.</span></span>

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="fa771-124">Después de etiquetar la imagen, use el comando `docker push` para enviar la imagen a la instancia de ACR.</span><span class="sxs-lookup"><span data-stu-id="fa771-124">After you've tagged the image, you use the `docker push` command to push the image to your ACR instance.</span></span>

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="fa771-125">Después de insertar una imagen en el registro, se recomienda quitar la imagen del entorno de Docker local mediante este comando:</span><span class="sxs-lookup"><span data-stu-id="fa771-125">After you push an image to the registry, it's a good idea to remove the image from your local Docker environment, using this command:</span></span>

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

<span data-ttu-id="fa771-126">Los desarrolladores rara vez deben introducir directamente desde sus equipos en un registro de contenedor.</span><span class="sxs-lookup"><span data-stu-id="fa771-126">Developers should rarely push directly from their machines to a container registry.</span></span> <span data-ttu-id="fa771-127">En su lugar, una canalización de compilación definida en una herramienta como Azure DevOps debe ser responsable de este proceso.</span><span class="sxs-lookup"><span data-stu-id="fa771-127">Instead, a build pipeline defined in a tool like Azure DevOps should be responsible for this process.</span></span> <span data-ttu-id="fa771-128">Obtenga más información en el [capítulo sobre DevOps nativo](devops.md)de la nube.</span><span class="sxs-lookup"><span data-stu-id="fa771-128">Learn more in the [Cloud-Native DevOps chapter](devops.md).</span></span>

## <a name="azure-kubernetes-service"></a><span data-ttu-id="fa771-129">Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="fa771-129">Azure Kubernetes Service</span></span>

<span data-ttu-id="fa771-130">Si la aplicación basada en contenedor implica varios contenedores, lo más probable es que quiera definir y administrar las interacciones entre los contenedores mediante un *orquestador* como Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="fa771-130">If your container-based application involves multiple containers, you'll most likely want to define and manage the interactions between the containers using an *orchestrator* like Kubernetes.</span></span> <span data-ttu-id="fa771-131">Una vez que haya implementado las imágenes de contenedor en ACR, puede configurar fácilmente Azure Kubernetes Services para implementar automáticamente imágenes actualizadas de ACR.</span><span class="sxs-lookup"><span data-stu-id="fa771-131">Once you've deployed your container images to ACR, you can easily configure Azure Kubernetes Services to automatically deploy updated images from ACR.</span></span> <span data-ttu-id="fa771-132">Una vez completada la canalización de CI/CD, puede configurar una estrategia de [versión Canarias](https://martinfowler.com/bliki/CanaryRelease.html) para minimizar el riesgo que conlleva la implementación rápida de las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="fa771-132">With a full CI/CD pipeline in place, you can configure a [canary release](https://martinfowler.com/bliki/CanaryRelease.html) strategy to minimize the risk involved when rapidly deploying updates.</span></span> <span data-ttu-id="fa771-133">La nueva versión de la aplicación está configurada inicialmente en producción sin ningún tráfico enrutado a ella y, a continuación, se enruta un número pequeño de usuarios a la versión implementada recientemente de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fa771-133">The new version of the app is initially configured in production with no traffic routed to it, and then a small number of users are routed to the newly-deployed version of the app.</span></span> <span data-ttu-id="fa771-134">A medida que el equipo gana confianza en la nueva versión del software, se implementan más instancias de la nueva versión y se retiran las instancias de la versión anterior.</span><span class="sxs-lookup"><span data-stu-id="fa771-134">As the team gains confidence in the new version of the software, more instances of the new version are rolled out and the previous version's instances are retired.</span></span> <span data-ttu-id="fa771-135">AKS admite fácilmente este estilo de implementación.</span><span class="sxs-lookup"><span data-stu-id="fa771-135">AKS easily supports this style of deployment.</span></span>

<span data-ttu-id="fa771-136">Como sucede con la mayoría de los recursos de Azure, puede crear clústeres de Azure Kubernetes mediante el portal o mediante herramientas de línea de comandos o herramientas de automatización de infraestructura como Helm o terraform.</span><span class="sxs-lookup"><span data-stu-id="fa771-136">As with most resources in Azure, you can create Azure Kubernetes clusters using the portal or using command line tools or infrastructure automation tools like Helm or Terraform.</span></span> <span data-ttu-id="fa771-137">Para empezar a trabajar con un nuevo clúster, debe proporcionar la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="fa771-137">To get started with a new cluster, you need to provide the following information:</span></span>

- <span data-ttu-id="fa771-138">Suscripción a Azure</span><span class="sxs-lookup"><span data-stu-id="fa771-138">Azure subscription</span></span>
- <span data-ttu-id="fa771-139">Grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="fa771-139">Resource group</span></span>
- <span data-ttu-id="fa771-140">Nombre del clúster de Kubernetes</span><span class="sxs-lookup"><span data-stu-id="fa771-140">Kubernetes cluster name</span></span>
- <span data-ttu-id="fa771-141">Región</span><span class="sxs-lookup"><span data-stu-id="fa771-141">Region</span></span>
- <span data-ttu-id="fa771-142">Versión de Kubernetes</span><span class="sxs-lookup"><span data-stu-id="fa771-142">Kubernetes version</span></span>
- <span data-ttu-id="fa771-143">Prefijo de nombre DNS</span><span class="sxs-lookup"><span data-stu-id="fa771-143">DNS name prefix</span></span>
- <span data-ttu-id="fa771-144">Tamaño del nodo</span><span class="sxs-lookup"><span data-stu-id="fa771-144">Node size</span></span>
- <span data-ttu-id="fa771-145">Recuento de nodos</span><span class="sxs-lookup"><span data-stu-id="fa771-145">Node count</span></span>

<span data-ttu-id="fa771-146">Esta información es suficiente para comenzar.</span><span class="sxs-lookup"><span data-stu-id="fa771-146">This information is sufficient to get started.</span></span> <span data-ttu-id="fa771-147">Como parte del proceso de creación en el portal de Azure, también puede configurar opciones para las siguientes características del clúster:</span><span class="sxs-lookup"><span data-stu-id="fa771-147">As part of the creation process in the Azure Portal, you can also configure options for the following features of your cluster:</span></span>

- <span data-ttu-id="fa771-148">Escala</span><span class="sxs-lookup"><span data-stu-id="fa771-148">Scale</span></span>
- <span data-ttu-id="fa771-149">Autenticación</span><span class="sxs-lookup"><span data-stu-id="fa771-149">Authentication</span></span>
- <span data-ttu-id="fa771-150">Redes</span><span class="sxs-lookup"><span data-stu-id="fa771-150">Networking</span></span>
- <span data-ttu-id="fa771-151">Supervisión</span><span class="sxs-lookup"><span data-stu-id="fa771-151">Monitoring</span></span>
- <span data-ttu-id="fa771-152">Etiquetas</span><span class="sxs-lookup"><span data-stu-id="fa771-152">Tags</span></span>

<span data-ttu-id="fa771-153">[En esta guía de inicio rápido se explica cómo implementar un clúster de AKS mediante el Azure portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).</span><span class="sxs-lookup"><span data-stu-id="fa771-153">This [quickstart walks through deploying an AKS cluster using the Azure portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).</span></span>

## <a name="azure-dev-spaces"></a><span data-ttu-id="fa771-154">Azure Dev Spaces</span><span class="sxs-lookup"><span data-stu-id="fa771-154">Azure Dev Spaces</span></span>

<span data-ttu-id="fa771-155">Los clústeres de Kubernetes complejos pueden requerir recursos importantes para hospedar, lo que puede dificultar a los desarrolladores la ejecución de toda la aplicación en un solo equipo (especialmente un portátil).</span><span class="sxs-lookup"><span data-stu-id="fa771-155">Complex Kubernetes clusters can require significant resources to host, which can make it difficult for developers to run the entire application on a single machine (especially a laptop).</span></span> <span data-ttu-id="fa771-156">Azure Dev Spaces ofrece una solución para esto, ya que permite a los desarrolladores trabajar con sus propias versiones de clústeres de Kubernetes de Azure hospedados en Azure.</span><span class="sxs-lookup"><span data-stu-id="fa771-156">Azure Dev Spaces offers a solution to this by allowing developers to work with their own versions of Azure Kubernetes clusters hosted in Azure.</span></span> <span data-ttu-id="fa771-157">Azure Dev Spaces está diseñado para facilitar el desarrollo de aplicaciones basadas en microservicios con AKS.</span><span class="sxs-lookup"><span data-stu-id="fa771-157">Azure Dev Spaces is designed to ease development of microservice-based applications using AKS.</span></span>

<span data-ttu-id="fa771-158">Para comprender el valor de Azure Dev Spaces, déjenos compartir este presupuesto de Gabe Monroy, PM Lead of containers en Microsoft Azure:</span><span class="sxs-lookup"><span data-stu-id="fa771-158">To understand the value of Azure Dev Spaces, let me share this quotation from Gabe Monroy, PM Lead of Containers at Microsoft Azure:</span></span>

<span data-ttu-id="fa771-159">"Imagine que es un nuevo empleado que intenta corregir un error en una aplicación de microservicios compleja formada por docenas de componentes, cada uno con su propia configuración y servicios de respaldo.</span><span class="sxs-lookup"><span data-stu-id="fa771-159">"Imagine you are a new employee trying to fix a bug in a complex microservices application consisting of dozens of components, each with their own configuration and backing services.</span></span> <span data-ttu-id="fa771-160">Para empezar, debe configurar el entorno de desarrollo local para que pueda imitar la producción, como la configuración del IDE, la creación de una cadena de herramientas, dependencias de servicio en contenedor, un entorno de Kubernetes local, simulacros para servicios de respaldo, etc.</span><span class="sxs-lookup"><span data-stu-id="fa771-160">To get started, you must configure your local development environment so that it can mimic production including setting up your IDE, building tool chain, containerized service dependencies, a local Kubernetes environment, mocks for backing services, and more.</span></span> <span data-ttu-id="fa771-161">Con todo el tiempo necesario para configurar el entorno de desarrollo, la corrección del primer error puede tardar días.</span><span class="sxs-lookup"><span data-stu-id="fa771-161">With all the time involved setting up your development environment, fixing that first bug could take days.</span></span>

> <span data-ttu-id="fa771-162">O bien, puede usar los espacios de desarrollo y AKS ".</span><span class="sxs-lookup"><span data-stu-id="fa771-162">Or you could use Dev Spaces and AKS."</span></span>

<span data-ttu-id="fa771-163">El proceso para trabajar con Azure Dev Spaces implica los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="fa771-163">The process for working with Azure Dev Spaces involves the following steps:</span></span>

1. <span data-ttu-id="fa771-164">Cree el espacio de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="fa771-164">Create the dev space.</span></span>
2. <span data-ttu-id="fa771-165">Configure el espacio de desarrollo raíz.</span><span class="sxs-lookup"><span data-stu-id="fa771-165">Configure the root dev space.</span></span>
3. <span data-ttu-id="fa771-166">Configure un espacio de desarrollo secundario (para su propia versión del sistema).</span><span class="sxs-lookup"><span data-stu-id="fa771-166">Configure a child dev space (for your own version of the system).</span></span>
4. <span data-ttu-id="fa771-167">Conéctese al espacio de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="fa771-167">Connect to the dev space.</span></span>

<span data-ttu-id="fa771-168">Todos estos pasos se pueden realizar mediante las herramientas de línea de comandos CLI de Azure y New `azds`.</span><span class="sxs-lookup"><span data-stu-id="fa771-168">All of these steps can be performed using the Azure CLI and new  `azds` command line tools.</span></span> <span data-ttu-id="fa771-169">Por ejemplo, para crear un nuevo espacio de desarrollo de Azure para un clúster de Kubernetes determinado, usaría un comando como este:</span><span class="sxs-lookup"><span data-stu-id="fa771-169">For example, to create a new Azure Dev Space for a given Kubernetes cluster, you would use a command like this one:</span></span>

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

<span data-ttu-id="fa771-170">A continuación, puede usar el comando `azds prep` para generar los recursos necesarios de Docker y Helm Chart para ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fa771-170">Next, you can use the `azds prep` command to generate the necessary Docker and Helm chart assets for running the application.</span></span> <span data-ttu-id="fa771-171">A continuación, ejecute el código en AKS con `azds up`.</span><span class="sxs-lookup"><span data-stu-id="fa771-171">Then you run your code in AKS using `azds up`.</span></span> <span data-ttu-id="fa771-172">La primera vez que ejecute este comando, se instalará el gráfico Helm y los contenedores se compilarán e implementarán de acuerdo con las instrucciones.</span><span class="sxs-lookup"><span data-stu-id="fa771-172">The first time you run this command, the Helm chart will be installed, and the container(s) will be built and deployed according to your instructions.</span></span> <span data-ttu-id="fa771-173">Esto puede tardar unos minutos la primera vez que se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="fa771-173">This may take a few minutes the first time it's run.</span></span> <span data-ttu-id="fa771-174">Sin embargo, después de realizar cambios, puede conectarse a su propio espacio de desarrollo secundario mediante `azds space select` y, a continuación, implementar y depurar las actualizaciones en el espacio de desarrollo secundario aislado.</span><span class="sxs-lookup"><span data-stu-id="fa771-174">However, after you make changes, you can connect to your own child dev space using `azds space select` and then deploy and debug your updates in your isolated child dev space.</span></span> <span data-ttu-id="fa771-175">Una vez que tenga el espacio de desarrollo en funcionamiento, puede enviarle actualizaciones volviendo a emitir el comando `azds up` o puede usar herramientas integradas en Visual Studio o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="fa771-175">Once you have your dev space up and running, you can send updates to it by re-issuing the `azds up` command or you can use built-in tooling in Visual Studio or Visual Studio Code.</span></span> <span data-ttu-id="fa771-176">Con VS Code, use la paleta de comandos para conectarse a su espacio de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="fa771-176">With VS Code, you use the command palette to connect to your dev space.</span></span> <span data-ttu-id="fa771-177">En la figura 3-12 se muestra cómo iniciar la aplicación web con Azure Dev Spaces en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fa771-177">Figure 3-12 shows how to launch your web application using Azure Dev Spaces in Visual Studio.</span></span>

<span data-ttu-id="fa771-178">![conectarse a Azure Dev Spaces en Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**figura 3-12**.</span><span class="sxs-lookup"><span data-stu-id="fa771-178">![Connect to Azure Dev Spaces in Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**Figure 3-12**.</span></span> <span data-ttu-id="fa771-179">Conexión a Azure Dev Spaces en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa771-179">Connect to Azure Dev Spaces in Visual Studio</span></span>

## <a name="references"></a><span data-ttu-id="fa771-180">Referencias</span><span class="sxs-lookup"><span data-stu-id="fa771-180">References</span></span>

- [<span data-ttu-id="fa771-181">Versión Canarias</span><span class="sxs-lookup"><span data-stu-id="fa771-181">Canary Release</span></span>](https://martinfowler.com/bliki/CanaryRelease.html)
- [<span data-ttu-id="fa771-182">Azure Dev Spaces con VS Code</span><span class="sxs-lookup"><span data-stu-id="fa771-182">Azure Dev Spaces with VS Code</span></span>](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [<span data-ttu-id="fa771-183">Azure Dev Spaces con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa771-183">Azure Dev Spaces with Visual Studio</span></span>](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
><span data-ttu-id="fa771-184">[Anterior](combine-containers-serverless-approaches.md)
>[Siguiente](scale-containers-serverless.md)</span><span class="sxs-lookup"><span data-stu-id="fa771-184">[Previous](combine-containers-serverless-approaches.md)
[Next](scale-containers-serverless.md)</span></span>