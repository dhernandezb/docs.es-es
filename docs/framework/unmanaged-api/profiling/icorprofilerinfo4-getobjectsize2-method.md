---
title: ICorProfilerInfo4::GetObjectSize2 (Método)
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ebbc3422f48c0c2b8ff7b807228c63fbb35dd7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454110"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 (Método)
Devuelve el tamaño de un objeto especificado. Reemplaza el [ICorProfilerInfo:: GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) método mediante la notificación de tamaños de los objetos que son más grandes que lo que se puede expresar en una `ULONG`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `objectId`  
 [in] El identificador del objeto.  
  
 `pcSize`  
 [out] Puntero al tamaño del objeto, en bytes.  
  
## <a name="remarks"></a>Comentarios  
 A menudo, distintos objetos de los mismos tipos tienen el mismo tamaño. Sin embargo, algunos tipos, como matrices o cadenas, pueden tener un tamaño diferente para cada objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorProfilerInfo4 (interfaz)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
