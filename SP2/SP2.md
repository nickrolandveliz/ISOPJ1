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

<img width="538" height="336" alt="Captura de pantalla de 2026-01-09 13-19-55" src="https://github.com/user-attachments/assets/4656d628-3b11-48e8-98d3-2147eeeaa206" />


<img width="540" height="91" alt="Captura de pantalla de 2026-01-09 13-20-12" src="https://github.com/user-attachments/assets/27de3aa5-07ed-4abb-9059-891e11d4f9c6" />


<img width="556" height="181" alt="Captura de pantalla de 2026-01-09 13-20-22" src="https://github.com/user-attachments/assets/a55d7234-67bf-405b-9c22-7dce050a69a6" />


<img width="386" height="146" alt="image" src="https://github.com/user-attachments/assets/3d893154-f043-4991-abc4-8f2bfa0341d4" />


<img width="792" height="180" alt="image" src="https://github.com/user-attachments/assets/36818072-8db1-4a54-9515-837b5ddc0dc4" />


<img width="651" height="115" alt="image" src="https://github.com/user-attachments/assets/b7a08fb4-bb65-40eb-97ff-d2358fca4b9a" />


<img width="578" height="160" alt="image" src="https://github.com/user-attachments/assets/757911f7-3546-477c-b09b-6ae657c27b5b" />


<img width="799" height="268" alt="image" src="https://github.com/user-attachments/assets/33eae41e-7cfe-43e4-9de5-0c4c1f4b1026" />


<img width="850" height="484" alt="image" src="https://github.com/user-attachments/assets/33590278-3746-46d0-87d3-90973b8b219c" />


## ACL

### Importància de les ACL a Ubuntu

Raons principals per utilitzar ACL

1. Flexibilitat en gestió de permisos

    Superen les limitacions del model usuari/grup/altres

    Permeten assignar múltiples usuaris i grups al mateix recurs

    Ofereixen control granular d'accés

2. Escalabilitat en entorns complexos

    Necessàries en sistemes amb múltiples usuaris i grups

    Essencials en servidors compartits

    Importants en entorns corporatius

3. Seguretat més precisa

    Permeten implementar polítiques d'accés detallades

    Milloren el principi de mínim privilegi

    Faciliten l'auditoria d'accés


## Umask

Què és la umask?

Màscara que determina els permisos per defecte per a nous arxius i directoris.

Comprovar umask actual:

**umask**

<img width="298" height="46" alt="image" src="https://github.com/user-attachments/assets/8fd46c0f-b7ed-43b2-9c85-1c5606961628" />


**Usuari root**:

<img width="387" height="44" alt="image" src="https://github.com/user-attachments/assets/fae6cb65-bac7-4fd3-ab85-a7ac9dff58cf" />


## Gestió de processos

Els processos són programes en execució dins del sistema. Cada procés té un PID (Identificador de Procés), un usuari propietari i pot trobar-se en diferents estats (actiu, en espera, aturat…). El sistema operatiu planifica i reparteix el temps de CPU entre ells.
Eines bàsiques per gestionar-los

    ps, top, htop: veure processos actius.

    kill, pkill: finalitzar un procés per PID o nom.

    nice, renice: ajustar la prioritat d'execució.

    systemctl, service: controlar serveis (daemons). No l'abordarem aquí específicament.

A nivell pràctic, cada procés hereta permisos de l'usuari que l'ha iniciat i pot estar vinculat a un servei o a una sessió d'usuari.

A continuació, veurem com utilitzar-les de manera bàsica.

**Ús de pstree**

```
Paràmetre	Funció
-p	Mostra el PID de cada procés.
-u	Mostra l'usuari propietari de cada procés.
-h	Ressalta el procés actual (útil quan es filtra).
-n	Ordena processos per PID dins de cada arbre.
-a	Mostra els arguments complets del procés (línia de comandes).
```

Per filtrar un procés, podem utilitzar grep en combinació amb altres eines.

Aquí he filtrat per els processos del usuari nickrolandveliz.

<img width="714" height="397" alt="image" src="https://github.com/user-attachments/assets/a1666e62-22e6-49d7-aad6-ca60fbf2a01e" />


