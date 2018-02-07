# TXTDelEmptyLines

Elimina todas las líneas vacías de un archivo de texto dado.

## Sintaxis

```pebakery
TXTDelEmptyLines,<FileName>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | The full path of the file. |

## Observaciones

Este comando se creó para hacer que algunos archivos INI específicos sean más pequeños en tamaño general.

Si `FileName` no existe, la operación fallará.

## Relacionado

[TXTAddLine](./TXTAddLine.md), [TXTDelLine](./TXTDelLine.md), [TXTDelSpaces](./TXTDelSpaces.md)

## Ejemplos

### Ejemplo 1

```pebakery
TxtDelEmptyLines,C:\myFile.txt
```
