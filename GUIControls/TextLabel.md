# Text Label Control

Muestra una línea de texto.

## Syntax

```pebakery
<Name>=<Caption>,<Visibility>,1,<PosX>,<PosY>,<Width>,<Height>,<FontSize>,<FontWeight>[,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | Texto que se muestra en el control. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `1` - El ID del control que especifica que esta es una etiqueta de texto. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Font Size | Tamaño de fuente en puntos. (ej. 12) |
| Font Weight | Puede ser `Normal`, `Bold`, `Italic`, `Underline`, o `Strike`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

Las etiquetas de texto envolverán el texto, permitiendo que se muestren varias líneas dentro del límite de 'Ancho' y 'Altura' de la Etiqueta de texto.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
pTextLabel1="¡Hola Mundo!",1,1,20,50,230,18,8,Normal
```
