---
title: Valores NULL (F#)
description: Obtenga información sobre cómo se usa el valor null en el lenguaje de programación F#.
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787907"
---
# <a name="null-values"></a>Valores NULL

Este tema describe cómo se usa el valor null en F#.

## <a name="null-value"></a>Valor nulo

El valor null no se usa normalmente en F# para valores o variables. Sin embargo, null aparece como valor anormal en determinadas situaciones. Si se define un tipo de F#, no se permite null como valor normal a menos que el [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atributo se aplica al tipo. Si se define un tipo en algún otro lenguaje. NET, null es un valor posible, y al interoperar con esos tipos, el código de F# puede encontrar los valores null.

Para un tipo definido en F# y usar estrictamente en F#, la única forma de crear un valor null mediante la biblioteca de F# directamente es usar [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) o [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Sin embargo, para un tipo de F# que se utilizan desde otros lenguajes. NET, o si está utilizando ese tipo con una API que no está escrita en F#, como .NET Framework, puede haber valores null.

Puede usar el `option` los tipos de F# cuándo se puede utilizar una variable de referencia con un posible valor null en otro lenguaje. NET. En lugar de null con F# `option` tipo, use el valor de opción `None` si no hay ningún objeto. Utilice el valor de opción `Some(obj)` con un objeto `obj` cuando hay un objeto. Para obtener más información, consulte [opciones](../options.md).

El `null` palabra clave es una palabra clave válida en el lenguaje F#, y tendrá que usarlo cuando se trabaja con la API de .NET Framework u otras API que se escribe en otro lenguaje. NET. Las dos situaciones en las que podría necesitar un valor null son al llamar a una API de .NET y pasar un valor null como argumento y al interpretar el valor devuelto o parámetro de salida de una llamada al método. NET.

Para pasar un valor null a un método. NET, solo tiene que usar el `null` palabra clave en el código de llamada. En el siguiente ejemplo código se muestra cómo hacerlo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Para interpretar un valor null que se obtiene de un método. NET, use la coincidencia de patrones si es posible. El ejemplo de código siguiente muestra cómo usar la coincidencia de patrones para interpretar el valor null que se devuelve desde `ReadLine` cuando intenta leer después del final de un flujo de entrada.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

También se pueden generar valores NULL para tipos de F# de otras maneras, como cuando se utiliza `Array.zeroCreate`, que llama a `Unchecked.defaultof`. Debe tener cuidado con este código para mantener los valores null encapsulados. En una biblioteca diseñada únicamente para F#, no es necesario comprobar si hay valores null en todas las funciones. Si está escribiendo una biblioteca para interoperar con otros lenguajes. NET, es posible que deba agregar comprobaciones para null los parámetros de entrada y producirán un `ArgumentNullException`, tal como haría en el código de C# o Visual Basic.

Puede usar el código siguiente para comprobar si un valor arbitrario es null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Vea también

- [Valores](index.md)
- [Expresiones de coincidencia](../match-expressions.md)
