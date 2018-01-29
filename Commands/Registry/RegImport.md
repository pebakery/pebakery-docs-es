# RegImport

Importa el contenido de un archivo de registro (*.reg) a su sistema de registro local.

Este comando tiene el mismo efecto que ejecutar `REG.exe IMPORT <RegFile>` desde Windows y es ideal para importar una gran cantidad de entradas de registro preparadas en su construcción.

## Sintaxis

```pebakery
RegImport,<RegFile>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| RegFile | La ruta completa del archivo * .reg a importar. |

## Observaciones

No se registrarán mensajes de advertencia si existen los valores de registro.

**Advertencia:**
Debido a que `RegImport` importará el archivo *.reg en su registro **local**, debe asegurarse de que el archivo contenga la ruta correcta a su sección de registro del PE montada, o corre el riesgo de corromper su registro local.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

Supongamos que tenemos el siguiente archivo *myFile.reg* que queremos importar a nuestro Registro del PE. Tenga en cuenta que ya hemos modificado las claves de registro para apuntar a la ruta en la que montaremos la sección SISTEMA del PE.

```pebakery
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\Tmp_System\ControlSet001\Control\Network]
"FilterClasses"=hex(7):6d,00,73,00,5f,00,66,00,69,00,72,00,65,00,77,00,61,00,\
  6c,00,6c,00,5f,00,75,00,70,00,70,00,65,00,72,00,00,00,73,00,63,00,68,00,65,\
  00,64,00,75,00,6c,00,65,00,72,00,00,00,65,00,6e,00,63,00,72,00,79,00,70,00,\
  74,00,69,00,6f,00,6e,00,00,00,63,00,6f,00,6d,00,70,00,72,00,65,00,73,00,73,\
  00,69,00,6f,00,6e,00,00,00,76,00,70,00,6e,00,00,00,6c,00,6f,00,61,00,64,00,\
  62,00,61,00,6c,00,61,00,6e,00,63,00,65,00,00,00,66,00,61,00,69,00,6c,00,6f,\
  00,76,00,65,00,72,00,00,00,64,00,69,00,61,00,67,00,6e,00,6f,00,73,00,74,00,\
  69,00,63,00,00,00,63,00,75,00,73,00,74,00,6f,00,6d,00,00,00,00,00
"IscsiSupportedProtocols"="Ndisuio,rspndr,lltdio,RasPppoe,Tcpip,Tcpip6"
"MaxNumFilters"=dword:00000008
```

```pebakery
// Asegúrese de que RegHiveLoad,<KeyPath> coincida con la ruta en su archivo *.reg
// ¡O sobrescribirá el registro de su sistema local!
RegHiveLoad,Tmp_System,%RegSystem%
RegImport,c:\myFile.reg
RegHiveUnLoad,Tmp_System
```
