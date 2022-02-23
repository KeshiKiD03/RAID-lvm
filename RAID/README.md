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

* El **`OBJETIVO`** del RAID es dividir y replicar la información en diferentes discos duros, y a parte incrementar la **`FIABILIDAD`** de la **`TRANSFERENCIA`**.

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

#### RAID 0 (Performance)

**`RAID0 = STRIPING / VOLUMEN DIVIDIDO`**.

* Orientado a striping o **distribución por bandas**.

**`NO TIENE REDUNDANCIA`**

* Los discos deben tener el **`mismo tamaño`** o uno **`mayor que otro`**.

* Distribuye los datos equitativamente entre **`DOS`** o más discos **`SIN INFORMACIÓN DE PARIDAD`** que proporcione **`REDUNDANCIA`**.

* Incrementa el **`rendimiento`**.

* Inconvenientes:

    * No existe **control de paridad** ni **tolerancia a fallos** --> No existe una garantía de **`integridad de datos`**.

    * Las **`posibilidades`** de `recuperar información` en un disco averiado es `0` en un RAID0.

![](http://www.mercadoit.com/blog/wp-content/uploads/2019/01/Raid-0.jpg)


#### RAID 1 (Redundancy)

**`RAID1 = MIRRORING / VOLUMEN ESPEJO`**.

* Orientado a espejo o **distribución por igual**.

* Primer modo que realmente tiene **`REDUNDANCIA`**.

* Si uno de los discos **`FALLA`**, los datos permanecerán **`INTACTOS`** puesto que se dispone otro disco.

* **`Rendimiento`** de las lecturas es la **`SUMA`** de los rendimientos de los discos.

* Crea una **`copia exacta`** de un conjunto de datos en **`dos`** o **`más discos`**. 

* Resulta útil cuando el **`rendimiento en lectura`** es más importante que la **`capacidad`**.

* RAID1 sólo puede ser **tan grande** como el **más pequeño de sus discos**.

    * Es decir, si tienen tamaños diferentes, se quedará con el tamaño del **`más pequeño`**.

    * Ya que se trata de una **`COPIA DE OTRO DISCO`**, entonces su **`TAMAÑO`** será **`IGUAL`**.

    * Si tenemos **3 discos** de **1TB**, la capacidad que tendremos es **`1TB`** --> **`PORQUE ES UNA COPIA`**.

* Para **PERDER LOS DATOS**, tienen que **FALLAR TODOS los DISCOS**.

    * Así no tendremos un **`SISTEMA REDUNDANTE`**

* Inconvenientes:

    * **Costoso**.

        * Puesto que se copia la misma información en todos los discos, cada disco tiene un precio.

![](http://www.mercadoit.com/blog/wp-content/uploads/2019/01/Raid-1.jpg)

#### RAID 2

**`RAID2 = RAID0 + RAID1`**.

* RAID0 y RAID1 a la vez.

* Se calcula con el código de Hamming.

* **Paridad de HAMMING**

![](https://www.profesionalreview.com/wp-content/uploads/2019/01/RAID-2.png)


#### PARIDAD

**PARIDAD**: Para explicarlo de una forma sencilla, la paridad es la suma de todos los dispositivos utilizados en una matriz. 

Recuperarse del fallo de dispositivo es posible leyendo los datos buenos que quedan y comparándolos con el dato de paridad almacenado en el conjunto. 

La paridad es usada por los niveles de RAID 2, 3, 4 y 5. 

RAID 1 no utiliza la paridad puesto que todos los datos están completamente duplicados al tratarse de un espejo.

#### RAID 3

**`RAID3 = RAID0 + PARIDAD (EN BYTES)`**.

* Es redundante.

* Usa **`data striping`** con un **`disco de paridad`** dedicado.

* Necesita mínimo 3 discos.

* Permite tasas de transferencia **ALTAS**.

* Se usan **`2 discos tipo RAID0`** y uno para **`PARIDAD`**.

* Si **`perdemos uno`** de los discos, **`podremos recuperarlo`** mediante el **`bit de paridad`**

![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Raid3.png/800px-Raid3.png?20100124125409)

#### RAID 4 (Error Checking)

**`RAID4 = RAID3 + PARIDAD (EN BLOQUES) - NO RECOMENDABLE`**.

* Parecido al RAID3, excepto porque divide a nivel de **`BLOQUES`** en lugar de **`BYTES`**.

* Todas las paridades están en el **`MISMO DISCO`**.

* La **`PARIDAD`** --> Es un archivo que con un cálculo puede recuperar lo que haga falta.

    * Ejemplo: (EX (Disc, Disc, Paritat): 7 4 28 --> x 4 28 --> sap que el que falta és 7)

* El problema que tiene es que genera un **`CUELLO de BOTELLA`** teniendo un **`SOLO DISCO COMO PARIDAD`**.

* RAID4 NO SE UTILIZA, por el tema del **`CUELLO DE BOTELLA`**.

    * **SOLO PUEDE FALLAR UN DISCO**

* El almacenamiento de RAID 4 es lo mismo que el **`miembro más pequeño`**.

![](https://static.thegeekstuff.com/wp-content/uploads/2011/12/raid4.png)

#### RAID 5 (Distributed Error Checking)

**`RAID5 = RAID4 + PARIDAD REPARTIDA (STRIPPING CON PARIDAD) - MIN 3 DISCOS`**.

* Lo mismo que el RAID4, pero las PARIDADES se reparten por **`TODOS LOS DISCOS`**

* Es el modo RAID **`más util`** cuando uno desea **`COMBINAR`** un mayor número de **`DISCOS`** y todavía conservar **`REDUNDANCIA`**.

* La **`CAPACIDAD`** de almacenamiento se SIEMPRE equilamente a la **`SUMA`** de todos los **`DISCOS`** menos **`UNO`**

* **Si uno de los datos falla, todos los `datos permanecerán` intactos, gracias a la `información de paridad`**.

* **Si `dos discos` `fallan` simultáneamente, `todos los discos permanecerán`. RAID5 puede sobrevivir a un `fallo de disco`.**

* **SÓLO PUEDE FALLAR UN DISCO**

* **Es la que más se usa**

* **`RAID5 elimina`** el **`CUELLO DE BOTELLA`** que generaba RAID4.

* Si falla alguno, la RAID5 se puede calcular y corregir.

**EJEMPLO**

**Si tengo 3 DISCOS de 1TB a RAID5, ¿Cuanta capacidad de almacenamiento tengo?**

* **`2TB`**. 

* La **`PARIDAD`** está repartida a los **`3 discos`** y acabamos perdiendo **`1TB`**

![](http://www.mercadoit.com/blog/wp-content/uploads/2019/01/RAID-5.jpg)

![](https://www.intel.com/content/dam/support/us/en/images/chipsets/imsm/sb/img/raid5.jpg)


#### RAID 6 (Redundant Error Checking)

**`RAID5 = STRIPPING CON PARIDAD DOBLE`**.

* Lo mismo que el **`RAID5`** pero a la hora de repartir los datos a todos los discos, se reparten **`más paridades`** (Dos paridades por DISCO DURO).

* **`SÓLO PUEDEN FALLAR 2 DISCOS!`**

![](http://www.mercadoit.com/blog/wp-content/uploads/2019/01/RAID-6.jpg)

#### RAID 0+1:

* RAID 1 + 0 hace **`STRIPPING y ESPEJO al MISMO TIEMPO`**

    * Se **`dividen`** en **`2 discos`** para aumentar la velocidad.

    * Al mismo tiempo están **`duplicadas`** en un otro disco, como mínimo. 

* Fem un RAID 1 sobre dos RAID 0 (tenim 4 discos d'1TB cadascún --> en total 4TB però aprofitables / útils només 2TB)

* Com fa el RAID 0, tindrem qúadruple (en aquest cas) de velocitat a l'hora de llegir i el doble a l'hora d'escriure

* **`NOMÉS PODEN FALLAR COM A MÀXIM 2 DISCOS (DEL MATEIX COSTAT!) `**--> NO POT FALLAR 1 DISC PER CADA COSTAT.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Raid0mas1.png/1024px-Raid0mas1.png)

#### RAID 10 (RAID 1+0):

* Fem un RAID 0 sobre dos RAID 1 (tenim 4 discos d'1TB cadascún --> en total 4TB però aprofitables / útils només 2TB)

* Ídem al RAID 0 (quàdruple de lectura i doble d'escriptura)

* NOMÉS POT FALLAR 1 PER CADA COSTAT (JA QUE SÓN UNA CÒPIA IDÈNTICA)

![](http://www.mercadoit.com/blog/wp-content/uploads/2019/01/Raid-10.png)

![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/RAID_10.svg/220px-RAID_10.svg.png)


![](https://github.com/KeshiKiD03/lvm/blob/main/Photos/raid6.png)


### IMPORTANT:
```yaml
* dm --> device mapper (dispositiu que fa una assignació (taula de correspondència) entre els discos que ens inventem contra els real)
* md --> multi-disk = RAID
* Magin : <number> --> identifica la partició
```
------------------------------------

# Pràctiques RAID:

## PRÁCTICA 1: TRABAJO BÁSICO CON RAID

### 1. CREAR EL RAID

**`EJEMPLO DE CREACIÓN DE UN RAID1`**
```yaml
mdadm --create /dev/md0 --chunk=4 --level=1 --raid-devices=3 /dev/loop0 /dev/loop1 /dev/loop2
```

------------------------------------

**1. CREAR FICHEROS DE IMAGEN**
```bash
dd if=/dev/zero of=disk01.img bs=1k count=100K ; 
dd if=/dev/zero of=disk02.img bs=1k count=100K ; 
dd if=/dev/zero of=disk03.img bs=1k count=100K # --> Crear ficheros de IMAGEN de un DISCO VIRTUAL
```

**2. ASIGNAR A LOOPBACK**
```bash
losetup /dev/loop0 /opt/lvm/disk01.img ;
losetup /dev/loop1 /opt/lvm/disk02.img ;
losetup /dev/loop2 /opt/lvm/disk03.img # --> Asocia un /dev/loopX a un DISCO (Físico o Virtual)
```

**3. VERIFICAR**
```bash
losetup -a # --> Mostra els dispositius /dev/loopX
```

**4. CREAR RAID1**
```bash
mdadm --create /dev/md0 --chunk=4 --level=1 --raid-devices=3 /dev/loop0 /dev/loop1 /dev/loop2
```

**5. VERIFICAR**
```bash
tree /dev/disk # --> Árbol de los discos
```


`| |-- md-name-portatil.localdomain:0 -> ../../md0`

`| | -- md-uuid-b5fd01dc:53a820d3:190ae832:4f3144f8 -> ../../md0`

**7. FORMATEAR**

* Disponemos de un dispositivo **`/dev/md0`** --> **RAID1** formado por las 3 particiones **`LOOP0, LOOP1, LOOP2.`**

* Se trata de un RAID de NIVEL1 con 3 discos **`ESPEJO / MIRRORING`**

* Ahora hay que añadirle un **`SISTEMA de FICHEROS / FORMATEARLO`** y **`MONTARLO al FILESYSTEM`**

* Se monta a **`/mnt`** por ejemplo.

* Se copian los datos de **`/boot`** por ejemplo.

* Observar el almacenamiento con **`df`**.

```bash
mkfs -t ext4 /dev/md0 # --> Formatea el RAID1 del tipo EXT4
```
**7. OBSERVAR DISCOS**
```bash
blkid # --> Dice el ID de cada ELEMENTO de HARDWARE, aunque sea VIRTUAL (Crea Block Device Atributes).
```

`/dev/md0: UUID="005caef9-e1e0-429a-bc81-7fcb5ba290cb" TYPE="ext4"`

**8. MONTAR**
```bash
mount /dev/md0 /mnt/ # --> Montamos el RAID1 (Multiple Disk 0) a /mnt
```
**9. POPULATE RAID1**
```bash
cp -r /boot/ /mnt/ # --> Copiamos los datos recursivos de BOOT a /mnt
```

**10. DISK FREE**
```bash
df -h # --> Muestra el DISK FREE.
```


### 2. Examinar el RAID

**`EJEMPLO DE EXAMINACIÓN DE RAID`**

* mdadm --detail --scan
* mdadm --detail /dev/md0
* mdadm --query /dev/loop0
* mdadm --examine /dev/loop0
* cat /proc/mdstat

**1. DETAIL SCAN (VEMOS RAID1 CREADA)**
```bash
mdadm --detail --scan # --> Vemos el ARRAY creada por el RAID1.
```

**2. DETAIL /DEV/MD0 (DETALLES RAID1)**
```bash
mdadm --detail /dev/md0 # --> Vemos los DETALLES creados por el RAID
```

**3. QUERY (SI ES UN ARRAY (MD))**
```bash
mdadm --query /dev/loop0 # --> Examina si es de tipo 'md' (Si no lo es, da ERROR)
```

**4. EXAMINE /DEV/LOOP0 (INFORMACIÓN DISPO)**
```bash
mdadm --examine /dev/loop0 # --> Da información de la partición VIRTUAL
```

**5. SE COMPRUEBA EL ESTADO EN /PROC/MDSTAT**
```bash
cat /proc/mdstat # --> Observamos los diferentes tipos de RAID y vemos cuales tenemos creadas.
# También que particiones virtuales tiene asociadas
```

### 3. Errada i recuperació

**`EJEMPLO DE FAIL Y RECUPERACIÓN RAID`**

* mdadm /dev/md0 --fail /dev/loop1
* mdadm /dev/md0 --remove /dev/loop1
* mdadm --manage /dev/md0 --add /dev/loop3

**1. PROVOCAR FAIL AL /DEV/LOOP1**
```bash
mdadm /dev/md0 --fail /dev/loop1 # --> Simula un ERROR del LOOP1 (AL SER RAID1 NO PASA NADA YA QUE SON MIRRORS!!!)
```

**2. SE COMPRUEBA EL ESTADO EN /PROC/MDSTAT AFTER FAIL**
```bash
cat /proc/mdstat # --> Observamos los diferentes tipos de RAID y vemos cuales tenemos creadas.
# También que particiones virtuales tiene asociadas
# Comprobamos AFTER FAIL
```

**3. DETAIL /DEV/MD0 (DETALLES RAID1) AFTER `FAIL`**
```bash
mdadm --detail /dev/md0 # --> Vemos los DETALLES creados por el RAID1.
# Comprobamos AFTER FAIL
```

**State: `clean`,` degraded` --> `clean` perquè hi ha `2 funcionant` i hi ha `redundancia` de dades (o s'han perdut) i `degraded` per la partició que s'ha `espatllat`**

**4. REMOVE DE /DEV/MD0 EL DISCO FALLADO /DEV/LOOP1 (AFTER FAIL)**
```bash
mdadm /dev/md0 --remove /dev/loop1 # --> Ahora que ha fallado, se retira del RAID (SE HACE EN CALIENTE)
# Comprobamos AFTER FAIL
```

`mdadm: hot removed /dev/loop1 from /dev/md0`

**5. SE COMPRUEBA EL ESTADO EN /PROC/MDSTAT AFTER `RETIRO`**
```bash
cat /proc/mdstat # --> Observamos los diferentes tipos de RAID y vemos cuales tenemos creadas.
# También que particiones virtuales tiene asociadas
# Comprobamos AFTER FAIL
```

**6. SE VUELVE A GENERAR OTRO DISCO VIRTUAL**
```bash
dd if=/dev/zero of=disk04.img bs=1k count=100k # --> Creem un altre imatge per afegir-la al RAID
```

**7. SE AÑADE LA IMAGEN AL LOOPBACK**
```bash
losetup /dev/loop3 disk04.img # --> Afegim la nova imatge al loopback
```

**8. AÑADIR EL NUEVO LOOPBACK (/DEV/LOOP3) A RAID**
```bash
* mdadm --manage /dev/md0 --add /dev/loop3 # --> Afegim el nou loopback al RAID --> 'manage' opcional
```

**Quan afegim un disc nou, en `background` va fent tota la '`pesca`' de sincronització (va volcant les dades del mirror)**

**9. SE COMPRUEBA EL ESTADO EN /PROC/MDSTAT AFTER `ADD DE /DEV/LOOP3`**
```bash
cat /proc/mdstat # --> Observamos los diferentes tipos de RAID y vemos cuales tenemos creadas.
# También que particiones virtuales tiene asociadas
# Comprobamos AFTER ADD /DEV/LOOP3
```

`loop3[3]`

**3. DETAIL /DEV/MD0 (DETALLES RAID1) AFTER `ADD DE /DEV/LOOP3`**
```bash
mdadm --detail /dev/md0 # --> Vemos los DETALLES creados por el RAID1.
# Comprobamos AFTER ADD /DEV/LOOP3
```

`active sync /dev/loop3`



### 4. Aturar / Engegar el RAID

Para encender **UN RAID** hay **`3 MECANISMOS`**:

* Pedirle a MDADM que EXAMINE todas las **PARTICIONES DEL SISTEMA** (**`SCAN`**).

    * Las particiones tienen un superblock --> Indica si son parte de un Array y de cual.

* Indicar a **`MDADM`** que ajunte las particiones concretas que le indiquemos como *`ARGUMENTOS`*.

    * **`FORZAR QUE USE PARTICIONES INDICADAS`**

* Generar un fichero de configuración *`/etc/mdadm.conf`* donde hay la información necesaria para **`automatizar el RAID`**.

    * Opción para poder encender los RAID al encender el **SISTEMA**.

**`EJEMPLO DE PARAR Y ENCENDER RAID`**

* mdadm --stop /dev/md0
* mdadm --assemble --scan
* mdadmin --assemble /dev/md0 --run /dev/loop0 /dev/loop1/dev/loop2
* mdadm --detail --scan > /etc/mdadm.conf

**1. PARAR EL RAID (NO DEJARÁ, ANTES UN UMOUNT)**
```bash
mdadm --stop /dev/md0 # --> NO ENS DEIXARÀ PERQUÈ ELS LOOPBACKS ESTAN MUNTATS A /mnt
```

**2. UMOUNT FIRST**
```bash
umount /mnt # --> Desmuntem el directori /mnt PRIMER per poder parar el RAID
```

**3. PARAR EL RAID (¡AHORA SI!)**
```bash
mdadm --stop /dev/md0 --> Ara SI podrem parar el RAID
```


**Les particions existeixen, però el RAID no apareix per exemple a 'tree /dev/disk'**

**Hem **`d'eliminar`** la **`marca del RAID`** un cop desmuntat per quan engegui l'ordinador no intenti muntar-lo. Ordre: `mdadm -v  --zero-superblock /dev/loop[]`**

**4. CANTIDAD DE DISCOS ACTIVOS (ASSEMBLE)**
```bash
mdadm --assemble --scan # --> Ens informa de amb quants dicos ha iniciat el RAID i ens informa de que l'array de md0 enacara està actiu ja que l'hem aturat, NO ELIMINAT!
#  Examina TODAS LAS PARTICIONES DEL SISTEMA e INTENTA "ENSAMBLAR" TODAS AQUELLAS QUE CREE QUE FORMAN UN RAID
```

`mdadm: giving up`

**`--assemble` (engega el RAID) | `--scan` (escaneja particions de RAID e intenta juntar)**

**`Examina` el discos e intenta `deduir` les coses, està `trobant 4 particions` i las `assigna` al `/dev/md0` quan aquest té assignades realment `3`, i les engega amb les últimes 3 trobades (ho enten igualment amb aquestes 3), encara que haguessin 2, ho hauria engegat igualment.**

**5. ESCOGER DISPOSITIVOS A UTILIZAR (ASSEMBLE)**
```bash
mdadm --assemble /dev/md0 --run /dev/loop2 /dev/loop3 /dev/loop4 # --> Triem els dispositius que volem que utilitzi, si possem per exemple /dev/loop1, iniciara 2 en compte de 3

```

**6. AÑADIR INFORMACIÓN DEL SCAN AL FICHERO EN CUESTIÓN (ASSEMBLE) (AUTOMÁTICO)**
```bash
mdadm --detail --scan > /etc/mdadmin.conf # --> Fiquem l'info del 'scan' al fitxer en questió (sabrà quin RAID ha d'arrancar, explicació + endevant)

```


**7. PARAR EL RAID**
```bash
mdadm --stop /dev/md0 # --> Aturem el RAID

```

**8. GENERAR EL ASSEMBLE Y EL SCAN DE NUEVO / CANTIDAD DE DISCOS ACTIVOS (MANUAL)**
```bash
mdadm --assemble --scan # --> Examina TODAS LAS PARTICIONES DEL SISTEMA e INTENTA "ENSAMBLAR" TODAS AQUELLAS QUE CREE QUE FORMAN UN RAID.
```

**9. ELIMINAR LA MARCA (TAG) DEL RAID**
```bash
mdadm -v --zero-superblock /dev/loop1 /dev/loop2 /dev/loop3 /dev/loop4 # --> Els hi treiem la marca (netejem)

```

### 5. Automatitzar l'arrancada del RAID

Para automatizar el arranque, se genera un fichero de configuración llamado **`mdadm.conf`**. Hace falta guardarlo en **`/etc/fstab`**.

Para que monte el RAID automáticamente.

**1. GENERAR EL ASSEMBLE Y EL SCAN DE NUEVO / CANTIDAD DE DISCOS ACTIVOS + AÑADIR INFO EN /ETC/MDADM.CONF (AUTOMÁTICO)**
```bash
mdadm --assemble --scan # --> Examina TODAS LAS PARTICIONES DEL SISTEMA e INTENTA "ENSAMBLAR" TODAS AQUELLAS QUE CREE QUE FORMAN UN RAID + AÑADE LA INFO DEL 'SCAN' AL FICHERO (SABRÁ QUE RAID TIENE QUE ARRANCAR).
```

**2. MODIFICAR EL /ETC/FSTAB**
```bash
cat /etc/fstab

```

`/dev/md0 /mnt ext4 default 0 0`

## PROPUESTA: RAID1 + SPARE

Crear un raid de Level1 amb dues particions (loop0 i loop1) i dos discs d’spare. I practicar:
● la creació del raid.
● observar-ne les dades.
● fail de un disc (spare entra en acció)
● fail de un altre disc (spare entra en acció)
● eliminar els dos dic fail.
● afegir de nou els dos disc (ara fan el rol de spare)



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