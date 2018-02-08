# Number Box Control

Un cuadro de entrada que acepta un número entre un rango mínimo y máximo determinado.

## Sintaxis

```pebakery
<Name>=<Name>,<Visibility>,2,<PosX>,<PosY>,<Width>,<Height>,<Value>,<Min>,<Max>,<Increment>[,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `2` - El ID de control que especifica que este es un cuadro numérico. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Min | El valor mínimo que el cuadro numérico permitirá. |
| Max | El valor máximo que el cuadro numérico permitirá. |
| Increment | Al hacer clic en las flechas arriba/abajo en el cuadro numérico aumentará el valor por un factor de *n*. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

El `Valor` del cuadro de número se puede leer haciendo referencia al control `Nombre` como una variable. Ej. `%NumberBox1%` o usando el comando `ReadInterface`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
NumberBox1=pNumberBox1,1,2,473,31,56,22,0,0,256,1,"__Incrementar el número positivo por un factor de 1"
NumberBox2=pNumberBox2,1,2,473,60,55,22,0,-256,256,2,"__Incremento o disminución del número por un factor de 2"
```
