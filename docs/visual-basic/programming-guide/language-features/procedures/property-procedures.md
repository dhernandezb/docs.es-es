---
title: Procedimientos de propiedad (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a0a73494c3573973d88823a7b5a5a83d2672e7d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656092"
---
# <a name="property-procedures-visual-basic"></a>Procedimientos de propiedad (Visual Basic)
Un procedimiento de propiedad es una serie de instrucciones de Visual Basic que manipulan una propiedad personalizada en un módulo, clase o estructura. Procedimientos de propiedad son también se denomina *descriptores de acceso de propiedad*.  
  
 Visual Basic se proporciona para los procedimientos de propiedad siguientes:  
  
-   A `Get` procedimiento devuelve el valor de una propiedad. Se llama cuando tiene acceso a la propiedad en una expresión.  
  
-   A `Set` procedimiento establece una propiedad en un valor, lo cual incluye una referencia de objeto. Se llama cuando se asigna un valor a la propiedad.  
  
 Normalmente se definen los procedimientos de propiedad en pares, mediante la `Get` y `Set` las instrucciones, pero puede definir cualquier procedimiento solamente si la propiedad es de solo lectura ([instrucción Get](../../../../visual-basic/language-reference/statements/get-statement.md)) o de solo escritura ([establecer Instrucción](../../../../visual-basic/language-reference/statements/set-statement.md)).  
  
 Puede omitir el `Get` y `Set` procedimiento cuando se usa una propiedad implementada automáticamente. Para obtener más información, vea [Propiedades implementadas automáticamente](./auto-implemented-properties.md).  
  
 Puede definir propiedades en las clases, estructuras y módulos. Las propiedades son `Public` de forma predeterminada, lo que significa que se pueden llamar desde cualquier lugar en la aplicación que pueda tener acceso al contenedor de propiedades.  
  
 Para obtener una comparación de propiedades y variables, consulte [diferencias entre propiedades y Variables en Visual Basic](./differences-between-properties-and-variables.md).  
  
## <a name="declaration-syntax"></a>Sintaxis de la declaración  
 Una propiedad en sí se define mediante un bloque de código delimitado por las [Property (instrucción)](../../../../visual-basic/language-reference/statements/property-statement.md) y `End Property` instrucción. Dentro de este bloque, cada procedimiento property aparece como un bloque interno encerrado entre una instrucción de declaración (`Get` o `Set`) y la búsqueda de coincidencias `End` declaración.  
  
 La sintaxis para declarar una propiedad y sus procedimientos es la siguiente:  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 La `Modifiers` puede especificar el nivel de acceso e información relativa a la sobrecarga, invalidación, uso compartido y sombreado, así como si la propiedad es de solo lectura o de solo escritura. El `AccessLevel` en el `Get` o `Set` procedimiento puede ser cualquier nivel más restrictivo que el nivel de acceso especificado para la propiedad en Sí. Para obtener más información, consulte [Property (instrucción)](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### <a name="data-type"></a>Tipo de datos  
 Tipo de datos de una propiedad y el nivel de acceso principal se definen en el `Property` instrucción y no en los procedimientos de propiedad. Una propiedad puede tener solo un tipo de datos. Por ejemplo, no se puede definir una propiedad que se va a almacenar un `Decimal` valor pero recuperar un `Double` valor.  
  
### <a name="access-level"></a>Nivel de acceso  
 Sin embargo, puede definir un nivel de acceso principal para una propiedad y restringir aún más el nivel de acceso en uno de los procedimientos de propiedad. Por ejemplo, puede definir un `Public` propiedad y, a continuación, defina un `Private Set` procedimiento. El `Get` procedimiento permanece `Public`. Puede cambiar el nivel de acceso sólo en uno de los procedimientos de una propiedad, y sea aún más restrictivo que el nivel de acceso principal. Para obtener más información, consulte [Cómo: declarar una propiedad con niveles de acceso mixtos](./how-to-declare-a-property-with-mixed-access-levels.md).  
  
## <a name="parameter-declaration"></a>Declaración de parámetro  
 Declarar cada parámetro de la misma manera que lo hace para [Sub (procedimientos)](./sub-procedures.md), salvo que el mecanismo para pasar argumentos debe ser `ByVal`.  
  
 La sintaxis para cada parámetro en la lista de parámetros es como sigue:  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Si el parámetro es opcional, también debe proporcionar un valor predeterminado como parte de su declaración. La sintaxis para especificar un valor predeterminado es como sigue:  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>Valor de propiedad  
 En un `Get` procedimiento, el valor devuelto se suministra a la expresión de llamada como el valor de la propiedad.  
  
 En un `Set` procedimiento, el nuevo valor de propiedad se pasa al parámetro de la `Set` instrucción. Si se declara explícitamente un parámetro, se debe declarar con el mismo tipo de datos como la propiedad. Si no se declara un parámetro, el compilador utiliza el parámetro implícito `Value` para representar el nuevo valor que se asignará a la propiedad.  
  
## <a name="calling-syntax"></a>Sintaxis de llamada  
 Invocar un procedimiento de propiedad implícitamente haciendo referencia a la propiedad. Utilice el nombre de la propiedad de la misma manera que se debe utilizar el nombre de una variable, excepto en que debe proporcionar valores para todos los argumentos que no son opcionales, y debe incluir la lista de argumentos entre paréntesis. Si no se proporcionan argumentos, se pueden omitir los paréntesis.  
  
 La sintaxis de una llamada implícita a un `Set` procedimiento es el siguiente:  
  
 `propertyname[(argumentlist)] = expression`  
  
 La sintaxis de una llamada implícita a un `Get` procedimiento es el siguiente:  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustración de declaración y llamada  
 La propiedad siguiente almacena un nombre completo como dos nombres que lo componen, el nombre y el apellido. Cuando se lee el código de llamada `fullName`, el `Get` procedimiento combina los dos nombres constituyentes y devuelve el nombre completo. Cuando el código de llamada asigna un nuevo nombre completo, el `Set` procedimiento intenta dividir en dos nombres que lo componen. Si no encuentra un espacio, lo almacena todos como el nombre.  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 El ejemplo siguiente muestra las llamadas típicas a los procedimientos de propiedad de `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos](./index.md)  
 [Procedimientos de función](./function-procedures.md)  
 [Procedimientos de operadores](./operator-procedures.md)  
 [Argumentos y parámetros de procedimiento](./procedure-parameters-and-arguments.md)  
 [Diferencias entre propiedades y Variables en Visual Basic](./differences-between-properties-and-variables.md)  
 [Crear una propiedad](./how-to-create-a-property.md)  
 [Llamar a un procedimiento de propiedad](./how-to-call-a-property-procedure.md)  
 [Cómo: declarar y llamar a una propiedad predeterminada en Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Establecer un valor en una propiedad](./how-to-put-a-value-in-a-property.md)  
 [Obtener un valor de una propiedad](./how-to-get-a-value-from-a-property.md)
