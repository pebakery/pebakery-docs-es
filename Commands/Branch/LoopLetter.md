# LoopLetter

Pasa por un rango de letras en orden alfabético.

## Sintaxis

```pebakery
Loop,<FileName>,<Section>,<StartLetter>,<EndLetter>[,Parameters]
```

```pebakery
Loop,BREAK
```

### Argumentos

#### Version 1

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa al script que contiene la 'Sección' para ejecutar. Sugerencia: utilice %ScriptFile% para hacer referencia al script actual. |
| Section | La [Sección] para ejecutar. |
| StartLetter | La letra inicial para comenzar. Cada vez que termine el ciclo, la letra se incrementará lexicográficamente. |
| EndLetter |  La letra final que se alcanzará al incrementar `StartLetter`. Una vez que se alcanza esta letra, el ciclo se detiene. |
| Parameters | **(Opcional)** Parámetros para pasar a la `Sección 'que se está ejecutando. |

#### Version 2

| Argumento | Descripción |
| --- | --- |
| BREAK | Inmediatamente sale del bucle. El script continuará procesándose con la línea inmediate siguiente al comando `Loop`. |

### Tokens

Los siguientes tokens son pasados por PEBakery y se pueden usar para realizar operaciones adicionales dentro del bucle.
| Token | Descripción |
| --- | --- |
| #1, #2, #3, etc. | Usado dentro de una 'Sección' para acceder a cualquier parámetro pasado. El esquema de numeración comienza desde `1` y continúa en el orden en que se pasaron los parámetros. Estos tokens se descartan cuando la sección termina de procesarse. |
| #a | Contiene la cantidad de parámetros pasados a `Sección`. |
| #c | Contiene el valor actual del bucle relativo a `StartValue` y `EndValue`. |

## Observaciones

PEBakery permite pasar un número ilimitado de parámetros a la `[Sección]` que se está ejecutando.

Aunque los parámetros mismos se pasan por valor usando tokens, todas las variables están en el alcance de todo el script, por lo que los valores originales pueden modificarse haciendo referencia a ellos por su nombre. Si es necesario, puede usar el comando `System,SetLocal` para aislar las variables modificadas dentro de la sección de ejecución.

## Relacionado

[Loop](./Loop.md), [System,SetLocal](../System/SetLocal.md), [System,EndLocal](../System/EndLocal.md)

## Ejemplos

### Ejemplo 1

Este ejemplo muestra cómo podemos desplazarnos por las letras de unidad A-Z buscando notepad.exe.

```pebakery
[Main]
Title=LoopLetter-A-Z Ejemplo
Description=Demostrar cómo recorrer las letras de unidad buscando un archivo.
Level=5
Version=2
Author=Homes32

[variables]

[process]
Set,%searchFile%,"Windows\notepad.exe"
LoopLetter,%ScriptFile%,Search-Drives,A,Z
If,EXISTFILE,%fullPath%,ShellExecute,OPEN,%fullPath%

[Search-Drives]
Echo,"Searching drive [#c:\]"
Set,%fullPath%,#c:\%searchFile%
If,EXISTFILE,%fullPath%,Loop,BREAK
```
