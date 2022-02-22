# M11-SAD Seguretat i alta disponibilitat
## Escola Del Treball
### 2HISX 2021-2022
### Aaron Andal

## INDEX

* **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **LVM**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)



* **RAID**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)


* **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **GPG**: [GPG](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)


## LVM

### LOGICAL VOLUME MANAGER

* Las particiones **LVM** tienen **`ciertas ventajas`** sobre las particiones estándares.

* LVM son formateados como **`Volúmenes físicos`**.

* 1 o más **LVM** son combinados en **`Grupos de Volumen`**.

    * Cada **`almacenamiento grupal`** está dividido en uno o más **`volúmenes lógicos`**.

        * Los **volúmenes lógicos** son como **particiones estándar**.

            * Tienen el `FILESYSTEM`, `ext4` y el `mountpoint`.


### Resumen: 

* LVM son una `pila de bloques`.

    * Un bloque es un `almacenamiento` que se usa para almacenar datos.

    * Los bloques pueden ser agrupados en un grupo (`stack`).

        * Los discos físicos son combinados en un *`volumen grupal`*.

        * El `stack resultante`, puede subdividirse en varios **`volúmenes de tamaño variable`.**.


* Un administrador puede hacer crecer o decrecer los **`volúmenes lógicos`** sin tener que **`destruir datos`**, en lugar de **`standard partitions`**. En caliente.


### ÓRDENES A UTILIZAR:

* apropos lvm `[Busca el MAN de LVM]` 

```
lvm (8)              - LVM2 tools
lvmconfig (8)        - Display and manipulate configuration information
lvmdiskscan (8)      - List devices that may be used as physical volumes
lvmdump (8)          - create lvm2 information dumps for diagnostic purposes
lvmraid (7)          - LVM RAID
lvmvdo (7)           - Support for Virtual Data Optimizer in LVM
pvcreate (8)         - Initialize physical volume(s) for use by LVM
pvremove (8)         - Remove LVM label(s) from physical volume(s)
...
```

* Ordres de gestió de Volums Lògics:

* pv [TAB]

```
       pvchange      Change attributes of a Physical Volume.
       pvck          Check Physical Volume metadata.
       pvcreate      Initialize a disk or partition for use by LVM.
       pvdisplay     Display attributes of a Physical Volume.
       pvmove        Move Physical Extents.
       pvremove      Remove a Physical Volume.
       pvresize      Resize a disk or partition in use by LVM2.
       pvs           Report information about Physical Volumes.
       pvscan        Scan all disks for Physical Volumes.
```

* vg [TAB]

```
       vgcfgbackup   Backup Volume Group descriptor area.
       vgcfgrestore  Restore Volume Group descriptor area.
       vgchange      Change attributes of a Volume Group.
       vgck          Check Volume Group metadata.
       vgconvert     Convert Volume Group metadata format.
       vgcreate      Create a Volume Group.
       vgdisplay     Display attributes of Volume Groups.
       vgexport      Make volume Groups unknown to the system.
       vgextend      Add Physical Volumes to a Volume Group.
       vgimport      Make exported Volume Groups known to the system.
       vgimportclone Import and rename duplicated Volume Group (e.g. a hardware snapshot).
       vgmerge       Merge two Volume Groups.
       vgmknodes     Recreate Volume Group directory and Logical Volume special files
       vgreduce      Reduce a Volume Group by removing one or more Physical Volumes.
       vgremove      Remove a Volume Group.
       vgrename      Rename a Volume Group.
       vgs           Report information about Volume Groups.
       vgscan        Scan all disks for Volume Groups.
       vgsplit       Split  a  Volume Group into two, moving any logical volumes from one Volume Group
                     to another by moving entire Physical Volumes.

```

* lv [TAB]

```
       lvchange      Change attributes of a Logical Volume.
       lvconvert     Convert a Logical Volume from linear to mirror or snapshot.
       lvcreate      Create a Logical Volume in an existing Volume Group.
       lvdisplay     Display attributes of a Logical Volume.
       lvextend      Extend the size of a Logical Volume.
       lvmconfig     Display the configuration information after loading  lvm.conf(5)  and  any  other
                     configuration files.
       lvmdiskscan   Scan for all devices visible to LVM2.
       lvmdump       Create lvm2 information dumps for diagnostic purposes.
       lvreduce      Reduce the size of a Logical Volume.
       lvremove      Remove a Logical Volume.
       lvrename      Rename a Logical Volume.
       lvresize      Resize a Logical Volume.
       lvs           Report information about Logical Volumes.
       lvscan        Scan (all disks) for Logical Volumes.

```


