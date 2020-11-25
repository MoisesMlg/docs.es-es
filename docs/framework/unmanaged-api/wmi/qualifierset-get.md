---
title: Función QualifierSet_Get (referencia de la API no administrada)
description: La función QualifierSet_Get obtiene un calificador con nombre.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd096287b85b4a51a8cae85dddcca95cc1a8dbae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721145"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="f301f-103">Función QualifierSet_Get</span><span class="sxs-lookup"><span data-stu-id="f301f-103">QualifierSet_Get function</span></span>

<span data-ttu-id="f301f-104">Obtiene el calificador con nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="f301f-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f301f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f301f-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="f301f-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f301f-106">Parameters</span></span>

<span data-ttu-id="f301f-107">`vFunc` de Este parámetro no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="f301f-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="f301f-108">`ptr` de Puntero a una instancia de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="f301f-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="f301f-109">`wszName` de Nombre del calificador cuyo valor se solicita.</span><span class="sxs-lookup"><span data-stu-id="f301f-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="f301f-110">`lFlags` de Sector.</span><span class="sxs-lookup"><span data-stu-id="f301f-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="f301f-111">Este parámetro debe ser 0.</span><span class="sxs-lookup"><span data-stu-id="f301f-111">This parameter must be 0.</span></span>

<span data-ttu-id="f301f-112">`pVal` enuncia Cuando se realiza correctamente, el tipo y el valor correctos para el calificador.</span><span class="sxs-lookup"><span data-stu-id="f301f-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="f301f-113">Si se produce un error en la función, el `VARIANT` señalado por `pVal` no se modifica.</span><span class="sxs-lookup"><span data-stu-id="f301f-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="f301f-114">Si este parámetro es `null` , se omite el parámetro.</span><span class="sxs-lookup"><span data-stu-id="f301f-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="f301f-115">`plFlavor` enuncia Un puntero a un LONG que recibe los bits de sabor del calificador para el calificador solicitado.</span><span class="sxs-lookup"><span data-stu-id="f301f-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="f301f-116">Si no se desea información de tipo, este parámetro puede ser `null` .</span><span class="sxs-lookup"><span data-stu-id="f301f-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f301f-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="f301f-117">Return value</span></span>

<span data-ttu-id="f301f-118">Los siguientes valores devueltos por esta función se definen en el archivo de encabezado *WbemCli. h* , o bien se pueden definir como constantes en el código:</span><span class="sxs-lookup"><span data-stu-id="f301f-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f301f-119">Constante</span><span class="sxs-lookup"><span data-stu-id="f301f-119">Constant</span></span>  |<span data-ttu-id="f301f-120">Value</span><span class="sxs-lookup"><span data-stu-id="f301f-120">Value</span></span>  |<span data-ttu-id="f301f-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="f301f-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f301f-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f301f-122">0x80041008</span></span> | <span data-ttu-id="f301f-123">Un parámetro no es válido.</span><span class="sxs-lookup"><span data-stu-id="f301f-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="f301f-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="f301f-124">0x80041002</span></span> | <span data-ttu-id="f301f-125">El calificador especificado no existe.</span><span class="sxs-lookup"><span data-stu-id="f301f-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f301f-126">0</span><span class="sxs-lookup"><span data-stu-id="f301f-126">0</span></span> | <span data-ttu-id="f301f-127">La llamada de función se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="f301f-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f301f-128">Comentarios</span><span class="sxs-lookup"><span data-stu-id="f301f-128">Remarks</span></span>

<span data-ttu-id="f301f-129">Esta función contiene una llamada al método [IWbemQualifierSet:: get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .</span><span class="sxs-lookup"><span data-stu-id="f301f-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f301f-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f301f-130">Requirements</span></span>  

 <span data-ttu-id="f301f-131">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f301f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f301f-132">**Encabezado:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="f301f-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f301f-133">**.NET Framework versiones:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f301f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f301f-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f301f-134">See also</span></span>

- [<span data-ttu-id="f301f-135">WMI y contadores de rendimiento (referencia de API no administrada)</span><span class="sxs-lookup"><span data-stu-id="f301f-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
