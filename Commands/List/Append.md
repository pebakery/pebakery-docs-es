# Lista, Anexar

Añade un valor al final de una lista.

## Sintaxis

```pebakery
List,Append,<%ListVar%>,<Value>[,Delim=<Str>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ListVar | La variable que contiene la lista. |
| Value | El valor para agregar. |
| Delim= | **(Opcional)** Delimitador utilizado para separar los elementos en la lista. Insensible a Mayúsculas y minúsculas. **Por defecto:** `\|` |

## Observaciones

Para insertar un elemento al principio de una lista, use el comando `List,Insert`.

## Relacionado

[List,Insert](./Insert.md), [List,Set](./Set.md)

## Ejemplos

### Ejemplo 1

Append _PEBakery_ to the end of a list.

```pebakery
[Main]
Title=List-Append Ejemplo
Description=Demostrar el uso de List,Append.
Level=5
Version=1
Author=Homes32

[Variables]
%myList%=Home|Professional|Enterprise|Starter|Ultimate

[Process]
List,Append,%myList%,"PEBakery"
Message,"myList: %myList%"
```
