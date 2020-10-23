---
title: Cambios importantes en las redes
description: Enumera los cambios importantes en las redes en .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: fdbd3f3bdcae5048b4f01e4d827f8a0e876c5c15
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050534"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="d46b9-103">Cambios importantes en las redes</span><span class="sxs-lookup"><span data-stu-id="d46b9-103">Networking breaking changes</span></span>

<span data-ttu-id="d46b9-104">En esta página se documentan los siguientes cambios importantes:</span><span class="sxs-lookup"><span data-stu-id="d46b9-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d46b9-105">Cambio importante</span><span class="sxs-lookup"><span data-stu-id="d46b9-105">Breaking change</span></span> | <span data-ttu-id="d46b9-106">Versión introducida</span><span class="sxs-lookup"><span data-stu-id="d46b9-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="d46b9-107">NegotiateStream y SslStream permiten operaciones Begin sucesivas</span><span class="sxs-lookup"><span data-stu-id="d46b9-107">NegotiateStream and SslStream allow successive Begin operations</span></span>](#negotiatestream-and-sslstream-allow-successive-begin-operations) | <span data-ttu-id="d46b9-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-108">5.0</span></span> |
| [<span data-ttu-id="d46b9-109">Socket.LocalEndPoint se actualiza después de llamar a SendToAsync</span><span class="sxs-lookup"><span data-stu-id="d46b9-109">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | <span data-ttu-id="d46b9-110">5.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-110">5.0</span></span> |
| [<span data-ttu-id="d46b9-111">WinHttpHandler quitado del entorno de ejecución de .NET</span><span class="sxs-lookup"><span data-stu-id="d46b9-111">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="d46b9-112">5.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-112">5.0</span></span> |
| [<span data-ttu-id="d46b9-113">MulticastOption.Group no acepta un valor NULL</span><span class="sxs-lookup"><span data-stu-id="d46b9-113">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="d46b9-114">5.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-114">5.0</span></span> |
| [<span data-ttu-id="d46b9-115">La administración de rutas de acceso de cookies ahora se ajusta a RFC 6265</span><span class="sxs-lookup"><span data-stu-id="d46b9-115">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265) | <span data-ttu-id="d46b9-116">5.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-116">5.0</span></span> |
| [<span data-ttu-id="d46b9-117">El valor predeterminado de HttpRequestMessage.Version ha cambiado a 1.1</span><span class="sxs-lookup"><span data-stu-id="d46b9-117">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="d46b9-118">3.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-118">3.0</span></span> |
| [<span data-ttu-id="d46b9-119">WebClient.CancelAsync no siempre se cancela inmediatamente</span><span class="sxs-lookup"><span data-stu-id="d46b9-119">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="d46b9-120">2.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-120">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d46b9-121">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-121">.NET 5.0</span></span>

[!INCLUDE [negotiatestream-sslstream-dont-fail-on-successive-begin-calls](../../../includes/core-changes/networking/5.0/negotiatestream-sslstream-dont-fail-on-successive-begin-calls.md)]

***

[!INCLUDE [localendpoint-updated-on-sendtoasync](../../../includes/core-changes/networking/5.0/localendpoint-updated-on-sendtoasync.md)]

***

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="d46b9-122">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-122">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="d46b9-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="d46b9-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
