# CopyOrExpand

Copiar o extraer archivos de un archivo de gabinete de Microsoft (*.CAB).

Si el archivo de origen existe, se copiará a `DestPath`. De lo contrario, PEBakery buscará un gabinete comprimido (*.ex_, *.dl_) y extraerá el archivo.

## Sintaxis

```pebakery
CopyOrExpand,<SrcFile>,<DestPath>,[PRESERVE],[NOWARN]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcFile | La ruta completa del archivo para copiar. Los comodines (*,?) Se pueden usar para copiar y expandir archivos múltiples. |
| DestPath | La ruta completa donde se copiará o extraerá el archivo. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| PRESERVE | No sobrescribir los archivos existentes. |
| NOWARN | No registrar una advertencia de sobrescritura si se sobrescribe un archivo. |

Flags se puede especificar en cualquier orden.

## Observaciones

PEBakery busca archivos en el siguiente orden:

1. Copy
1. Expand

Este comando se usa principalmente para extraer archivos comprimidos EXE (\ *. EX \ _) y DLL (\ *. DL \ _) de fuentes NT5 (WindowsXP).

Depende de `cabinet.dll`. (Incluido con Windows)

## Relacionado

[Expand](./Expand.md)

## Ejemplos

```pebakery
// Si EXPLORER.EXE existe, se copiará a %DestDir%.
// Si EXPLORER.EXE no existe, EXPLORER.EXE se extraerá de EXPLORER.EX_.
CppyOrExpand,%SrcDir%\EXPLORER.EXE,%DestDir%
```

```pebakery
// Si EXPLORER.EXE existe, se copiará a %DestDir% con el nuevo nombre NEWEXP.EXE.
// Si EXPLORER.EXE no existe, EXPLORER.EXE se extraerá de EXPLORER.EX_ con el nuevo nombre NEWEXP.EXE.
CppyOrExpand,%SrcDir%\EXPLORER.EXE,%DestDir%\NEWEXP.EXE
```
