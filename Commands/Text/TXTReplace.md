# TXTReplace

Buscar dentro de un archivo determinado y reemplazar todo el texto que coincida con el valor de OldString y reemplazarlo con NewString...

## Sintaxis

```pebakery
TXTReplace,<FileName>,<OldString>,<NewString>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| OldString | Cadena para ser reemplazada en el archivo. `OldString` **no** es sensible a mayúsculas y minúsculas. |
| NewString | Cadena que reemplazará a `OldString` |

## Observaciones

Se debe tener precaución al usar este comando, ya que **cualquier** instancia de `OldString` será reemplazada, incluso si es parte de otra palabra.

If `FileName` does not exist the operation will fail.

PEBakery will optimize multiple `TXTReplace` in a row to single command.

## Relacionado

[TXTAddLine](./TXTAddLine.md), [TXTDelEmptyLines](./TXTDelEmptyLines.md), [TXTDelLines](./TXTDelLines.md), [TXTDelSpaces](./TXTDelSpaces.md) 

## Ejemplos

### Ejemplo 1

Supongamos que tenemos el siguiente archivo:

```pebakery
// C:\myFile.txt
Hola Mundo
HolaMundo
holamundo
HolaAdiósholaadiósHolaAdiós
```

En este ejemplo, todas las instancias de la palabra `Hola` en el interior C:\myFile.txt serán reemplazadas con la palabra "Adiós"

```pebakery
TXTReplace,C:\myFile.txt,"Hola",Adiós
```

Resultado:

```pebakery
// C:\myFile.txt
Adiós Mundo
AdiósMundo
Adiós Mundo
AdiósAdiósAdiósadiósAdiósAdiós
```
