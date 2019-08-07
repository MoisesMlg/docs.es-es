---
title: Implementación de comunicación basada en eventos entre microservicios (eventos de integración)
description: Arquitectura de microservicios de .NET para aplicaciones .NET en contenedor | Información sobre los eventos de integración para implementar la comunicación basada en eventos entre microservicios.
ms.date: 10/02/2018
ms.openlocfilehash: 8a5cfa280063da742dc1693905fc44cf870c1fcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676102"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a><span data-ttu-id="22276-103">Implementación de comunicación basada en eventos entre microservicios (eventos de integración)</span><span class="sxs-lookup"><span data-stu-id="22276-103">Implementing event-based communication between microservices (integration events)</span></span>

<span data-ttu-id="22276-104">Como se describió anteriormente, si utiliza una comunicación basada en eventos, un microservicio publica un evento cuando sucede algo importante, como cuando actualiza una entidad de negocio.</span><span class="sxs-lookup"><span data-stu-id="22276-104">As described earlier, when you use event-based communication, a microservice publishes an event when something notable happens, such as when it updates a business entity.</span></span> <span data-ttu-id="22276-105">Otros microservicios se suscriben a esos eventos.</span><span class="sxs-lookup"><span data-stu-id="22276-105">Other microservices subscribe to those events.</span></span> <span data-ttu-id="22276-106">Cuando un microservicio recibe un evento, puede actualizar sus propias entidades de negocio, lo que puede comportar que se publiquen más eventos.</span><span class="sxs-lookup"><span data-stu-id="22276-106">When a microservice receives an event, it can update its own business entities, which might lead to more events being published.</span></span> <span data-ttu-id="22276-107">Esta es la esencia del concepto de la coherencia final.</span><span class="sxs-lookup"><span data-stu-id="22276-107">This is the essence of the eventual consistency concept.</span></span> <span data-ttu-id="22276-108">Este sistema de publicación/suscripción normalmente se realiza mediante una implementación de un bus de eventos.</span><span class="sxs-lookup"><span data-stu-id="22276-108">This publish/subscribe system is usually performed by using an implementation of an event bus.</span></span> <span data-ttu-id="22276-109">El bus de eventos puede diseñarse como una interfaz con la API necesaria para suscribirse a eventos, cancelar las suscripciones y publicar eventos.</span><span class="sxs-lookup"><span data-stu-id="22276-109">The event bus can be designed as an interface with the API needed to subscribe and unsubscribe to events and to publish events.</span></span> <span data-ttu-id="22276-110">También puede tener una o más implementaciones basadas en cualquier comunicación de mensajería o entre procesos, como una cola de mensajes o un bus de servicio que admita la comunicación asincrónica y un modelo de publicación/suscripción.</span><span class="sxs-lookup"><span data-stu-id="22276-110">It can also have one or more implementations based on any inter-process or messaging communication, such as a messaging queue or a service bus that supports asynchronous communication and a publish/subscribe model.</span></span>

<span data-ttu-id="22276-111">Puede usar eventos para implementar transacciones de negocio que abarquen varios servicios, lo cual proporciona una eventual coherencia entre dichos servicios.</span><span class="sxs-lookup"><span data-stu-id="22276-111">You can use events to implement business transactions that span multiple services, which gives you eventual consistency between those services.</span></span> <span data-ttu-id="22276-112">Una eventual transacción coherente consta de una serie de acciones distribuidas.</span><span class="sxs-lookup"><span data-stu-id="22276-112">An eventually consistent transaction consists of a series of distributed actions.</span></span> <span data-ttu-id="22276-113">En cada acción, el microservicio actualiza una entidad de negocio y publica un evento que desencadena la siguiente acción.</span><span class="sxs-lookup"><span data-stu-id="22276-113">At each action, the microservice updates a business entity and publishes an event that triggers the next action.</span></span>

![El microservicio Catalog usa comunicación orientada a eventos a través de un bus de eventos para lograr la coherencia final con el microservicio Basket y microservicios adicionales.](./media/image19.png)

<span data-ttu-id="22276-115">**Figura 6-18**.</span><span class="sxs-lookup"><span data-stu-id="22276-115">**Figure 6-18**.</span></span> <span data-ttu-id="22276-116">Comunicación orientada a eventos basada en un bus de eventos</span><span class="sxs-lookup"><span data-stu-id="22276-116">Event-driven communication based on an event bus</span></span>

