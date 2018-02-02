# StrFormat,Split

Divide una cadena en subcadenas basadas en los delimitadores dados.

## Sintaxis

```pebakery
StrFormat,Split,<String>,<Delimiter>,<Index>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | La cadena a dividir. |
| Delimiter | El delimitador utilizado para dividir las subcadenas. |
| Index | Un número entero que representa el número de veces que se dividirá el `String`. |
|| 0 - Contiene el número de veces que el `String` se dividirá usando el `Delimiter` dado. |
|| 1...n - La ocurrencia del delimitador para dividir en`DestVar`. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

Este comando se usa con mayor frecuencia junto con el comando `Loop` para dividir una cadena dada separada por un delimitador conocido, como un espacio, una coma o un carácter `| `, y actuar sobre los componentes individuales.

## Relacionado

[Loop](../Branch/Loop.md), [StrFormat,Left](./Left.md), [StrFormat,Right](./Right.md), [StrFormat,Len](./Len.md), [StrFormat,SubStr](./SubStr.md), [StrFormat,RTrim](./RTrim.md), [StrFormat,LTrim](./LTrim.md), [StrFormat,CTrim](./CTrim.md), [StrFormat,NTrim](./NTrim.md), [StrFormat,LCase](./LCase.md), [StrFormat,UCase](./UCase.md), [StrFormat,Pos](./Pos.md), [StrFormat,PosX](./PosX.md), [StrFormat,Replace](./Replace.md), [StrFormat,ReplaceX](./ReplaceX.md)

## Ejemplos

### Ejemplo 1

Este script de ejemplo usa el comando `Loop` para mostrar palabras individuales en la cadena suministrada.

```pebakery
[Main]
Title=StrFormat-Split Ejemplo
Description=Mostrar el uso del comando StrFormat,Split.
Level=5
Version=1
Author=Homes32

[variables]
%string%="El zorro marrón rápido salta sobre el perro perezoso."

[process]
// Recupere el número de veces que la cadena se dividirá utilizando un carácter [espacio]. (Index: 0)
// Nosotros podemos usar " " o #$s para representar el caracter [espacio].
StrFormat,SPLIT,%string%,#$s,0,%count%

// Comenzar un ciclo usando el conteo que recuperamos de Index: 0 para repetir a través de las palabras.
Loop,%ScriptFile%,DisplayWords,1,%count%

[DisplayWords]
StrFormat,Split,%string%," ",#c,%result%
Message,"Dividir [#c] de [%count%]: %result%"
```
