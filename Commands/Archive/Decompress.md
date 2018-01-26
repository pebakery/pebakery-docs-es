# Decompress

Extrae archivos de un archivo.

**¡Advertencia!** Este comando es inestable y puede cambiarse en una versión futura.

## Sintaxis

```pebakery
Decompress,<FileName>,<DestDir>,[Encoding]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | Ruta completa del archivo para extraer. |
| DestDir | Ruta completa al directorio donde se extraerá el archivo |
| Encoding | **(Opcional)** Codificación utilizada en el nombre del archivo. Los tipos admitidos son: `UTF8`, `UTF16`, `UTF16BE`, `ANSI`. |

## Formatos de archivo admitidos

Si el argumento `Encoding` no está especificado, *SevenZipExtractor* se usará para lograr el máximo rendimiento. De otra manera *SharpCompress* se utilizará.

| Modo | Formatos de archivo admitidos |
| --- | --- |
| Native (7z.dll) | 7z, APM, AR, ARJ, BZIP2, CAB, CHM, CPIO, CramFS, DEB, DMG, EXT, FAT, GPT, GZIP, HFS, IHEX, ISO, LZH, LZMA, MBR, MSI, NSIS, NTFS, QCOW2, RAR, RPM, SquashFS, TAR, UDF, UEFI, VDI, VHD, VMDK, WIM, XAR, XZ, Z, ZIP |
| Managed (SharpCompress.dll) | 7z, BZIP2, CAB, GZIP, RAR (RAR5 **no** es soportado), TAR, ZIP |

## Observaciones

Este comando depende de [SharpCompress](https://github.com/adamhathcock/sharpcompress) (Managed) o [SevenZipExtractor](https://github.com/adoconnection/SevenZipExtractor) y `7z.dll` (Native).

## Relacionado

[Compress](./Compress.md)

## Ejemplo

```pebakery
// Setting.7z será extraído a %DestDir%.
Decompress,%SrcDir%\Setting.7z,%DestDir%
