---
title: 'Comando dotnet nuget push: CLI de .NET Core'
description: El comando dotnet nuget push inserta un paquete en el servidor y lo publica.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: b9c0fad886cd1234325c58bf61b1a010bce421d9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50200031"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>nombre

`dotnet nuget push`: inserta un paquete en el servidor y lo publica.

## <a name="synopsis"></a>Sinopsis

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a>Descripción

El comando `dotnet nuget push` inserta un paquete en el servidor y lo publica. El comando push usa los detalles del servidor y de las credenciales encontrados en el archivo de configuración NuGet del sistema o en la cadena de archivos de configuración. Para más información sobre los archivos de configuración, consulte [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior) (Configuración del comportamiento de NuGet). La configuración predeterminada de NuGet se obtiene mediante la carga de *%AppData%\NuGet\NuGet.config* (Windows) o *$HOME/.local/share* (Linux/macOS), y luego la carga de cualquier archivo *nuget.config* o *.nuget\nuget.config* comenzando desde la raíz de la unidad y finalizando en el directorio actual.

## <a name="arguments"></a>Argumentos

`ROOT`

Especifica la ruta de acceso al archivo en la que se debe insertar el paquete.

## <a name="options"></a>Opciones

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Deshabilita el almacenamiento en búfer al realizar inserciones en un servidor HTTP(S) para reducir el uso de memoria.

`--force-english-output`

Fuerza la ejecución de la aplicación mediante una referencia cultural en inglés invariable.

`-h|--help`

Imprime una corta ayuda para el comando.

`-k|--api-key <API_KEY>`

La clave de API para el servidor.

`-n|--no-symbols`

No inserta símbolos (incluso si está presente).

`--no-service-endpoint`

No agrega "api/v2/paquete" a la dirección URL de origen.

`-s|--source <SOURCE>`

Especifica la dirección URL del servidor. Esta opción es necesaria a menos que el valor de configuración `DefaultPushSource` esté establecido en el archivo de configuración de NuGet.

`-sk|--symbol-api-key <API_KEY>`

La clave de API para el servidor de símbolos.

`-ss|--symbol-source <SOURCE>`

Especifica la dirección URL del servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica el tiempo de espera para la inserción en un servidor en segundos. El valor predeterminado es 300 segundos (5 minutos). Si se especifica 0 (cero segundos), se aplica el valor predeterminado.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Deshabilita el almacenamiento en búfer al realizar inserciones en un servidor HTTP(S) para reducir el uso de memoria.

`--force-english-output`

Fuerza la ejecución de la aplicación mediante una referencia cultural en inglés invariable.

`-h|--help`

Imprime una corta ayuda para el comando.

`-k|--api-key <API_KEY>`

La clave de API para el servidor.

`-n|--no-symbols`

No inserta símbolos (incluso si está presente).

`-s|--source <SOURCE>`

Especifica la dirección URL del servidor. Esta opción es necesaria a menos que el valor de configuración `DefaultPushSource` esté establecido en el archivo de configuración de NuGet.

`-sk|--symbol-api-key <API_KEY>`

La clave de API para el servidor de símbolos.

`-ss|--symbol-source <SOURCE>`

Especifica la dirección URL del servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica el tiempo de espera para la inserción en un servidor en segundos. El valor predeterminado es 300 segundos (5 minutos). Si se especifica 0 (cero segundos), se aplica el valor predeterminado.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Deshabilita el almacenamiento en búfer al realizar inserciones en un servidor HTTP(S) para reducir el uso de memoria.

`--force-english-output`

Fuerza la ejecución de la aplicación mediante una referencia cultural en inglés invariable.

`-h|--help`

Imprime una corta ayuda para el comando.

`-k|--api-key <API_KEY>`

La clave de API para el servidor.

`-n|--no-symbols`

No inserta símbolos (incluso si está presente).

`-s|--source <SOURCE>`

Especifica la dirección URL del servidor. Esta opción es necesaria a menos que el valor de configuración `DefaultPushSource` esté establecido en el archivo de configuración de NuGet.

`-sk|--symbol-api-key <API_KEY>`

La clave de API para el servidor de símbolos.

`-ss|--symbol-source <SOURCE>`

Especifica la dirección URL del servidor de símbolos.

`-t|--timeout <TIMEOUT>`

Especifica el tiempo de espera para la inserción en un servidor en segundos. El valor predeterminado es 300 segundos (5 minutos). Si se especifica 0 (cero segundos), se aplica el valor predeterminado.

---

## <a name="examples"></a>Ejemplos

Inserta *foo.nupkg* en el origen de inserción predeterminado, y especifica una clave de API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Inserta *foo.nupkg* en el origen de inserción personalizado `https://customsource`, y especifica una clave de API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/`

Inserta *foo.nupkg* en el origen de inserción predeterminado:

`dotnet nuget push foo.nupkg`

Inserta *foo.symbols.nupkp* en el origen de símbolos predeterminado:

`dotnet nuget push foo.symbols.nupkg`

Inserta *foo.nupkg* en el origen de inserción predeterminado, y especifica un tiempo de espera de 360 segundos:

`dotnet nuget push foo.nupkg --timeout 360`

Inserta todos los archivos *.nupkg*  del directorio actual en el origen de inserción predeterminado:

`dotnet nuget push *.nupkg`
