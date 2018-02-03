# System,GetFreeDrive

Devuelve la letra de unidad libre más alta disponible, generalmente la unidad "Z:".

## Sintaxis

```pebakery
System,GetFreeDrive,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| %DestVar% | La variable donde se almacenará la letra de la unidad. |

## Observaciones

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=GetFreeDrive Ejemplo
Description=Mostrar el uso del comando System,GetFreeDrive.
Level=5
Version=1
Author=Homes32

[variables]

[process]
System,GetFreeDrive,%driveLetter%
Message,"La última letra de unidad disponible es: %driveLetter%"
```
