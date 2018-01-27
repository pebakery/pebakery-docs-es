# IniWriteTextLine

Escribe una línea de texto en una sección dentro de un archivo .ini estándar.

## Sintaxis

```pebakery
IniWriteTextLine,<FileName>,<Section>,<Line>[,APPEND]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| Section | La sección donde se escribirá la cadena. |
| Line | La cadena a escribir. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| APPEND | **(Opcional)** Si se especifica, esto hará que la cadena se inserte al final de la sección. |

## Observaciones

A menos que se especifique el indicador `APPEND`, se insertará `Line` al principio de la sección.

PEBakery optimizará múltiples comandos `IniWriteTextLine` en una fila en una sola operación de escritura.

## Ejemplo

Supongamos que tenemos el siguiente archivo .ini:

```pebakery
// C:\myFile.ini
[mySection]
myKey=myValue
anotherKey=anotherValue
```

En el siguiente ejemplo, la cadena `Hello World!` se escribirá al comienzo de la sección.
Además, la cadena `Goodbye World!` se escribirá al final de la sección.

```pebakery
IniWriteTextLine,C:\myFile.ini,mySection,"Hello World!"
IniWriteTextLine,C:\myFile.ini,mySection,"Goodbye World!",APPEND
```

El archivo .ini resultante:

```pebakery
// C:\myFile.ini
[mySection]
Hello World!
myKey=myValue
anotherKey=anotherValue
Goodbye World!
```
