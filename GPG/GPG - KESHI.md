# M11-SAD Seguretat i alta disponibilitat
## Escola Del Treball
### 2HISX 2021-2022
### Aaron Andal

https://geekland.eu/aprender-markdown-en-minutos/ 

#### EMOJIS CHEATSHEET

👹 🤬  😍 🥰  🥺  👾  👽  👍  🔥  🌈 ☀️  🌤 ☄️  🚧 ☢️ 

☣️ ⛔️  💮  🆚 ❗️ ❗️ ❗️ ❓ ❓  💯 ❤️‍🔥  💛  🧡  💟 


# Rubén Rodríguez García
# GPG (GNU Privacy Guard)

### Apunts generals:
PGP --> Pretty Good Privacity (Software de xifrat de privacitat / seguretat).

GNU --> Va crear GPG (Software lliure).

**Els següents individus (Alice i Bob), és volen communicar de manera segura, com ho fan?**

Mitjançant *criptografía simètrica* (secret compartit).

* Info: La velocitat de transformació és + ràpida que la 'asmètrica', el cost computacional és - petit i les claus són + petites

El receptor com sap el 'secret' pot rebre, l'inconvenient, és que el 'secret' és comparti, llavors apareix...

*Criptografía asimètrica* (Cada usuari té una clau privada i una clau pública).

* Info: La velocitat de transformació és + lenta, el cost computacional és + gran i les claus són + grans.
* Inconvenient: No té rendiment per poder processar en fluxe contínu el tràfic *'in-motion'*.

Encara això, **LES DOS CLAUS SÓN IGUAL DE SEGURES, S'UTILITZEN PER PROPÒSITS DIFERENTS**.

L'objectiu de la clau privada és que **NOMÉS** la pot tenir **EL PROPIETARI**.

L'objectiu de la clau pública és **PROPAGARLA**, quan més persones la coneguin, millor.

Les dues claus formen un 'joc' conjunt, el que una fà, l'altra ho desfà.

**Com pot fer l'Alice per enviar-li un missatge secret a Bob fent servir 'criptografía asimètrica'?**

L'Alice enviarà el **missatge + clau pública** d'en Bob, i aquest ho rebrà amb la seva pròpia clau privada (aquesta només la te ell perquè és la SEVA clau privada)

*Xifrar / desxifrar*

Quan en Bob **Xifri + possi la seva clau privada** llavors obtindrà el missatge original.

*Signar:*

* Autoría --> Comprovar que l'autor del document en qüestió és qui diu ser.
* Integritat --> Comprovar que el document no ha sigut modificat.
* No repudi --> No pots dir que no has sigut tú.

**GPGs --> criptografía simètrica, criptografía asimètrica, xifrar / desxifrar, signar.**

**Com fa l'Alice per enviarun document signat al Bob?**

Agafa el missatge, i a aquest li aplica una transformació amb la seva clau privada i ho envía (perquè vol demostrar que és seu).

El Bob agafa el missatge signat, i li aplica la clau pública de l'Alice (quan fa això pot extreure el missatge original).

*Criptografía híbrida* --> El client i el servidor fan servir *'asimètric'* per acordar un **'secret'** compartit, llavors el **'tub'** de transmissió de dades serà *'simètric'*

