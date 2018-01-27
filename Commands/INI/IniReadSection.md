# IniReadSection

Lee el contenido de una sección en un archivo .ini estándar.

## Sintaxis

```pebakery
IniReadSection,<FileName>,<Section>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo para leer. |
| Section | La sección a leer. |
| DestVar | El valor se guardará en esta variable. |

## Observaciones

Este comando fue diseñado para registrar más información para ayudar a solucionar problemas.

La cadena que se almacenará en %DestVar% es legible por humanos en lugar de amigable con la codificación, y está destinado a ser utilizado con `Echo`.

PEBakery optimizará múltiples comandos `IniReadSection` en una fila para un solo comando de lectura.

## Ejemplo

Supongamos que un archivo `%SrcFile%` contiene estas líneas:

```pebakery
[English]
1=One
2=Two
3=Three

[Korean]
1=하나
2=둘
```

### Ejemplo 1

En el siguiente ejemplo, la sección `Inglés` se almacenará en el interior de `%Dest%`.

```pebakery
IniReadSection,%SrcFile%,English,%Dest%

// IniReadSection devolverá estas líneas en %Dest%.
[English]
1=One
2=Two
3=Three
```

### Ejemplo 2

IniReadSection devolverá la sección `Korean` en `%Dest%`.

```pebakery
IniReadSection,%SrcFile%,Korean,%Dest%

// IniReadSection devolverá estas líneas en %Dest%.
[Korean]
1=하나
2=둘
```
