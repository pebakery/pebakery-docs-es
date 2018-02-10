# System,GetFreeSpace

Devuelve el espacio libre en disco de una ruta, en Megabytes.

## Sintaxis

```pebakery
System,GetFreeSpace,<Path>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Path | La ruta completa de la unidad o directorio para recibir información de. |
| %DestVar% | La variable donde se almacenará la letra de la unidad. |

## Observaciones

PEBakery calcula 1 Megabyte = 1024 Bytes.

El tamaño de espacio libre se puede convertir de megabytes a KB/GB/TB/PB usando varios comandos `StrFormat`.

## Relacionado

[StrFormat,Ceil](../String/Ceil.md), [StrFormat,Floor](../String/Floor.md), [StrFormat,Round](../String/Round.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=GetFreeSpace Ejemplo
Description=Mostrar el uso del comando System,GetFreeDrive.
Level=5
Version=1
Author=Homes32

[variables]
%RequiredFreeMB%=800

[process]
// Verificar si tenemos suficiente espacio libre para construir este proyecto.
System,GetFreeSpace,%TargetDir%,%varTarget%
If,%varTarget%,SMALLER,%RequiredFreeMB%,Then,Halt,"Tu solo tienes %varTarget% MB espacio libre en su directorio de destino. Necesitas al menos %RequiredFreeMB% MB libres para construir este proyecto."
```
