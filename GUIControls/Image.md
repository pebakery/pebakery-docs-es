# Image Control

Muestra una imagen incrustada en el script.

## Sintaxis

```pebakery
<Name>=<Image>,<Visibility>,5,<PosX>,<PosY>,<Width>,<Height>[,<URL>][,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| Image | El nombre de la imagen codificada para mostrar en el control. Formatos compatibles `BMP` `JPG` `PNG` `GIF` `ICO` `SVG` |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `5` - El ID del control que especifica que esto es una imagen. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| URL | El sitio web para iniciar si se hace clic en la imagen. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

Los archivos de imagen están codificados e incrustados en la carpeta `ScriptEncoded` de la secuencia de comandos.

Si no se define una `URL`, al hacer clic en la imagen se abrirá en el visor de imágenes predeterminado del sistema operativo.

SI se define una `URL`, PEBakery mostrará los primeros 47 caracteres de la `URL` en la `Información sobre herramientas`.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
[Interface]
// Imagen sin URL
pImage1=FAQ.gif,1,5,20,230,40,40

// Imagen con URL e información sobre herramientas
pImage2=FAQ.gif,1,5,20,330,40,40,"https://www.google.com","__Search the Internet"

[InterfaceEncoded]
FAQ.gif=2066,2755

[EncodedFile-InterfaceEncoded-FAQ.gif]
lines=0
0=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

```
