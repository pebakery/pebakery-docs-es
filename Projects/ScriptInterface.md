# Sección de Script [Interface] (Interfaz)

La sección Interfaz contiene una o más líneas que definen los controles de la interfaz gráfica de usuario principal de un script.

Consulte los `Controles GUI` para obtener una lista completa de los controles que se pueden usar.

## Sintaxis

Las secciones de interfaz usan el formato estilo .INI `Key=Value` `(Clave=Valor)` y deben contener solo las definiciones compatibles `Control` y `Comments`.

## Observaciones

Un script puede tener múltiples interfaces y es posible alternar entre ellas, cambiando el valor de la tecla `Interface` situada en la sección del script `[Main]'.

## Relacionado

[GUI Controls](/GUIControls/README.md), [Project Main](./ProjectMain.md), [Project Process](./ProjectProcess.md), [Project Variables](./ProjectVariables.md), [Script Main](./ScriptMain.md), [Script Process](./ScriptProcess), [Script Variables](./ScriptVariables.md), [System,RefreshInterface](/Commands/System/RefreshInterface.md)

## Ejemplos

### Ejemplo 1

Una sección de interfaz típica.

```pebakery
[Interface]
pBevel_Shortcut=Shortcuts,1,12,1,25,188,116
CB_StartMenu="Start menu",1,3,11,72,122,18,True
CB_QuickLaunch=Quicklaunch,1,3,11,52,122,18,False
CB_Desktop=Desktop,1,3,11,35,120,15,False
SM_Folder="Start menu folder (. for root):",1,0,12,109,168,21,.
LBL_Shortcuts=Shortcuts,1,1,4,6,75,20,8,Bold
```

### Ejemplo 2

Este ejemplo demuestra cómo puede alternar entre múltiples secciones de interfaz dentro de un script.

```pebakery
[main]
Title=RefreshInterface Ejemplo
Description=Mostrar el uso del comando System,RefreshInterface usando múltiples páginas de interfaz.
Level=5
Version=1
Author=Homes32
Interface=Interface

[variables]

[process]

[ShowAdvanced]
// Mostrar la interfaz avanzada
IniWrite,%ScriptFile%,Main,Interface,Interface-Advanced
// Necesitamos refrescar o no veremos la nueva interfaz
System,REFRESHINTERFACE

[ShowMain]
// Mostrar la interfaz principal
IniWrite,%ScriptFile%,Main,Interface,Interface
// Necesitamos refrescar o no veremos la nueva interfaz
System,REFRESHINTERFACE

[Interface]
pBevel_Shortcut=pBevel1,1,12,1,25,188,116
CB_StartMenu="Start menu",1,3,11,72,122,18,True
CB_QuickLaunch=Quicklaunch,1,3,11,52,122,18,False
CB_Desktop=Desktop,1,3,11,35,120,15,False
LBL_Shortcuts=Shortcuts,1,1,4,6,75,20,8,Bold
SM_Folder="Start menu folder (. for root):",1,0,12,109,168,21,.
BTN_AdvancedOpts="Advanced Options",1,8,225,25,120,25,ShowAdvanced,0,True,_ShowAdvanced_,True

[Interface-Advanced]
LBL_AdvOpts="Advanced Options ",1,1,1,1,330,20,10,Bold
BTN_Save=Save,1,8,451,11,80,25,ShowMain,0,True,_ShowMain_,True
BVL_CustCmd=pBevel2,1,12,1,47,530,130
CB_CustomCMD="Run custom commands",1,3,11,62,220,20,False
RunProg="Command to execute",1,0,21,102,370,21,%SystemRoot%\System32\MyProgram.exe
LBL_CustomCmds="Custom Commands",1,1,5,28,125,20,8,Bold
RunFlag=@SW_SHOW,1,4,406,102,115,21,@SW_SHOW,@SW_HIDE,@SW_MINIMIZE,@SW_MAXIMIZE
RunParm=Parameters,1,0,21,147,370,21,
LBL_WinState="Window State",1,1,406,85,115,18,8,Normal
```
