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

A la configuració de qualsevol maquina virtual Ubuntu que tinguessim, afegirrem un nou disc dur de 20GB que sera on es guardaran les copies.

<img width="515" height="120" alt="image" src="https://github.com/user-attachments/assets/6f97eb02-1ffb-42bc-b590-b038bd7b7a5e" />


Dins la maquina instal·larem primer el timeshift, que es un programa que realitza captures del nostre disc dur.
<img width="795" height="387" alt="Captura de pantalla de 2025-10-07 12-55-21" src="https://github.com/user-attachments/assets/12bbc816-55cf-4e38-80e5-418d4e9b9695" />


Despres crearem una nova partició per al disc nou que hem afegit. 
<img width="818" height="552" alt="Captura de pantalla de 2025-10-07 13-06-16" src="https://github.com/user-attachments/assets/31174256-f3c2-4df5-b055-ff17de1c10e4" />


Podem veure aqui que ja s'ha montat.
<img width="616" height="161" alt="Captura de pantalla de 2025-10-07 13-07-44" src="https://github.com/user-attachments/assets/3f19afe9-7332-4045-b620-f43db66e17b9" />


Seguidament li donarem un format a la partició amb la seguent comanda.
<img width="809" height="314" alt="Captura de pantalla de 2025-10-07 13-08-33" src="https://github.com/user-attachments/assets/9279da8f-16ca-4137-9389-627ddf114681" />


Despres per a la prova crearem un arxiu i una carpeta que mes tard borrarem.
<img width="612" height="119" alt="Captura de pantalla de 2025-10-07 13-08-58" src="https://github.com/user-attachments/assets/ccc1893b-0d19-484e-a483-ab92bada682c" />


Obrirem el programa de "Timeshift" i elegirem aquesta opció de "RSYNC".
<img width="587" height="189" alt="image" src="https://github.com/user-attachments/assets/fb3cb0c7-f7ff-4d89-b01c-6055fddb848a" />


A la seguent, ara haurem d'elegir del disc nou la seva partició.
<img width="600" height="229" alt="image" src="https://github.com/user-attachments/assets/3c707a77-901b-4f1b-be94-b271b3e6fa59" />


Configurarem quan volem que les faigui i posarem cada vegada que arranqui el sistema.
<img width="450" height="513" alt="image" src="https://github.com/user-attachments/assets/29f04a50-52ac-4bff-bbb0-caa09aad655d" />


Seguidament la carpeta personal del usuari.
<img width="615" height="151" alt="image" src="https://github.com/user-attachments/assets/03d69fa6-1494-4f60-9688-57bb2107c49e" />


Una vegada fet aixo finalitzarem i s'anira creant.
<img width="773" height="616" alt="image" src="https://github.com/user-attachments/assets/af5c2d3f-13c2-46c2-b13c-3ffe83288051" />


Veurem que s'haura creat.
<img width="799" height="162" alt="image" src="https://github.com/user-attachments/assets/3e93ed85-d1d0-4dcd-b0eb-36375016ce99" />


Ara borrarem la carpeta i fitxer de prova que hem creat.
<img width="608" height="98" alt="Captura de pantalla de 2025-10-07 13-24-30" src="https://github.com/user-attachments/assets/ab9d3d0c-5502-45cc-bd3f-4f4d57a14545" />
<img width="805" height="112" alt="Captura de pantalla de 2025-10-07 13-24-44" src="https://github.com/user-attachments/assets/60ab6d5d-0170-49ba-92df-e04ac4fc37ef" />


I  a la instantania que s'havia creat, la restaurarem.
<img width="479" height="354" alt="image" src="https://github.com/user-attachments/assets/21b97d82-1162-4f87-a0e5-41b1ff7a3f27" />


Ens tocara esperar una estona ja que tarda un poc en restaurar-se.
<img width="478" height="491" alt="image" src="https://github.com/user-attachments/assets/31e7d09d-7d5e-47e2-aa89-ba8380757df3" />


Confirmarem totes les accions.

<img width="495" height="520" alt="Captura de pantalla de 2025-10-07 13-30-39" src="https://github.com/user-attachments/assets/9cb6e7e1-c294-46ec-9258-ba1e1edfcef4" />


Deixariem tot el proces per a que es restaure.
<img width="953" height="694" alt="image" src="https://github.com/user-attachments/assets/dddaf008-e025-4f38-bcea-362f89a3df89" />


I al terminal fent el "ls", podem veure que s'ha restaurat i surten el fitxer i la carpeta de prova que haviem esborrat abans.
<img width="611" height="97" alt="Captura de pantalla de 2025-10-07 13-32-56" src="https://github.com/user-attachments/assets/9e077beb-efbf-41bd-bf0f-dce57f605d41" />


## Configuració de la xarxa

Per al tema de la configuració de la xarxa anirem als parametres i crearem una nova de forma manual posant la IP que vulguessem.
<img width="720" height="443" alt="image" src="https://github.com/user-attachments/assets/3faa86fa-2b4b-4edc-b13e-71d3cf6f041e" />


Podem veure que ens faria ping a internet i a google.com.
<img width="811" height="399" alt="Captura de pantalla de 2025-10-07 13-44-13" src="https://github.com/user-attachments/assets/707c77fd-62b0-4f01-951a-c787052da9cf" />


Una altra forma seria manualment a traves de comandes amb netplan, on entrariem al seu fitxer i l'editariem al nostre gust pero ben estructurat i en sentit.
<img width="562" height="374" alt="Captura de pantalla de 2025-10-07 13-51-43" src="https://github.com/user-attachments/assets/7a00664e-5458-44c1-8c4a-12a2ec324052" />


Una vegada editat, guardarem aquest fitxer i per aplicar tot el que hem posat, utilitzarem aquesta comanda "netplan apply".
<img width="808" height="294" alt="Captura de pantalla de 2025-10-07 13-52-01" src="https://github.com/user-attachments/assets/68fc84ca-b41c-4330-bf3c-f5088eb12c78" />


I veuriem que tambe tindriem sortida a internet i a google.
<img width="810" height="402" alt="Captura de pantalla de 2025-10-07 13-53-10" src="https://github.com/user-attachments/assets/2fb97207-294d-4918-b146-89123b64bd09" />


## Comandes generals i instal·lacions


<img width="768" height="260" alt="image" src="https://github.com/user-attachments/assets/6e7a5306-aa8b-4f0f-8fe3-ed212d7a7997" />


<img width="545" height="122" alt="image" src="https://github.com/user-attachments/assets/96210a67-2a4d-4de7-8691-9864159f94d6" />



<img width="771" height="650" alt="image" src="https://github.com/user-attachments/assets/5567f364-c163-49a1-8bb9-582ab9de0dd1" />


<img width="532" height="75" alt="image" src="https://github.com/user-attachments/assets/ec17037f-813f-42ef-9e09-a96d918b33ac" />


<img width="774" height="58" alt="image" src="https://github.com/user-attachments/assets/5b4e9430-ac72-44a2-8db3-c93981965d92" />


