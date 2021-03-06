---
title: Espacio de pila insuficiente (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593290"
---
# <a name="out-of-stack-space-visual-basic"></a>Espacio de pila insuficiente (Visual Basic)
La pila es un área de trabajo de memoria que aumenta y disminuye dinámicamente con las demandas del programa en ejecución. Se ha superado su límite.  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Compruebe que los procedimientos no están anidados de un nivel demasiado profundo.  
  
2.  Asegúrese de que los procedimientos recursivos terminan correctamente.  
  
3.  Si las variables locales requieren más espacio de variable local que está disponible, intente declarar algunas variables en el nivel de módulo. También puede declarar todas las variables en el procedimiento estático poniendo el `Property`, `Sub`, o `Function` palabra clave con `Static`. O bien puede usar el `Static` instrucción para declarar variables estáticas individuales dentro de los procedimientos.  
  
4.  Volver a definir algunas de las cadenas de longitud fija como cadenas de longitud variable, como cadenas de longitud fija usan más espacio de pila que las cadenas de longitud variable. También puede definir la cadena en el nivel de módulo donde no requiere ningún espacio de pila.  
  
5.  Compruebe el número de anidada `DoEvents` llamadas a funciones, mediante el uso de la `Calls` cuadro de diálogo para ver qué procedimientos están activos en la pila.  
  
6.  Asegúrese de que no ha provocado "eventos en cascada" desencadenando un evento que llama a un procedimiento de evento ya en la pila. Un evento en cascada es similar a una llamada de procedimiento recursiva indefinida, pero es menos obvio, dado que la llamada se realiza mediante Visual Basic, en lugar de una llamada explícita en el código. Use la `Calls` cuadro de diálogo para ver qué procedimientos están activos en la pila.  
  
## <a name="see-also"></a>Vea también  
 [Ventana Memoria](/visualstudio/debugger/memory-windows)
