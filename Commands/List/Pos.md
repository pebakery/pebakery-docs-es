# List,Pos

Devuelve la posición del valor dado dentro de la lista especificada. **Insensible a mayúsculas/minúsculas.**

## Sintaxis

```pebakery
List,Pos,<%ListVar%>,<Value>,<%DestVar%>[,Delim=<Str>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ListVar | La variable que contiene la lista. |
| Value | El valor a encontrar dentro de la lista. |
| DestVar | La variable donde se guardará el resultado. |
| Delim= | **(Opcional)** Delimitador utilizado para separar los elementos en la lista. Insensible a Mayúsculas y minúsculas. **Por 

defecto:** `\|` |

## Observaciones

Si no se encuentra el `Valor', `% DestVar%` devolverá cero.

Si existen múltiples apariciones de `Valor` dentro de la lista, solo se devolverá la primera ocurrencia.

## Relacionado

[List,LastPos](./LastPos.md), [List,LastPosX](./LastPosX.md), [List,PosX](./PosX.md)

## Ejemplos

### Ejemplo 1

Obtenga el índice de la primera aparición de _Starter_.

```pebakery
[Main]
Title=List-Pos Ejemplo
Description=Demostrar el uso de List,Pos.
Level=5
Version=1
Author=Homes32

[variables]
%myList%=Home|UlTiMaTe|StarteR|Professional|Starter|Enterprise|PrOfEsSiOnAl|Starter|Ultimate

[process]
List,Pos,%myList%,Starter,%result%
Message,"Valor [Starter] está en la posición: %result%"
```
