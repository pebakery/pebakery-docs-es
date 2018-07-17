# List,LastPosX

Devuelve la última posición del valor especificado dentro de la lista especificada. **Distingue mayúsculas y minúsculas.**

## Sintaxis

```pebakery
List,LastPosX,<%ListVar%>,<Value>,<%DestVar%>[,Delim=<Str>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ListVar | La variable que contiene la lista. |
| Value | El valor a encontrar dentro de la lista. |
| DestVar | La variable donde se guardará el resultado. |
| Delim= | **(Opcional)** Delimitador utilizado para separar los elementos en la lista. Insensible a Mayúsculas y minúsculas. **Por defecto:** `\|` |

## Observaciones

Si no se encuentra el `Valor`, `% DestVar%` devolverá cero.

Si existen múltiples apariciones de `Valor` dentro de la lista, solo se devolverá la última ocurrencia.

## Relacionado

[List,LastPos](./LastPos.md), [List,Pos](./Pos.md), [List,PosX](./PosX.md)

## Ejemplos

### Ejemplo 1

Obtenga el índice de la última aparición de _Starter_.

```pebakery
[Main]
Title=List-LastPosX Ejemplo
Description=Demostrar el uso de List,LastPosX.
Level=5
Version=1
Author=Homes32

[variables]
%myList%=Home|UlTiMaTe|StarteR|Professional|Starter|Enterprise|PrOfEsSiOnAl|starter|Ultimate

[process]
List,LastPosX,%myList%,Starter,%result%
Message,"El último valor de [Starter] está en la posición: %result%"
```
