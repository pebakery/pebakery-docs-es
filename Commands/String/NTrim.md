# StrFormat,NTrim

Elimina todos los números del final de una cadena.

## Sintaxis

```pebakery
StrFormat,NTrim,<String>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Si no existen números al final de la cadena, no se modificará.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-NTrim Ejemplo
Description=Mostrar el uso del comando StrFormat,NTrim.
Level=5
Version=1
Author=Homes32

[variables]
%string%="ABCDEFG12345678"

[process]
StrFormat,NTrim,%string%,%result%
Message,"Después de eliminar los números del final, la cadena restante es: %result%"
```
