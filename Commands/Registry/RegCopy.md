# RegCopy

Copia todas las subclaves y valores de una clave de registro a otra.

Este comando tiene el mismo efecto que ejecutar `REG.exe COPY <SrcRegPath> <DestRegPath> /S /F` desde Windows.

## Sintaxis

```pebakery
RegCopy,<SrcKey>,<SrcKeyPath>,<DestKey>,<DestKeyPath>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcKey | La clave raíz de origen debe ser una de las siguientes: |
|| HKEY_LOCAL_MACHINE or HKLM |
|| HKEY_CURRENT_CONFIG or HKCC |
|| HKEY_CLASSES_ROOT or HKCR |
|| HKEY_CURRENT_USER or HKCU |
|| HKEY_USERS or HKU |
| SrcKeyPath | La ruta completa de la clave de registro para copiar. |
| DestKey | La clave raíz de destino debe ser una de las siguientes: |
|| HKEY_LOCAL_MACHINE or HKLM |
|| HKEY_CURRENT_CONFIG or HKCC |
|| HKEY_CLASSES_ROOT or HKCR |
|| HKEY_CURRENT_USER or HKCU |
|| HKEY_USERS or HKU |
| DestKeyPath | La ruta completa de la clave de destino. Los valores existentes serán sobrescritos. |

## Observaciones

`RegCopy` copiará desde su registro ** local **, por lo que debe asegurarse de que `SrcKeyPath` y/o `DestKeyPath` apuntan a su sección de PE montada si tiene la intención de copiar hacia/desde el registro PE.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md)

## Ejemplos

### Ejemplo 1

```pebakery
RegHiveLoad,Tmp_Ins_System,InstallSrc\windows\system32\config\SYSTEM
RegHiveLoad,Tmp_System,%RegSystem%
// Copy HKLM\System\ControlSet001\Services\Tcpip y todas las subclaves/valores del registro Install.wim al registro Boot.wim
RegCopy,HKLM,Tmp_Ins_System\ControlSet001\Services\Tcpip,HKLM,Tmp_System\ControlSet001\Services\Tcpip
RegHiveUnLoad,Tmp_System
RegHiveUnLoad,Tmp_Ins_System
```
