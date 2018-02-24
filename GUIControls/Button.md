# Button Control

Un botón simple que se puede usar para ejecutar una sección de código dentro del script.

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,8,<PosX>,<PosY>,<Width>,<Height>,<SectionToRun>,<Image>,<ShowProgress>[,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | El texto que se muestra en el botón. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `8` - El ID del control que especifica que este es un Botón. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| SectionToRun | Define la [Sección] dentro del script que se procesará cuando se presione el botón. La sección especificada debe residir dentro del script actual. |
| Image | El nombre de la imagen codificada para mostrar en el control. Use `0` para ninguna imagen. |
| ShowProgress | True/False - Muestre la pantalla * Build progress * mientras se está ejecutando `SectionToRun`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

Los botones creados con el editor de interfaz interno de Winbuilder 082 tienen argumentos adicionales que incluyen parámetros duplicados para `_SectionToRun_` y `ShowProgress`. Estos campos son ignorados por PEBakery. Ver ejemplo 2.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

### Ejemplo 1
```pebakery
// Botón sin imagen
Button1=Button,1,8,361,27,98,25,pButton1,0,False
// Botón con imagen
Button2="Image Button",1,8,360,66,99,25,pButton2,if_hammer_screwdriver_11945.bmp,False
```

### Ejemplo 2

El siguiente control de botón se generó usando el editor de interfaz integrado de Winbuilder.

```pebakery
// Name=<Caption>,<Visibility>,8,<PosX>,<PosY>,<Width>,<Height>,<SectionToRun>,<Image>,<ShowProgress>,<False>,<_SectionToRun_>,<ShowProgress>][,<ToolTip>]
// El editor de interfaz de Winbuilder crea los parámetros # 12 y # 13 para _SectionToRun,ShowProgress pero en realidad no los usa, sino que usa los parámetros # 8 y # 10.
// El parámetro # 11 siempre es creado por el editor de interfaz de Winbuilder con un valor falso pero no se usa en Winbuilder o PEBakery..
// Winbuilder 077b2 a 078 usó este parámetro para la información sobre herramientas del botón.
pButton2="Button 2",1,8,23,75,80,25,runMe,tools.bmp,True,False,_runMe_,True
```
