---
title: ICorDebugDataTarget::GetThreadContext (Método)
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab2fbf6bb08a33158ea450f0f19eca50e280d8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412885"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext (Método)
Devuelve el contexto del subproceso actual para el subproceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwThreadID`  
 [in] El identificador del subproceso cuyo contexto está va a recuperar. El identificador está definido por el sistema operativo.  
  
 `contextFlags`  
 [in] Una combinación bit a bit de marcas dependientes de la plataforma que indican qué partes del contexto se deben leer.  
  
 `contextSize`  
 [in] Tamaño de `pContext`.  
  
 `pContext`  
 [out] El búfer donde se almacenará el contexto del subproceso.  
  
## <a name="remarks"></a>Comentarios  
 En plataformas de Windows, `pContext` debe ser un `CONTEXT` estructura (que se definen en WinNT.h) que sea adecuada para el tipo de equipo especificado por el [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método. `contextFlags` debe tener los mismos valores que la `ContextFlags` campo de la `CONTEXT` estructura. El `CONTEXT` estructura es específica del procesador; consulte el archivo WinNT.h para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [ICorDebugDataTarget (interfaz)](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Interfaces de depuración](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuración](../../../../docs/framework/unmanaged-api/debugging/index.md)
