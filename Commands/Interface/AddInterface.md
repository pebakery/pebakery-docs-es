# AddInterface

Carga variables de otra sección de interfaz en el alcance local.

## Sintaxis

```pebakery
AddInterface,<ScriptFile>,<Interface>,<Prefix>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ScriptFile | La ruta completa del script que contiene la interfaz. **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual.|
| Interface | El nombre de la sección que contiene la interfaz que desea leer. |
| Prefix |  Prefijo para las variables de interfaz. Los prefijos lo protegen en caso de que la interfaz que está cargando tenga los mismos nombres de componente que la sección principal [Interfaz]. Las variables se cargan como `%<prefix>_<componentName>%`. |

## Observaciones

El comando `AddInterface` es necesario para leer todos los componentes en su script en el caso de que haga uso de múltiples "páginas" de interfaz. También puede usar `AddInterface` para acceder a los valores de los componentes en otro script, siempre que sepa los nombres de los componentes.

Siempre que sus nombres de control sean únicos o use un `Prefix`, puede cargar tantas interfaces a la vez como necesite.

## Relacionado

[Script Interface](/Projects/ScriptInterface.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=AddInterface Ejemplo
Description=Mostrar el uso del comando AddInterface usando múltiples páginas de interfaz.
Level=5
Version=1
Author=Homes32
Interface=Interface

[variables]

[process]

// Echo no devolverá el valor del cuadro de texto %RunProg%
// porque los componentes en [Interface-Advanced] no están dentro del alcance.
Message,"The value of text box RunProg is: %RunProg%"

// Agregue nuestra interfaz avanzada. Como sabemos que no tenemos
// nombres de componentes duplicados vamos a especificar un prefijo en blanco.
AddInterface,%ScriptFile%,Interface-Advanced,""

// Ahora podemos leer el valor del cuadro de texto RunProg
Message,"The value of text box RunProg is: %RunProg%"

[ShowAdvanced]
// Mostrar la interfaz avanzada
IniWrite,%ScriptFile%,Main,Interface,Interface-Advanced
System,REFRESHINTERFACE

[ShowMain]
// Mostrar la interfaz principal
IniWrite,%ScriptFile%,Main,Interface,Interface
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
