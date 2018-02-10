# System,Cursor

Alterna el cursor del mouse entre el estado `WAIT` y` NORMAL`.

## Sintaxis

```pebakery
System,Cursor,<State>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| State | Los siguientes estados de cursor están disponibles: |
|| NORMAL - Muestra un cursor normal como lo define su sistema operativo. (Por lo general una flecha) |
|| WAIT - Muestra un cursor de espera según lo define su sistema operativo. (Por lo general, un reloj de arena o spinner) |

## Observaciones

Debe devolver el cursor al estado `NORMAL` cuando haya terminado o permanecerá en el estado` WAIT`. Es una buena idea incluir `System,Cursor,NORMAL` en la función `System,OnBuildExit` de su proyecto para asegurarse de que el cursor no se "atasque" en un estado de espera debido a que el usuario presione el botón Detener o una falla de script.

El ícono exacto del cursor que se muestra depende de tu sistema operativo.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=Cursor Ejemplo
Description=Mostrar el uso del comando System,Cursor. Cambiar el valor del cuadro combinado o haz click en "Play"
Level=5
Version=1
Author=Homes32

[variables]

[process]
System,CURSOR,WAIT
Echo,"El cursor está en estado de espera .#$xPausing por 5 segundos..."
Wait,5
System,CURSOR,NORMAL

[Toggle_Advanced_Options]
System,CURSOR,WAIT
Message,"El cursor está en estado de espera .#$xPausing por 5 segundos...",INFORMACIÓN,5
If,%SB_CfgProfile%,Equal,"Advanced",Begin
  Visible,%BVL_AdvOptions%,True
  Visible,%LBL_AdvOptions%,True
  Visible,%CB_Adv1%,True
  Visible,%CB_Adv2%,True
End
Else,Begin
  Visible,%BVL_AdvOptions%,False
  Visible,%LBL_AdvOptions%,False
  Visible,%CB_Adv1%,False
  Visible,%CB_Adv2%,False
End
System,CURSOR,NORMAL

[Interface]
LBL_CfgProfile="Perfil de configuración:",1,1,12,16,120,20,8,Bold
SB_CfgProfile=Simple,1,4,135,10,150,21,Simple,Advanced,_Toggle_Advanced_Options_,True
TXT_FilePath="Ruta de archivo",1,0,16,78,200,21,C:\Temp
BVL_AdvOptions=pBevel1,0,12,10,115,170,80,
LBL_AdvOptions="Opciones avanzadas:",0,1,23,120,147,18,8,Bold
CB_Adv1="Opción 1",0,3,20,150,145,20,True
CB_ADV2="Opción 2",0,3,20,170,135,20,True
```
