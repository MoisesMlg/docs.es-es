---
title: ICorDebugManagedCallback2::Exception (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: c5be9231bcd5aaddfa0cf1b0051f8e1184faef04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687637"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="a9dc1-102">ICorDebugManagedCallback2::Exception (Método)</span><span class="sxs-lookup"><span data-stu-id="a9dc1-102">ICorDebugManagedCallback2::Exception Method</span></span>

<span data-ttu-id="a9dc1-103">Notifica al depurador que se ha iniciado una búsqueda de un controlador de excepciones.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9dc1-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="a9dc1-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9dc1-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a9dc1-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="a9dc1-106">de Un puntero a un objeto ICorDebugAppDomain que representa el dominio de aplicación que contiene el subproceso en el que se produjo la excepción.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a9dc1-107">de Un puntero a un objeto ICorDebugThread que representa el subproceso en el que se produjo la excepción.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="a9dc1-108">de Un puntero a un objeto ICorDebugFrame que representa un marco, determinado por el `dwEventType` parámetro.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="a9dc1-109">Para obtener más información, vea la tabla de la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="a9dc1-110">de Un entero que especifica un desplazamiento, tal y como lo determina el `dwEventType` parámetro.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="a9dc1-111">Para obtener más información, vea la tabla de la sección Comentarios.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="a9dc1-112">de Valor de la enumeración Cordebugexceptioncallbacktype (que especifica el tipo de esta devolución de llamada de excepción.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a9dc1-113">de Un valor de la enumeración [cordebugexceptionflags (](cordebugexceptionflags-enumeration.md) que especifica información adicional sobre la excepción.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9dc1-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="a9dc1-114">Remarks</span></span>  

 <span data-ttu-id="a9dc1-115">La `Exception` devolución de llamada se llama en varios puntos durante la fase de búsqueda del proceso de control de excepciones.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="a9dc1-116">Es decir, se puede llamar más de una vez al desenredar una excepción.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="a9dc1-117">La excepción que se está procesando se puede recuperar desde el objeto ICorDebugThread al que hace referencia el `pThread` parámetro.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="a9dc1-118">El parámetro y el desplazamiento concretos vienen determinados por el parámetro de la `dwEventType` siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a9dc1-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="a9dc1-119">Valor de `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="a9dc1-119">Value of `dwEventType`</span></span>|<span data-ttu-id="a9dc1-120">Valor de `pFrame`</span><span class="sxs-lookup"><span data-stu-id="a9dc1-120">Value of `pFrame`</span></span>|<span data-ttu-id="a9dc1-121">Valor de `nOffset`</span><span class="sxs-lookup"><span data-stu-id="a9dc1-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="a9dc1-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a9dc1-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="a9dc1-123">Marco que produjo la excepción.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-123">The frame that threw the exception.</span></span>|<span data-ttu-id="a9dc1-124">Puntero de instrucción en el marco.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="a9dc1-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="a9dc1-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="a9dc1-126">Marco de código de usuario más cercano al punto de la excepción iniciada.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="a9dc1-127">Puntero de instrucción en el marco.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="a9dc1-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="a9dc1-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="a9dc1-129">Marco que contiene el controlador Catch.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="a9dc1-130">Desplazamiento del lenguaje intermedio de Microsoft (MSIL) del principio del controlador Catch.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="a9dc1-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="a9dc1-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="a9dc1-132">NULL</span><span class="sxs-lookup"><span data-stu-id="a9dc1-132">NULL</span></span>|<span data-ttu-id="a9dc1-133">Sin definir.</span><span class="sxs-lookup"><span data-stu-id="a9dc1-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9dc1-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9dc1-134">Requirements</span></span>  

 <span data-ttu-id="a9dc1-135">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9dc1-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9dc1-136">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9dc1-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9dc1-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9dc1-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9dc1-138">**.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9dc1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9dc1-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9dc1-139">See also</span></span>

- [<span data-ttu-id="a9dc1-140">ICorDebugManagedCallback2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="a9dc1-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a9dc1-141">ICorDebugManagedCallback (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="a9dc1-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
