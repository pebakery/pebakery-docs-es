# IniDeleteSection

Elimina una sección, junto con todas las claves y valores que contiene desde un archivo .ini estándar.

## Sintaxis

```pebakery
IniDeleteSection,<Filename>,<Section>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo. |
| Section | La sección que se eliminará. |

## Observaciones

PEBakery optimizará múltiples comandos `IniDeleteSection` en una fila para un solo comando de eliminación.

## Ejemplo

En el siguiente ejemplo, la sección `mySection` se eliminará junto con las claves y valores que contiene.

```pebakery
IniDeleteSection,C:\myFile.ini,mySection
```
