# List,Count

Devuelve la cantidad de elementos en una lista.

## Sintaxis

```pebakery
List,Count,<%ListVar%>,<%DestVar%>[,Delim=<Str>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ListVar | La variable que contiene la lista. |
| DestVar |La variable donde se guardará el resultado. |
| Delim= | **(Opcional)** Delimitador utilizado para separar los elementos en la lista. Insensible a Mayúsculas y minúsculas. **Por defecto:** `\|` |

## Observaciones

The first element of a list is indexed by subscript of 1 (1-based index) and incremented for each additional item in the list.

## Relacionado

## Ejemplos

### Ejemplo 1

Use `List,Count` para recuperar el último elemento en una lista.

```pebakery
[Main]
Title=List-Count Ejemplo 1
Description=Demostrar el uso de List,Count.
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

### Ejemplo 2

Pasa a través de una lista completa.

```pebakery
[Main]
Title=List-Count Ejemplo 2
Description=Demostrar el uso de List,Count.
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
