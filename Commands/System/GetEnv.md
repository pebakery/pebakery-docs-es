# System,GetEnv

Obtiene el valor de la variable de entorno del sistema operativo del host.

## Sintaxis

```pebakery
System,GetEnv,<EnvVar>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| EnvVar | El nombre de la variable de entorno para leer. **NO** incluye los signos circundantes `%`. Ejemplos comunes son `SystemDrive SystemRoot TEMP WINDIR` |
| %DestVar% | La variable donde se almacenará el valor de la variable de entorno. |

## Observaciones

Si `EnvVar` no existe `%DestVar%` contendrá un valor en blanco.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=GetEnv Example
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
