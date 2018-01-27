# IniDelete

Elimina una clave de un archivo .ini estándar.

## Sintaxis

```pebakery
IniDelete,<FileName>,<Section>,<Key>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| Section | La sección que contiene el valor que se eliminará. |
| Key | El valor que se eliminará.|

## Observaciones

PEBakery optimizará múltiples `IniDelete` en una fila para un solo comando.

## Ejemplo

Supongamos que tenemos el siguiente archivo .ini:

```pebakery
// C:\myFile.ini
[mySection]
myKey=myValue
anotherKey=anotherValue
```

En el siguiente ejemplo, se eliminará la clave `myKey` y su valor.

```pebakery
IniDelete,C:\myFile.ini,mySection,myKey
```
