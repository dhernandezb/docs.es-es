---
title: CorSymSearchPolicyAttributes (Enumeración)
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4c3aedea4cc8ce2d8fb8c0c0bf3fead727dcf64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425865"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>CorSymSearchPolicyAttributes (Enumeración)
Especifica la directiva que se utilizará al realizar una búsqueda de un lector de símbolos. Estas constantes se utilizan por la [ISymUnmanagedBinder2:: Getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) y [ISymUnmanagedBinder3:: GetReaderFromCallback](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md) métodos.  
  
> [!IMPORTANT]
>  Es un riesgo de seguridad para abrir un archivo de programa (PDB) de la base de datos desde un origen de confianza.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,       
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //      
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|`AllowRegistryAccess`|Consulta el registro de las rutas de acceso de búsqueda de símbolos.|  
|`AllowSymbolServerAccess`|Tiene acceso a un servidor de símbolos.|  
|`AllowOriginalPathAccess`|Busca la ruta de acceso especificada en el directorio de depuración.|  
|`AllowReferencePathAccess`|Busca el archivo PDB en el lugar donde está el archivo .exe.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones de almacén de símbolos de diagnósticos](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
