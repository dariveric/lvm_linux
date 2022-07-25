# VirtualBox
### Creamos una maquina virtual en virtualbox con estas especificaciones para el ejemplo
![vb_img_01](img/vb_img_01.png)
![vb_img_02](img/vb_img_02.png)

# lsblk
### Iniciar sesión de preferencia con la cuenta administrador en la maquian virtual, ejecutamos el comando ***lsblk*** para ver información de los ***hdd***

`[roo@rhel8 ~]# lsblk`

![lsblk_01](img/lsblk_01.png)

# fdisk
### Ejecutamos el comando ***fdisk*** para seleccionar los ***hdd*** a formatear con ***filesystem LVM*** para luego agregarlos al grupo de volumen y extenderlo

`[roo@rhel8 ~]# fdisk /dev/sdb`

![fdisk_01](img/fdisk_01.png)