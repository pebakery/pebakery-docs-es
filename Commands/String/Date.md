# StrFormat,Date

Devuelve la fecha y la hora actual en el formato especificado.

Este comando usa las reglas de formato de Fecha/Hora de Winbuilder. Para el formato de fecha/hora utilizando las opciones de formato estándar, use `StrFormat,DateTime`.

## Sintaxis

```pebakery
StrFormat,Round,<%DestVar%>,<FormatString>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | Variable donde se almacenará el resultado. |
| FormatString | La cadena de formato para la fecha/hora. |

### Cadenas de formato Fecha/Hora de WinBuilder

| Especificador de formato | Descripción | Ejemplos |
| --- | --- | --- |
| d | Día de la semana | `d` - day<br/>`dd` - día, incluidos los ceros a la izquierda<br/>`ddd` - Día 3 letras<br/>`dddd` - Día completo |
| m | Mes | `m` - mes<br/>`mm` - mes incluidos los ceros a la izquierda<br/>`mmm` - mes 3 letras<br/>`mmmm` - Mes completo |
| y | Año | `y` - año 2 digitos<br/>`yy` - año 2 digitos<br/>`yyyy` - año 4 digitos |
| h | Horas | `h` - hora del dia<br/>`hh` - hora del dia incluidos los ceros a la izquierda |
| n | Minutos | `n` - minutes<br/>`nn` - minutos incluidos los ceros a la izquierda |
| s | Segundos | `s` - segundos<br/>`ss` - segundos incluidos los ceros a la izquierda |
| z | Milisegundos | `z` - milisegundos |
| t | Hora (formato 12 hr) | `t` - Tiempo corto de 12 horas Ej. *2:13 PM*<br/>`tt` - Tiempo largo de 12 horas Ej. *2:13:25 PM* |
| g | Era gregoriana | muestra  `A.C.` o `D.C.` |
| AM/PM | Muestra la hora en formato de 12h. | `hh:nn AM/PM`
| : / - . | separador de fecha/hora |

## Observaciones

PEBakery devuelve todos los formatos de fecha/hora utilizando una cultura invariable.

## Relacionado

[StrFormat,DateTime](./DateTime.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Date
Description=Mostrar el uso de StrFormat,Date.
Level=5
Version=1
Author=Homes32

[Variables]

[Process]
// Formatos de fecha comunes
StrFormat,date,%longDate1%,"dddd, MMMM dd, yyyy"
StrFormat,date,%longDate2%,"ddd, MMM dd, yyy"
StrFormat,date,%shortDate1%,"yyyy-mm-dd"
StrFormat,date,%shortDate2%,"mm/dd/yyy"
// Formatos de hora comunes
StrFormat,date,%time1%,"hh:nn"
StrFormat,date,%time2%,"hh:nn:ss"
StrFormat,date,%time3%,"hh:nn:ss:z"
StrFormat,date,%time4%,"hh:nn AM/PM"
StrFormat,date,%time5%,"yyyy-mm-dd hh:nn AM/PM"
StrFormat,date,%time6%,"t"
StrFormat,date,%time7%,"tt"
StrFormat,date,%datetime%,"dddd, MMMM dd, yyyy hh:nn:ss"
Message,"%longDate1%#$x%longDate2%#$x%shortDate1%#$x%shortDate2%#$x#$x%time1%#$x%time2%#$x%time3%#$x%time4%#$x%time5%#$x%time6%#$x%time7%#$x%datetime%"
```
