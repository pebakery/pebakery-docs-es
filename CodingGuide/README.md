# Guía de codificación

## Comprobación de sintaxis

PEBakery suporta comprobación de sintaxis.

### Comprobando declaraciones o sección

Copiar códigos en `Comprobador de sintaxis` (Syntax Checker) proporcionado en `Utilidad` (Utility).

### Comprobación de Script

Asegúrese de que su script es visible en el árbol del proyecto. Abrir la interface de script, y haz clic en el botón de pregunta cerca del título del script.

Si `Comprobación de errores de sintaxis automática` (Auto Syntax Check Error) está habilitado, el ícono del botón y su color reportan si existe error.

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
- WimExtract
- WimPathAdd, WimPathDelete, WimPathRename

Cuando los comandos están optimizados, la lectura/escritura de múltiples archivos se compacta en una sola lectura/escritura, mejorando el desempeño.

La optimización ocurre solo si **los mismos comandos** manipulan **el mismo archivo** son **colocado en una fila**.

Asegurese de que su código puede optimizarse para el rendimiento.

### Ejemplo de Comandos Optimizados

TXTAddLine escribe múltiples líneas en el mismo archivo `%ProjectTemp%\Korean_IME_Reference.txt`. Ellos son optimizados a un solo comando TXTAddLineOp, escribiendo el texto completo a la vez.

```pebakery
Set,%w%,%ProjectTemp%\Korean_IME_Reference.txt
FileCreateBlank,%w%
TXTAddLine,%w%,"<Korean IME Plugin - Reference>",Append
TXTAddLine,%w%,,Append
TXTAddLine,%w%," [TechNet] Add Input Method Editor (IME) to Windows PE 3.0",Append
TXTAddLine,%w%,"  - https://technet.microsoft.com/en-us/library/dd744589%28v=ws.10%29.aspx",Append
TXTAddLine,%w%,,Append
TXTAddLine,%w%," [Blog] Add Hangul IME support on Windows PE 4.0",Append
TXTAddLine,%w%,"  - http://cappleblog.co.kr/549",Append
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

TXTDelLine y TXTAddLine son comandos diferentes.

```pebakery
TXTDelLine,%target_sys%\autorun.cmd,exit
TXTAddLine,%target_sys%\autorun.cmd,"hiderun.exe IMEReg.cmd",Append
```

Multiple TXTAddLine están escribiendo en el mismo archivo, pero no se colocan en una fila.

```pebakery
TXTAddLine,%DestDir%\hello.txt,"Hello World!",Append
Echo,"Hello World!"
TXTAddLine,%DestDir%\hello.txt,"Have a nice day.",Append
```

Estos WimExtract manejan el mismo archivo, pero tienen diferentes flags.

``` pebakery
WimExtract,%WimDir%\LZX.wim,1,Z.txt,%DestDir%,CHECK
WimExtract,%WimDir%\LZX.wim,1,A?.txt,%DestDir%,NOACL
```

### Posible problema con la optimización

Cuando la optimización está desactivada, un comando es independiente de los demás. Lo que significa que incluso si falla un comando, no afecta a otros comandos. Pero si los comandos están optimizados, sí afectan otros comandos.

Supongamos un archivo wim `LZX.wim` contiene estos archivos:

```pebakery
LZX.wim
|--- AZ.txt
|--- B.txt
|--- Z.txt
```

Segundo WimExtract intenta extraer un archivo que no existe, por lo que generará un error. Estos comandos se optimizan para un comando cuando se ejecutan, y el error arrojado por el segundo WimExtract hará que fallen todos los WimExtracts.

```pebakery
WimExtract,%WimDir%\LZX.wim,1,Z.txt,%DestDir%,CHECK
WimExtract,%WimDir%\LZX.wim,1,A.txt,%DestDir%,CHECK
WimExtract,%WimDir%\LZX.wim,1,B.txt,%DestDir%,CHECK
```
