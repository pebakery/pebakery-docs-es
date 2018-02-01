# StrFormat,PosX

Devuelve la posición de la subcadena dada dentro de la cadena especificada. **Sensible a mayúsculas y minúsculas.**

## Sintaxis

```pebakery
StrFormat,PosX,<String>,<SubString>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| SubString | La cadena a encontrar dentro de `String`. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Si no se encuentra el `SubString`,`% DestVar% `devolverá cero.

Si existen múltiples apariciones de `SubString` dentro de la cadena, solo se devolverá la primera aparición.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,LCase](./LCase.md), [StrFormat,UCase](./UCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-PosX Ejemplo
Description=Mostrar el uso del comando StrFormat,PosX.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."
%subStr%="zorro"

[process]
StrFormat,PosX,%string%,%subStr%,%result%
Message,"Subcadena [%subStr%] está en posición: %result%"
```
