# System,IsAdmin

Comprueba si PEBakery fue iniciado por una cuenta con privilegios de "Administrador".

## Sintaxis

```pebakery
System,IsAdmin,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| %DestVar% | La variable devolverá uno de los siguientes valores: |
|| True - PEBakery se inició con privilegios de "Administrador". |
|| False - PEBakery no se inició con privilegios de "Administrador". |

## Observaciones

Este comando se incluye por compatibilidad con Winbuilder 082. PEBakery siempre requiere privilegios de administrador para ejecutarse.

## Relacionado

## Examples

### Ejemplo 1

```pebakery
[main]
Title=IsAdmin Ejemplo
Description=Mostrar el uso del comando System,IsAdmin.
Level=5
Version=1
Author=Homes32

[variables]

[process]
System,IsAdmin,%isAdmin%
If,%isAdmin%,Equal,True,Message,"PEBakery se está ejecutando como administrador."
Else,Message,"PEBakery NO se está ejecutando como administrador."
```
