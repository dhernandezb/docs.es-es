---
title: CoEEShutDownCOM (Función)
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0b30cc2c499644ffc97a734e1554e4e352b34af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431895"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM (Función)
Obliga a common language runtime (CLR) para liberar todos los punteros de interfaz que tiene en los contenedores invocables en tiempo de ejecución (RCW). Esto tiene el efecto de liberar todas las cachés RCW. Esta función global está desusada en la [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. En su lugar, utilice el punto de entrada para un runtime concreto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Comentarios  
 El `CoEEShutDownCOM` función primero libera todos los RCW en todos los contextos y en todas las memorias caché y, a continuación, quita cualquier notificación de anulación existente en el programa de instalación. Se produce ninguna descarga de DLL.  
  
> [!CAUTION]
>  Esta función afecta a todos los runtimes que se cargan en el proceso.  
  
 A partir del [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], llame al punto de entrada para esta función en el tiempo de ejecución específico que desea que se vea afectada. Para obtener el punto de entrada, llame a la [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) método y especifique "CoEEShutDownCOM".  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** incluye como recurso en MsCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Funciones estáticas globales para metadatos](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
