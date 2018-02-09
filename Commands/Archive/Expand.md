# Expand

Extrae archivos de un archivo de gabinete de Microsoft (*.CAB).

## Sintaxis

```pebakery
Expand,<CabFile>,<DestDir>,[FileName],[PRESERVE],[NOWARN]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| CabFile | La ruta completa del archivo contenedor para extraer. |
| DestDir | Directorio donde se extraerán los archivos. |
| FileName | **(Opcional)** Extraer solo este archivo específico. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| PRESERVE | **(Opcional)** No sobrescribir los archivos existentes cuando `Solo archivo` (`SingleFile`) es especificado. |
| NOWARN | **(Opcional)** No registrar una advertencia de sobrescritura si se sobrescribe un archivo al extraer un solo archivo. |

Flags se puede especificar en cualquier orden.

## Observaciones

Este comando se usa principalmente para extraer archivos comprimidos EXE (\ *. EX \ _) y DLL (\ *. DL \ _) de fuentes NT5 (WindowsXP).

Depende de `cabinet.dll`. (Incluido con Windows)

## Relacionado

[CopyOrExpand](./CopyOrExpand.md)

## Ejemplos

```pebakery
// ex1.cab será descomprimido en %DestDir%.
Expand,%SrcDir%\ex1.cab,%DestDir%
```

```pebakery
// EXPLORER.EXE será extraído de EXPLORER.EX_
Expand,%Source_Win%\EXPLORER.EX_,%Target_Win%
```

```pebakery
// Extraer solo BatteryLine.exe de multi.cab, sobrescriba con una advertencia si el archivo existe.
Expand,%SrcDir%\multi.cab,%DestDir%,BatteryLine.exe
```

```pebakery
// Extraer solo BatteryLine.exe de multicab, no sobrescribir si el archivo existe.
Expand,%SrcDir%\multi.cab,%DestDir%,BatteryLine.exe,PRESERVE
```
