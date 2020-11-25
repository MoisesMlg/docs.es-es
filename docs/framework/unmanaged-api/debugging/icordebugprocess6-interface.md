---
title: Interfaz ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: ba70bab28eeddad6e3cf3c2b82b196a69ce68647
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732611"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="5d919-102">Interfaz ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="5d919-102">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="5d919-103">Extiende la interfaz ICorDebugProcess de manera lógica para habilitar características como la descodificación de eventos de depuración administrados que están codificados en eventos de depuración de excepción nativos o la división de módulos virtuales.</span><span class="sxs-lookup"><span data-stu-id="5d919-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d919-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5d919-104">Methods</span></span>  
  
|<span data-ttu-id="5d919-105">Método</span><span class="sxs-lookup"><span data-stu-id="5d919-105">Method</span></span>|<span data-ttu-id="5d919-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d919-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d919-107">Método DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="5d919-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="5d919-108">Descodifica los eventos de depuración administrados encapsulados en la carga de los eventos de depuración de excepción nativos especialmente diseñados.</span><span class="sxs-lookup"><span data-stu-id="5d919-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="5d919-109">Método EnableVirtualModuleSplitting</span><span class="sxs-lookup"><span data-stu-id="5d919-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="5d919-110">Habilita o deshabilita la división de módulos virtuales.</span><span class="sxs-lookup"><span data-stu-id="5d919-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="5d919-111">Método GetCode</span><span class="sxs-lookup"><span data-stu-id="5d919-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="5d919-112">Obtiene información sobre el código administrado en una dirección de código determinado.</span><span class="sxs-lookup"><span data-stu-id="5d919-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="5d919-113">Método GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="5d919-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="5d919-114">Proporciona información sobre las funciones exportadas en tiempo de ejecución para ayudar a recorrer el código administrado.</span><span class="sxs-lookup"><span data-stu-id="5d919-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="5d919-115">Método MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="5d919-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="5d919-116">Cambia el estado interno del código que se está depurando para que el método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la biblioteca de clases .NET Framework devuelva `true`.</span><span class="sxs-lookup"><span data-stu-id="5d919-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="5d919-117">Método ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="5d919-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="5d919-118">Notifica a [ICorDebug](icordebug-interface.md) que el proceso se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="5d919-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d919-119">Comentarios</span><span class="sxs-lookup"><span data-stu-id="5d919-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d919-120">La interfaz solo está disponible con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5d919-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="5d919-121">Al intentar llamar a `QueryInterface` para recuperar un puntero a interfaz, devuelve `E_NOINTERFACE` para escenarios de ICorDebug fuera de .NET nativo.</span><span class="sxs-lookup"><span data-stu-id="5d919-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d919-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d919-122">Requirements</span></span>  

 <span data-ttu-id="5d919-123">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d919-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d919-124">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d919-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d919-125">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d919-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d919-126">**.NET Framework versiones:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d919-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d919-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5d919-127">See also</span></span>

- [<span data-ttu-id="5d919-128">Interfaces para depuración</span><span class="sxs-lookup"><span data-stu-id="5d919-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5d919-129">Depuración</span><span class="sxs-lookup"><span data-stu-id="5d919-129">Debugging</span></span>](index.md)
