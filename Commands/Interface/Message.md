# Message

Muestra un cuadro de mensaje simple con tiempo de espera opcional.

## Sintaxis

```pebakery
Message,<Message>,<Icon>[,Timeout]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Message | El texto que se mostrará al usuario. |
| Icon | **(Opcional)** Define el icono para mostrar. Las opciones válidas son: |
|| Información - **(Por defecto)** Muestra un icono de información |
|| Confirmación - Muestra un icono de pregunta |
|| Error - Muestra un icono de error |
|| Advertencia - Muestra un icono de advertencia |
| Timeout | **(Opcional)** Tiempo en segundos antes de que el mensaje se cierre automáticamente. |

## Observaciones

El ícono exacto que se muestra puede variar según la configuración de su sistema operativo.

Los mensajes bloquean el procesamiento posterior hasta que se confirma el mensaje. A menos que la situación requiera la intervención del usuario, se recomienda establecer un período de tiempo de espera razonable o utilizar el comando `Echo` para permitir que el script continúe el procesamiento.

## Relacionado

[Echo](./Echo.md), [If,QUESTION](../Branch/If.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=Message Ejemplo
Description=Mostrar el uso del comando mensaje.
Level=5
Version=1
Author=Homes32

[variables]

[process]
Message,"Informational Message",INFORMATION,10
Message,"Error Message",ERROR,10
Message,"Warning Message",WARNING,10
Message,"Confirmation Message",CONFIRMATION,10
```
