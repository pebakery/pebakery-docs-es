# StrFormat,Right

Devuelve una cantidad de caracteres del lado derecho de una cadena.

## Sintaxis

```pebakery
StrFormat,Right,<String>,<Count>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| Count | La cantidad de caracteres a devolver. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

`Integer` debe ser un valor positivo.

Si `Count` excede la longitud de la cadena, se devuelve la cadena completa.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,Len](./Len.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Right Ejemplo
Description=Mostrar el uso del comando StrFormat,Right.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."
%count%=19

[process]
StrFormat,Right,%string%,%count%,%result%
Message,"Los %Count% caracteres de la derecha son: %result%"
```
