# Echo

Mostrar un mensaje en la ventana de compilación mientras se ejecuta el script.

Este mensaje persistirá hasta que se muestre otro mensaje o finalice la ejecución del script.

## Sintaxis

```pebakery
Echo,<Message>[,WARN]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Message | El texto que se mostrará al usuario. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| WARN | **(Opcional)** FMarca el `Message` como una advertencia en el registro. |

## Observaciones

`Echo` admite mostrar texto de varias líneas cuando especifica el código de escape `#$x` de nueva línea.

`Echo` se usa con mayor frecuencia para mantener al usuario actualizado sobre en qué está trabajando el script, sin embargo, también se puede usar como una herramienta de depuración, ya que el resultado de la declaración se escribe en el registro.

## Relacionado

[EchoFile](./EchoFile.md), [Message](./Message.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=Echo Ejemplo
Description=Muestra el uso del comando Echo.
Level=5
Version=1
Author=Homes32

[variables]
%Message1%="Hello World!"

[process]
Echo,%Message1%
WAIT,5
Echo,"This is a#$xMulti#$xLine#$xMessage!"
WAIT,5
Echo,"Something went very wrong!",WARN
WAIT,5
```