I aqui podem veure de root.

<img width="802" height="350" alt="image" src="https://github.com/user-attachments/assets/a075494e-668a-4b88-82b6-138f7c5d9ce1" />


**ps** Aquesta comanda, mostra informació sobre una selecció dels processos actius. Si volem una actualització repetitiva de la selecció i la informació mostrada, hauriem de usar top en comptes d’això.

Alguns dels parametres mes comuns són:

```
a: mostra processos de tots els usuaris, no només del terminal actual.
u: mostra informació en format d’usuari, amb columnes com %CPU, %MEM, USER.
x: inclou processos sense terminal associat (daemons i serveis).
-e: Mostra tots els processos del sistema, equivalent a -A.
-o: Permet personalitzar exactament quines columnes vols que surti.
i molts més
```

<img width="807" height="353" alt="image" src="https://github.com/user-attachments/assets/91387798-50d2-4d09-8d70-2bf51455def0" />

Podem filtrar per obtenir les terminals que l’usuari fa servir amb ps aux | grep usuari | grep tty

Aixó, mostra els processos d’un usuari concret que s’estan executant en terminals.

```
ps aux: mostra tots els processos amb informació detallada.
grep usuario: filtra només els processos propietat de l’usuari “usuario”.
grep tty: filtra només els processos que tenen un terminal associat (tty).
```

<img width="806" height="134" alt="image" src="https://github.com/user-attachments/assets/d5ef8fa4-b909-4d1d-a236-c735d3dfbe3f" />

Si volem matar un proces, podem fer servir kill, te diversos modes de terminar:

```
Tipus de Kill 	Senyal 	Descripció 	Comanda

Kill suau 	SIGTERM 	Demana al procés finalitzar netament 	kill PID
Kill forçat 	SIGKILL 	Mata immediatament, sense netejar recursos 	kill -9 PID
Recarregar config 	SIGHUP 	Demana al procés que recarregui la configuració 	kill -1 PID
Pausa 	SIGSTOP 	Pausa l’execució del procés 	kill -STOP PID
Continuar 	SIGCONT 	Continua un procés pausat 	kill -CONT PID
Interrupció Ctrl-C 	SIGINT 	Senyal d’interrupció (Ctrl+C) 	kill -2 PID
Abortar 	SIGABRT 	Senyal d’error abortat, sovint genera core dump 	kill -6 PID
```

Aqui tenim un exemple obrint xclock al fons amb el “&” i matant-lo suau, mentres comprovem amb ps aux que s’ha mort.

<img width="804" height="262" alt="image" src="https://github.com/user-attachments/assets/4d8cfe71-4995-4c30-9996-cbdcee901bc6" />

Tambe tenim la comanda **top**.

**Top** es una comanda que mostra informació en temps real sobre processos i l'ús del sistema.

<img width="799" height="543" alt="image" src="https://github.com/user-attachments/assets/f52d2460-0acb-4b8b-b69d-d37380334bcb" />

```
Part superior (resum del sistema):

    Temps: Temps d'execució del sistema

    Usuaris: Nombre d'usuaris connectats

    Load average: Càrrega mitjana (1, 5, 15 minuts)

    Tasques: Total, en execució, dormint, aturades, zombie

    %CPU: Ús del processador (us, sy, ni, id, wa, hi, si, st)

    Memòria: Total, lliure, usada, memòria buffer/cache

    Swap: Memòria d'intercanvi (swap) total i usada

Part inferior (llista de processos):

    PID: Identificador del procés

    USUARI: Propietari del procés

    PR: Prioritat

    NI: Valor "nice" (prioritat ajustable)

    VIRT: Memòria virtual utilitzada

    RES: Memòria resident (física)

    SHR: Memòria compartida

    %CPU: Percentatge d'ús de CPU

    %MEM: Percentatge d'ús de memòria

    TEMPS+: Temps total d'execució

    COMANDAMENT: Nom de la comanda
```

També tenim htop que es el mateix pero de manera interactiva.

<img width="795" height="576" alt="image" src="https://github.com/user-attachments/assets/fc5f2857-1fdb-4bf4-b621-eb91ab45b5ed" />

