# StrFormat,ReplaceX

Reemplaza todas las apariciones de una subcadena dentro de una cadena. **Sensible a mayúsculas y minúsculas.**

## Sintaxis

```pebakery
StrFormat,ReplaceX,<String>,<SearchString>,<ReplaceString>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| SearchString | La cadena a encontrar dentro `String`. |
| ReplaceString | La cadena de reemplazo. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

If the `SubString` is not found `%DestVar%` will not be modified.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,LCase](./LCase.md), [StrFormat,UCase](./UCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-ReplaceX Ejemplo
Description=Mostrar el uso del comando StrFormat,ReplaceX.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El rápido zorro marrón salta sobre el perezoso perro marrón."
%search%="marrón"
%replace%="rojo"

[process]
StrFormat,ReplaceX,%string%,%search%,%replace%,%result%
Message,"Subcadena [%search%] fue reemplazado por [%replace%]: %result%"
```
