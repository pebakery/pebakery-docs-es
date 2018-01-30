# StrFormat,CTrim

Elimina caractere(s) específico(s) del principio o el final de una cadena si existen.

## Sintaxis

```pebakery
StrFormat,CTrim,<String>,<Chars>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cuerda a leer. |
| Chars | El(Los) caracter(es) para recortar. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Si `Chars` no existe al principio o al final de la cadena, no se modificará.

Este comando se puede utilizar para eliminar (recortar) los caracteres `\` al principio o al final de una ruta, sin tener una declaración separada para verificar si existen..

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,UCase](./UCase.md), [StrFormat,LCase](./LCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-CTrim Example
Description=Mostrar el uso de StrFormat,CTrim.
Level=5
Version=1
Author=Homes32

[variables]
%string%="%BaseDir%\Projects\"
%URL%="https://www.google.com"

[process]
StrFormat,CTrim,%string%,"\",%result%
Message,"Después de eliminar caracteres [\], la cadena restante es: %result%"
StrFormat,CTrim,%URL%,"https://",%result%
Message,"Después de eliminar los caracteres [https://], la cadena restante es: %result%"
```
