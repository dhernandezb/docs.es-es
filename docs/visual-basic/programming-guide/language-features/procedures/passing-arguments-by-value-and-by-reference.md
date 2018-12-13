---
title: Pasar argumentos por valor y por referencia (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 2d333bc873ba055d7a7b53c50fcfeec4cc0f9491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654182"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Pasar argumentos por valor y por referencia (Visual Basic)
En Visual Basic, puede pasar un argumento a un procedimiento *por valor* o *por referencia*. Esto se conoce como el *mecanismo para pasar argumentos*, y determina si el procedimiento puede modificar el elemento de programación subyacente del argumento en el código de llamada. La declaración de procedimiento determina el mecanismo de paso para cada parámetro especificando el [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) o [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palabra clave.  
  
## <a name="distinctions"></a>Diferencias  
 Cuando se pasa un argumento a un procedimiento, tenga en distintas condiciones que interactúan entre sí:  
  
-   Si el elemento de programación subyacente es modificable o no modificables  
  
-   Si el propio argumento es modificable o no modificables  
  
-   Si el argumento que se ha pasado por valor o por referencia  
  
-   Si el tipo de datos del argumento es un tipo de valor o un tipo de referencia  
  
 Para obtener más información, consulte [diferencias entre modificables y no modificables argumentos](./differences-between-modifiable-and-nonmodifiable-arguments.md) y [las diferencias entre pasar un argumento por valor y por referencia](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Elección del mecanismo para pasar argumentos  
 Debe elegir el mecanismo de paso cuidadosamente para cada argumento.  
  
-   **Protección**. Al elegir entre uno de los 2 mecanismos a pasar, el criterio más importante es la exposición de la llamada a las variables a cambiar. La ventaja de pasar un argumento `ByRef` es que el procedimiento puede devolver un valor para el código que realiza la llamada a través de ese argumento. La ventaja de pasar un argumento `ByVal` es que evita que una variable se cambie mediante el procedimiento.  
  
-   **Rendimiento**. Aunque el mecanismo de paso puede afectar al rendimiento del código, la diferencia es suele ser insignificante. Una excepción a esto es un tipo de valor que se pasa `ByVal`. En este caso, Visual Basic copia el contenido de todos los datos del argumento. Por lo tanto, para un tipo de valor grande, como una estructura, puede ser más eficaz para pasarlo `ByRef`.  
  
     Para los tipos de referencia, solo el puntero a los datos es (cuatro bytes copiados en plataformas de 32 bits, ocho bytes en plataformas de 64 bits). Por lo tanto, puede pasar argumentos de tipo `String` o `Object` por valor sin perjudicar al rendimiento.  
  
## <a name="determination-of-the-passing-mechanism"></a>Determinación del mecanismo para pasar argumentos  
 La declaración de procedimiento especifica el mecanismo de paso para cada parámetro. El código de llamada no puede reemplazar un `ByVal` mecanismo.  
  
 Si se declara un parámetro con `ByRef`, el código de llamada puede forzar al mecanismo para `ByVal` , incluya el nombre del argumento paréntesis en la llamada. Para obtener más información, consulte [Cómo: forzar un argumento para pasar por valor](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 El valor predeterminado en Visual Basic es pasar argumentos por valor.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Cuándo se debe pasar un argumento por valor  
  
-   Si el elemento de código que realiza la llamada subyacente del argumento es un elemento no modificable, declare el parámetro correspondiente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Ningún código puede cambiar el valor de un elemento no modificable.  
  
-   Si el elemento subyacente es modificable, pero no desea que el procedimiento para que pueda cambiar su valor, declare el parámetro `ByVal`. Solo el código de llamada puede cambiar el valor de un elemento modificable que se pasan por valor.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Cuándo se debe pasar un argumento por referencia  
  
-   Si el procedimiento tiene una necesidad original para cambiar el elemento subyacente en el código de llamada, declare el parámetro correspondiente [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Si la ejecución correcta del código depende del procedimiento que cambia el elemento subyacente en el código de llamada, declare el parámetro `ByRef`. Si se pasa por valor, o si el código que realiza la llamada pasa por alto el `ByRef` mecanismo para pasar argumentos, incluya el argumento entre paréntesis, la llamada al procedimiento podría producir resultados inesperados.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra cuándo se debe pasar argumentos por valor y cuándo se debe pasar por referencia. Procedimiento `Calculate` tiene un `ByVal` y un `ByRef` parámetro. Dado un tipo de interés, `rate`y una suma de dinero, `debt`, la tarea del procedimiento consiste en calcular un nuevo valor para `debt` que es el resultado de aplicar el tipo de interés en el valor original de `debt`. Dado que `debt` es un `ByRef` parámetro, el nuevo total se refleja en el valor del argumento en el código de llamada que corresponde a `debt`. Parámetro `rate` es un `ByVal` parámetro porque `Calculate` no deben cambiar su valor.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos](./index.md)  
 [Argumentos y parámetros de procedimiento](./procedure-parameters-and-arguments.md)  
 [Pasar argumentos a un procedimiento](./how-to-pass-arguments-to-a-procedure.md)  
 [Cambiar el valor de un argumento de procedimiento](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Proteger un argumento de procedimiento para que no se realicen cambios de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Forzar un argumento para que pase como un valor](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Paso de argumentos por posición o por nombre](./passing-arguments-by-position-and-by-name.md)  
 [Tipos de valores y tipos de referencias](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
