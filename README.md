## MUESTRA INFORMACION DE LOS GRUPOS DE VOLUMENES
´
[root@rhel8 ~]# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  almalinux   1   2   0 wz--n- <7.00g    0 
[root@rhel8 ~]#
´

## MUESTRA INFORMACION DE LOS VOLUMENES LOGICOS
[root@rhel8 ~]# lvs
  LV   VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root almalinux -wi-ao----  <6.20g                                                    
  swap almalinux -wi-ao---- 820.00m                                                    
[root@rhel8 ~]#

## IMPRIME INFORMACION DE LOS HDD DEL SISTEMAS
[root@rhel8 ~]# lsblk
NAME               MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                  8:0    0    8G  0 disk 
├─sda1               8:1    0    1G  0 part /boot
└─sda2               8:2    0    7G  0 part 
  ├─almalinux-root 253:0    0  6.2G  0 lvm  /
  └─almalinux-swap 253:1    0  820M  0 lvm  [SWAP]
sdb                  8:16   0    8G  0 disk 
sdc                  8:32   0    8G  0 disk 
sdd                  8:48   0    8G  0 disk 
sr0                 11:0    1 1024M  0 rom  
[root@rhel8 ~]# 

## FORMATEAMOS LOS HDD
[root@rhel8 ~]# fdisk /dev/sdb
[root@rhel8 ~]# fdisk /dev/sdc
[root@rhel8 ~]# fdisk /dev/sdd

## AGREGAMOS LOS HDD PARA LVM
[root@rhel8 ~]# pvcreate /dev/sdb1 /dev/sdc1 /dev/sdd1
  Physical volume "/dev/sdb1" successfully created.
  Physical volume "/dev/sdc1" successfully created.
  Physical volume "/dev/sdd1" successfully created.
[root@rhel8 ~]# 

## REMOVER LOS HDD LVM
[root@rhel8 ~]# pvremove /dev/sdb1 /dev/sdc1 /dev/sdd1
  Labels on physical volume "/dev/sdb1" successfully wiped.
  Labels on physical volume "/dev/sdc1" successfully wiped.
  Labels on physical volume "/dev/sdd1" successfully wiped.
[root@rhel8 ~]# 


## MOSTRAMOS INFORMACION DE LVM AGREGADOS
[root@rhel8 ~]# pvs
  PV         VG        Fmt  Attr PSize  PFree 
  /dev/sda2  almalinux lvm2 a--  <7.00g     0 
  /dev/sdb1            lvm2 ---  <8.00g <8.00g
  /dev/sdc1            lvm2 ---  <8.00g <8.00g
  /dev/sdd1            lvm2 ---  <8.00g <8.00g
[root@rhel8 ~]# 

## AGREGAMOS HDD AL GRUPO DE VOLUMEN
[root@rhel8 ~]# vgextend almalinux /dev/sdb1 /dev/sdc1 /dev/sdd1
  Volume group "almalinux" successfully extended
[root@rhel8 ~]# 

## REDUCIR HDD DEL GRUPO DE VOLUMENES
[root@rhel8 ~]# vgreduce almalinux /dev/sdb1 /dev/sdc1 /dev/sdd1
  Removed "/dev/sdb1" from volume group "almalinux"
  Removed "/dev/sdc1" from volume group "almalinux"
  Removed "/dev/sdd1" from volume group "almalinux"
[root@rhel8 ~]# 

