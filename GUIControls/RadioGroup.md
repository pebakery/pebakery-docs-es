# Radio Group Control

Un grupo de botones de radio Solo se puede seleccionar un botón de opción por grupo a la vez

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,14,<PosX>,<PosY>,<Width>,<Height>,<Item1>,<Item2>,<ItemN>,<SelectedIndex>[,<SectionToRun>,<ShowProgress>][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | Etiqueta que se muestra en la parte superior del grupo de radio. Use `""` para ninguno. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `14` - El ID de control que especifica que este es un grupo de radio. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Option | Opciones para mostrar en el grupo de radio. Múltiples valores están separados por comas. |
| SelectedIndex | Índice basado en cero de la `Opción'seleccionada. |
| SectionToRun | **(Opcional)** Define la [Sección] dentro de la secuencia de comandos que se procesará cuando se presione el botón o se cambie el valor del control. El nombre de la sección debe estar encerrado en guión bajo `_` caracter s. *Ejempplo:* `_RunMe_` |
| ShowProgress | **(Opcional)** True/False - Mostrar la pantalla de progreso de compilación mientras se está ejecutando `SectionToRun`. Este argumento siempre debe seguir el argumento `SectionToRun`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

El `Valor` del grupo de radio se puede leer haciendo referencia al control `Nombre` como una variable. Ej. `%RadioGroup1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
// Un Grupo de Radio llamado "Radio Group" con 3 opciones. La opción "Option1" está seleccionada.
RadioGroup1="Radio Group",1,14,433,115,90,69,Option1,Option2,Option3,1
```
