# Niveles de scripts

Los niveles son utilizados por PEBakery para determinar la agrupación correcta y la secuencia en la que se procesarán los scripts.

## Orden de procesamiento

PEBakery utilizará las siguientes propiedades para determinar el orden de procesamiento de un script:

1. Script Level (Nivel del script)
1. Folder Name (Nombre de la carpeta)
1. File Name (Nombre del archivo)

### Niveles

Hay 10 niveles definidos por PEBakery. El proceso comienza en el nivel 1 y continúa hasta el nivel posterior después de todos los scripts bajo el nivel actual se procesan.

Los scripts con niveles negativos se ocultarán del árbol del proyecto y no se procesarán. Estas secuencias de comandos están destinadas a ser utilizadas como una biblioteca para almacenar configuración, macros, código o archivos adjuntos utilizados por otras secuencias de comandos cuando el usuario final no necesita acceder directamente a dichos elementos.

La siguiente tabla muestra los distintos niveles de script y su uso recomendado. El estricto cumplimiento de esta política no se aplica por PEBakery, pero se recomienda encarecidamente para maximizar la interoperabilidad entre proyectos.

| Nivel | Uso | Descripción |
| ---: | --- | --- |
| 1<br/>-1 | Pre-Process | Opciones de proyecto, Configurar archivos de origen, Montar/Extraer WIM, etc.  |
| 2<br/>-2 | Build | Crear carpetas, copiar/expandir/extraer archivos, secciones del registro, WOW64, etc. |
| 3<br/>-3 | Shell & Components | Shell, Ramdisk/FBWF, Redes, Componentes opcionales (Bitlocker, Búsqueda, .Net/VC++ Runtime, etc.) |
| 4<br/>-4 | Settings/Tweaks | Configuraciones como fondo de pantalla, tema, opciones de energía, nombre de la computadora, sistema local, etc. |
| 5<br/>-5 | Applications | Programas y herramientas que se utilizan en el entorno de PE. |
| 6<br/>-6 | Drivers | Controladores adicionales necesarios. (Chipset/LAN/SATA/RAID/VGA/WLAN) |
| 7<br/>-7 | OtherOS | Imágenes de sistema operativo que se agregarán al objetivo. Normalmente se usa para incluir imágenes de arranque precompiladas como chntpw, Hirens, Memtest86 +, PartedMagic, UBCD, etc. que pueden cargarse usando un gestor de arranque como grub4dos o syslinux. |
| 8<br/>-8 | Post-Processing | Crear accesos directos, capturar WIM, limpieza, etc.. |
| 9<br/>-9 | Emulation & Media Creation | Crear/Grabar ISO, Copiar a USB, Probar con Qemu/vmWare/VirtualPC |
| 10<br/>-10 | Project Tools | Herramientas adicionales para trabajar con un proyecto pero que generalmente no forman parte del proceso de compilación. (Manipulación de WIM, edición Hive, ajuste de objetivos, etc.) | 

### Nombres de carpeta

Las carpetas y las Subcarpetas se pueden usar para organizar y agrupar scripts dentro del mismo nivel. Las carpetas se procesan en orden alfa numérico y el nombre de la carpeta se muestra en el árbol del proyecto.

Las carpetas pueden estar duplicadas en el árbol del proyecto si los archivos de script con diferentes niveles residen dentro de la misma carpeta.

### Nombres de archivos

Los archivos de script dentro de su carpeta correspondiente se procesan en orden alfa numérico según su nombre de archivo.

## Observaciones

Ninguna.