Estats principals

Codi	Estat (Català)	Descripció
R	En execució (Running)	El procés està actiu o llest per ser assignat a la CPU
W	En espera (Waiting)	El procés espera un recurs o un esdeveniment
S	Aturat (Stopped)	El procés ha estat detingut, normalment per un senyal, sovint durant depuració
Z	Zombi (Zombie)	El procés ha finalitzat però encara conserva una entrada a la taula de processos
T	Trencat	Procés aturat per depuració o per senyal de trencament
D	Dormint	Procés inactiu, esperant I/O, no pot ser interromput
I	Inactiu (Idle)	El procés està completament inactiu, sense consumir CPU; molt habitual en fils del kernel


Mostra la llista de feines (processos) que tens en execució o aturades dins de la sessió actual del terminal.

Exemple de sortida:

[1]+  Aturat     nano fitxer.txt
[2]-  Executant  sleep 100 &


Això vol dir:

[1] i [2] són els números de feina

Aturat → el procés està pausat

Executant → el procés està funcionant en segon pla

🔹 fg %1

Serveix per portar una feina del segon pla o pausada al primer pla (foreground).

fg = foreground

%1 indica la feina número 1 (segons el que mostra jobs)

En aquest cas:

fg %1

Recupera la feina número 1 i la torna a executar ocupant el terminal.

Llencar processos amb &

# Còpies de seguretat i automatització de tasques

## Teoria copies de seguretat

Còpies de seguretat

Una còpia de seguretat és una duplicació de les dades que permet recuperar informació en cas de pèrdua, dany, error humà, virus o qualsevol altre desastre. Aquestes còpies s’emmagatzemen de manera independent de les dades originals, preferiblement en un altre dispositiu, servidor o servei al núvol.

Normalment segueixen polítiques definides, com ara el temps de retenció, el nombre de versions guardades i la realització de proves de restauració per assegurar que les dades es poden recuperar correctament.

Tipus principals de còpia de seguretat
Còpia completa

Desa totes les dades cada vegada que es fa la còpia.

És la més lenta i la que ocupa més espai, però també la més segura i la més fàcil de restaurar, ja que només cal una única còpia per recuperar tota la informació.

Còpia incremental

Només guarda els canvis realitzats des de l’última còpia, sigui completa o incremental.

És molt ràpida i ocupa poc espai. L’inconvenient principal és que, per restaurar les dades, cal disposar de la còpia completa inicial i de totes les còpies incrementals posteriors.

Còpia diferencial

Guarda tots els canvis fets des de l’última còpia completa.

És més ràpida que la còpia completa i ocupa un espai intermig. La restauració és més senzilla que amb les incrementals, però cada nova còpia diferencial ocupa més espai fins que es fa una nova còpia completa.

Exemples de funcionament
Còpia completa

Dilluns: còpia completa
Dimarts: còpia completa
Dimecres: còpia completa

Si es perd un fitxer dijous, només cal restaurar la còpia completa de dimecres.

Còpia incremental

Dilluns: còpia completa
Dimarts: còpia incremental
Dimecres: còpia incremental

Per recuperar un fitxer perdut dijous, cal la còpia completa de dilluns i totes les còpies incrementals fins dimecres.

Còpia diferencial

Dilluns: còpia completa
Dimarts: còpia diferencial
Dimecres: còpia diferencial

Si es perd un fitxer dijous, cal la còpia completa de dilluns i l’última còpia diferencial, la de dimecres.

RAID i emmagatzematge

Els sistemes RAID combinen diversos discs perquè funcionin conjuntament, millorant el rendiment i/o la seguretat segons el tipus de RAID utilitzat.

RAID 0 uneix la capacitat i la velocitat de diversos discs, però no ofereix cap protecció: si un disc falla, es perden totes les dades.
RAID 1 crea una còpia mirall: les dades es dupliquen i, si un disc falla, l’altre continua funcionant.
RAID 5 i RAID 6 reparteixen les dades i la informació de paritat entre diversos discs, oferint un bon equilibri entre velocitat i seguretat.
RAID 10 combina la velocitat del RAID 0 amb la seguretat del RAID 1.

