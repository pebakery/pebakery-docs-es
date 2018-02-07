# System,OnScriptExit

Especifica el comando que se ejecutará antes de que finalice el script actual.

## Sintaxis

```pebakery
System,OnScriptExit,<Command>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Command | El comando que se ejecutará antes de que termine el script. |

### Códigos de razón (reason)

Si el `Command`(comando) es `Run` (ejecutar), *reason* (razón) de la salida pasa como parámetro # 1. Esto le permite realizar un procesamiento adicional para controlar qué acciones se toman.

*Reason* puede ser uno de los siguientes valores:

| Reason | Descripción |
| --- | --- |
| DONE | Todos los comandos fueron procesados sin errores. |
| STOP | El usuario hizo clic en el botón *STOP*. |
| ERROR | Un script terminó debido a un error. |
| COMMAND | Un script finalizó debido a un comando `System, Halt` or `System, Exit`. |
| EXCEPTION | Se produjo una excepción del sistema durante el procesamiento. *Incluido para compatibilidad con Winbuilder 082. PEBakery no devuelve este motivo.*|

## Observaciones

Esta declaración se puede escribir en cualquier lugar dentro de la parte de ejecución del script. Llamar a este comando veces adicionales sobrescribirá el último valor de `Command`.

## Relacionado

[System,OnBuildExit](./OnBuildExit.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=OnScriptExit/OnBuildExit
Author=Homes32
Description=Mostrar el uso de los comandos System,OnScriptExit y System,OnBuildExit.
Version=1
Level=5

[Interface]
Callback=Callback,1,14,27,15,117,65,OnScriptExit,OnBuildExit,Both,0
Simulation="Callback Event",1,14,154,15,204,117,SUCCESS,ERROR,STOP,HALT,EXIT,"CRITICAL EXCEPTION",0
RunSimulation="Run Simulation",1,8,390,25,80,25,Process,0,False,_Process_,False

[variables]

[process]

// Definir nuestra función de salida
If,%Callback%,Equal,0,Begin
  System,OnScriptExit,Run,%ScriptFile%,CLEANUP
End
If,%Callback%,Equal,1,Begin
  System,OnBuildExit,Run,%ScriptFile%,CLEANUP
End
If,%Callback%,Equal,2,Begin
  System,OnScriptExit,Run,%ScriptFile%,CLEANUP
  System,OnBuildExit,Run,%ScriptFile%,CLEANUP
End

If,%Simulation%,Equal,0,Echo,"Ejecución exitosa de simulación de salida."
If,%Simulation%,Equal,1,Begin
  Echo,"Ejecutando simulación de error."
  // Forzar que ocurra un error
  FileCopy,foo,bar
End
If,%Simulation%,Equal,2,Begin
  Echo,"Ejecutando simulación del botón STOP (PARO) del usuario. ..#$xEl script ahora se detendrá por 5 segundos. Ahora es tu oportunidad de presionar el botón PARO..."
  Wait,5
End
If,%Simulation%,Equal,3,Halt,"Detener la simulación"
If,%Simulation%,Equal,4,Exit,"Salir de simulación."
If,%Simulation%,Equal,5,Echo,"PEBakery no devuelve esta razón actualmente."

[CLEANUP]
Echo,"Entrar en la función de limpieza..."
// Error
If,#1,EQUAL,ERROR,Begin
  Beep,ERROR
  Message,"Ocurrió un error. Saliendo...",ERROR,5
End

// PARO de usuario
If,#1,EQUAL,STOP,Begin
  Beep,Asterisk
  Message,"Presionó el botón PARO. Saliendo...",WARNING,5
End

// Construir/Script finalizado
If,#1,EQUAL,DONE,Begin
  Beep,OK
  Message,¡Procesamiento terminado! Saliendo...",INFORMATION,5
End

// COMANDO HALT/EXIT
If,#1,EQUAL,COMMAND,Begin
  Beep,CONFIRMATION
  Message,"Un comando de detención o salida se emitió. Saliendo...",ERROR,5
End

// Excepción crítica
If,#1,EQUAL,EXCEPTION,Begin
  Beep,ERROR
  Message,"Una excepción crítica ocurrió. Saliendo...",ERROR,5
End

// TODO
// Todos estos comandos se procesarán independientemente de REASON.
Echo,"Descargando secciones del Registro..."
RegHiveUnload,%Software_Temp%
Echo,"Llamando a otra función..."
Run,%ScriptFile%,CLEANUP-2
Echo,"Fin de la limpieza."

[CLEANUP-2]
Echo,"Podemos ejecutar comandos desde otras secciones también..."

```
