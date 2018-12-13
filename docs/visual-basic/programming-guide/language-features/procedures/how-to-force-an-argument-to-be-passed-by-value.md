---
title: 'Cómo: Forzar un argumento para que pase como un valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: adc58c34150030eb0fc82050576bfecc453e21ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651082"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>Cómo: Forzar un argumento para que pase como un valor (Visual Basic)
La declaración de procedimiento determina el mecanismo de paso. Si se declara un parámetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic espera pasar el argumento correspondiente por referencia. Esto permite que el procedimiento cambie el valor del elemento de programación subyacente del argumento en el código de llamada. Si desea proteger el elemento subyacente frente a estos cambios, puede invalidar el `ByRef` llamando al mecanismo de paso en el procedimiento, incluya el nombre del argumento entre paréntesis. Estos paréntesis son además los paréntesis que encierran la lista de argumentos en la llamada.  
  
 El código de llamada no puede reemplazar un mecanismo [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>Para forzar un argumento para pasar por valor  
  
-   Si el parámetro correspondiente está declarado `ByVal` en el procedimiento, no es necesario realizar ningún paso adicional. Visual Basic ya tiene previsto pasar el argumento por valor.  
  
-   Si el parámetro correspondiente está declarado `ByRef` en el procedimiento, incluya el argumento entre paréntesis en la llamada a procedimiento.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se reemplaza un parámetro declarado `ByRef` . En la llamada que obliga a `ByVal`, tenga en cuenta los dos niveles de paréntesis.  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 Cuando `str` se encierra entre paréntesis adicionales dentro de la lista de argumentos, la `setNewString` procedimiento no puede cambiar su valor en el código que realiza la llamada, y `MsgBox` muestra "No se puede reemplazar si pasa ByVal". Cuando `str` no se incluye entre paréntesis adicionales, el procedimiento puede cambiar, y `MsgBox` muestra "Es un nuevo valor para el argumento inString".  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Cuando se pasa una variable por referencia, debe utilizar el `ByRef` palabra clave para especificar este mecanismo.  
  
 El valor predeterminado en Visual Basic es pasar argumentos por valor. Sin embargo, resulta recomienda incluir la [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) o [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palabra clave con cada parámetro declarado. Esto hace que el código más fácil de leer.  
  
## <a name="robust-programming"></a>Programación sólida  
 Si un procedimiento declara un parámetro [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), la correcta ejecución del código puede depender poder cambiar el elemento subyacente en el código de llamada. Si el código que realiza la llamada pasa por alto este mecanismo de llamada encerrando el argumento entre paréntesis, o si se pasa un argumento no modificable, el procedimiento no puede cambiar el elemento subyacente. Esto podría producir resultados inesperados en el código de llamada.  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Siempre es un riesgo potencial al permitir a un procedimiento cambiar el valor subyacente a un argumento en el código de llamada. Asegúrese de que se espera que este valor puede cambiar, y estar preparado para comprobar su validez antes de usarlo.  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos](./index.md)  
 [Argumentos y parámetros de procedimiento](./procedure-parameters-and-arguments.md)  
 [Pasar argumentos a un procedimiento](./how-to-pass-arguments-to-a-procedure.md)  
 [Paso de argumentos por valor y por referencia](./passing-arguments-by-value-and-by-reference.md)  
 [Diferencias entre argumentos modificables y no modificables](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Diferencias entre pasar un argumento por valor y por referencia](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Cambiar el valor de un argumento de procedimiento](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Proteger un argumento de procedimiento para que no se realicen cambios de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Paso de argumentos por posición o por nombre](./passing-arguments-by-position-and-by-name.md)  
 [Tipos de valores y tipos de referencias](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
