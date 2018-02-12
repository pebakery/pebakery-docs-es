# System,GetEnv

Obtiene el valor de la variable de entorno del sistema operativo del host.

## Sintaxis

```pebakery
System,GetEnv,<EnvVar>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| EnvVar | El nombre de la variable de entorno para leer. **NO** incluye los signos circundantes `%`. |
| %DestVar% | La variable donde se almacenará el valor de la variable de entorno. |

### Variables de entorno comunes

La siguiente es una lista de variables de entorno utilizadas comúnmente definidas en las versiones modernas de Microsoft Windows. Se puede obtener una lista completa de las variables de entorno en uso en su sistema emitiendo el comando `set` desde el símbolo del sistema de Windows.

| Variable de entorno | Descripción |
| --- | --- |
| APPDATA | La ruta a la carpeta Application Data de los usuarios locales. Generalmente `C:\Users\%username&\AppData\Roaming`. |
| CommonProgramFiles | La ruta al directorio Common Files. Generalmente `C:\Program Files\Common Files`. |
| CommonProgramFiles(x86) | En los sistemas operativos de 64 bits, esta es la ruta a la carpeta que contiene 32 bits Common Files. Usually `C:\Program Files (x86)\Common Files`. |
| COMPUTERNAME | El nombre de la computadora. |
| NUMBER_OF_PROCESSORS | La cantidad de núcleos de procesador en su CPU. |
| OS | Familia del sistema operativo. Ej. `Windows_NT`. |
| PROCESSOR_ARCHITECTURE | Arquitectura del CPU. Ex. `x86` or `AMD64`. |
| ProgramData | La ruta a la carpeta que contiene Shared Application Data. Usually `C:\ProgramData`. |
| ProgramFiles | La ruta a la carpeta que contiene las aplicaciones instaladas. Usually `C:\Program Files`. |
| ProgramFiles(x86) | En los sistemas operativos de 64 bits, esta es la ruta a la carpeta que contiene las aplicaciones de 32 bits instaladas. Generalmente `C:\Program Files (x86)`. |
| SystemDrive | La letra de la unidad donde está instalado Windows. Generalmente `C:` |
| SystemRoot | El directorio donde está instalado Windows. Generalmente `C:\Windows`. |
| TEMP | The local user's temp directory. Usually `C:\Users\%username%\AppData\Local\Temp`. |
| USERNAME | El nombre del usuario actual. |
| USERPROFILE | El directorio de inicio del usuario actual. Generalmente `C:\Users\%username%`. |
| windir | El directorio de Windows. Generalmente `C:\Windows`. |

## Observaciones

Si `EnvVar` no existe `%DestVar%` contendrá un valor en blanco.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=GetEnv Ejemplo
Description=Mostrar el uso del comando System,GetEnv.
Level=5
Version=1
Author=Homes32

[variables]

[process]
System,GetEnv,TEMP,%hostTemp%
System,GetEnv,PROCESSOR_ARCHITECTURE,%hostARCH%
Message,"#$pTEMP#$p = %hostTemp%#$x#$pPROCESSOR_ARCHITECTURE#$p = %hostARCH%",INFORMATION
```
