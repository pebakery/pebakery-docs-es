# Guía de codificación

## Comprobación de sintaxis

PEBakery suporta comprobación de sintaxis.

### Comprobando declaraciones o sección

Copiar códigos en `Comprobador de sintaxis` (Syntax Checker) proporcionado en `Utilidad` (Utility).

### Comprobación de Script

Asegúrese de que su script es visible en el árbol del proyecto. Abrir la interface de script, y haga clic en el botón de verificación a la derecha.

Si `Comprobación de errores de sintaxis automática` (Auto Syntax Check Error) está habilitado, el color del botón reporta si existe error.

## Optimización

PEBakery optimiza automáticamente algunos comandos relacionados con la manipulación de texto.

- TXTAddLine
- TXTReplace
- TXTDelLine
- INIRead
- INIWrite
- INIDelete
- INIReadSection
- INIAddSection
- INIDeleteSection
- INIWriteTextLine
- Visible

Cuando los comandos están optimizados, la lectura/escritura de múltiples archivos se compacta en una sola lectura/escritura, mejorando el desempeño.

La optimización ocurre solo si **los mismos comandos** manipulan **el mismo archivo** son **colocado en una fila**.

Asegurese de que su código puede optimizarse para el rendimiento.

### Ejemplo de Comandos Optimizados

TXTAddLine escribe múltiples líneas en el mismo archivo `%ProjectTemp%\Korean_IME_TheOven.txt`. Ellos son optimizados a un solo comando TXTAddLineOp, escribiendo el texto completo a la vez.

```pebakery
Set,%w%,%ProjectTemp%\Korean_IME_TheOven.txt
FileCreateBlank,%w%
TXTAddLine,%w%,"<Korean IME Plugin - TheOven Topics>",Append
TXTAddLine,%w%,,Append
TXTAddLine,%w%," [TheOven] Korean IME for Win8.1SE topic",Append
TXTAddLine,%w%,"  - http://TheOven.org/index.php?topic=825",Append
TXTAddLine,%w%,,Append
TXTAddLine,%w%," [TheOven] Korean IME for Win10PESE topic",Append
TXTAddLine,%w%,"  - http://TheOven.org/index.php?topic=1440",Append
Call,StartDoc,%w%
```

El comando visible sólo afecta al script mismo.

```pebakery
Visible,%pBevel3%,True,PERMANENT
Visible,%pCheckBox4%,True,PERMANENT
Visible,%pCheckBox5%,True,PERMANENT
Visible,%pCheckBox6%,True,PERMANENT
Visible,%pCheckBox7%,True,PERMANENT
```

### Ejemplo de comandos no optimizados

TXTDelLine y TXTAddLine es un comando diferente.

```pebakery
TXTDelLine,%target_sys%\autorun.cmd,exit
TXTAddLine,%target_sys%\autorun.cmd,"hiderun.exe IMEReg.cmd",Append
```

Multiple TXTAddLine está escribiendo en el mismo archivo, pero no se colocan en una fila.

```pebakery
TXTAddLine,%DestDir%\hello.txt,"Hello World!",Append
Echo,"Hello World!"
TXTAddLine,%DestDir%\hello.txt,"Have a nice day.",Append
```

### Posible problema con la optimización

Si los comandos optimizados fallan, todos los datos no pueden ser procesados correctamente.

Así que asegúrese de que sus códigos eviten excepciones.
