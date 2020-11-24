---
title: ICLRValidator::Validate (Método)
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 4ce50f7706583f291d2e6a141d40ab6dd3e4b3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674390"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="0a222-102">ICLRValidator::Validate (Método)</span><span class="sxs-lookup"><span data-stu-id="0a222-102">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="0a222-103">Valida el ejecutable portable (PE) o el lenguaje intermedio de Microsoft (MSIL) en el archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="0a222-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a222-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0a222-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0a222-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0a222-105">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="0a222-106">de Puntero a una `IVEHandler` instancia de que controla los errores de validación.</span><span class="sxs-lookup"><span data-stu-id="0a222-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="0a222-107">de Identificador del actual <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="0a222-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="0a222-108">de Combinación de valores de [ValidatorFlags (](validatorflags-enumeration.md) , que indica el tipo de validación que se debe realizar.</span><span class="sxs-lookup"><span data-stu-id="0a222-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="0a222-109">de Número máximo de errores que se permiten antes de salir de la validación.</span><span class="sxs-lookup"><span data-stu-id="0a222-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="0a222-110">[in] Sin utilizar.</span><span class="sxs-lookup"><span data-stu-id="0a222-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="0a222-111">de Nombre del archivo que se va a validar.</span><span class="sxs-lookup"><span data-stu-id="0a222-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="0a222-112">de Puntero al búfer de archivos.</span><span class="sxs-lookup"><span data-stu-id="0a222-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="0a222-113">de Tamaño, en bytes, del archivo que se va a validar.</span><span class="sxs-lookup"><span data-stu-id="0a222-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a222-114">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0a222-114">Return Value</span></span>  
  
|<span data-ttu-id="0a222-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a222-115">HRESULT</span></span>|<span data-ttu-id="0a222-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="0a222-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a222-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a222-117">S_OK</span></span>|<span data-ttu-id="0a222-118">`Validate` se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="0a222-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="0a222-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a222-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a222-120">El Common Language Runtime (CLR) no se ha cargado en un proceso o el CLR se encuentra en un estado en el que no puede ejecutar código administrado ni procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="0a222-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a222-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a222-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a222-122">Se agotó el tiempo de espera de la llamada.</span><span class="sxs-lookup"><span data-stu-id="0a222-122">The call timed out.</span></span>|  
|<span data-ttu-id="0a222-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a222-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a222-124">El autor de la llamada no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="0a222-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a222-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a222-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a222-126">Se canceló un evento mientras un subproceso o fibra bloqueados estaba esperando en él.</span><span class="sxs-lookup"><span data-stu-id="0a222-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a222-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a222-127">E_FAIL</span></span>|<span data-ttu-id="0a222-128">Se produjo un error grave desconocido.</span><span class="sxs-lookup"><span data-stu-id="0a222-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a222-129">Cuando un método devuelve E_FAIL, CLR ya no se puede usar en el proceso.</span><span class="sxs-lookup"><span data-stu-id="0a222-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a222-130">Las llamadas subsiguientes a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0a222-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a222-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0a222-131">Requirements</span></span>  

 <span data-ttu-id="0a222-132">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a222-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a222-133">**Encabezado:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="0a222-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="0a222-134">**Biblioteca:** Se incluye como un recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a222-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a222-135">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a222-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a222-136">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0a222-136">See also</span></span>

- [<span data-ttu-id="0a222-137">ICLRValidator (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="0a222-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
