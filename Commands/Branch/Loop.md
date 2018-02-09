# Loop

Pasa por una serie de comandos basados en el valor de un contador.

## Sintaxis

```pebakery
Loop,<FileName>,<Section>,<StartValue>,<EndValue>[,Parameters]
```

```pebakery
Loop,BREAK
```

### Argumentos

#### Version 1

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa al script que contiene la 'Sección' para ejecutar. Sugerencia: utilice %ScriptFile% para hacer referencia al script actual. |
| Section | La [Sección] para ejecutar. |
| StartValue | El valor inicial para comenzar. Cada vez que termine el ciclo, el valor se incrementará. |
| EndValue |  El valor final que se alcanzará al incrementar `StartValue`. Una vez que se alcanza este valor, el ciclo se detiene. |
| Parameters | **(Opcional)** Parámetros para pasar a la 'Sección' que se está ejecutando. |

#### Version 2

| Argumento | Descripción |
| --- | --- |
| BREAK | Inmediatamente sale del bucle. El script continuará procesándose con la siguiente línea siguiendo el comando `Loop`. |

### Tokens

Los siguientes tokens son pasados por PEBakery y se pueden usar para realizar operaciones adicionales dentro del bucle.

| Token | Descripción |
| --- | --- |
| #1, #2, #3, etc. | Usado dentro de una 'Sección' para acceder a cualquier parámetro pasado. El esquema de numeración comienza desde `1` y continúa en el orden en que se pasaron los parámetros. Estos tokens se descartan cuando la sección finaliza el procesamiento. |
| #a | Contiene la cantidad de parámetros pasados a `Sección`. |
| #c | Contiene el valor actual del bucle relativo a `StartValue` y` EndValue`. |

## Observaciones

PEBakery permite pasar un número ilimitado de parámetros a la `[Sección]` que se está ejecutando.

Aunque los parámetros mismos se pasan por valor usando tokens, todas las variables están en el alcance de todo el script, por lo que los valores originales pueden modificarse haciendo referencia a ellos por su nombre. Si es necesario, puede usar el comando `System,SetLocal` para aislar las variables modificadas dentro de la sección de ejecución.

*Nota:* Winbuilder permite el bucle a través de los caracteres A-Z además de enteros. El comando `LoopLetter` de PEBakery reemplaza esta funcionalidad.

## Relacionado

[LoopLetter](./LoopLetter.md), [System,SetLocal](../System/SetLocal.md), [System,EndLocal](../System/EndLocal.md)

## Ejemplos

### Ejemplo 1

Un bucle simple que cuenta hasta 10 y muestra un cuadro de mensaje que muestra el recuento de bucle actual.

```pebakery
[main]
Title=Loop-Count Ejemplo
Description=Demostrar cómo recuperar el conteo en un bucle.
Level=5
Version=1
Author=Homes32

[variables]

[process]
Loop,%ScriptFile%,Count,1,10

[Count]
Message,"Count: #c"
```

### Ejemplo 2

También podemos usar Loop para procesar rápidamente una gran cantidad de controles de interfaz. En el siguiente ejemplo, tenemos 10 cuadros de entrada que representan las extensiones de archivo que queremos registrar. En lugar de escribir 10 sentencias `If,xxx,Equal,True,Run,%ScriptFile%,Process-Ext,xxx` podemos hacer la misma cantidad de trabajo usando solo 2 líneas de código. Si queremos agregar más controles de interfaz, solo necesitamos crear el control y aumentar nuestro contador, lo que lo convierte en un script muy pequeño y rápido.

```pebakery
[main]
Title=Loop-Interface Ejemplo
Description=Demostrar cómo pasar por los controles de interfaz.
Level=5
Version=1
Author=Homes32

[variables]

[process]
Loop,%ScriptFile%,Process-Ext,1,10

[Process-Ext]
// #c es el valor actual de nuestro contador de bucle
If,%CB_Asso_#c%,Equal,True,Run,%ScriptFile%,Register-Ext,%IN_Asso_#c%

[Register-Ext]
// #1 es el primer (y único) parámetro que pasamos a
// esta sección y representa el valor del cuadro de entrada actual
Echo,"Registrando extensión de archivo [#1]..."

[Interface]
pTextLabel5_1="File associations:",1,1,9,21,99,18,8,Bold
CB_Asso_1=,1,3,11,46,20,20,True
IN_Asso_1=,1,0,31,46,50,20,txt
CB_Asso_2=,1,3,11,72,20,20,True
IN_Asso_2=,1,0,31,71,50,20,pdf
CB_Asso_3=,1,3,11,96,20,20,True
IN_Asso_3=,1,0,31,96,50,20,script
CB_Asso_4=,1,3,11,121,18,20,True
IN_Asso_4=,1,0,31,121,50,20,log
CB_Asso_5=,1,3,11,146,18,20,False
IN_Asso_5=,1,0,31,146,50,20,
CB_Asso_6=,1,3,11,171,20,20,True
IN_Asso_6=,1,0,31,171,50,20,exe
CB_Asso_7=,1,3,11,197,18,20,False
IN_Asso_7=,1,0,31,196,50,20,
CB_Asso_8=,1,3,11,222,18,20,False
IN_Asso_8=,1,0,31,221,50,20,
CB_Asso_9=,1,3,11,247,18,20,False
IN_Asso_9=,1,0,31,246,50,20,
CB_Asso_10=,1,3,11,272,18,20,False
IN_Asso_10=,1,0,31,271,50,20,
```

### Ejemplo 3

En este ejemplo, estamos buscando en todos los archivos *oem#.inf* en la ruta *C:\Windows\inf\* (oem0.inf hasta oem100.inf) para la entrada llamada *VBoxUSB.sys* en la sección *[SourceDisksFiles]*. Si se encuentra la entrada, el nombre del archivo *oem#.inf* correcto se guarda en nuestro resultado y el ciclo finaliza.


NOTA: los archivos oem.inf siempre comienzan con CERO (oem0.inf).

```pebakery
[main]
Title=Loop-Ini-Search
Description=Demostrar cómo recorrer los archivos.
Level=5
Version=1
Author=Homes32

[variables]
%Result%="[Not Found]"

[process]
Loop,%ScriptFile%,Try-OEM,0,100,SourceDisksFiles,VBoxUSB.sys
Echo,Found VBoxUSB.sys in [%Result%]

[Try-OEM]
Set,%file%,C:\Windows\inf\oem#c.inf
If,ExistFile,%file%,IniRead,%file%,#1,#2,%var%
If,Not,-%var%,Equal,-,Begin
  Set,%Result%,%file%
  Loop,BREAK
End
```
