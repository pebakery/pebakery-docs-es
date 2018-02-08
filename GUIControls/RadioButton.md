# Radio Button Control

Un botón circular que puede tener solo un botón de opción seleccionado en la interfaz a la vez.

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,11,<PosX>,<PosY>,<Width>,<Height>,<Value>[,<SectionToRun>,<ShowProgress>][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | Etiqueta que se muestra al lado del botón de radio. Use `""` para ninguno. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `11` - El ID de control que especifica que se trata de un botón de opción. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Value | True/False - Selected `True` Deselected `False` |
| SectionToRun | **(Opcional)** Define la [Sección] dentro de la secuencia de comandos que se procesará cuando se presione el botón o se cambie el valor del control. El nombre de la sección debe estar encerrado en guión bajo `_` caracteres. *Ejemplo:* `_RunMe_` |
| ShowProgress | **(Opcional)** True/False - Muestre la pantalla de progreso de compilación mientras se está ejecutando `SectionToRun`. Este argumento siempre debe seguir el argumento `SectionToRun`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"`
 |

## Observaciones

TEl `Valor` del botón de opción se puede leer haciendo referencia al control `Nombre` como una variable. Ej. `%RadioButton1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
RadioButton1=RadioButton1,1,11,324,124,100,20,True
RadioButton2=RadioButton2,1,11,324,144,100,20,False
RadioButton3=RadioButton3,1,11,324,164,100,20,False
```
