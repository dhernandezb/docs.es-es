---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 601e3fafd9aa876186b7f78dfdcb87a2336ddfcd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185776"
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase SecurityBindingElement no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase SecurityBindingElement posee las siguientes propiedades:  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Especifica los algoritmos que se van a utilizar con la clase.  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 Tipo de datos: booleano  
  
 Tipo de acceso: solo lectura  
  
 Valor booleano que especifica si cada mensaje contiene una marca de tiempo.  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Origen de la entropía utilizada para crear claves.  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 Tipo de datos: LocalServiceSecuritySettings  
  
 Tipo de acceso: solo lectura  
  
 Las propiedades de seguridad específicas del enlace del servicio local.  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Versión utilizada para la seguridad del mensaje.  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 Tipo de datos: cadena  
  
 Tipo de acceso: solo lectura  
  
 Orden de los elementos en el encabezado de seguridad de este enlace.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