### Ejercicio Práctico 1: Usar LVM

* Se crean **`tres unidades físicas imaginarias`** usando **`dd`** para generar espacio de disco virtual.

* Se asignan ficheros a un **`dispositivo`** de disco físico de **`loopback`**. 

* Se crean **`3 particiones`** **`/dev/loop0`**, **`/dev/loop1`**, **`/dev/loop2`**.

1. Crear los 3 **`ficheros de imagen`**

#### **DD (Conver and COPY a FILE) --> /dev/zero (Imaginario)**

```
root@i11:/opt/lvm# dd if=/dev/zero of=disk01.img bs=1k count=500K

512000+0 records in
512000+0 records out
524288000 bytes (524 MB, 500 MiB) copied, 0.533952 s, 982 MB/s
```
```
root@i11:/opt/lvm# dd if=/dev/zero of=disk02.img bs=1k count=500K

512000+0 records in
512000+0 records out
524288000 bytes (524 MB, 500 MiB) copied, 0.540251 s, 970 MB/s

```
```
# dd if=/dev/zero of=disk03.img bs=1k count=100K
102400+0 records in
102400+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 0.146417 s, 716 MB/s
```

* Se crea una carpeta en `/opt` 

* mkdir `lvm`

* Se los asigna al `LOOPBACK` como `ROOT` Del 0-2 | (Se empieza del 2 al 3) # En la CLASE.

    * **`Troubleshoot`**

```
## ¡¡ YA ESTÁ OCUPADO !!
root@i11:/opt/lvm# losetup /dev/loop0 disk01.img 
losetup: disk01.img: failed to set up loop device: Device or resource busy
```

* Si ya tuvieramos los LOOPS ocupados con el comando --> **losetup -d /dev/loopX** --> **Podemos eliminar el LOOP**.

```
root@i11:/opt/lvm# losetup -d /dev/loop2
root@i11:/opt/lvm# losetup -d /dev/loop3

root@i11:/opt/lvm# losetup -a
/dev/loop1: [66306]:4333633 (/var/lib/snapd/snaps/core_11993.snap)
/dev/loop0: [66306]:4333635 (/var/lib/snapd/snaps/msnake_10.snap)
root@i11:/opt/lvm# 
```

#### **Asignarlos a un dispositivo LOSETUP (/dev/loop2 /dev/loop3)**

* Añadimos a un **`DISPOSITIVO LOSETUP`**
```
root@i11:/opt/lvm# losetup -a
/dev/loop0: ...
/dev/loop1: ...
/dev/loop2: ...

```
```
root@i11:/opt/lvm# losetup /dev/loop0 disk01.img 
root@i11:/opt/lvm# losetup /dev/loop1 disk02.img
root@i11:/opt/lvm# losetup /dev/loop2 disk03.img 

```

* `Verificamos`

```
root@i11:/opt/lvm# losetup -a

/dev/loop0: [66306]:4365633 (/opt/lvm/disk01.img)

/dev/loop1: [65406]:4333612 (/opt/lvm/disk02.img)

/dev/loop2: [66806]:4398633 (/opt/lvm/disk03.img)

root@i11:/opt/lvm# 
```



#### **Crear la RAID1 con los DOS DISCOS (/dev/loop2 /dev/loop3)**

* Creamos el RAID 1
```
root@i11:/opt/lvm# mdadm --create /dev/md/raid_lvm0 --level=1 --raid-devices=2 /dev/loop2 /dev/loop3

mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
Continue creating array? yes

mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md/raid_lvm0 started.

```
* Comprobamos que está bien creada // **IMPORTANTE MD127: active raid1 loop3[1] loop2[0]**
```
root@i11:/opt/lvm# cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 

md127 : active raid1 loop3[1] loop2[0]
      510976 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
```
```
root@i11:/opt/lvm# mdadm --detail /dev/md/raid_lvm0

/dev/md/raid_lvm0:
           Version : 1.2
     Creation Time : Fri Feb 18 10:26:24 2022
        Raid Level : raid1
        Array Size : 510976 (499.00 MiB 523.24 MB)
     Used Dev Size : 510976 (499.00 MiB 523.24 MB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Fri Feb 18 10:26:26 2022
             State : clean 
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

              Name : i11:raid_lvm0  (local to host i11)
              UUID : 342cdb30:85f0d347:c5215212:31d4f70c
            Events : 17

    Number   Major   Minor   RaidDevice State
       0       7        2        0      active sync   /dev/loop2
       1       7        3        1      active sync   /dev/loop3
root@i11:/opt/lvm# 

```

## RAID

## GPG