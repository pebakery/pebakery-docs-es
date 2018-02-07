# ShellExecuteEx

Ejecuta un programa externo y continúa procesando inmediatamente.

## Sintaxis

```pebakery
ShellExecuteEx,<Action>,<FilePath>[,Params][,WorkDir]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Action | El método utilizado para iniciar el archivo externo. Puede ser uno de los siguientes: |
|| Open - Si el archivo es un ejecutable, se lanzará. Si el archivo no es ejecutable, se abrirá con la aplicación predeterminada asociada a ese tipo de archivo.  |
|| Hide - El archivo se iniciará en modo oculto. Los programas de la consola que escriben en las secuencias StdOut y StdErr tendrán su salida redireccionada a la ventana de compilación PEBakerys y se escribirá en el registro. |
|| Print - Imprimir el contenido del archivo con la impresora predeterminada del sistema. |
|| Explore - Abrir una ventana del explorador (Se puede usar para mostrar los contenidos del sistema de archivos local). |
|| Min - Igual que Open, pero inicia el programa minimizado a la barra de tareas. |
| FilePath | El archivo para ejecutar Si no se especifica una ruta completa, PEBakery intentará localizarla utilizando la variable %PATH% del sistema operativo. |
| Params | **(Opcional)** Cualquier argumento que desee pasar al programa. Use ("") para ninguno. |
| WorkDir | **(Opcional)** El directorio de trabajo para el programa. Use ("") para especificar el directorio de trabajo actual. |

## Observaciones

La mayoría de las veces se utiliza para iniciar programas y navegadores desde la interfaz gráfica de un script.

## Relacionado

[ShellExecute](./ShellExecute.md), [ShellExecuteDelete](./ShellExecuteDelete.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=ShellExecuteEx Ejemplo
Author=Homes32
Description=Mostrar el uso del comando ShellExecuteEx.
Version=1
Level=5

[Interface]

[variables]

[process]

// Abrir notepad.exe
ShellExecuteEx,open,notepad.exe

// Abrir nuestro %BaseDir% en un navegador de archivos.
ShellExecuteEx,explore,%BaseDir%

// "Abrir" un programa "Minimizado".
Echo,"Ejecutando una aplicación de consola minimizada..."
ShellExecuteEx,min,cmd.exe,"/C PING 127.0.0.1 -n 10"
```
