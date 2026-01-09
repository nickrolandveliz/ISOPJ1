---
layout: custom
title: "SPRINT 2: INSTAL·LACIÓ, CONFIGURACIÓ DE PROGRAMARI DE BASE I GESTIÓ DE FITXERS"
---

# SISTEMES DE FITXERS I PARTICIONS

## Mida de sector
És la unitat mínima física on es guarden les dades en un disco i per defecte són 512 bytes, no es pot canviar la mida

## Mida block
És la unitat mínima lògica on es guarden les dades a nivell d'OS i per defecte 4096 bytes, es pot canviar la mida quan formateixes un disco

Exemple: 
 * Amb aquest cas podem veure amb la primera comanda el que pesa el text "Bon dia" (8 bytes), i amb la segona comanda podem observar la mida en disc, aquest es l'espai minim que el sistema de fitxers reserva per a un fitxer
<img width="525" height="155" alt="image" src="https://github.com/user-attachments/assets/ec604926-4a11-4b47-8a1b-05c821f4dca3" />


## Fragmentacio interna
És quan es desaprofita espai perque els blocs són massa grans per al que s'ha de guardar dins.

## Fragmentació externa
És quan a mesura que vas treballant l'espai lliure total es va trencant en petits trossos separats.

## Tipus de formateig
 * Baix nivell

Borrra sistemes de fitxers, borra formateig, etc. És a dir, que borra totes les dades i el deixa com a nou. Des del sistema operatiu no es pot formatar, es necessiten programes adients

 * Mig nivell

Només borra sistema de fitxers pero si hi han sectors defectuosos els marca pero no els arregla.

 * Alt nivell

El format d'alt nivell només borra el sistema de fitxers.

## Gestió de particions
És una agrupació logica de particions i/o discos, es posar una capa d'abstracció damunt de les particions.

## Comandes
 * Amb la comanda 'fdisk -l' podem veure l'espai.
<img width="619" height="198" alt="image" src="https://github.com/user-attachments/assets/5cf0d9cb-dc84-4766-932b-9ba92d78eca9" />


 * Amb aquesta comanda podem mirar la mida del block de la partició, i filtrem amb grep per la paraula "Block".
<img width="622" height="87" alt="image" src="https://github.com/user-attachments/assets/304bc236-f8ec-43d3-9618-9ca4d9493b8a" />


 * Per a la fragmentació externa podem fer-ho amb la comanda "e4defrag", aqui ens indica si fa falta fragmentar alguna partició.
<img width="622" height="293" alt="image" src="https://github.com/user-attachments/assets/57ff222c-0fad-430f-b7d2-d8df7a69fe80" />


 * En cas de voler-ho fragmentar podem executar la comanda pero sense el parametre "-c". Sense "-c" es desfragmentaria.
<img width="624" height="306" alt="image" src="https://github.com/user-attachments/assets/6f2b93f8-edc9-4e2b-ac46-eca585e082eb" />


## GPARTED
 * Primerament, diem que gparted es el editor de particions de GNOME per a crear, reorganitzar i eliminar particions de disc.
 * Permet triar el sistema de fitxers (FAT32, EXT4, NTFS...) pero no es pot modificar la mida del block.

# Via interficie gràfica (GPARTED)
Els passos a seguir son primerament executem l'eina i seleccionem el disc dalt a la dreta.
<img width="618" height="194" alt="image" src="https://github.com/user-attachments/assets/d99f48a8-a880-4866-ad43-0e17ac9f75db" />
 * Ara anirem a "Dispositivo" i "Crear tabla de particiones".











# Via CLI (Command Line Interface)
Per realitzar-ho farem amb la comanda **fdisk**.
Anteriorment com que ja identificat quina es la meva partició, un cop ja ho sabem executem la comanda i seguim els passos que s'observen a la captura de pantalla.
<img width="689" height="339" alt="image" src="https://github.com/user-attachments/assets/f123d20f-fd14-413a-bd0f-fde8b862dd1c" />

 * Ara creem la partició
<img width="690" height="268" alt="image" src="https://github.com/user-attachments/assets/e5928bd8-fe58-4b34-862b-0c4ddc552d8c" />

 * Aqui podem observar que esta creat correctament 
<img width="553" height="219" alt="image" src="https://github.com/user-attachments/assets/5a7ed630-2237-44e2-8d80-09f3095beafc" />


 * Ara amb la comanda "mkfs.ext4" podem canviar la mida del bloc amb aquest cas ho posare amb **2048**.
