# Comandos obsoletos

## Obsoletos de WinBuilder 082

### FileByteExtract

Ya no se usa.

### RegReadBin / RegWriteBin

Innecesario. PEBakery tiene soporte nativo para QWORDs y cadenas Unicode en RegRead y RegWrite.

### ExtractAllFilesIfNotExist

Ya no se usa Se puede lograr a través de otros métodos.

### ExtractAndRun

Debido a las limitaciones del comando Winbuilder original, esto se puede lograr mejor a través de una macro.

### StrFormat,CharToOEM / OEMToChar

DOS charset ya no se usa.

### System,Comp80

PEBakery es la nueva implementación de WinBuilder 082, no hay espacio para WinBuilder 080.

### System,FileRedirect / RegRedirect

PEBakery se puede compilar en Cualquier CPU / x64, se puede ejecutar sin WOW64.

### System,IsTerminal

Ya no se usa.

### System,Log

Ya no se usa.

### System,SplitParameters

Ya no se usa, PEBakery siempre dividirá los parámetros.

### If,License

Ya no se usa.

## Comandos que estarán en desuso

### ExtractAndRun

Debido a las limitaciones del comando original de Winbuilder, esto se implementa mejor como una macro utilizando Extract estándar y ShellExecuteDelete

### WebGetIfNotExist

Este comando está roto en WB082, y es mejor implementar esto como macro.

### StrFormat,ShortPath / LongPath

El éxito de la conversión a ruta corta depende del valor de registro `HKLM\System\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreation`.

Por lo tanto, no se puede garantizar que estos comandos funcionen correctamente en todos los sistemas.

### System,HasUAC

Actualmente PEBakery siempre devuelve `True` a este comando.

El Control de cuentas de usuario (UAC) está habilitado de forma predeterminada en todas las versiones compatibles de Windows, lo que hace que este comando sea en gran medida innecesario. Además, muchos usuarios no son conscientes de los peligros de deshabilitar el UAC, por lo tanto, es mejor diseñar su proyecto para trabajar en sistemas habilitados para UAC en lugar de alentar a los usuarios a deshabilitar las funciones de seguridad para construir un proyecto.

### System,RebuildVars

Mientras que el manual WB082 afirma que este comando actualizará las variables para usar un valor más nuevo, simplemente borrará las variables en WB082 en realidad.

Actualmente, PEBakery restablece las variables a las variables de script predeterminadas.

### GetParam / PackParam

Esos comandos están totalmente rotos en WB082, por lo que no se usó.

PEBakery admite un número infinito de parámetros de sección, por lo que estos comandos ya no son necesarios.
