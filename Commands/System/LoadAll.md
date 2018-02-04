# System,LoadAll

**Alias:** `System,ReScanScripts`

Escanea el directorio *Projects* para proyectos y scripts nuevos/modificados y los agrega al árbol del proyecto.

## Sintaxis

```pebakery
System,LoadAll
```

### Argumentos

Este comando no tiene argumentos.

## Observaciones

Este comando se puede usar para reconstruir el árbol del proyecto cuando se agrega o modifica una secuencia de comandos y realiza la misma operación que presionando el botón **Refresh** en la ventana principal.

## Relacionado

[System,Load](./Load.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=LoadAll Ejemplo
Author=Homes32
Description=Mostrar el uso del comando System,LoadAll.
Version=1
Level=5
Selected=True

[Interface]
BTN_Clean=Cleanup,1,8,100,60,80,25,Clean,0,True,_Clean_,True

[variables]
%myProject%=%BaseDir%\Projects\myProject\script.project
%myScript%=%BaseDir%\Projects\myProject\myScript.script

[Clean]
Echo,"Eliminar myProject Examplo..."
If,EXISTDIR,%BaseDir%\Projects\myProject\,DirDelete,%BaseDir%\Projects\myProject\
System,LoadAll

[process]
If,Not,ExistFile,%myProject%,FileCreateBlank,%myProject%
If,Not,ExistFile,%myScript%,FileCreateBlank,%myScript%

// Proyecto
IniWrite,%myProject%,Main,Title,myProject
IniWrite,%myProject%,Main,Author,Homes32
IniWrite,%myProject%,Main,Description,"¡Un nuevo proyecto!"
IniWrite,%myProject%,Main,Version,1
IniWrite,%myProject%,Main,Level,5

TXTAddLine,%myProject%,"[Variables]",Append
TXTAddLine,%myProject%,"",Append
TXTAddLine,%myProject%,"[Process]",Append
TXTAddLine,%myProject%,"[Interface]",Append
TXTAddLine,%myProject%,"",Append

// Script
IniWrite,%myScript%,Main,Title,myScript
IniWrite,%myScript%,Main,Author,Homes32
IniWrite,%myScript%,Main,Description,"¡Un nuevo Script!"
IniWrite,%myScript%,Main,Version,1
IniWrite,%myScript%,Main,Level,5
IniWrite,%myScript%,Main,Selected,False

TXTAddLine,%myScript%,"[Variables]",Append
TXTAddLine,%myScript%,"",Append
TXTAddLine,%myScript%,"[Process]",Append
TXTAddLine,%myScript%,"[Interface]",Append
TXTAddLine,%myScript%,"",Append

// Ahora necesitamos llamar al siguiente comando para que nuestro nuevo proyecto y script se muestren en la ventana principal.
System,LoadAll
```
