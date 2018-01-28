# RegDelete

Elimina una clave o valor del registro.

## Sintaxis

```pebakery
RegDelete,<HKEY>,<KeyPath>[,ValueName]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| HKEY | La clave raíz debe ser una de las siguientes: |
|| HKEY_LOCAL_MACHINE or HKLM |
|| HKEY_CURRENT_CONFIG or HKCC |
|| HKEY_CLASSES_ROOT or HKCR |
|| HKEY_CURRENT_USER or HKCU |
|| HKEY_USERS or HKU |
| KeyPath | La ruta completa de la clave de registro. |
| ValueName | **[Opcional]** Si se especifica solo el valor será eliminado. |

## Observaciones

Ninguna.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

Eliminar un valor de registro.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
RegDelete,HKLM,Tmp_System\ControlSet001\Services\VgaSave\Device0,DefaultSettings.XResolution
RegHiveUnLoad,Tmp_System
```

### Ejemplo 2

Eliminar una clave de registro.

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%
RegDelete,HKLM,Tmp_System\ControlSet001\Services\VgaSave\Device0
RegHiveUnLoad,Tmp_System
```
