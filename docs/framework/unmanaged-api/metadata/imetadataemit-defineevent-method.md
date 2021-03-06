---
title: IMetaDataEmit::DefineEvent (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce94765467899ac7c906b0dfcdf0ceb78c659b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448209"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent (Método)
Crea una definición para un evento con la firma de metadatos especificada y obtiene un símbolo (token) para dicha definición de evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `td`  
 [in] El token para la interfaz o clase de destino. Esto es un `mdTypeDef` o `mdTypeDefNil` símbolo (token).  
  
 `szEvent`  
 [in] El nombre del evento.  
  
 `dwEventFlags`  
 [in] Marcas de evento.  
  
 `tkEventType`  
 [in] El token para la clase de eventos. Se trata de un `mdTypeDef`, `mdTypeRef`, o un `mdTokenNil` símbolo (token).  
  
 `mdAddOn`  
 [in] El método utilizado para suscribirse al evento, o null.  
  
 `mdRemoveOn`  
 [in] El método utilizado para cancelar la suscripción al evento, o null.  
  
 `mdFire`  
 [in] El método utilizado (por una clase derivada) para generar el evento.  
  
 `rmdOtherMethods[]`  
 [in] Una matriz de símbolos (tokens) de otros métodos asociados al evento. La matriz termina con un `mdMethodDefNil` símbolo (token).  
  
 `pmdEvent`  
 [out] El token de metadatos asignado al evento.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** usada como recurso en MSCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [IMetaDataEmit (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
