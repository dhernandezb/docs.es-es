---
title: Palabra clave char (Referencia de C#)
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 4d4e4719eabf7dbe31a59cc2e1e3d3d9019f080d
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2018
ms.locfileid: "43742031"
---
# <a name="char-c-reference"></a>char (Referencia de C#)

La palabra clave `char` se usa para declarar una instancia de la estructura <xref:System.Char?displayProperty=nameWithType> que .NET Framework usa para representar un carácter Unicode. El valor de un objeto `Char` es un valor numérico de 16 bits (ordinal).

 Los caracteres Unicode se usan para representar la mayoría de los idiomas escritos del mundo.

|Tipo|Intervalo|Tamaño|Tipo de .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 a U+FFFF|Carácter Unicode de 16 bits|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literales

Las constantes de tipo `char` pueden escribirse como literales de caracteres, secuencias de escape hexadecimal o representaciones Unicode. También se pueden convertir los códigos de caracteres enteros. En el siguiente ejemplo se inicializan cuatro variables `char` con el mismo carácter `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Conversiones

Un `char` se puede convertir implícitamente a [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) o [decimal](../../../csharp/language-reference/keywords/decimal.md). En cambio, no hay ninguna conversión implícita de otros tipos al tipo `char`.

El tipo <xref:System.Char?displayProperty=nameWithType> proporciona varios métodos estáticos para trabajar con valores `char`.

## <a name="c-language-specification"></a>Especificación del lenguaje C#  

Para obtener más información, vea la sección [Tipos enteros](~/_csharplang/spec/types.md#integral-types) de la [Especificación del lenguaje C#](../language-specification/index.md). La especificación del lenguaje es la fuente definitiva de la sintaxis y el uso de C#.

## <a name="see-also"></a>Vea también

- <xref:System.Char>  
- [Referencia de C#](../../../csharp/language-reference/index.md)  
- [Guía de programación de C#](../../../csharp/programming-guide/index.md)  
- [Palabras clave de C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabla de tipos enteros](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabla de tipos integrados](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabla de conversiones numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabla de conversiones numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Tipos que aceptan valores NULL](../../../csharp/programming-guide/nullable-types/index.md)  
- [Cadenas](../../../csharp/programming-guide/strings/index.md)