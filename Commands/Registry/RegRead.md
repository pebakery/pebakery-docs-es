# RegRead

Lee un valor del registro.

## Sintaxis

```pebakery
RegRead,<HKey>,<KeyPath>,<ValueName>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| HKEY | La clave raíz debe ser una de las siguientes: |
|| HKEY_LOCAL_MACHINE o HKLM |
|| HKEY_CURRENT_CONFIG o HKCC |
|| HKEY_CLASSES_ROOT o HKCR |
|| HKEY_CURRENT_USER o HKCU |
|| HKEY_USERS o HKU |
| KeyPath | La ruta completa de la clave de registro. |
| ValueName | El nombre del valor. |
| DestVar | La %Variable% donde se almacenará el valor. |

## Observaciones

Si la clave de registro no existe, la operación fallará.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
RegRead,HKLM,Tmp_System\ControlSet001\Services\VgaSave\Device0,DefaultSettings.XResolution,%myXresolution%
Echo, %myXresolution%
RegHiveUnLoad,Tmp_System
```
