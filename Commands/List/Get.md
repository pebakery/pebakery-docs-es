# List,Get

Extrae un elemento específico de una estructura de lista.

## Sintaxis

```pebakery
List,Get,<%ListVar%>,<Index>,<%DestVar%>[,Delim=<Str>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ListVar | La variable que contiene la lista. |
| Index | El índice donde se encuentra el elemento a recuperar. |
| DestVar | La variable donde se guardará el resultado. |
| Delim= | **(Opcional)** Delimitador utilizado para separar los elementos en la lista. Insensible a Mayúsculas y minúsculas. **Por defecto:*** `\|` |

## Observaciones

El comando `List,Count` se puede usar para recuperar el número de elementos en la lista.

Especificar un 'Índice' mayor o menor que el número de elementos en la lista dará como resultado un error.

## Relacionado

[List,Count](./Count.md)

## Ejemplos

### Ejemplo 1

Obtenga el 3er artículo en una lista.

```pebakery
[Main]
Title=List-Get Ejemplo 1
Description=Demonstrate usage of List,Get.
Level=5
Version=1
Author=Homes32

[Variables]
%myList%=Home|Professional|Enterprise|Starter|Ultimate

[Process]
List,Get,%myList%,3,%DestVar%
Message,"Item #3: %DestVar%"
```

### Ejemplo 2

Get the last item in a list.

```pebakery
[Main]
Title=List-Get Ejemplo 2
Description=Demostrar el uso de List,Get.
Level=5
Version=1
Author=Homes32

[Variables]
%myList%=Home|Professional|Enterprise|Starter|Ultimate

[Process]
List,Count,%myList%,%n%
List,Get,%myList%,%n%,%DestVar%
Message,"Last Item: %DestVar%"
```

### Ejemplo 3

Loop through an entire list.

```pebakery
[Main]
Title=List-Get Ejemplo 3
Description=Demostrar el uso de List,Get.
Level=5
Version=1
Author=Homes32

[Variables]
%myList%=Home|Professional|Enterprise|Starter|Ultimate

[Process]
List,Count,%myList%,%n%
Loop,%ScriptFile%,GetListItem-Loop,1,%n%

[GetListItem-Loop]
List,Get,%myList%,#c,%DestVar%
Message,"Item [#c/%n%]: %DestVar%"
```
