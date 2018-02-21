# RegExport

Exporta los contenidos de una clave de registro a un archivo *.reg.

Este comando tiene el mismo efecto que ejecutar `REG.exe EXPORT <RegPath> /Y` desde Windows.

## Sintaxis

```pebakery
RegExport,<HKey>,<KeyPath>,<RegFile>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| HKEY | The root key must be one of the following: |
|| HKEY_LOCAL_MACHINE or HKLM |
|| HKEY_CURRENT_CONFIG or HKCC |
|| HKEY_CLASSES_ROOT or HKCR |
|| HKEY_CURRENT_USER or HKCU |
|| HKEY_USERS or HKU |
| KeyPath | La ruta completa de la clave de registro a exportar. |
| RegFile | La ruta completa del archivo de destino *.reg. Si existe `RegFile`, se sobrescribirá. |

## Observaciones

`RegImport` exportará desde su registro **local**, por lo que debe asegurarse de que `KeyPath` apunte a su sección de registro del PE montada, si intenta exportar desde el registro del PE.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

```pebakery
// Asegurese que RegHiveLoad,<KeyPath> coincide con la ruta en su *.reg file
RegHiveLoad,Tmp_System,%RegSystem%
RegExport,HKEY_LOCAL_MACHINE,Tmp_System\ControlSet001\Control\Network,c:\myFile.reg
RegHiveUnLoad,Tmp_System
```