<img width="562" height="230" alt="image" src="https://github.com/user-attachments/assets/288ff108-65f3-43c4-bf09-31ccf03a5157" />

 * I podem comprovar-ho amb aquesta comanda. 
<img width="447" height="62" alt="image" src="https://github.com/user-attachments/assets/a1aba64a-b911-4978-ba39-7eb8a85065fe" />

 * I a l'altra partició com **NTFS** per a que Windows ho reconeixi.
<img width="489" height="59" alt="image" src="https://github.com/user-attachments/assets/90a70c56-110c-45ce-a39d-5c433b3a3360" />
<img width="474" height="46" alt="image" src="https://github.com/user-attachments/assets/1fa66097-8d33-4026-b251-75bfead538c8" />

 * Finalment podem entrar al **GPARTED** i comprovar-ho.
<img width="560" height="189" alt="image" src="https://github.com/user-attachments/assets/3a6d1c98-f778-404b-9753-3a8a0661a512" />


### Muntatge

 * Per fer aquest apartat primerament començarem creant una carpeta i arxiu a la ruta **/mnt**.
<img width="418" height="79" alt="image" src="https://github.com/user-attachments/assets/8327e6c5-37ad-4527-a40e-ccb9d63d79cf" />

 * Muntem temporalment amb ```mount -t ext4 /dev/sdb1``` **/mnt/particio1, i afegim un arxiu dintre.
<img width="561" height="85" alt="image" src="https://github.com/user-attachments/assets/3f6a33b7-4cf7-40a1-a1e0-864c0f98a5c2" />

 * Si reiniciem la partició que acabem de muntar ja no es trobara, pero els arxius que hem creat no se han borrat ja que encara estan emmagatzemades al disc.

 * A continuació podem fer-ho de manera persistent. Per fer-ho editarem el fitxer **/etc/fstab**.
<img width="562" height="223" alt="image" src="https://github.com/user-attachments/assets/3cb5e15b-d12d-48fd-9147-b8b90f309ad3" />

 * Si ara reiniciem amb aquest cas es persistent.
<img width="361" height="36" alt="image" src="https://github.com/user-attachments/assets/56a18098-2ca1-4ec4-b352-a84caef602eb" />

## Gestió de processos
Un procés eés la instància d'un programa en execució. A cadascun se li assigna un identificador únic (PID), està associat a un usuari propietari i pot trobar-se en diversos estats (com ara en execució, en espera o aturat). El sistema operatiu és el responsable de la planificació i la distribució del temps de CPU entre tots els processos.

## Eines bàsiques de gestiío de processos

Per gestionar els processos, disposem d'unes eines fonamentals:

    Per visualitzar-los:

        ps, top, htop → Mostren els processos actius.

    Per finalitzar-los:

        kill, pkill → Tanquen un procés pel seu PID o nom.

    Per gestionar la prioritat:

        nice, renice → Ajusten la prioritat d'execució.

    Per controlar serveis (daemons):

        systemctl, service → Inicien, aturen o reinicien serveis del sistema.

**Aspectes pràctics**: Cal recordar que un procés hereta els permissos de l'usuari que l'ha llançat i pot estar associat tant a un servei del sistema com a una sessió d'usuari.

 * A continuació, veuremcom utilitzar aquestes eines  a nivell bàsic.

## Gestió d'usuaris i grups i permissos

El model de seguretat de Linux es basa enels conceptes d'usuaris i grups, que defineixen de manera precisa qui pot accedir, modificar o executar arxius i processos al sistema.

### Tipus d'usuaris

**Usuari normal**: Un usuari estandard que pot iniciar sessio i treballar dins del seu entorn i espai personal. Els seus permissos són limitats per protegir la integritat del sistema.

**Superusuari (root)**: L'administrador del sistema. Té accés i control absolut sobre totes les operacions i arxius. S'ha d'utilitzar amb extrema cura.

**Usuari de servei(Daemon)**: Comptes especials creats per a l'execució de serveis o aplicacions (com www-data per a un servidor web o mysql per a la base de dades). No poden iniciar sessió interactiva.

**Usuari de sistema**: Són similar als usuaris de servei i solen tenir un UID (User ID) baix (normalment per sota 1000). Estan reservats per a processos i funcions internes del sistema operatiu.

### Grups
Un grup és una col·lecció d'usuaris que comparteixen els mateixos permisos sobre certs arxius o directoris. Cada usuari pertany a:

    Un grup principal, que es defineix al crear l'usuari.

    Múltiples grups secundaris, als quals es pot afegir posteriorment.

