# TXTDelSpaces

Eliminar todos los espacios desde el comienzo de cada línea dentro de un archivo de texto.

## Sintaxis

```pebakery
TXTDelSpaces,<FileName>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |

## Observaciones

Este comando fue creado para hacer que algunos archivos INI específicos sean más pequeños en tamaño total.

Si `FileName` no existe, la operación fallará.

## Relacionado

[TXTAddLine](./TXTAddLine.md), [TXTDelEmptyLines](./TXTDelEmptyLines.md), [TXTDelLine](./TXTDelLine.md)

## Ejemplos

### Ejemplo 1

```pebakery
TxtDelSpaces,C:\myFile.txt
```
