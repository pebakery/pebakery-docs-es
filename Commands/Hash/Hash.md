# Hash

Calcula el hash criptográfico de un archivo. 

El resultado se puede comparar con un valor conocido para verificar la integridad de un archivo.

## Sintaxis

```pebakery
Hash,<HashType>,<FilePath>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| HashType | El tipo de Hash para calcular. Los algoritmos soportados son: `MD5`, `SHA1`, `SHA256`, `SHA384`, `SHA512`.
| FilePath | La ruta completa del archivo al hash. |
| DestVar | La variable donde se guardará el resumen hash. |

## Observaciones

El comando `WebGet` tiene verificación hash integrada de los archivos descargados.

## Relacionado

## Ejemplos

### Ejemplo 1

El siguiente ejemplo usa la función `Hash` para verificar que *notepad.exe* no esté dañado.

```pebakery
[Main]
Title=Hash Example
Description=Mostrar el uso del comando Hash
Author=Homes32
Level=5
Version=1

[Variables]
%notepadHash%=233a35e4b579ccde25951f8e543f1d16ae3e7b5b3f29c1d56e691ffb075ced15

[Process]
Hash,SHA256,%WindowsDir%\System32\notepad.exe,%Hash%
If,%Hash%,Equal,%notepadHash%,Message,"¡Notepad.exe verificado!#$x#$xHash: %Hash%"
Else,Message,"¡Falló la verificación de Notepad.exe!#$x#$xHash: %Hash%#$x#$xno coincide#$x#$x%notepadHash%"
```
