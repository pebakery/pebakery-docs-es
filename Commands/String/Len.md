# StrFormat,Len

Devuelve la cantidad de caracteres en una cadena.

## Sintaxis

```pebakery
StrFormat,Len,<String>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Ninguna.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Len Ejemplo
Description=Mostrar el uso del comando StrFormat,Len.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."

[process]
StrFormat,Len,%string%,%length%
Message,"La cantidad de caracteres es: %length%"
```
