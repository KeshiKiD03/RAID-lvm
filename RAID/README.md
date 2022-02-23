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

### TIPOS DE RAID

#### RAID 0

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