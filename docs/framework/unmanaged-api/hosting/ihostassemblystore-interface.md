---
title: IHostAssemblyStore (Interfaz)
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: 4b2fed963d2d0ebec54e5f7a4d95cba26c1bac1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680959"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore (Interfaz)

Proporciona métodos que permiten a un host cargar ensamblados y módulos independientemente del Common Language Runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descripción|  
|------------|-----------------|  
|[Método ProvideAssembly](ihostassemblystore-provideassembly-method.md)|Obtiene una referencia a un ensamblado al que no hace referencia el [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) devuelto de una llamada a [IHostAssemblyManager:: GetNonHostStoreAssemblies (](ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[Método ProvideModule](ihostassemblystore-providemodule-method.md)|Resuelve un módulo dentro de un ensamblado o un archivo de recursos vinculado (no incrustado).|  
  
## <a name="remarks"></a>Comentarios  

 `IHostAssemblyStore` proporciona una forma para que un host cargue los ensamblados de forma eficaz en función de la identidad del ensamblado. El host carga los ensamblados devolviendo `IStream` instancias que apuntan directamente a los bytes.  
  
 CLR determina si un host se ha implementado `IHostAssemblyStore` mediante una llamada a en la `IHostAssemblyManager::GetNonHostAssemblyStores` inicialización. Esto permite al host controlar el enlace a ensamblados de usuario, pero basarse en el tiempo de ejecución para enlazar a ensamblados de .NET Framework.  
  
> [!NOTE]
> Al proporcionar una implementación de `IHostAssemblyStore` , el host especifica su intención de resolver todos los ensamblados a los que no hace referencia el `ICLRAssemblyReferenceList` devuelto de `IHostAssemblyManager::GetNonHostStoreAssemblies` .  
  
> [!NOTE]
> La versión 2,0 de .NET Framework no proporciona una manera para que el host cargue la imagen nativa de un ensamblado, tal y como lo proporciona la utilidad de [generación de imágenes nativas (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) .  
  
## <a name="requirements"></a>Requisitos  

 **Plataformas:** Vea [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE. h  
  
 **Biblioteca:** Se incluye como un recurso en MSCorEE.dll  
  
 **.NET Framework versiones:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte también

- [ICLRAssemblyReferenceList (Interfaz)](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager (Interfaz)](ihostassemblymanager-interface.md)
- [Interfaces de hospedaje](hosting-interfaces.md)
