# StrFormat,Replace

Reemplaza todas las apariciones de una subcadena dentro de una cadena. **Insensible a mayúsculas y minúsculas..**

## Sintaxis

```pebakery
StrFormat,Replace,<String>,<SearchString>,<ReplaceString>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a leer. |
| SearchString | La cadena a encontrar dentro de `String`. |
| ReplaceString | La cadena para reemplazar en `SearchString`. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Si no se encuentra `SubString`,`% DestVar%` no se modificará.

## Relacionado

[StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,LCase](./LCase.md), [StrFormat,UCase](./UCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,ReplaceX](./ReplaceX.md), [StrFormat,Split](./Split)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Replace Ejemplo
Description=Mostrar el uso del comando StrFormat,Replace.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perezoso perro marrón."
%search%="marrón"
%replace%="rojo"

[process]
StrFormat,Replace,%string%,%search%,%replace%,%result%
Message,"Subcadena [%search%] fue reemplazado por [%replace%]: %result%"
```
