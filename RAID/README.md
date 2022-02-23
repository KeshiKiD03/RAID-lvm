# M11-SAD Seguretat i alta disponibilitat
## Escola Del Treball
### 2HISX 2021-2022
### Aaron Andal

## INDEX

* **RAID**: [LVM](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)

    * **RAID**: [RAID](https://github.com/KeshiKiD03/samba21#pr%C3%A1ctica-pam---ldap---samba-en-aws-educate)


## RAID

### ¿QUE ES RAID?

**Reduntant Array of Inexpensive Disks**

* The basic idea behind RAID is to combine multiple small, inexpensive disk drives into an array to accomplish performance or redundancy goals not attainable with one large and expensive drive. 

* La idea del **`RAID`** es **`combinar`** múltiples pequeños discos en un **`ARRAY`** para incrementar el **`RENDIMIENTO`** o la **`REDUNDANCIA`** no alcanzables con un solo disco **`CARO`**.

* This array of drives appears to the computer as a single logical storage unit or drive.

* Este **`ARRAY DE DISCOS`**, aparecen como un único **`ALMACENAMIENTO LÓGICO`** o **`UNIDAD`**.

* RAID permite que la información se **`propague`** en diferentes discos.

* RAID usa técnicas como:

    * **`RAID0 --> Disk striping.`**.

    * **`RAID1 --> Disk mirroring`**.

    * **`RAID5 --> Disk striping with parity`**.

* **Todo para obtener `REDUNDANCIA`, baja `LATENCIA`, incrementar el `ANCHO de BANDA` y maximizar la habilidad de `RECUPERACIÓN` en caso de `FAIL`**.

**SOFTWARE RAID**

* Implementa varios RAID LEVEL en el Kernel (**`SOFTWARE`**).

* Es la más barata ya que no requieres controladores de disco o hot-swap chassis.

* Linux Kernel contiene **`MD`** --> **`Multi Disc`** driver que permite **`RAID`**

### TIPOS DE RAID

#### RAID 0

**`RAID0 = STRIPING`**.

* Orientado a striping o **distribución por bandas**.

* Los discos deben tener el **`mismo tamaño`** o uno **`mayor que otro`**.

#### RAID 1

#### RAID 2

#### RAID 3

#### RAID 4

#### RAID 5

#### RAID 6

#### RAID 10

#### LINEAR RAID






# Pràctiques RAID:

## PRÁCTICA 1: TRABAJO BÁSICO CON RAID

### 1. CREAR EL RAID

* mdadm --create /dev/md0 --chunk=4 --level=1 --raid-devices=3 /dev/loop0 /dev/loop1 /dev/loop2

### 2. Examinar el RAID

* mdadm --detail --scan
* mdadm --detail /dev/md0
* mdadm --query /dev/loop0
* mdadm --examine /dev/loop0
* cat /proc/mdstat

### 3. Errada i recuperació

* mdadm /dev/md0 --fail /dev/loop1
* mdadm /dev/md0 --remove /dev/loop1
* mdadm --manage /dev/md0 --add /dev/loop3

### 4. Aturar / Engegar el RAID

* mdadm --stop /dev/md0
* mdadm --assemble --scan
* mdadmin --assemble /dev/md0 --run /dev/loop0 /dev/loop1/dev/loop2
* mdadm --detail --scan > /etc/mdadm.conf

### 5. Automatitzar l'arrancada del RAID

### 6. Practica proposada: RAID1 + SPARE


## PRÁCTICA 2: RAID LEVEL 5

### 1. RAID5: Degradar i FAILED

### 2. RAID5: Degradar i RECUPERAR

## PRÁCTICA 3: START / STOP / ASSEMBLE / MD127

### 1. Ordre MDADM

### 2. Exemple 1: Regeneració Automàtica / Regeneració per nom de RAID

### 3. Exemple 2: Assemble indicant les parts

### 4. Exemple 3: Múltiples RAID

## Reshape: Raid-Devices / Level / Size

### 1. Reshape RAID Devices

### 2. Exemple 1: Regeneració Automàtica / Regeneració per nom de RAID

### 3. Reshape: LEVEL

#### Convertir un RAID1 a un RAID5

#### Impossibily Level Change

### 4. Reshape: SIZE