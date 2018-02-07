# TXTDelLine

Eliminar las líneas de un archivo de texto determinado que comienzan con una cadena específica.

## Sintaxis

```pebakery
TXTDelLine,<FileName>,<String>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| String   | Cadena de texto utilizada para marcar el comienzo de la línea que se eliminará. `String` es sensible a mayúsculas y minúsculas.

## Observaciones

Se debe tener precaución al usar este comando, ya que el valor de `String` no necesita ser el valor de toda la línea, solo debe coincidir con el comienzo de la línea.

Si `FileName` no existe, la operación fallará.

PEBakery optimizará múltiples comandos `TXTDelLine` en una fila en un único comando de eliminación.

## Relacionado

[TXTAddLine](./TXTAddLine.md), [TXTDelEmptyLines](./TXTDelEmptyLines.md), [TXTDelSpaces](./TXTDelSpaces.md)

## Ejemplos

### Ejemplo 1

Assume we have the following file:

```pebakery
// C:\myFile.txt
1. Hola Mundo
2. HolaMundo
3. Esta será la única línea restante.
```

En este ejemplo, se eliminarán todas las líneas que comiencen con "Hola" dentro de C:\myFile.txt, dejando la línea 3 como la única línea restante en el archivo.

```pebakery
TXTDelLine,C:\myFile.txt,"Hola"
```
