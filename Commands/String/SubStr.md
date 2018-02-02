# StrFormat,SubStr

Extrae una cantidad de caracteres de un punto de inicio específico en una cadena.

## Sintaxis

```pebakery
StrFormat,SubStr,<String>,<StartPos>,<Count>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| StartPos | La posición del caracter desde la izquierda para comenzar a leer. |
| Count | La cantidad de caracteres a devolver. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

If `Count` exceeds the string length then the entire remainder of the string is returned.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-SubStr Ejemplo
Description=Mostrar el uso del comando StrFormat,SubStr.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."
%start%=21
%count%=10

[process]
StrFormat,SubStr,%string%,%start%,%count%,%result%
Message,"Los %count% caracteres que comienzan desde %start% son: %result%"
```
