# StrFormat,LTrim

Elimina una cantidad de caracteres del lado izquierdo de una cadena.

## Sintaxis

```pebakery
StrFormat,LTrim,<String>,<Count>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| Count | El número de caracteres a devolver. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Si `Count` excede la longitud de la cadena, se devuelve una cadena vacía.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-LTrim Ejemplo
Description=Mostrar el uso del comando StrFormat,LTrim.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."
%count%=19

[process]
StrFormat,LTrim,%string%,%count%,%result%
Message,"Después de eliminar %count% caracteres de la izquierda, la cadena restante es: %result%"
```
