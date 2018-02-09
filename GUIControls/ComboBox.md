# Combo Box Control

Una lista desplegable que le permite seleccionar un solo valor.

## Sintaxis

```pebakery
<Name>=<Value>,<Visibility>,4,<PosX>,<PosY>,<Width>,<Height>,<Option1>,<Option2>,<OptionN>[,<SectionToRun>,<ShowProgress>][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Value | El valor actualmente seleccionado por el cuadro combinado. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `4` - El ID del control que especifica que se trata de un cuadro combinado. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Option | Opciones para mostrar en el cuadro combinado. Múltiples valores están separados por comas. |
| SectionToRun | **(Opcional)** Define la [Sección] dentro de la secuencia de comandos que se procesará cuando se presione el botón o se cambie el valor del control. El nombre de la sección debe estar encerrado en guión bajo `_` caracteres. *Ejemplo:* `_RunMe_` |
| ShowProgress | **(Opcional)** True/False - Muestre la pantalla de progreso de compilación mientras se está ejecutando `SectionToRun`. Este argumento siempre debe seguir el argumento `SectionToRun`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

El `Valor` del cuadro combinado se puede leer haciendo referencia al control `Nombre` como una variable. Ej. `%ComboBox1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
// Combobox con 3 opciones
ComboBox1="Option 1",1,4,136,134,115,21,"Option 1","Option 2","Option 3"

// Combobox con 3 opciones que ejecutará `mySection` cuando se cambie un valor
ComboBox2="Option 1",1,4,136,154,115,21,"Option 1","Option 2","Option 3",_mySection_,True
```
