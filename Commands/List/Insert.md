# List,Insert

Insertar un nuevo valor en una ubicación específica en una lista.

## Sintaxis

```pebakery
List,Insert,<%ListVar%>,<Index>,<Value>[,Delim=<Str>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ListVar | La variable que contiene la lista. |
| Index | El índice donde se escribirá el artículo. |
| Value |El valor para insertar. |
| Delim= | **(Opcional)** Delimitador utilizado para separar los elementos en la lista. Insensible a Mayúsculas y minúsculas. **Por defecto:** `\|` |

## Remarks

`List,Insert` no sobrescribirá un valor de índice existente, sino que empujará el valor existente y los elementos subsiguientes a la lista.

Al especificar un 'Índice' mayor que el número de elementos +1 o menos, el número de elementos en la lista dará como resultado un error.

## Relacionado

[List,Append](./Append.md), [List,Set](./Set.md)

## Ejemplos

### Ejemplo 1

Anteponer _PEBakery_ al principio de una lista.

```pebakery
[Main]
Title=List-Insert Ejemplo 1
Description=Demostrar el uso de List,Insert.
Level=5
Version=1
Author=Homes32

[Variables]
%myList%=Home|Professional|Enterprise|Starter|Ultimate

[Process]
List,Insert,%myList%,1,"PEBakery"
Message,"myList: %myList%"
```

### Ejemplo 2

Inserte _PEBakery_ en la 4ª posición en una lista.

```pebakery
[Main]
Title=List-Insert Ejemplo 2
Description=Demostrar el uso de List,Insert.
Level=5
Version=1
Author=Homes32

[Variables]
%myList%=Home|Professional|Enterprise|Starter|Ultimate

[Process]
List,Insert,%myList%,4,"PEBakery"
Message,"myList: %myList%"
```
