# VirtualBox
### Creamos una maquina virtual en virtualbox con estas especificaciones para el ejemplo
![vb_img_01](img/vb_img_01.png)
![vb_img_02](img/vb_img_02.png)

# lsblk
### Iniciar sesión de preferencia con la cuenta administrador en la maquian virtual, ejecutamos el comando **lsblk** para ver información de los **hdd**

`[roo@rhel8 ~]# lsblk`

![lsblk_01](img/lsblk_01.png)

# fdisk
### Ejecutamos el comando **fdisk** para seleccionar los **hdd** a formatear, con **filesystem LVM** para luego agregarlos al grupo de volumen y extenderlo.

`[roo@rhel8 ~]# fdisk /dev/sdb`

![fdisk_01](img/fdisk_01.png)

### presionamos **o** para generar una nueva tabla de partición **DOS vacía**
> nota: por que **o** y no otras de las demas, por que estamos usando un sistemas con bios normal y si usaramos efi seria **g** 

![fdisk_02](img/fdisk_02.png)


### luego de eso presionamos **n** para crear una nueva partition, escogemos **p** para selecionar una partición primaria y a todo lo demas lo dejamos por default, presionando enter para continuar

![fdisk_03](img/fdisk_03.png)

### luego de eso cambiamos el tipo de partición presionamos **t** y luego **L** para imprimir los tipos de particiones y buscamos la **Linux LVM** que su codigo es **8e**


![fdisk_04](img/fdisk_04.png)

### presionamos enter para guardar los cambios en la nueva particion creada

![fdisk_05](img/fdisk_05.png)

### presionamos **i** para imprimir un resumen de los cambios realizados

![fdisk_06](img/fdisk_06.png)

## luego presionamos **w** para guardar los cambios realizados en la nueva tabla de particiones. Esto lo hacemos con los demas disco que tiene la maquina virtual

![fdisk_07](img/fdisk_07.png)

`[roo@rhel8 ~]# fdisk /dev/sdc`

`[roo@rhel8 ~]# fdisk /dev/sdd`