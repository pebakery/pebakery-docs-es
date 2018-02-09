# Check Box Control

Una caja que se puede "marcar" o "desmarcar".

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,3,<PosX>,<PosY>,<Width>,<Height>,<Value>[,<SectionToRun>,<ShowProgress>][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | Etiqueta que se muestra junto a la casilla de verificación. Utilizar `""` para ninguno. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `3` - El ID del control que especifica que se trata de una casilla de verificación. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Value | True/False - Marcado 'Verdadero' Desmarcado 'Falso' |
| SectionToRun | **(Opcional)** Define la [Sección] dentro de la secuencia de comandos que se procesará cuando se presione el botón o se cambie el valor del control. El nombre de la sección debe estar encerrado en guión bajo `_` caracteres. *Ejemplo:* `_RunMe_` |
| ShowProgress | **(Opcional)** True/False - Muestre la pantalla de progreso de compilación mientras se está ejecutando `SectionToRun`. Este argumento siempre debe seguir el argumento `SectionToRun`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

El `Valor` de la casilla de verificación se puede leer haciendo referencia al control` Nombre` como una variable. Ej. `%CheckBox1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
// Casilla de verificación en el estado "desmarcado" (Falso)
CheckBox1=CheckBox,1,3,137,110,104,20,False
```
