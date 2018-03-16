# WebGet

Descarga archivos de Internet.

## Sintaxis

```pebakery
WebGet,<URL>,<DestPath>[,Hash=<HashType>,<HashDigest>],[NOERR]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| URL | URL del archivo para descargar.|
| DestPath | La ruta completa donde se guardará el archivo descargado. Si la ruta no existe, se creará. Si el archivo existe, se sobrescribirá. |
| Hash=   | **(Opcional)** Tipo de hash para calcular. Tipos de hash admitidos: `MD5`, `SHA1`, `SHA256`, `SHA384`, `SHA512`. |
| HashDigest | **(Opcional)** El resumen Hash utilizado para verificar el archivo descargado. |

`Hash=` y `HashDigest` deben ser usados al mismo tiempo.

### Flags (Indicadores)

Los indicadores se pueden especificar en cualquier orden

| Flag | Descripción |
| --- | --- |
| NOERR | **(Opcional)** No detenga la construcción si falla la descarga. Será responsabilidad del desarrollador del script manejar la situación con gracia. |

### Códigos de retorno

| Variable | Descripción |
| --- | --- |
| %StatusCode% | Contiene el código de estado HTTP de la operación WebGet más reciente. Cuando se usa junto con el indicador `NOERR`, el código de estado puede probarse y tomarse medidas correctivas cuando se produce una falla. Se puede encontrar una lista de códigos de estado HTTP en [HTTP Status Code Registry](https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml). |

## Observaciones

No se realizan comprobaciones para garantizar que la máquina local tenga una conexión a Internet válida o que haya suficiente espacio en disco para descargar el archivo. Si es necesario, estas pruebas pueden realizarse con PEBakery *Conditional Operators*.

## Relacionado

[Conditional Operators](../Branch/Operators.md)

## Ejemplos

### Ejemplo 1

```pebakery
// El código fuente zlib se descargará a %BaseDir%\zlib.tar.gz.
WebGet,"https://zlib.net/zlib-1.2.11.tar.gz",%BaseDir%\zlib.tar.gz

// El archivo tar.gz descargado se validará con su resumen SHA256.
WebGet,"https://zlib.net/zlib-1.2.11.tar.gz",%BaseDir%\zlib.tar.gz,Hash=SHA256,c3e5e9fdd5004dcb542feda5ee4f0ff0744628baf8ed2dd5d66f8ca1197cb1a1
```

### Ejemplo 2

El siguiente script es un ejemplo de cómo podemos usar WebGet, así como anular su comportamiento predeterminado y solo descargar el archivo si no existe.

```pebakery
[Main]
Title=WebGet Example
Description=Mostrar el uso del comando WebGet
Author=Homes32
Level=5
Version=1

[Variables]
WebGetIfNotExistEx=Run,%ScriptFile%,WebGetIfNotExistEx

[Process]
// Llamar a nuestra macro
WebGetIfNotExistEx,"https://zlib.net/zlib-1.2.11.tar.gz",%BaseDir%\zlib.tar.gz

[WebGetIfNotExistEx]
// Sintaxis: WebGetIfNotExistEx,<URL>,<DestFile>
Echo,"Checking for #2..."
If,Not,ExistFile,#2,Begin
// ¡El archivo no existe!. ¡Vamos a descargarlo!
Echo,"Descargando #2..."
WebGet,#1,#2
End
Else,Begin
// El archivo ya existe en el disco.
Echo,"#2 ¡ya existe! Saltarse la descarga."
End
```
