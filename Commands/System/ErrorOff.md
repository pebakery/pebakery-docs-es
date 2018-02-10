# System,ErrorOff

Impide que un proceso falle en caso de que ocurra un error.

Los errores que normalmente provocarían la falla de un comando se ignorarán y el procesamiento continuará.

## Sintaxis

```pebakery
System,ErrorOff[,Lines]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Lines | **(Opcional)** - El número de líneas sucesivas en las que se ignorarán los errores. El valor predeterminado es ignorar solo la línea que sigue inmediatamente al comando `System,ErrorOff`.|

## Observaciones

Este comando le permite anular el comportamiento predeterminado de "Fallar en caso de error" de comandos como `FileCopy` `RegRead`.

Aún se generará un mensaje de error en el registro, sin embargo, tendrá un estado `Muted`.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=ErrorOff Ejemplo
Author=Homes32
Description=Mostrar el uso del comando System,ErrorOff.
Version=1
Level=5

[Interface]

[variables]

[process]

// No interrumpir el procesamiento si myFile.exe no se puede copiar a nuestro directorio de destino.
System,ERROROFF
FileCopy,C:\Temp\myFile.exe,%TargetDir%\myFile.exe


// No detener el procesamiento si los siguientes valores de registro no existen.
System,ERROROFF,2
RegRead,HKCR,Wow6432Node\Applications\vmware-mount.exe\shell\Mount\command,,%VMtmp%
RegRead,HKLM,"CurrentControlSet\Services\Eventlog\Application\VMware Virtual Mount Service Extended",EventMessageFile,%VMtmp%
```
