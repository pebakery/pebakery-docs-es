# RegHiveLoad

Carga una sección de registro externo en su registro local.

## Sintaxis

```pebakery
RegHiveLoad,<KeyPath>,<HiveFile>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| KeyPath | La clave de registro donde se cargará `HiveFile`. |
| HiveFile | La ruta completa de la sección del Registro a cargar. |

## Observaciones

`RegHiveLoad` siempre cargará `KeyPath` bajo la clave registro local **HKLM**.

Una sección de registro montada con `RegHiveLoad` debe desmontarse con `RegHiveUnload`.

## Relacionado

[RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

La mayoría de los proyectos definirán un conjunto de variables que contienen rutas a las secciones del registro para facilitar el desarrollo.
Ejemplos comunes de esto son:

```pebakery
%RegSystem%=%TargetDir%\Windows\System32\config\System
%RegSoftware%=%TargetDir%\Windows\System32\config\Software
%RegDefault%=%TargetDir%\Windows\System32\config\Default
%RegComponents%=%TargetDir%\Windows\System32\config\Components
```

En este ejemplo, cargaremos la sección HKLM\Software definida por el proyecto en una clave llamada `Tmp_Software` en nuestro registro local.

```pebakery
// Cargar la sección Software (%RegSoftware% está definido por el proyecto)
RegHiveLoad,Tmp_Software,%RegSoftware%
Echo,"Escribiendo nuevos valores en la sección del registro.."
RegWrite,HKLM,0x1,"Tmp_Software\MyProgram","ProgramVersion","1.2.3"
// Descargue siempre cuando hayamos terminado.
RegHiveUnLoad,Tmp_Software
```
### Ejemplo 2

```pebakery
RegHiveLoad,Tmp_Setup,%targetdir%\I386\system32\setupreg.hiv
// Descargue siempre cuando hayamos terminado.
RegHiveUnLoad,Tmp_Setup
```
