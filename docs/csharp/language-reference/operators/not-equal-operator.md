---
title: Operador != (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837833"
---
# <a name="-operator-c-reference"></a>Operador != (Referencia de C#)
El operador de desigualdad (`!=`) devuelve false si sus dos operandos son iguales; en caso contrario, devuelve true. Los operadores de desigualdad están predefinidos para todos los tipos, incluidos string y object. Los tipos definidos por el usuario pueden sobrecargar el operador `!=`.  
  
## <a name="remarks"></a>Comentarios  
 Para los tipos de valor predefinidos, el operador de desigualdad (`!=`) devuelve true si los valores de sus operandos son diferentes, y false en caso contrario. Para los tipos de referencia, excepto `string`, `!=` devuelve true si sus dos operandos hacen referencia a objetos diferentes. Para el tipo `string`, `!=` compara los valores de las cadenas.  
  
 Los tipos de valor definidos por el usuario pueden sobrecargar el operador `!=` (vea [operator](../../../csharp/language-reference/keywords/operator.md)). Al igual que los tipos de referencia definidos por el usuario, aunque de manera predeterminada `!=` se comporta como se ha descrito anteriormente para los tipos de referencia definidos por el usuario y predefinidos. Si `!=` está sobrecargado, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) también debe estar sobrecargado. Las operaciones de tipos enteros suelen estar permitidas en la enumeración.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>Vea también

- [Referencia de C#](../../../csharp/language-reference/index.md)  
- [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
- [Operadores de C#](../../../csharp/language-reference/operators/index.md)
