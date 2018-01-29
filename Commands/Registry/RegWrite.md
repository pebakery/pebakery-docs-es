# RegWrite

Crear o modificar una clave o valor en el registro.

## Sintaxis

```pebakery
RegWrite,<HKey>,<ValueType>,<KeyPath>,<ValueName>,<Value>,[NOWARN]
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
| ValueType   | El tipo de datos que contiene el valor. Los tipos admitidos son: |
||0x0 - (REG_NONE) Clave vacía |
||0x1 - (REG_SZ) Cadena |
||0x2 - (REG_EXPAND_SZ) Cadena expandida: ampliará cualquier valor variable contenido dentro de %%. (por ejemplo, %temp%) |
||0x3 - (REG_BINARY) Datos binarios: los datos se especifican en HEX, con cada byte especificado por grupos de dos dígitos que dividen cada valor con comas. |
||0x4 - (REG_DWORD) Entero de 32 bits |
||0x7 - (REG_MULTI_SZ) Múltiples cadenas separadas nulas |
||0x11 - (REG_QWORD) Entero de 64 bits |
| KeyPath | La ruta completa de la clave de registro. |
| ValueName | El nombre del valor. |
| Value | El valor para escribir.<br/>Los valores grandes se pueden ajustar para una lectura más fácil usando el carácter `\` para indicar que el valor continúa en la siguiente línea, similar al formato de archivo .reg. **Nota:** Si el `Valor` que debe escribirse es el caracter `\`, por ej. `RegWrite,HKLM,0x1,Tmp_System\Setup,OsLoaderPath,"\"` asegúrese de ajustarlo entre comillas dobles para que no se confunda con una continuación de línea.  |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| NOWARN | **(Opcional)** Suprimir los mensajes OverWrite en el registro si el `Valor` ya existe. |

## Observaciones

PEBakery no permite el uso de variables en `HKey` y` ValueType`.

Si necesita modificar el valor de un valor REG_MULTI_SZ ***existente***, considere usar el comando `RegMulti` para insertar y eliminar valores sin sobreescribir la lista de valores completa.

## Relacionado

[RegHiveLoad](./RegHiveLoad.md), [RegHiveUnload](./RegHiveUnload.md), [RegMulti](./RegMulti.md)

## Ejemplos

### Ejemplo 1

