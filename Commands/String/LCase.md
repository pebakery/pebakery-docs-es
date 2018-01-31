# StrFormat,LCase

Convierte una cadena a minúscula.

## Sintaxis

```pebakery
StrFormat,LCase,<String>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | The string to read. |
| DestVar | The variable where the result will be saved. |

## Observaciones

Ninguna.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-LCase Ejemplo
Description=Mostrar el uso del comando StrFormat,LCase.
Level=5
Version=1
Author=Homes32

[variables]
%string%="The Quick BROWN FOX Jumps Over The LAZY DOG."

[process]
StrFormat,LCase,%string%,%result%
Message,"Lowercase string is: %result%"
```
