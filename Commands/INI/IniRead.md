# IniRead

Lee un valor de un archivo .ini estándar.

## Sintaxis

```pebakery
IniRead,<FileName>,<Section>,<Key>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo para leer. |
| Section | La sección que contiene el valor a leer. |
| Key | El valor a leer. |
| DestVar | El valor se guardará en esta variable. |

## Observaciones

PEBakery optimizará múltiples `IniRead` en una fila para un solo comando.

## Ejemplo

Supongamos que tenemos el siguiente archivo .ini:

```pebakery
// C:\myFile.ini
[mySection]
myKey=myValue
anotherKey=anotherValue
```

En el siguiente ejemplo, el valor de la clave `myKey` se almacenará en el interior de `%myVariable%`.

```pebakery
IniRead,C:\myFile.ini,mySection,myKey,%myVariable%
```
