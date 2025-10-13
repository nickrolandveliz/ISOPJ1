--- 
layout: default
title: "Sprint 1: Instal·lació i COnfiguració Inicial"
---

## Virtualització i instal·lació del SO Ubuntu
Per comenzar amb aquesta practica entrarem dins del nostre VirtualBox i crearem una nova maquina que la direm "UbuntuDesktop" amb la iso d'Ubuntu 22.04 que ens hem descarregat anteriorment.
<img width="724" height="365" alt="image" src="https://github.com/user-attachments/assets/6afa9647-f90f-45c0-9c57-6deae4d6e9cb" />

Seguidament haurem de posar-li el nom d'usuari i el nom de l'equip corresponent que sera el nostre nom.
<img width="718" height="320" alt="image" src="https://github.com/user-attachments/assets/a78c386a-53b1-4594-bf24-dabce7c542b4" />

Despres la RAM que necessitara segons el que he trobat en internet amb 6 GB per treballar be amb 2 processadors.
<img width="718" height="210" alt="image" src="https://github.com/user-attachments/assets/f6983d62-ebe1-4bfc-8b3b-d137131b8a26" />

Seguim amb l'espai del disc dur virtual, que segons el que ens demana la practica posarem 80 GB, on la meitat serà per a Ubuntu.
<img width="721" height="304" alt="image" src="https://github.com/user-attachments/assets/ab8d5a77-b020-40b8-9367-56bad40cb2a2" />

I aqui podem veure un resum de la maquina que crearem.
<img width="858" height="467" alt="image" src="https://github.com/user-attachments/assets/8173f133-4780-4374-b2cb-78d206e876d1" />

Una vegada fet iniciarem la instal·lació, on elegirem el idioma.
<img width="813" height="633" alt="image" src="https://github.com/user-attachments/assets/5a591948-c048-4be6-a376-80c4ba7fc348" />


<img width="771" height="399" alt="image" src="https://github.com/user-attachments/assets/b25b9cc2-7099-46ad-910d-91fa798b582f" />

En VirtualBox crearem una Xarxa NAT i seguidament la posariem ja que he pensat que seria la millor opció ja que té una IP fixa, amb internet i es pot connectar amb l'equip amfitrio.bet365 contacto
<img width="768" height="118" alt="image" src="https://github.com/user-attachments/assets/c10b067a-2be0-49f4-bd51-f522e7f11d91" />

I aqui ja el tindriem posat.

<img width="559" height="237" alt="image" src="https://github.com/user-attachments/assets/2b877267-8078-45ed-90a1-352eb3dd4023" />

La xarxa NAT és la millor opció per aquesta màquina perquè et dona internet de manera immediata, és segura (no exposa la màquina a la xarxa local) i no requereix configuració addicional.

## Llicènciament
Ubuntu Desktop 22.04 està llicenciat sota diverses llicències de programari lliure i codi obert. La major part del sistema està sota la llicència GNU General Public License (GPL), mentre que altres components utilitzen llicències compatibles com MIT, Apache o BSD. La documentació oficial d’Ubuntu es distribueix sota Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0).

## Gestors d'arrencada per a l'instal·lació DUALS

Per fer l'instal·lació dual, primer que tot a la configuració de la maquina haurem d'activar aquesta opció per instal·lar l'ubuntu.
<img width="872" height="401" alt="image" src="https://github.com/user-attachments/assets/495817f6-a2cd-4f37-a42a-6ebe6cda7a33" />

Seguidament posarem la iso de Windows.
<img width="269" height="181" alt="image" src="https://github.com/user-attachments/assets/a516e756-e029-4a34-a6ca-bd4b322e17f9" />

Començarem amb l'instal·lació. L'assignarem a l'espai lliure que tenim al disc dur.
<img width="641" height="471" alt="image" src="https://github.com/user-attachments/assets/e2f73cdb-9e3c-4b76-b1e3-e8b7e5d4f062" />

L'assignarem a l'espai lliure que tenim al disc dur.
<img width="633" height="371" alt="image" src="https://github.com/user-attachments/assets/467169b5-8aea-4226-b0bf-e35efa28d6d0" />

Fins que s'instal·le.
<img width="1018" height="822" alt="image" src="https://github.com/user-attachments/assets/184fe631-083d-43b8-88a0-dcbac5c098a9" />

Anirem amb el seguent pas de recuperar el GRUB, descarreguerem la ISO del "Super Grub2" i l'afegirem a la maquina.
<img width="478" height="131" alt="image" src="https://github.com/user-attachments/assets/3bfd0a58-75ca-4477-9d42-c7af792743e1" />

Iniciarem la maquina desde la ISO.
<img width="632" height="320" alt="image" src="https://github.com/user-attachments/assets/a8fd14ac-045a-4ed1-992f-0d71aa791fb4" />

Clicarem aquesta opció per detectar i visualitzar els boot menus.
<img width="603" height="227" alt="image" src="https://github.com/user-attachments/assets/72232dd5-7be1-48b8-89f2-2f99549ef766" />

Buscarem aquest, que ens portara al Ubuntu.
<img width="607" height="319" alt="image" src="https://github.com/user-attachments/assets/b2e867f4-e04f-4b81-83b0-35718a1475ad" />

Una vegada l'iniciem, executarem les seguents comandes per arreglar el grub.
<img width="727" height="419" alt="image" src="https://github.com/user-attachments/assets/1982351c-84e3-47d8-a3b3-97881ecda8be" />

Una vegada fet reiniciarem la maquina, ja ens surtira per elegir.
<img width="450" height="125" alt="image" src="https://github.com/user-attachments/assets/e4027854-7b1f-4e97-93b3-7821d35fe11c" />



## Punts de restauració
## Configuració de la xarxa
## Comandes generals i instal·lacions