<span data-ttu-id="22276-117">En esta sección se describe cómo puede implementar este tipo de comunicación con .NET mediante un bus de eventos genéricos, como se muestra en la Figura 6-18.</span><span class="sxs-lookup"><span data-stu-id="22276-117">This section describes how you can implement this type of communication with .NET by using a generic event bus interface, as shown in Figure 6-18.</span></span> <span data-ttu-id="22276-118">Hay varias implementaciones posibles, cada una de las cuales usa una tecnología o infraestructura distinta, como RabbitMQ, Azure Service Bus o cualquier otro bus de servicio de código abierto de terceros o comercial.</span><span class="sxs-lookup"><span data-stu-id="22276-118">There are multiple potential implementations, each using a different technology or infrastructure such as RabbitMQ, Azure Service Bus, or any other third-party open-source or commercial service bus.</span></span>

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a><span data-ttu-id="22276-119">Uso de buses de agentes y servicios de mensajería para sistemas de producción</span><span class="sxs-lookup"><span data-stu-id="22276-119">Using message brokers and services buses for production systems</span></span>

<span data-ttu-id="22276-120">Como se indicó en la sección de arquitectura, puede escoger entre diferentes tecnologías de mensajería para implementar el bus de eventos abstractos.</span><span class="sxs-lookup"><span data-stu-id="22276-120">As noted in the architecture section, you can choose from multiple messaging technologies for implementing your abstract event bus.</span></span> <span data-ttu-id="22276-121">Pero estas tecnologías se encuentran en distintos niveles.</span><span class="sxs-lookup"><span data-stu-id="22276-121">But these technologies are at different levels.</span></span> <span data-ttu-id="22276-122">Por ejemplo, RabbitMQ, un transporte de agentes de mensajería, está en un nivel inferior al de productos comerciales como Azure Service Bus, NServiceBus, MassTransit o Brighter.</span><span class="sxs-lookup"><span data-stu-id="22276-122">For instance, RabbitMQ, a messaging broker transport, is at a lower level than commercial products like Azure Service Bus, NServiceBus, MassTransit, or Brighter.</span></span> <span data-ttu-id="22276-123">La mayoría de estos productos puede trabajar encima de RabbitMQ o Azure Service Bus.</span><span class="sxs-lookup"><span data-stu-id="22276-123">Most of these products can work on top of either RabbitMQ or Azure Service Bus.</span></span> <span data-ttu-id="22276-124">La selección que haga del producto depende de la cantidad de características y de la escalabilidad de serie que necesite para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="22276-124">Your choice of product depends on how many features and how much out-of-the-box scalability you need for your application.</span></span>

<span data-ttu-id="22276-125">Para implementar solo una prueba de concepto de bus de eventos para su entorno de desarrollo, como en el ejemplo de eShopOnContainers, una implementación sencilla encima de RabbitMQ ejecutándose como contenedor podría ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="22276-125">For implementing just an event bus proof-of-concept for your development environment, as in the eShopOnContainers sample, a simple implementation on top of RabbitMQ running as a container might be enough.</span></span> <span data-ttu-id="22276-126">Pero para sistemas importantes y de producción que necesiten alta escalabilidad, se recomienda evaluar y usar Azure Service Bus.</span><span class="sxs-lookup"><span data-stu-id="22276-126">But for mission-critical and production systems that need high scalability, you might want to evaluate and use Azure Service Bus.</span></span>

