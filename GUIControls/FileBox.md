# File Box Control

Un cuadro de entrada con un botón de navegación que le permite seleccionar un archivo o directorio.

## Sintaxis

```pebakery
<Name>=<Value>,<Visibility>,13,<PosX>,<PosY>,<Width>,<Height>[,FLAG][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Value | La ruta actualmente ingresada en el cuadro de archivo. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `13` - El ID del control que especifica que se trata de un cuadro de archivo. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| ToolTip | **(Optional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

### Flags (Indicadores)

Las siguientes banderas son mutuamente excluyentes.

| Argumento | Descripción |
| --- | --- |
| DIR | **(Por defecto)** El botón Examinar mostrará un diálogo de selección de directorio. |
| FILE |El botón Examinar mostrará un diálogo de selección de archivo. |

## Observaciones

El `Value` del File Box se puede leer haciendo referencia al control `Name` como una variable. Ex. `%FileBox1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
//Seleccione un archivo
FileBox1=,1,13,330,219,172,20,file

// Seleccione un directorio
FileBox2=,1,13,330,262,172,20,dir
```
