# Bevel Control

Un marco rectangular utilizado para organizar controles.

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,12,<PosX>,<PosY>,<Width>,<Height>[,<FontSize>][,<FontWeight>][,<FontStyle>][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | Etiqueta que se muestra en la parte superior del bisel. Use `""` para ninguno. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `12` - El ID del control que especifica que se trata de un bisel. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| Font Size | **(Opcional)** Tamaño de fuente en puntos. (ej. 12) |
| Font Weight | **(Opcional)** Puede ser `Normal`, `Bold`. |
| Font Style | **(Opcional)** Puede ser `Italic`, `Underline`, `Strike`. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

Para que se muestre el `Caption`, se debe especificar un` Tamaño de fuente`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
// Bisel sin leyenda (no se especifica el tamaño de la fuente)
Bevel1=Bevel1,1,12,128,8,414,287
Bevel2="",1,12,250,109,184,62,10,Bold

// Bisel con leyenda
Bevel3="Hello World!",1,12,250,19,104,82,10

// Bevel with 10pt font and Bold caption
Bevel4="Settings",1,12,135,239,400,50,10,Bold
```