```pebakery
RegHiveLoad,Tmp_System,%RegSystem%

// Escribir un DWORD
RegWrite,HKLM,0x4,Tmp_System\ControlSet001\Services\VgaSave\Device0,DefaultSettings.XResolution,1024

// Escribir un valor BINARIO
RegWrite,HKLM,0x3,Tmp_System\ControlSet001\Control\Network\{4d36e975-e325-11ce-bfc1-08002be10318}\{12F2EEA2-EE86-4933-8C0B-346E5E57F332},InstallTimeStamp,d9,07,07,00,02,00,0e,00,04,00,31,00,20,00,fd,00

// Escribir un valor Multi-String (Multi-Cadena)
RegWrite,HKLM,0x7,Tmp_System\ControlSet001\Control\Network,FilterClasses,ms_firewall_upper,scheduler,encryption,compression,vpn,loadbalance,failover,diagnostic,custom

// Escribe un valor BINARIO grande usando múltiples líneas para facilitar la lectura
RegWrite,HKLM,0x3,Tmp_Default\Software\Microsoft\Windows\CurrentVersion\Explorer\Streams\Desktop,TaskbarWinXP,0c,\
00,00,00,08,00,00,00,02,00,00,00,00,00,00,00,b0,e2,2b,d8,64,57,d0,11,a9,6e,00,c0,4f,d7,05,a2,22,00,1c,00,0a,10,00,00,01,00,00,00,01,00,00,00,00,00,00,\
00,00,00,00,00,00,00,00,00,4c,00,00,00,01,14,02,00,00,00,00,00,c0,00,00,00,00,00,00,46,81,01,00,00,11,00,00,00,64,54,7a,06,bd,b2,cb,01,ea,2f,16,74,ca,\
b8,cb,01,ea,2f,16,74,ca,b8,cb,01,00,10,00,00,00,00,00,00,01,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,04,02,14,00,1f,44,47,1a,03,59,72,3f,a7,44,89,\
c5,55,95,fe,6b,30,ee,7e,00,74,00,1c,00,43,46,53,46,16,00,31,00,00,00,00,00,2d,3e,57,07,12,20,41,70,70,44,61,74,61,00,00,00,74,1a,59,5e,96,df,d3,48,8d,\
67,17,33,bc,ee,28,ba,c5,cd,fa,df,9f,67,56,41,89,47,c5,c7,6b,c0,b6,7f,3c,00,08,00,04,00,ef,be,2d,3e,56,07,2d,3e,57,07,2a,00,00,00,e4,01,00,00,00,00,02,\
00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,41,00,70,00,70,00,44,00,61,00,74,00,61,00,00,00,42,00,52,00,31,00,00,00,00,00,32,3e,d3,7c,10,20,52,6f,61,\
6d,69,6e,67,00,3c,00,08,00,04,00,ef,be,2d,3e,56,07,32,3e,d3,7c,2a,00,00,00,e5,01,00,00,00,00,02,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,52,00,6f,\
00,61,00,6d,00,69,00,6e,00,67,00,00,00,16,00,58,00,31,00,00,00,00,00,32,3e,da,90,14,20,4d,49,43,52,4f,53,7e,31,00,00,40,00,08,00,04,00,ef,be,2d,3e,56,\
07,32,3e,da,90,2a,00,00,00,e6,01,00,00,00,00,02,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,4d,00,69,00,63,00,72,00,6f,00,73,00,6f,00,66,00,74,00,00,\
00,18,00,68,00,31,00,00,00,00,00,ee,3a,85,1a,10,00,49,4e,54,45,52,4e,7e,31,00,00,50,00,08,00,04,00,ef,be,2d,3e,56,07,2d,3e,56,07,2a,00,00,00,f4,01,00,\
00,00,00,02,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,49,00,6e,00,74,00,65,00,72,00,6e,00,65,00,74,00,20,00,45,00,78,00,70,00,6c,00,6f,00,72,00,65,\
00,72,00,00,00,18,00,5e,00,31,00,00,00,00,00,34,3e,40,8e,11,00,51,55,49,43,4b,4c,7e,31,00,00,46,00,08,00,04,00,ef,be,2d,3e,56,07,34,3e,40,8e,2a,00,00,\
00,f5,01,00,00,00,00,02,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,51,00,75,00,69,00,63,00,6b,00,20,00,4c,00,61,00,75,00,6e,00,63,00,68,00,00,00,18,\
00,00,00,60,00,00,00,03,00,00,a0,58,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,52,cb,74,30,40,c1,22,45,81,05,c7,54,dd,94,b1,\
ad,9f,09,e0,19,75,24,e0,11,89,f4,00,50,56,c0,00,08,52,cb,74,30,40,c1,22,45,81,05,c7,54,dd,94,b1,ad,9f,09,e0,19,75,24,e0,11,89,f4,00,50,56,c0,00,08,00,\
00,00,00,8d,00,00,00,40,07,00,00,00,00,00,00,1e,00,00,00,00,00,00,00,00,00,00,00,1e,00,00,00,00,00,00,00,01,00,00,00,01,00,00,00,aa,4f,28,68,48,6a,d0,\
11,8c,78,00,c0,4f,d9,18,b4,a9,04,00,00,40,0d,00,00,00,00,00,00,1e,00,00,00,00,00,00,00,00,00,00,00,1e,00,00,00,00,00,00,00,01,00,00,00

RegHiveUnLoad,Tmp_System
```

### Ejemplo 2

En los casos en que una clave de registro contiene un carácter `#` seguido de números, PEBakery puede interpretar erróneamente esto como un parámetro pasado de un comando `Ejecutar`, incluso cuando esto no sea intencionado. El siguiente ejemplo demuestra cuándo puede ocurrir este comportamiento y una solución que se puede utilizar para garantizar el resultado deseado.

```pebakery

[Variables]
%hash%=#

[Process]
Run,%ScriptFile%,Test

[Test]
RegHiveLoad,Tmp_System,%RegSystem%

// Resultado previsto: HKLM\Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394#609E&10483\Service
// Debido a que #609 se interpreta como un parámetro
// Resultado actual: HKLM\Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394E&10483\Service
RegWrite,HKLM,0x1,Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394%hash%609E&10483,Service,sbp2port

// Solución alternativa utiliza una variable para escribir el carácter # en la ruta de registro
// Resultado: HKLM\Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394#609E&10483\Service
RegWrite,HKLM,0x1,Tmp_System\ControlSet001\Control\CriticalDeviceDatabase\1394%hash%609E&10483,Service,sbp2port

RegHiveUnLoad,Tmp_System
```