Els grups són una eina essencial per a la gestió eficient de permisos, ja que permeten, per exemple, concedir accés a una carpeta compartida a tot un equip de treball d'una sola vegada, en lloc de configurar els permisos per a cada usuari individualment.

## Fitxers importants

 * En Linux, la informació d'usuaris i grups es gestiona de manera centralitzada mitjançant fitxers de configuració de text ubicats dins del directori **/etc**.

Explicació **/etc/passwd**:
<img width="777" height="503" alt="image" src="https://github.com/user-attachments/assets/97534db9-7302-4cd1-8af0-4f0f6101a492" />

Cada línia representa un usuari i conté 7 camps separats per dos punts:

**nom_usuari:x:UID:GID:GECOS:directori_home:shell**

Descripció detallada de cada camp

1. **nom_usuari**

    Exemple: root, anna, mysql

    Descripció:

        Nom únic que identifica l'usuari al sistema

        És el que s'utilitza per iniciar sessió

        Normalment té un màxim de 32 caràcters

2. **x (camp de contrasenya)**

    Exemple: x, *, !

    Descripció:

        x indica que la contrasenya està emmagatzemada a /etc/shadow

        * o ! vol dir que el compte està blocat

        Si està buit, l'usuari no té contrasenya (insicur)

3. **UID (User ID)**

    Exemple: 0, 1000, 33

    Descripció:

        Número d'identificació únic de l'usuari

        0 = usuari root (superusuari)

        1-999 = usuaris del sistema (serveis)

        1000+ = usuaris normals

4. **GID (Group ID)**

    Exemple: 0, 1000, 33

    Descripció:

        Número del grup principal de l'usuari

        Defineix els permisos per defecte per a nous arxius

5. **GECOS (Informació addicional)**

    Exemple: Anna Garcia,,,, Pere Lopez,Vendes,555-1234

    Descripció:

        Informació opcional sobre l'usuari

        Normalment només s'inclou el nom complet

        Format: Nom complet,Despatx,Telefon,Altres

6. **directori_home**

    Exemple: /home/anna, /root, /var/www

    Descripció:

        Directori personal de l'usuari

        On s'emmagatzemen els seus arxius personals

        Directori per defecte en iniciar sessió

7. **shell**

    Exemple: /bin/bash, /bin/sh, /usr/sbin/nologin

    Descripció:

        Intèrpret d'ordres que s'executa en iniciar sessió

        /bin/bash = shell Bash normal

        /usr/sbin/nologin o /bin/false = no permet inici de sessió (comptes de servei)

Explicació **/etc/shadow**:

<img width="487" height="492" alt="image" src="https://github.com/user-attachments/assets/b4605343-ecd6-48b2-888e-fdaf44992815" />

L'arxiu /etc/shadow conté la informació de les contrasenyes dels usuaris i les polítiques d'expiració. És un arxiu segur que només pot llegir l'usuari root.

Cada línia representa un usuari i conté 9 camps separats per dos punts:

**nom_usuari:contrasenya_encryptada:darrers_canvis:minims:maxims:avis:inactiu:caducitat:camp_reserva**

Descripció detallada de cada camp

1. **nom_usuari**

    Exemple: root, anna, mysql

    Descripció:

        Nom de l'usuari (ha de coincidir amb /etc/passwd)

        Serveix com a clau d'enllaç entre els dos arxius

2. **contrasenya_encryptada**

    Exemple: $6$rounds=5000$t..., *, !!

    Descripció:

        Contrasenya encryptada amb hash

        * o !! = compte blocat o sense contrasenya

        Format: $algoritme$salt$hash

        Algoritmes comuns: $1$ (MD5), $5$ (SHA-256), $6$ (SHA-512)

3. **darrers_canvis (last change)**

    Exemple: 19157, 0

    Descripció:

        Data de l'últim canvi de contrasenya en dies des de l'1/1/1970

        0 = ha de canviar-la en el proper login

        19157 = 19,157 dies des de l'1/1/1970

4. **minims (minimum days)**

    Exemple: 0, 7

    Descripció:

        Dies mínims que han de passar abans de poder canviar la contrasenya

        0 = es pot canviar en qualsevol moment

5. **maxims (maximum days)**

    Exemple: 99999, 90

    Descripció:

        Dies màxims que la contrasenya és vàlida

        99999 = quasi etern (273 anys)

        90 = ha de canviar-la cada 90 dies

