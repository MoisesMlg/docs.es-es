---
title: Autenticación en WCF
description: Obtenga información sobre varios mecanismos de WCF que proporcionan autenticación, como la autenticación de Windows, los certificados X. 509 y el nombre de usuario y contraseña.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: e2334a8c024238f38e1c927a278a4e25e7dabd9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247543"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="2f224-103">Autenticación en WCF</span><span class="sxs-lookup"><span data-stu-id="2f224-103">Authentication in WCF</span></span>

<span data-ttu-id="2f224-104">En los temas siguientes se muestran una serie de mecanismos diferentes en Windows Communication Foundation (WCF) que proporcionan autenticación, por ejemplo, la autenticación de Windows, los certificados X. 509 y el nombre de usuario y contraseñas.</span><span class="sxs-lookup"><span data-stu-id="2f224-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f224-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="2f224-105">In This Section</span></span>  

 [<span data-ttu-id="2f224-106">Procedimiento para usar el proveedor de pertenencia de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2f224-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="2f224-107">Las características de ASP.NET incluyen una pertenencia y proveedor de funciones, una base de datos para almacenar pares de nombre de usuario/contraseña para la autenticación y funciones de usuario para la autorización.</span><span class="sxs-lookup"><span data-stu-id="2f224-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="2f224-108">En este tema se explica cómo los servicios WCF pueden usar la misma base de datos para autenticar y autorizar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="2f224-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="2f224-109">Procedimiento para usar un nombre de usuario personalizado y un validador de contraseñas</span><span class="sxs-lookup"><span data-stu-id="2f224-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="2f224-110">Muestra cómo integrar un validador de nombre de usuario/contraseña personalizado.</span><span class="sxs-lookup"><span data-stu-id="2f224-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="2f224-111">Identidad del servicio y autenticación</span><span class="sxs-lookup"><span data-stu-id="2f224-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="2f224-112">Como medida de seguridad adicional, un cliente puede autenticar el servicio especificando la *identidad* esperada del servicio.</span><span class="sxs-lookup"><span data-stu-id="2f224-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="2f224-113">Si la identidad esperada y la identidad devuelta por el servicio no coinciden, se produce un error de autenticación.</span><span class="sxs-lookup"><span data-stu-id="2f224-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="2f224-114">Negociación de seguridad y tiempos de espera</span><span class="sxs-lookup"><span data-stu-id="2f224-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="2f224-115">Describe cómo se utiliza la propiedad <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> en la clase <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.</span><span class="sxs-lookup"><span data-stu-id="2f224-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="2f224-116">Depuración de errores de autenticación de Windows</span><span class="sxs-lookup"><span data-stu-id="2f224-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="2f224-117">Se centra en los problemas comunes que se producen cuando se usa la autenticación de Windows.</span><span class="sxs-lookup"><span data-stu-id="2f224-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2f224-118">Referencia</span><span class="sxs-lookup"><span data-stu-id="2f224-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="2f224-119">Secciones relacionadas</span><span class="sxs-lookup"><span data-stu-id="2f224-119">Related Sections</span></span>  

 [<span data-ttu-id="2f224-120">Escenarios de seguridad comunes</span><span class="sxs-lookup"><span data-stu-id="2f224-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="2f224-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="2f224-121">See also</span></span>

- [<span data-ttu-id="2f224-122">Información general sobre seguridad</span><span class="sxs-lookup"><span data-stu-id="2f224-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="2f224-123">[Modelo de seguridad para Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2f224-123">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
