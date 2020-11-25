---
title: IMetaDataImport::GetCustomAttributeByName (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: 3eb894aaf8ccdc99ea23ddf946f39f3ec71773d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711213"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="6bb31-102">IMetaDataImport::GetCustomAttributeByName (Método)</span><span class="sxs-lookup"><span data-stu-id="6bb31-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>

<span data-ttu-id="6bb31-103">Obtiene el atributo personalizado, dado su nombre y propietario.</span><span class="sxs-lookup"><span data-stu-id="6bb31-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb31-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6bb31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bb31-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6bb31-105">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="6bb31-106">de Un token de metadatos que representa el objeto que posee el atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6bb31-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="6bb31-107">de Nombre del atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6bb31-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="6bb31-108">enuncia Puntero a una matriz de datos que es el valor del atributo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6bb31-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="6bb31-109">enuncia Tamaño en bytes de los datos devueltos en \* `ppData` .</span><span class="sxs-lookup"><span data-stu-id="6bb31-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bb31-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="6bb31-110">Remarks</span></span>  

 <span data-ttu-id="6bb31-111">Es legal definir varios atributos personalizados para el mismo propietario. incluso pueden tener el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="6bb31-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="6bb31-112">Sin embargo, `GetCustomAttributeByName` devuelve solo una instancia.</span><span class="sxs-lookup"><span data-stu-id="6bb31-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="6bb31-113">( `GetCustomAttributeByName` devuelve la primera instancia que encuentra). Para buscar todas las instancias de un atributo personalizado, llame al método [IMetaDataImport:: enumcustomattributes (](imetadataimport-enumcustomattributes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6bb31-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb31-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bb31-114">Requirements</span></span>  

 <span data-ttu-id="6bb31-115">**Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb31-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb31-116">**Encabezado:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6bb31-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bb31-117">**Biblioteca:** Se incluye como un recurso en MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6bb31-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bb31-118">**.NET Framework versiones:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb31-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb31-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="6bb31-119">See also</span></span>

- [<span data-ttu-id="6bb31-120">IMetaDataImport (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="6bb31-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6bb31-121">IMetaDataImport2 (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="6bb31-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