6. **avis (warning days)**

    Exemple: 7, 0

    Descripció:

        Quants dies abans de la caducitat s'envia un avís

        7 = avisa 7 dies abans que caduqui

7. **inactiu (inactive days)**

    Exemple: -1, 30

    Descripció:

        Dies de gràcia després de caducar abans que el compte es desactivi

        -1 = sense període d'inactivitat

8. **caducitat (expiration date)**

    Exemple: ``, 20000

    Descripció:

        Data absoluta de caducitat del compte en dies des de l'1/1/1970

        Buit = el compte no caduca mai

9. **camp_reserva (reserved field)**

    Exemple: (buit)

    Descripció:

        Camp reservat per a ús futur

        Normalment està buit

Explicació **/etc/group**:
<img width="493" height="500" alt="image" src="https://github.com/user-attachments/assets/e73d0813-041e-4194-a34b-a243902469b2" />

L'arxiu /etc/group conté la informació dels grups del sistema i els seus membres. Defineix els grups d'usuaris i les seves relacions.

Estructura de cada línia

Cada línia representa un grup i conté 4 camps separats per dos punts:

**nom_grup:contrasenya_grup:GID:llista_membres**

Descripció detallada de cada camp

1. **nom_grup**

    Exemple: root, users, sudo, www-data

    Descripció:

        Nom del grup

        Ha de ser únic al sistema

        Normalment en minúscules

2. **contrasenya_grup**

    Exemple: x, *

    Descripció:

        x indica que la contrasenya del grup està a /etc/gshadow

        * o buit = no hi ha contrasenya de grup

        Rarament s'utilitza en sistemes moderns

3. **GID (Group ID)**

    Exemple: 0, 100, 1000, 33

    Descripció:

        Número d'identificació únic del grup

        0 = grup root

        1-999 = grups del sistema

        1000+ = grups d'usuaris normals

4. **llista_membres**

    Exemple: anna,pere,marta, root, (buit)

    Descripció:

        Llista d'usuaris que són membres del grup, separats per comes

        No inclou l'usuari que té aquest grup com a grup primari

        Buit = cap usuari addicional al grup

Explicació **/etc/gshadow**:
<img width="624" height="617" alt="image" src="https://github.com/user-attachments/assets/f0346d0e-ba56-4f4e-9479-bccbca7f17ea" />

L'arxiu **/etc/gshadow** conté la informació segura dels grups, incloent contrasenyes de grup i administradors. És la contrapart segura de **/etc/group**.

Estructura de cada línia

Cada línia representa un grup i conté 4 camps separats per dos punts:

**nom_grup:contrasenya_encryptada:administradors:membres**

Descripció detallada de cada camp

1. **nom_grup**

    Exemple: root, sudo, developers

    Descripció:

        Nom del grup (ha de coincidir amb /etc/group)

        Serveix com a clau d'enllaç entre els dos arxius

2. **contrasenya_encryptada**

    Exemple: !, $6$rounds=5000$..., *

    Descripció:

        Contrasenya encryptada per canviar al grup amb newgrp

        ! o * = no hi ha contrasenya de grup

        Contrasenya vàlida = hash encryptat

        Rarament s'utilitza en sistemes moderns

3. **administradors**

    Exemple: anna,root, pere, (buit)

    Descripció:

        Llista d'usuaris que poden gestionar el grup

        Poden afegir/eliminar membres i canviar la contrasenya del grup

        Separats per comes

4. **membres**

    Exemple: marta,jordi, user1,user2, (buit)

    Descripció:

        Llista d'usuaris que són membres del grup

        Ha de coincidir amb el camp de membres de /etc/group

        Separats per comes

També tenim l’utilitat que ve en instal·lar **gnome-system-tools**. Que permet un poquet més.

<img width="774" height="311" alt="image" src="https://github.com/user-attachments/assets/99ff8e3e-2057-472f-8792-b49d3fc1ccc9" />

## Comandes bàsiques

### Adduser

<img width="774" height="501" alt="image" src="https://github.com/user-attachments/assets/bdbfc45d-4a0a-47cb-ad16-ffae9f8925d5" />

### Userdel
 * Aqui elimino el usuari.

<img width="646" height="187" alt="image" src="https://github.com/user-attachments/assets/69749400-bb1e-425b-85de-3e7e689e2987" />

 * Aqui creo l'usuari amb useradd i faig les comprovacions adients. Tambe canvio el tipus de shell.





### Permisos