És important recordar que RAID no és una còpia de seguretat. Si s’esborren fitxers o un virus afecta les dades, l’error es replica a tots els discs.

Imatge de disc

Una imatge de disc és una còpia exacta de tot un disc o partició, incloent el sistema operatiu, els programes, la configuració i les dades. S’utilitza per clonar equips o restaurar un sistema complet tal com estava en un moment concret.

És molt completa, però requereix molt espai i temps per crear-se. A canvi, permet restaurar un ordinador sencer en molt poc temps.

Snapshot

Un snapshot és una captura instantània de l’estat d’un sistema de fitxers o d’un dispositiu d’emmagatzematge. Normalment depèn de la tecnologia utilitzada (LVM, ZFS, Btrfs, màquines virtuals, etc.) i és molt ràpid de crear, ja que només guarda els canvis fets a partir del moment en què es crea.

Els snapshots són útils per tornar enrere ràpidament o fer proves, però no són una còpia de seguretat segura si es guarden al mateix disc. Si el disc falla, el snapshot també es perd.

Resum final

La còpia de seguretat serveix per protegir les dades guardant-les en un lloc segur.
La imatge de disc copia tot el sistema exactament com és en un moment concret.
El snapshot permet tornar enrere ràpidament, però no protegeix contra fallades del mateix disc.

No s’ha de confiar només en snapshots locals com a única protecció. La millor estratègia combina snapshots per recuperacions ràpides i còpies de seguretat externes per protegir-se davant desastres.

1. cp -> Es una copia simple no inteligent nomes transfereix fitxers localment es molt simple de utilitzar pero no optimitzar
2. rsync -> Es una eina inteligent que nomes copia els fitxers modificats i la sincronitzacio pot ser local o en remot via ssh
3. dd -> Es una eina per a clonar discs o particions i no es inteligent copia tots els sectors

### Comanda cp

Comanda cp (teoria)

La comanda cp s’utilitza en sistemes operatius Linux i Unix per copiar fitxers i directoris d’una ubicació a una altra. Permet duplicar informació mantenint, si es vol, atributs com permisos, dates i propietari.

Funcionament general

cp copia un o més fitxers cap a un fitxer o directori de destí. Quan el destí ja existeix, el fitxer pot ser sobreescrit segons les opcions utilitzades. Per defecte, cp només copia fitxers; per copiar directoris cal indicar-ho explícitament.

Opcions i paràmetres principals
Còpia recursiva

Permet copiar directoris sencers amb tots els seus subdirectoris i fitxers. Sense aquesta opció, els directoris no es copien.

Mode interactiu

Fa que el sistema demani confirmació abans de sobreescriure un fitxer existent, evitant pèrdues accidentals d’informació.

Mode forçat

Sobreescriu els fitxers de destí sense demanar confirmació, fins i tot si estan protegits contra escriptura.

Mode detallat

Mostra informació del procés de còpia, indicant quins fitxers s’estan copiant.

Actualització

Només copia els fitxers que són més nous que els del destí o que encara no existeixen, estalviant temps i espai.

Conservació d’atributs

Manté els permisos, el propietari, el grup i les dates originals dels fitxers copiats.

Mode arxiu

Realitza una còpia completa conservant l’estructura, els atributs i els enllaços, i és l’opció més utilitzada per fer còpies de seguretat de directoris.

Gestió d’enllaços

La comanda pot tractar els enllaços simbòlics de diverses maneres:

Copiar l’enllaç com a enllaç

Seguir l’enllaç i copiar el fitxer real

No seguir l’enllaç i conservar-lo tal com és

També permet crear enllaços simbòlics o enllaços durs en lloc de fer una còpia real del fitxer.


### Comanda rsync

La comanda rsync és una eina de Linux/Unix utilitzada per sincronitzar fitxers i directoris entre dues ubicacions, ja sigui dins del mateix sistema, entre diferents discs o entre equips a través de la xarxa. És especialment eficient per a còpies de seguretat i transferències de dades grans.

Funcionament general

