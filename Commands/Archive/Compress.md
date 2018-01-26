# Compress

Comprime un archivo o directorio en el archivo.

**¡Advertencia!** Este comando es inestable y puede cambiarse en una versión futura.

## Sintaxis

```pebakery
Compress,<Format>,<SrcPath>,<DestArchive>,[CompressLevel],[Encoding]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Format | Formato de archivo. Solo `Zip` es compatible en este momento. |
| SrcPath | Ruta completa del archivo/directorio para comprimir. |
| DestArchive | Ruta completa donde se creará el archivo. |
| CompressLevel | **(Opcional)** Esto afecta el tamaño de archivo y el tiempo de compresión. Compresión soportada: `Store`, `Fastest`, `Normal`, `Best`. **por defecto** is `Normal`. |
| Encoding | **(Opcional)** Codificación para ser utilizado en nombre de archivo. Opciones compatibles: `UTF8`, `UTF16`, `UTF16BE`, `ANSI`. **Default** is `UTF8`. |

`CompressLevel` y `Encoding` se puede usar de forma independiente.

## Observaciones

Este comando depende de [SharpCompress](https://github.com/adamhathcock/sharpcompress)

## Relacionado

[Decompress](./Decompress.md)

## Ejemplos

```pebakery
// PEBakery.ini se comprimirá en Setting.zip.
Compress,Zip,%BaseDir%\PEBakery.ini,%BaseDir%\Setting.zip
```

```pebakery
// PEBakery.ini se almacenará en Setting.zip.
Compress,Zip,%BaseDir%\PEBakery.ini,%BaseDir%\Setting.zip,Store
```