*Hash / Funció Resum* --> MD5, SHA2. Donat un contingut, genera un resum (aquest, és únic, si canviem alguna cosa, el HASH serà totalment diferent) (256 o 512 bits --> l'actual).

La probilitat de que el HASH geenrat sigui igual a un altre, és pràcticament imposible (99%).

S'utlitza molt en les operacions de signatura.

Donat un document (missatge), és genera el HASH del missatge, és signa amb la clau privada (és transforma) i s'envía. De manera que, l'Alice i en Bob, en lloc de signar el missatge, el missatge s'envía tal qual i és signa el HASH.

El destinatari rep el missatge i del missatge que rep, calcula el HASH. (Quan aplica la clau pública d'Alice sobre el missatge, obté el HASH, ademés és demostra que és de l'Alice si el HASH és el mateix que ha enviat l'Alice).

PKI --> Publick Key Infrastructure (model de seguretat).

GPG funciona en el model 'Web Of Trust' (Xarxa de confiança).

Web Of Trust --> Cada usuari ha de decidir en qui confía.


#### GPG MANUAL

* **Pretty Good Privacity**. Es un cifrado de seguridad. Ofrece seguridad en las comunicaciones.

* No le gusta al tio SAM. (Linux)

* Tener cuidado con los delincuentes.

* En el libro en el código estaba en código C --> Lo pasa en C y tienes tu programa.

* PGP es el ORIGINAL.

* GNU hizo la versión pública.

* **GNU PG --> GPG** 

---------------------------

* ALICE

* BOB

* Se quieren comunicar de forma segura.

* Con criptografía simétrica.

    * Hay un secreto compartido.

    * El emisor encripta su secreto y el receptor, como conoce el secreto, lo desencripta.

    * El secreto tiene que ser compartido.

* Criptografía **asimétrica**

    * Cada usuario tiene una **CLAVE PRIVADA** Y UNA **CLAVE PÚBLICA**.

    * Es un secreto privado.

    * La clave **PÚBLICA** es *propagarla* a cualquier host.

* Las 2 claves hacen algo conjunto, las 2 hacen y las dos deshacen. Funcionan por **PAREJAS**.- ---> **ASIMÉTRICA**



### ENVÍO ASIMÉTRICA

* El EMISOR envía y firma su mensaje con SU CLAVE PRIVADA.

* EL RECEPTOR recibe y desencriba el mensaje con al CLAVE PÚBLICA del EMISOR.


* Si hay clave pública y clave privada es **ASIMÉTRICA**

#### Ejemplo

1. Alice envía el MENSAJE FIRMADO y lo CIFRA con la CLAVE PRIVADA la de ALICE.

2. BOB recibe el Mensaje FIRMADO de ALICe y lo DESENCRIPTA con la clave pública de ALICE.

3. Se recibe el MENSAJE.




### ENVÍO SIMÉTRICA

* Velocidad transformación y coste de envío es más rápida que la asimétrica.

* El coste computacional es más pequeño.

* Las claves son más pequeñas.

* Los algoritmos son más pequeños y más eficientes.

* Todo contrasta con el ASIMÉTRICO

    * Más lento.

    * Más costoso de Mem/CPU

    * Claves más grandes.


**LA ASIMÉTRICA NO ES MÁS SEGURA**

**LA SIMÉTRICA PESA MENOS**

**LAS DOS SON IGUAL DE SEGURASS**


**EL SECRETO RADICA EN QUE PUEDES COMPARTIR UN SECRETO O NO**.

* NO HAY UNA MÁS SEGURA QUE EL OTRO, SE USAN POR PROPÓSITOS DIFERENTES.

* Igual de segurs uno y otro.


* **TLS/SSL = DATA IN MOTION (VIAJA EN CRIPTOGRAFÍA SIMÉTRICA)**

* **Certificado DIGITAL** es **CLAVE PUBLICA y CLAVE PRIVADA**.


#### CRIPTOGRAFÍA HÍBRIDA

* El **cliente** y el **SERVER** usan **ASIMÉTRICO** para establecer un **SECRETO COMPARTIDO**. --> El tubo de transmisión de datos es **SIMÉTRICO**.


* SSH usa clave pública / clave privada --> Pero solo para HOST.

* Se negocia una clave principal de SESIÓN y luego se negocia una CLAVE en que se ENVIAN los datos.

    * Cada 60 SEGUNDOS, o K , cambiaremos la CLAVE DE TRANSMISIÓN.

    * Un atacante que intenta atacar con el WIRESHARK, no le servirá porque no tendrá mucho tiempo, para rebentar la **clave de transmisión**. 

    * ASIMÉTRICA nos sirve para VALIDAR en un BANCO y eso y SIMETRICO para **ENVIO DE DATOS**.



#### HASH

* Donado un contenido - Genera un RESUMEN.

* MD5

* SHA2

* Este resumen es único. Si se modifica algo, se crea otro hash.


* El HASH + FIRMA (Se Cifra con la Clave Privada.)

* Se firma el HASH.

* El destinatario recibe el MENSAJE HASH y calcula el HASH RECIBIDO.


ALICE                   BOB

[MENSAJE] --------------> [MENSAJE-RECIBIDO]

([HASH] + SIGNA Hash (Clau Privada)) ---> [HASH-SIGNAT] + CLAU PUBLICA ALICE 


                                    ----> SE GENERA OTRO **HASH** PARA VERIFICAR CON EL ORIGEN. 

* Se demuestra que son iguales.

    * Si no se ha falsifidado o tempered



* HASH es donado el contenido ORIGEN, se GENERARÁ SIEMRPE EL MISMO HASH.

    * Se verifica con el EMISOR si es la MISMA.

    * Se obtiene el MENSAJE ORIGINAL.

    * Desenlace con la clave pública de ALICE demuestra que el HASH es el CORRECTO.




**Ejemplo**

* Se aplica una transformación. 

* Una vez descifrada el HASH RECIBIDO, se desencripta el MENSAJE y se verifica con la clave pública del EMISOR si coincide con el MENSAJE ORIGINAL y el HASH del EMISOR.

--------------------------------------------------------------



**EJERCICIOS**

* adduser pere | marta | user

* useradd -m -s /bin/bash user

* gpg --gen-key (User Pere) 

```
pere@i11:~$ gpg --gen-key
gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

gpg: directory '/home/pere/.gnupg' created
gpg: keybox '/home/pere/.gnupg/pubring.kbx' created
Note: Use "gpg --full-generate-key" for a full featured key generation dialog.

GnuPG needs to construct a user ID to identify your key.

Real name: Pere Pou Prat
Email address: pere@edt.org
You selected this USER-ID:
    "Pere Pou Prat <pere@edt.org>"

Change (N)ame, (E)mail, or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: Permission denied
Key generation failed: Permission denied

```

* pere@i11:~$ export GPG_TTY="$(tty)"

* pere@i11:~$ gpg --full-generate-key


**SON PAREJAS DE CLAVES PUBLICA - PRIVADA**

```
pere@i11:~$ gpg --full-generate-key
gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 

```


* TIPOS:

    * RSA = Nueva versión del DSA.

    * Elgamal = Otro algorismo.


* Enter --> Genera un RSA Key de 1024 Keys.

    * Por defecto da 3072 de tamaño.


* TIME

```
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 


```

* Por defecto da 0 (No expira nunca).



```
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Pere Pou Prat
Email address: pere@edt.org
Comment: lo pere d'alcarràs
You are using the 'utf-8' character set.
You selected this USER-ID:
    "Pere Pou Prat (lo pere d'alcarràs) <pere@edt.org>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: agent_genkey failed: Permission denied
Key generation failed: Permission denied

```


#### DA ERROR

* pere@i11:~$ ls -l $(tty)
crw--w---- 1 www-data tty 136, 0 Feb 22 11:51 /dev/pts/0
pere@i11:~$ sudo chown pere $(tty)
pere@i11:~$ ls -l $(tty)
crw--w---- 1 pere tty 136, 0 Feb 22 11:51 /dev/pts/0
pere@i11:~$ 


1. Añadir el USUARIO al SUDO. sudo adduser pere sudo

2. IMPORTANTE TIENE QUE ESTAR EL USUARIO DE LA SESIÓN DE TERMINAL COMO PROPIETARIO DE LA TERMINAL.

3. SU -L PERE 

4. ls -l $(tty)

5. sudo chown pere $(tty)


```
pere@i11:~$ ls -l $(tty)
crw--w---- 1 www-data tty 136, 0 Feb 22 11:51 /dev/pts/0
pere@i11:~$ sudo chown pere $(tty)
pere@i11:~$ ls -l $(tty)
crw--w---- 1 pere tty 136, 0 Feb 22 11:51 /dev/pts/0
pere@i11:~$ gpg --full-generate-key
gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
  (14) Existing key from card
Your selection? 
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (3072) 
Requested keysize is 3072 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 0
Key does not expire at all
Is this correct? (y/N) y

GnuPG needs to construct a user ID to identify your key.

Real name: Pere
Name must be at least 5 characters long
Real name: Pere Papito
Email address: pere@edt.org
Comment: Hola
You selected this USER-ID:
    "Pere Papito (Hola) <pere@edt.org>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
gpg: /home/pere/.gnupg/trustdb.gpg: trustdb created
gpg: key F8C029DA130F5D1B marked as ultimately trusted
gpg: directory '/home/pere/.gnupg/openpgp-revocs.d' created
gpg: revocation certificate stored as '/home/pere/.gnupg/openpgp-revocs.d/42DE3CC00E0A6A88F116304BF8C029DA130F5D1B.rev'
public and secret key created and signed.

pub   rsa3072 2022-02-22 [SC]
      42DE3CC00E0A6A88F116304BF8C029DA130F5D1B
uid                      Pere Papito (Hola) <pere@edt.org>
sub   rsa3072 2022-02-22 [E]

```


#### .GNUPG [DIR DE RECOVACIONES - COSES PRIVADES]


6. Accedemos a la carpeta **.gnupg**

    * RING es **LLAVERO** no es ANILLO.

    * Es un llavero de **CLAVES**.

    * pubring = **LLAVERO**.

#### GPG --LIST-KEYS

7. gpg --list-keys

```
pere@i11:~/.gnupg$ gpg --list-keys
gpg: checking the trustdb
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
/home/pere/.gnupg/pubring.kbx
-----------------------------
pub   rsa3072 2022-02-22 [SC]
      42DE3CC00E0A6A88F116304BF8C029DA130F5D1B
uid           [ultimate] Pere Papito (Hola) <pere@edt.org>
sub   rsa3072 2022-02-22 [E]

pub   rsa3072 2022-02-22 [SC]
      EDC60BDECEAB275809A4C17EE4A32747748C67BE
uid           [ultimate] Pere Papito Perez (secret) <pere@edt.org>
sub   rsa3072 2022-02-22 [E]

pere@i11:~/.gnupg$ 

```

* Es una clave RSA3072 -- 2022-02-22 [SC] --> Signar i fitxhear

* Descripció i correu - Cualquiera sirve para describir la clave.

* [Ultimate] --_> Cuando confia PERE, realmente sea de PERE.


---

* Los leones exportan las claves públicas y compartirlas.










----

#### EXPORTAR

* gpg --output /tmp/pere.gpg --export pere@edt.org

* ls /tmp/pere.gpg

* file /tmp/pere.gpg

* cat /tmp/pere.gpg

    * Está representado en BINARIO.

---

* gpg --armor --output /tmp/pere.pem --export pere@edt.org

* file /tmp/pere.pem

* cat /tmp/pere.gpg

    * Es el clasico formato PEM de los DOCUMENTOS.

        * El BINARIO se le añade Base64 (Se le añade una CABECERA Y UN PIE) y se genera ASCII.

        * Se le añade una cabecera (BEGIN...) y en el pie (Lo cierra).

* Es la clave **pública de PERE**









#### HOY 23.02.22 GPG

**LEER practica1.md**



