# TXTAddLine

Inserta una línea de texto en la ubicación especificada dentro de un archivo.

## Sintaxis

```pebakery
TXTAddLine,<FileName>,<String>,<Action>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| String | El texto que se agregará. |
| Action | Elija una de las siguientes directivas:|
|| **Prepend** - Insertará la línea de texto en la parte superior del archivo. |
|| **Append** - Insertará la línea de texto al final del archivo.

## Observaciones

Si `FileName` no existe, la operación fallará.

La implementación de TxtAddLine por parte de WinBuilder permitió una `Action` llamada **Place** que permitiría al desarrollador especificar un número de línea donde el texto debería insertarse. Esta característica se depreció en PEBakery debido a la falta de utilidad percibida.

PEBakery optimizará múltiples comandos `TXTAddLine` seguidos en un solo comando de escritura.

## Relacionado

[TXTDelEmptyLines](./TXTDelEmptyLines.md), [TXTDelLine](./TXTDelLine.md), [TXTDelSpaces](./TXTDelSpaces.md), [TXTReplace](./TXTReplace.md)

## Ejemplos

### Ejemplo 1

En este ejemplo, agregamos una línea que dice `¡Hola mundo!` Al final del archivo.

```pebakery
TXTAddLine,C:\myFile.txt,¡Hola mundo!,Append
```
