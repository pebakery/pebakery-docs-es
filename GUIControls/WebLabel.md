# Web Label Control

Un hipervínculo que abrirá una página web en el navegador predeterminado.

## Sintaxis

```pebakery
<Name>=<Caption>,<Visibility>,10,<PosX>,<PosY>,<Width>,<Height>,<URL>[,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Caption | Texto que se muestra en el control. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `10` - El ID de control que especifica que esta es una etiqueta web. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| URL | El sitio web para lanzar si se hace clic en el hipervínculo. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

PEBakery siempre mostrará los primeros 47 caracteres de la `URL` en `ToolTip`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
// Etiqueta web
pWebLabel1=GitHub,1,10,250,160,32,18,https://github.com/
// Etiqueta web con información sobre herramientas
pWebLabel1=GitHub,1,10,250,260,32,18,https://github.com/v/PEBakery"__Contribute to PEBakery's development."
```