<span data-ttu-id="22276-127">Si necesita abstracciones de alto nivel y características más potentes, como [Sagas](https://docs.particular.net/nservicebus/sagas/), para procesos de larga duración que faciliten el desarrollo distribuido, vale la pena tener en cuenta otros buses de servicio comerciales y de código abierto, como NServiceBus, MassTransit y Brighter.</span><span class="sxs-lookup"><span data-stu-id="22276-127">If you require high-level abstractions and richer features like [Sagas](https://docs.particular.net/nservicebus/sagas/) for long-running processes that make distributed development easier, other commercial and open-source service buses like NServiceBus, MassTransit, and Brighter are worth evaluating.</span></span> <span data-ttu-id="22276-128">En este caso, las abstracciones y la API que se van a utilizar suelen ser las proporcionadas directamente por los buses de servicio de alto nivel, en vez de las propias abstracciones (como las [abstracciones de bus de eventos sencillos proporcionadas en eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)).</span><span class="sxs-lookup"><span data-stu-id="22276-128">In this case, the abstractions and API to use would usually be directly the ones provided by those high-level service buses instead of your own abstractions (like the [simple event bus abstractions provided at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)).</span></span> <span data-ttu-id="22276-129">Con este propósito, puede analizar [eShopOnContainers bifurcado con NServiceBus](https://go.particular.net/eShopOnContainers) (ejemplo derivado adicional implementado por Particular Software).</span><span class="sxs-lookup"><span data-stu-id="22276-129">For that matter, you can research the [forked eShopOnContainers using NServiceBus](https://go.particular.net/eShopOnContainers) (additional derived sample implemented by Particular Software)</span></span>

<span data-ttu-id="22276-130">Obviamente, siempre puede crear sus propias características de bus de servicio sobre tecnologías de nivel inferior, como RabbitMQ y Docker, pero el trabajo necesario para "volver a inventar la rueda" puede ser demasiado costoso para una aplicación de empresa personalizada.</span><span class="sxs-lookup"><span data-stu-id="22276-130">Of course, you could always build your own service bus features on top of lower-level technologies like RabbitMQ and Docker, but the work needed to “reinvent the wheel” might be too costly for a custom enterprise application.</span></span>

<span data-ttu-id="22276-131">Para reiterar: las abstracciones de bus de eventos de ejemplo y la implementación presentada en el ejemplo de eShopOnContainers están diseñadas para usarse solo como una prueba de concepto.</span><span class="sxs-lookup"><span data-stu-id="22276-131">To reiterate: the sample event bus abstractions and implementation showcased in the eShopOnContainers sample are intended to be used only as a proof of concept.</span></span> <span data-ttu-id="22276-132">Una vez que haya decidido que quiere tener comunicación asincrónica y controlada por eventos, como se explica en la sección actual, debe elegir el producto de bus de servicio que mejor se adapte a sus necesidades de producción.</span><span class="sxs-lookup"><span data-stu-id="22276-132">Once you have decided that you want to have asynchronous and event-driven communication, as explained in the current section, you should choose the service bus product that best fits your needs for production.</span></span>

## <a name="integration-events"></a><span data-ttu-id="22276-133">Eventos de integración</span><span class="sxs-lookup"><span data-stu-id="22276-133">Integration events</span></span>

<span data-ttu-id="22276-134">Los eventos de integración se utilizan para sincronizar el estado de dominio en varios microservicios o sistemas externos.</span><span class="sxs-lookup"><span data-stu-id="22276-134">Integration events are used for bringing domain state in sync across multiple microservices or external systems.</span></span> <span data-ttu-id="22276-135">Esto se realiza mediante la publicación de eventos de integración fuera del microservicio.</span><span class="sxs-lookup"><span data-stu-id="22276-135">This is done by publishing integration events outside the microservice.</span></span> <span data-ttu-id="22276-136">Cuando se publica un evento en varios microservicios de receptor (en tantos microservicios como estén suscritos al evento de integración), el controlador de eventos correspondiente en cada microservicio de receptor controla el evento.</span><span class="sxs-lookup"><span data-stu-id="22276-136">When an event is published to multiple receiver microservices (to as many microservices as are subscribed to the integration event), the appropriate event handler in each receiver microservice handles the event.</span></span>

<span data-ttu-id="22276-137">Un evento de integración es básicamente una clase de almacenamiento de datos, como en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="22276-137">An integration event is basically a data-holding class, as in the following example:</span></span>

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

<span data-ttu-id="22276-138">Los eventos de integración pueden definirse en el nivel de aplicación de cada microservicio, por lo que se separan de otros microservicios de una forma comparable a cómo se define ViewModels en el servidor y en el cliente.</span><span class="sxs-lookup"><span data-stu-id="22276-138">The integration events can be defined at the application level of each microservice, so they are decoupled from other microservices, in a way comparable to how ViewModels are defined in the server and client.</span></span> <span data-ttu-id="22276-139">Lo que no se recomienda es compartir una biblioteca de eventos de integración común entre varios microservicios. De hacerlo, podría estar acoplando esos microservicios a una biblioteca de datos de definición de eventos únicos.</span><span class="sxs-lookup"><span data-stu-id="22276-139">What is not recommended is sharing a common integration events library across multiple microservices; doing that would be coupling those microservices with a single event definition data library.</span></span> <span data-ttu-id="22276-140">Esto no le interesa por el mismo motivo que no le interesa compartir un modelo de dominio común entre varios microservicios: los microservicios deben ser completamente autónomos.</span><span class="sxs-lookup"><span data-stu-id="22276-140">You do not want to do that for the same reasons that you do not want to share a common domain model across multiple microservices: microservices must be completely autonomous.</span></span>

<span data-ttu-id="22276-141">Solo hay unos cuantos tipos de bibliotecas que debería compartir entre microservicios.</span><span class="sxs-lookup"><span data-stu-id="22276-141">There are only a few kinds of libraries you should share across microservices.</span></span> <span data-ttu-id="22276-142">Por un lado, las bibliotecas que son bloques de aplicaciones finales, como la [API de cliente de bus de eventos](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), como en eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="22276-142">One is libraries that are final application blocks, like the [Event Bus client API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), as in eShopOnContainers.</span></span> <span data-ttu-id="22276-143">Por otro lado, las bibliotecas que constituyen herramientas que también se podrían compartir como componentes de NuGet, igual que los serializadores JSON.</span><span class="sxs-lookup"><span data-stu-id="22276-143">Another is libraries that constitute tools that could also be shared as NuGet components, like JSON serializers.</span></span>

## <a name="the-event-bus"></a><span data-ttu-id="22276-144">El bus de eventos</span><span class="sxs-lookup"><span data-stu-id="22276-144">The event bus</span></span>

<span data-ttu-id="22276-145">Un bus de eventos permite una comunicación de estilo de suscripción/publicación entre microservicios, sin requerir que los componentes se reconozcan entre sí, como se muestra en la Figura 6-19.</span><span class="sxs-lookup"><span data-stu-id="22276-145">An event bus allows publish/subscribe-style communication between microservices without requiring the components to explicitly be aware of each other, as shown in Figure 6-19.</span></span>

![El microservicio A, que tiene un patrón básico de suscripción/publicación, publica en el bus de eventos, que distribuye a los microservicios suscritos B y C sin necesidad de que el publicador conozca los suscriptores.](./media/image20.png)

<span data-ttu-id="22276-147">**Figura 6-19**.</span><span class="sxs-lookup"><span data-stu-id="22276-147">**Figure 6-19**.</span></span> <span data-ttu-id="22276-148">Aspectos básicos de publicación/suscripción con un bus de eventos</span><span class="sxs-lookup"><span data-stu-id="22276-148">Publish/subscribe basics with an event bus</span></span>

<span data-ttu-id="22276-149">El bus de eventos está relacionado con el patrón de observador y con el patrón de publicación/suscripción.</span><span class="sxs-lookup"><span data-stu-id="22276-149">The event bus is related to the Observer pattern and the publish-subscribe pattern.</span></span>

### <a name="observer-pattern"></a><span data-ttu-id="22276-150">Patrón de observador</span><span class="sxs-lookup"><span data-stu-id="22276-150">Observer pattern</span></span>

<span data-ttu-id="22276-151">En el [patrón de observador](https://en.wikipedia.org/wiki/Observer_pattern), su objeto principal (conocido como "Observable") proporciona información pertinente (eventos) a otros objetos interesados (conocidos como "Observadores").</span><span class="sxs-lookup"><span data-stu-id="22276-151">In the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern), your primary object (known as the Observable) notifies other interested objects (known as Observers) with relevant information (events).</span></span>

### <a name="publishsubscribe-pubsub-pattern"></a><span data-ttu-id="22276-152">Patrón de publicación/suscripción (Pub/Sus)</span><span class="sxs-lookup"><span data-stu-id="22276-152">Publish/Subscribe (Pub/Sub) pattern</span></span>

<span data-ttu-id="22276-153">El propósito del [patrón de publicación/suscripción ](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) es el mismo que el del modelo de observador: informar a otros servicios de la realización de determinados eventos.</span><span class="sxs-lookup"><span data-stu-id="22276-153">The purpose of the [Publish/Subscribe pattern](https://docs.microsoft.com/previous-versions/msp-n-p/ff649664(v=pandp.10)) is the same as the Observer pattern: you want to notify other services when certain events take place.</span></span> <span data-ttu-id="22276-154">Pero hay una diferencia importante entre los patrones Observador y Pub/Sus.</span><span class="sxs-lookup"><span data-stu-id="22276-154">But there is an important difference between the Observer and Pub/Sub patterns.</span></span> <span data-ttu-id="22276-155">En el patrón de observador, la difusión se realiza directamente desde el objeto observable a los observadores, por lo que "se reconocen" entre sí.</span><span class="sxs-lookup"><span data-stu-id="22276-155">In the observer pattern, the broadcast is performed directly from the observable to the observers, so they “know” each other.</span></span> <span data-ttu-id="22276-156">Pero cuando se usa un patrón Pub/Sus, hay un tercer componente, denominado "agente", "mensaje de agente" o "bus de eventos", que tanto el publicador como el suscriptor conocen.</span><span class="sxs-lookup"><span data-stu-id="22276-156">But when using a Pub/Sub pattern, there is a third component, called broker or message broker or event bus, which is known by both the publisher and subscriber.</span></span> <span data-ttu-id="22276-157">Por lo tanto, al utilizar el patrón Pub/Sus, el publicador y los suscriptores se desvinculan precisamente gracias al bus de eventos o al mensaje de agente mencionados.</span><span class="sxs-lookup"><span data-stu-id="22276-157">Therefore, when using the Pub/Sub pattern the publisher and the subscribers are precisely decoupled thanks to the mentioned event bus or message broker.</span></span>

### <a name="the-middleman-or-event-bus"></a><span data-ttu-id="22276-158">El intermediario o bus de eventos</span><span class="sxs-lookup"><span data-stu-id="22276-158">The middleman or event bus</span></span>

<span data-ttu-id="22276-159">¿Cómo se consigue el anonimato entre el publicador y el suscriptor?</span><span class="sxs-lookup"><span data-stu-id="22276-159">How do you achieve anonymity between publisher and subscriber?</span></span> <span data-ttu-id="22276-160">Una forma sencilla de hacerlo es permitir que un intermediario se ocupe de toda la comunicación.</span><span class="sxs-lookup"><span data-stu-id="22276-160">An easy way is let a middleman take care of all the communication.</span></span> <span data-ttu-id="22276-161">Un bus de eventos es un intermediario de este tipo.</span><span class="sxs-lookup"><span data-stu-id="22276-161">An event bus is one such middleman.</span></span>

<span data-ttu-id="22276-162">Normalmente, los buses de eventos están compuestos de dos partes:</span><span class="sxs-lookup"><span data-stu-id="22276-162">An event bus is typically composed of two parts:</span></span>

- <span data-ttu-id="22276-163">La abstracción o interfaz.</span><span class="sxs-lookup"><span data-stu-id="22276-163">The abstraction or interface.</span></span>

- <span data-ttu-id="22276-164">Una o varias implementaciones.</span><span class="sxs-lookup"><span data-stu-id="22276-164">One or more implementations.</span></span>

<span data-ttu-id="22276-165">En la Figura 6-19 puede ver cómo, desde el punto de vista de la aplicación, el bus de eventos no es más que un canal de Pub/Sus.</span><span class="sxs-lookup"><span data-stu-id="22276-165">In Figure 6-19 you can see how, from an application point of view, the event bus is nothing more than a Pub/Sub channel.</span></span> <span data-ttu-id="22276-166">La forma de implementar este tipo de comunicación asincrónica puede variar.</span><span class="sxs-lookup"><span data-stu-id="22276-166">The way you implement this asynchronous communication can vary.</span></span> <span data-ttu-id="22276-167">Puede tener varias implementaciones para intercambiarlas dependiendo de los requisitos del entorno (por ejemplo, entornos de producción frente a entornos de desarrollo).</span><span class="sxs-lookup"><span data-stu-id="22276-167">It can have multiple implementations so that you can swap between them, depending on the environment requirements (for example, production versus development environments).</span></span>

<span data-ttu-id="22276-168">En la Figura 6-20 puede ver una abstracción de un bus de eventos con varias implementaciones basadas en tecnologías de mensajería de infraestructura, como RabbitMQ, Azure Service Bus u otro agente de eventos o de mensajería.</span><span class="sxs-lookup"><span data-stu-id="22276-168">In Figure 6-20 you can see an abstraction of an event bus with multiple implementations based on infrastructure messaging technologies like RabbitMQ, Azure Service Bus, or another event/message broker.</span></span>

![Es conveniente definir el bus de eventos través de una interfaz, de forma que pueda implementarse con varias tecnologías, como RabbitMQ y Azure Service Bus entre otras.](./media/image21.png)

<span data-ttu-id="22276-170">**Figura 6-20**.</span><span class="sxs-lookup"><span data-stu-id="22276-170">**Figure 6- 20.**</span></span> <span data-ttu-id="22276-171">Varias implementaciones de un bus de eventos</span><span class="sxs-lookup"><span data-stu-id="22276-171">Multiple implementations of an event bus</span></span>

<span data-ttu-id="22276-172">Pero, como se ha mencionado anteriormente, usar sus propias abstracciones (la interfaz del bus de eventos) solo es una buena opción si necesita características de bus de eventos compatibles con sus abstracciones.</span><span class="sxs-lookup"><span data-stu-id="22276-172">However, and as mentioned previously, using your own abstractions (the event bus interface) is good only if you need basic event bus features supported by your abstractions.</span></span> <span data-ttu-id="22276-173">Si necesita características más completas del bus de servicio, probablemente tendrá que usar la API y las abstracciones proporcionadas por el bus de servicio comercial que prefiera, en vez de usar sus propias abstracciones.</span><span class="sxs-lookup"><span data-stu-id="22276-173">If you need richer service bus features, you should probably use the API and abstractions provided by your preferred commercial service bus instead of your own abstractions.</span></span>

### <a name="defining-an-event-bus-interface"></a><span data-ttu-id="22276-174">Definición de una interfaz de bus de eventos</span><span class="sxs-lookup"><span data-stu-id="22276-174">Defining an event bus interface</span></span>

<span data-ttu-id="22276-175">Comencemos con código de implementación para la interfaz de bus de eventos y las posibles implementaciones para fines de exploración.</span><span class="sxs-lookup"><span data-stu-id="22276-175">Let’s start with some implementation code for the event bus interface and possible implementations for exploration purposes.</span></span> <span data-ttu-id="22276-176">La interfaz debe ser sencilla y genérica, como la interfaz siguiente.</span><span class="sxs-lookup"><span data-stu-id="22276-176">The interface should be generic and straightforward, as in the following interface.</span></span>

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

<span data-ttu-id="22276-177">El método `Publish` es sencillo.</span><span class="sxs-lookup"><span data-stu-id="22276-177">The `Publish` method is straightforward.</span></span> <span data-ttu-id="22276-178">El bus de eventos difunde el evento de integración que ha recibido a cualquier microservicio, o incluso a una aplicación externa, que se haya suscrito a ese evento.</span><span class="sxs-lookup"><span data-stu-id="22276-178">The event bus will broadcast the integration event passed to it to any microservice, or even an external application, subscribed to that event.</span></span> <span data-ttu-id="22276-179">El microservicio que está publicando el evento utiliza este método.</span><span class="sxs-lookup"><span data-stu-id="22276-179">This method is used by the microservice that is publishing the event.</span></span>

<span data-ttu-id="22276-180">Los microservicios que quieren recibir eventos utilizan los métodos `Subscribe` (puede tener varias implementaciones dependiendo de los argumentos).</span><span class="sxs-lookup"><span data-stu-id="22276-180">The `Subscribe` methods (you can have several implementations depending on the arguments) are used by the microservices that want to receive events.</span></span> <span data-ttu-id="22276-181">Este método tiene dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="22276-181">This method has two arguments.</span></span> <span data-ttu-id="22276-182">El primero es el evento de integración para suscribirse a (`IntegrationEvent`).</span><span class="sxs-lookup"><span data-stu-id="22276-182">The first is the integration event to subscribe to (`IntegrationEvent`).</span></span> <span data-ttu-id="22276-183">El segundo es el controlador del evento de integración (o el método de devolución de llamada), denominado `IIntegrationEventHandler<T>`, que se ejecuta cuando el microservicio receptor recibe ese mensaje de evento de integración.</span><span class="sxs-lookup"><span data-stu-id="22276-183">The second argument is the integration event handler (or callback method), named `IIntegrationEventHandler<T>`, to be executed when the receiver microservice gets that integration event message.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="22276-184">[Anterior](database-server-container.md)
> [Siguiente](rabbitmq-event-bus-development-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="22276-184">[Previous](database-server-container.md)
[Next](rabbitmq-event-bus-development-test-environment.md)</span></span>