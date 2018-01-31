# StrFormat,Left

Devuelve una cantidad de caracteres desde el lado izquierdo de una cadena.

## Sintaxis

```pebakery
StrFormat,Left,<String>,<Count>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| Count | El número de caracteres a devolver. |
| DestVar | La variable donde se guardará el resultado. |

## Remarks

`Integer` must be a positive value.

If `Count` exceeds the string length then the entire string is returned.

## Observaciones

[StrFormat,Right](./Right.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,Len](./Len.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Left Ejemplo
Description=Mostrar el uso del comando StrFormat,Left.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."
%count%=19

[process]
StrFormat,Left,%string%,%count%,%result%
Message,"Los %count% caracteres mas a la izquierda son: %result%"
```
