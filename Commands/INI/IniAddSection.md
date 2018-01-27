# IniAddSection

Agrega una nueva sección vacía dentro de un archivo .ini estándar.

## Sintaxis

```pebakery
IniAddSection,<FileName>,<Section>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| Section | El nombre de la Sección que se agregará. |

## Observaciones

Si la sección ya existe, ninguna acción será tomada.

PEBakery optimizará múltiples `IniAddSection` en una fila para un solo comando.

## Ejemplo

En el siguiente ejemplo, la sección `mySection` se creará dentro de C:\myFile.ini.

```pebakery
IniAddSection,C:\myFile.ini,mySection
```