rsync compara els fitxers d’origen i destí i només transfereix les diferències, fent que sigui molt més ràpid i eficient que copiar tot el contingut de nou. Pot treballar amb fitxers locals o remots i permet mantenir atributs i permisos dels fitxers originals.

Opcions i paràmetres principals
Mode recursiu

Permet copiar directoris sencers, incloent subdirectoris i fitxers. Sense aquesta opció, només es copien fitxers individuals.

Conservació d’atributs

Manté propietari, grup, permisos, dates i atributs especials dels fitxers copiats. Això assegura que la còpia sigui exacta a l’original.

Compressió

Redueix la quantitat de dades transferides quan s’utilitza en xarxa, comprimint els fitxers durant la transmissió.

Modes detallats

Permet mostrar informació del procés de sincronització, indicant quins fitxers es transfereixen i quins ja estan actualitzats.

Actualització i sincronització

Només copia fitxers que han canviat o que no existeixen al destí, evitant duplicacions innecessàries i estalviant temps i espai.

Eliminació de fitxers obsolets

Permet eliminar del destí els fitxers que ja no existeixen a l’origen, mantenint les dues ubicacions sincronitzades exactament.

Modes segurs

Pot funcionar a través de connexions segures (per exemple SSH) quan es sincronitzen fitxers entre diferents equips, protegint la informació durant la transferència.

Enllaços i enllaços simbòlics

Rsync pot copiar enllaços simbòlics com a enllaços o bé seguir-los i copiar el contingut real, segons es configuri.

Altres funcionalitats

Permet filtrar fitxers per extensió, nom o directoris específics.

Admet transferències parcials per reprendre còpies interrompudes.

Pot funcionar de manera programada per automatitzar còpies de seguretat regulars.

És molt eficaç per sincronitzar grans quantitats de dades entre servidors, discs locals o sistemes de backup.

### Comanda dd

La comanda dd és una eina de Linux/Unix utilitzada per copiar i transformar dades a baix nivell, normalment fitxers, discs o dispositius de blocs. És molt potent i flexible, ja que treballa amb dades binàries directament i permet fer còpies exactes sector per sector.

Funcionament general

dd llegeix dades des d’una font i les escriu en un destí especificat, amb la possibilitat de transformar-les durant el procés. Es pot utilitzar per crear imatges de discs, copiar particions, fer còpies de seguretat de dispositius complets o fins i tot escriure fitxers d’arrencada.

Opcions i paràmetres principals
Input (if)

Defineix el fitxer o dispositiu d’origen d’on s’han de llegir les dades.

Output (of)

Especifica el fitxer o dispositiu de destí on s’escriuran les dades.

Block size (bs)

Permet establir la mida dels blocs de dades llegits i escrits. Ajustar aquesta mida pot millorar el rendiment de la còpia.

Count

Indica quants blocs s’han de copiar des de l’origen. Permet limitar la quantitat de dades copiades.

Skip

Permet saltar un nombre determinat de blocs al començar a llegir de l’origen, útil per treballar amb fragments de discs o fitxers grans.

Seek

Permet saltar blocs al destí abans de començar a escriure, facilitant la còpia parcial dins d’un dispositiu o fitxer.

conv

Permet aplicar transformacions a les dades durant la còpia, com per exemple canviar majúscules/minúscules, convertir entre formats o truncar dades.

Status

Mostra informació del progrés de la còpia, útil en operacions amb grans quantitats de dades.


## Quotes d'usuari

Que es una quota?

En Linux, una quota és un mecanisme de control d’ús d’espai i fitxers dins d’un sistema de fitxers. Serveix per limitar la quantitat de disc o nombre d’inodes (fitxers) que un usuari o grup pot utilitzar, evitant que una sola persona ocupi tot l’espai i afecti la resta de l’equip.

```
edquota -u usuari -> veure quotes un usuari

setquota -u usuari -> establir quotes 1 usuari

repquota /dev/sdb1 -> informe quotes de tots els usuaris el que ocupen

quotaon /mnt/dades -> activar

quotaoff /mnt/dades -> desactivar

quotacheck -cug /mnt/dades -> crear arxius per a quotes usuari i grup si no estan per defecte
```

