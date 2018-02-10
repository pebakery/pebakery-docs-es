# Text File Control

Muestra un archivo de texto incrustado en el script.

## Sintaxis

```pebakery
<Name>=<FileName>,<Visibility>,6,<PosX>,<PosY>,<Width>,<Height>[,<ToolTip>]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Name | Nombre único utilizado para hacer referencia a este control. |
| FileName | El nombre del archivo codificado para mostrar. |
| Visibility | `True`/`False` - Mostrar u ocultar el control. |
| ControlID | `6` - El ID del control que especifica que este es un archivo de texto. |
| PosX | Posición horizontal medida desde la esquina superior izquierda del control. |
| PosY | Posición vertical medida desde la esquina superior izquierda del control. |
| Width | Ancho del control. |
| Height | Altura del control. |
| ToolTip | **(Opcional)** Texto de ayuda que se mostrará cuando el usuario pase el control. Este argumento siempre debe comenzar con un doble guion bajo `__`. *Ejemplo:* `"__Alguna información útil"` |

## Observaciones

Los archivos de texto están codificados e incrustados en la carpeta `ScriptEncoded` de la secuencia de comandos.

## Relacionado

[ReadInterface](/Commands/Interface/ReadInterface.md), [WriteInterface](/Commands/Interface/WriteInterface.md)

## Ejemplos

```pebakery
[Interface]
TextFile1=TextFile.txt,1,6,135,209,175,76

[InterfaceEncoded]
TextFile.txt=99,132

[EncodedFile-InterfaceEncoded-TextFile.txt]
lines=0
0=eJzzSM3JyVcIzy/KSVHk5fIgiwcA61sVjnic4wlJrShxy8xJ1SupKGEYBSMNuEBpSRzyN1W/mTEwAQAtYwdJj9s6pwEAAAACAAAAJgAAABkAAAAAAAAAAQAAAAAAAAAAAAAA
```
