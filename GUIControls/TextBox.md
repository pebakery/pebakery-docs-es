# Text Box Control

Un cuadro de entrada que acepta una sola línea de texto.

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,0,<PosX>,<PosY>,<Width>,<Height>,<Value>[,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | La etiqueta que se muestra sobre el cuadro de texto. Use `""` para ninguno. |
| Visibility | `True`/`False` - Mostrar u Ocultar el control. |
| ControlID | `0` - El ID de control que especifica que se trata de un cuadro de texto. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Value | El valor del cuadro de texto. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guión bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

El `Valor` del cuadro de texto se puede leer haciendo referencia al control `Nombre` como una variable. Ej. `% TextBox1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
TextBox1=TextBox,1,0,138,179,171,21,"abc.."
```