Per dur a terme aquesta part necesitem instalar el paquet **quota**.

<img width="624" height="233" alt="image" src="https://github.com/user-attachments/assets/8ff1a8ba-3875-4d86-ae7a-bef12aa2ffb3" />

Ara crearem una carpeta anomenada dades.

<img width="418" height="84" alt="image" src="https://github.com/user-attachments/assets/17b454c3-3308-4e83-847f-8b40a24654ca" />

I farem el muntatge de aquesta carpeta permanentment, ademes aquí afegirem usrquota i grpquota per a que puguesim configurar les quotes aqui.

<img width="806" height="333" alt="image" src="https://github.com/user-attachments/assets/a8534df8-15c9-46cb-a9b0-a9ddef3a7cee" />

Fem un reboot i amb aquesta comanda podem comprovar que esta muntat correctament.

<img width="755" height="287" alt="image" src="https://github.com/user-attachments/assets/f9e291f8-beba-4d98-a48c-aefe4b00a7d6" />

Amb aquesta comanda podem generar els 2 arxius per a les quotes.

<img width="493" height="65" alt="image" src="https://github.com/user-attachments/assets/ce63ad16-afb8-4c40-b1ce-3d3959c3e5a1" />

I amb aquesta comanda activem les quotes.

<img width="415" height="26" alt="image" src="https://github.com/user-attachments/assets/328cc77f-f3d9-47a7-99c9-97b3f2e51633" />

Ara farem la quota per al usuari gina.

<img width="508" height="47" alt="image" src="https://github.com/user-attachments/assets/f0d4cb74-3713-449d-bbbc-5abb403c5d1b" />

I li direm el maxim que pot arribar a gastar en espai amb aquella carpeta.

<img width="804" height="126" alt="image" src="https://github.com/user-attachments/assets/89f8f407-a1d7-4f14-8d53-b3b75085346b" />

Amb aquesta comanda podem veure els dies de gracia.

<img width="712" height="284" alt="image" src="https://github.com/user-attachments/assets/de0030be-487c-4a32-934f-ea63117bed60" />

Ara entrem desde el usuari gina i anem a la carpeta aquesta.

<img width="545" height="219" alt="image" src="https://github.com/user-attachments/assets/8f2c871f-ece3-4378-a161-60c65986c3b7" />

Podem veure que per al usuari gina ens apareix.

<img width="721" height="180" alt="image" src="https://github.com/user-attachments/assets/06db0c71-883a-4ff4-b39e-17ce6ce9f16f" />

Canviarem permisos i amb aquesta comanda crearem un arxiu.

<img width="432" height="173" alt="image" src="https://github.com/user-attachments/assets/f411b6fb-abc6-4356-9078-83adf6062ded" />

<img width="616" height="89" alt="image" src="https://github.com/user-attachments/assets/6d2f23d1-ae14-4468-bfd6-23b17dad11e2" />

I tornem a crear un altre arxiu per a ocupar espai amb aquesta carpeta.

<img width="621" height="88" alt="image" src="https://github.com/user-attachments/assets/adccb718-b27c-419c-9734-e0ff7a8d7f16" />

Si observem estem apunt d'excedirnos del limit.

<img width="719" height="180" alt="image" src="https://github.com/user-attachments/assets/2276dd72-56b4-459a-8af9-167b4f7f23c1" />

Finalment crearem un altre arxiu.

<img width="663" height="112" alt="image" src="https://github.com/user-attachments/assets/d46cf1c8-81f8-4619-baf7-5132f7fd6230" />

I aquest no se ha afegit ja que ens hem excedit.

<img width="555" height="219" alt="image" src="https://github.com/user-attachments/assets/dd61b691-8636-4e5e-bca0-b7db4bfb08e0" />

I si creo un altre arxiu ja no hem deixara.

<img width="629" height="154" alt="image" src="https://github.com/user-attachments/assets/1a055305-684f-451c-be2c-49b1c0ef6869" />

Amb aquesta comanda podem modificar els dies de gracia.

<img width="714" height="174" alt="image" src="https://github.com/user-attachments/assets/aa9915c0-e8b1-4caf-8ca8-0460bd435074" />

