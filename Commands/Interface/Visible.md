# Visible

Establece la visibilidad de un control de IU.

**Este comando ha quedado obsoleto y se eliminará en una versión futura. Se recomienda que actualice su código para usar `WriteInterface,Visible` tan pronto como sea posible para evitar romper su script.**

## Sintaxis

```pebakery
Visible,<%Control%>,<Boolean>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| %Control% | La variable que representa el control de interfaz que se modificará. |
| Boolean | Uno de los siguientes valores: |
|| Verdadero - Muestra el control. |
|| Falso - Oculta el control. |

## Observaciones

Los cambios realizados en la visibilidad de un control son persistentes.

## Relacionado

[WriteInterface](./WriteInterface.md)

## Ejemplos

### Ejemplo 1

Script de muestra que alternará la visibilidad de un grupo de controles cuando cambie el valor de un cuadro combinado.

```pebakery
[main]
Title=Visibility Ejemplo
Description=Mostrar el uso del comando Visible
Level=5
Version=1
Author=Homes32

[variables]

[process]

[Toggle_Advanced_Options]
System,CURSOR,WAIT
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
LBL_CfgProfile="Configuration Profile:",1,1,12,16,120,20,8,Bold
SB_CfgProfile=Simple,1,4,135,10,150,21,Simple,Advanced,_Toggle_Advanced_Options_,True
TXT_FilePath="File Path",1,0,16,78,200,21,C:\Temp
BVL_AdvOptions=pBevel1,0,12,10,115,170,80,
LBL_AdvOptions="Advanced Options:",0,1,23,120,147,18,8,Bold
CB_Adv1="Option 1",0,3,20,150,145,20,True
CB_ADV2="Option 2",0,3,20,170,135,20,True
```
