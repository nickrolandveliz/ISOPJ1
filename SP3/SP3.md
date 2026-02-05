---
layout: custom
title: "SPRINT 3: ADMINISTRACIÓ DE DOMINIS I SEGURETAT"
---

## Configuració del servidor

Primer, obrim un terminal dintre de la màquina servidor, executem la comanda **ip a**, ens apuntem l'adreça IP que rebem per dhcp, i la posarem de manera estàtica amb interficie gràfica. Quan configurem un servidor **sempre hem de posar l'adreça IP estatica**, ja que una adreça dinàmica complicaría l'accés als serveis que ofereix, degut a que cada dia en tindria una de diferent.
<img width="746" height="459" alt="Captura de pantalla de 2026-01-08 13-24-13" src="https://github.com/user-attachments/assets/9a3ec543-8a7e-4345-83bc-fcec314ada22" />

<img width="804" height="335" alt="Captura de pantalla de 2026-01-08 13-24-33" src="https://github.com/user-attachments/assets/281fa3ae-7b3e-4150-aad1-dfeac7709e19" />


Tot seguit, accedim a **/etc/hostname** amb la comanda **nano**, on **modificarem el nom del dispositiu**.
<img width="513" height="92" alt="Captura de pantalla de 2026-01-08 13-26-39" src="https://github.com/user-attachments/assets/2561caec-30f0-4f96-8a15-62777ef3ac9d" />

El mateix al **/etc/hosts** i posarem el nou hostname a l'adreça de loopback del dispositiu. També posarem el domini que crearem pròximament lligat a l'adreça IP que ens hem configurat estàticament.

<img width="512" height="134" alt="Captura de pantalla de 2026-01-08 13-28-39" src="https://github.com/user-attachments/assets/e27650e9-98c6-4c48-915c-a8cd61e8e403" />

A continuació, instal·lem els serveis per a instal·lar i gestionar ldap.

<img width="642" height="132" alt="Captura de pantalla de 2026-01-08 13-29-46" src="https://github.com/user-attachments/assets/78e2337c-fb76-42ce-b949-c8f86cc4bf31" />

Durant l'instal·lació, ens demanara una contrasenya per a l'usuari d'administrador de ldap, mes avant haurem de recordar.

<img width="671" height="374" alt="Captura de pantalla de 2026-01-08 13-31-56" src="https://github.com/user-attachments/assets/5392226b-889e-4e41-a255-5bccb631efa7" />

En la comanda **slapcat** per a veure tots els elements del domini.

<img width="454" height="279" alt="image" src="https://github.com/user-attachments/assets/655e7727-4a91-4b40-9967-c8011ebdcd58" />

Ara anem a **Descargas**, i descomprimim el zip que ens descarregat del moodle.

<img width="560" height="209" alt="image" src="https://github.com/user-attachments/assets/29d8f3b4-fe45-46b1-9b69-f6e78299bddc" />

Amb **dpkg-reconfigure slapd**, podem configurar i afegir elements al domini més facilment. Alternativament, podem fer servir els fitxers de configuració **.ldif** que hem descomprimit, però aquests no són tan practics.

<img width="561" height="18" alt="image" src="https://github.com/user-attachments/assets/66131f3e-973c-4abc-b772-652b85e35fbf" />

Posem al domini que hem indicat previament al **/etch/hosts**.

<img width="553" height="282" alt="image" src="https://github.com/user-attachments/assets/793b33e6-413f-4346-b200-07e5a1daef42" />

El nom de l'organitazció.

<img width="559" height="240" alt="image" src="https://github.com/user-attachments/assets/811115e3-1ab1-4134-a40e-1ee3612ff251" />

Una contrasenya, podem ficar la mateia que abans.

<img width="558" height="264" alt="image" src="https://github.com/user-attachments/assets/de8287b0-7aa8-46cd-8daa-47bf738354bf" />

Eliminarem la base de dades en purgar.

<img width="557" height="257" alt="image" src="https://github.com/user-attachments/assets/7d7478e7-c514-49ee-8822-d53268df0aa0" />

Finalment, movem la base de ades antiga, i executem la comanda **slapcat** per a comprovar que tots els canvis que acabem de configurar s'han aplicat correctament.

<img width="559" height="266" alt="image" src="https://github.com/user-attachments/assets/fe1d9ac2-ff6b-4567-8da6-73b4a271012a" />

De moment no tenim elements (usuaris, grups, unitats organitzatives) però el domini ja apareix configurat correctament.

<img width="474" height="275" alt="image" src="https://github.com/user-attachments/assets/3d073a90-8fd4-4aa7-bfa3-af6a6c547c54" />

Ara crearem una unitat organitzativa mitjançant un fitxer, **uo.ldif** que ens hem descarregat, l'editarem per a que s'adapte als nostres parametres, que seria canviar **dc=nick,dc=cat**, que vindria a ser el nostre domini.

<img width="520" height="147" alt="image" src="https://github.com/user-attachments/assets/56a1b938-a9ca-4e31-bf24-a42dbecb3883" />

Per executar-lo utilitzarem aquesta comanda, que serveix per afegir contingut al servidor LDAP llegint-lo des d'un fitxer.

**ldapadd:** És l'ordre principal per afegir entrades a la base de dades LDAP.

**-c (continue):** Si troba un error (per exemple, si una entrada ja existeix), no s'atura; continua afegint la resta de coses del fitxer.

**-x:** Utilitza autenticació simple (amb contrasenya normal), en lloc de xifrats complexos.

**-D "cn=admin...":** És l'usuari amb qui t'identifiques per fer els canvis (el login). Aquí estàs entrant com a admin del domini nick.cat.

**-W:** Et demana la contrasenya després de prémer Intro (per seguretat, perquè no quedi guardada a l'historial de comandes).

**-f uo.ldif:** Indica el fitxer d'on ha de llegir les dades que vols afegir (en aquest cas, el fitxer uo.ldif).

<img width="559" height="61" alt="image" src="https://github.com/user-attachments/assets/b86f4ea6-1103-4a17-9e9d-ff1a77cd4a4d" />

Ara tocaria per a crear un usuari amb el fitxer **usu.ldif**, igual canviarem els parametres adaptant-ho als nostres. 

<img width="519" height="410" alt="image" src="https://github.com/user-attachments/assets/c6da8fc6-af50-40dc-a4bb-fc0b35edb043" />

Seguidament executariem la mateixa comanda per afegir-ho, nomes canviant el nom del fitxer.

<img width="558" height="67" alt="image" src="https://github.com/user-attachments/assets/91619933-fb51-4109-8f94-1afd7ed16922" />

Tocaria per a l'ultim que es el fitxer de **grup.ldif** que canviariem el mateix que als altres dos fitxers.

<img width="514" height="188" alt="image" src="https://github.com/user-attachments/assets/70886093-9063-493a-a619-ab30dd4b22d4" />

I mateixa comanda canviant el nom del fitxer.

<img width="560" height="61" alt="image" src="https://github.com/user-attachments/assets/4ba3d2f3-2529-4f97-949c-776ef8434b40" />

Mitjançant la comanda de **slapcat**, podriem confirmar que se'ns ha creat.

<img width="475" height="516" alt="image" src="https://github.com/user-attachments/assets/30652036-f9eb-464f-ba38-53e2bc305140" />

<img width="456" height="536" alt="image" src="https://github.com/user-attachments/assets/307f58c1-02e4-45ad-b985-40f19688ac73" />

<img width="457" height="258" alt="image" src="https://github.com/user-attachments/assets/708f5daa-d00d-447c-9c1f-5f4c19ae6712" />


## Configuració del client

Ara seria el torn per al client, previament hauriem fet la compravacio que tenen connexio entre els dos. Despres descarregarem els paquets necessaris.

<img width="557" height="21" alt="image" src="https://github.com/user-attachments/assets/98a56ec0-7bb9-4c6f-b8aa-bb0b82a307ba" />

En la instal·lació, apareixera l'assistent que ens demanara l'adreça IP del domini.

<img width="562" height="279" alt="image" src="https://github.com/user-attachments/assets/de5f7ed7-10ad-4da0-84fa-19ebae6ac55b" />

Posarem tambe el nom.

<img width="562" height="274" alt="image" src="https://github.com/user-attachments/assets/06d2f696-d34f-4f5b-8df3-524e36b9b16f" />

Elegirem la versió de LDAP 3.

<img width="560" height="291" alt="image" src="https://github.com/user-attachments/assets/58f0f443-5d90-4ba1-82c5-50877bade699" />

Si a les seguents dos opcions.

<img width="554" height="337" alt="image" src="https://github.com/user-attachments/assets/aa5bf757-42d2-4adf-9562-a091abd39a02" />

<img width="561" height="317" alt="image" src="https://github.com/user-attachments/assets/af2d330d-4249-4c3e-abaa-b941072cf15f" />

Posarem l'usuari d'adminsitrador.

<img width="503" height="314" alt="image" src="https://github.com/user-attachments/assets/0b4abaf2-fc1c-4adf-868d-ae4acfdb8384" />

La seva contrasenya.

<img width="556" height="299" alt="image" src="https://github.com/user-attachments/assets/e20e6492-1a5b-47b0-90a8-7910ec183fe1" />

I ja ho tindriem, pero en cas que en algun punt ens haguessim equivocat, podem tornar a configurar-ho amb aquesta comanda.

<img width="552" height="22" alt="image" src="https://github.com/user-attachments/assets/55bb59b4-7b15-4b0d-884f-75d212aacfe9" />

Seguidament editarem el fitxer **/etc/nsswitch.conf** i afegirem **files systemd** al mig de cada linia.

<img width="561" height="212" alt="image" src="https://github.com/user-attachments/assets/e1bc2fdc-bbb5-4c4d-a96d-a6a3487bb2f1" />

Despres al fitxer **/etc/pam.d/common-password** haurem de borrar aquesta part d'una linia.

<img width="561" height="245" alt="image" src="https://github.com/user-attachments/assets/da692876-b4ee-4f83-a05e-d5d20bea2353" />

Casi acabariem i dins d'aquest fitxer **/etc/pam.d/common-session** afegirem l'ultima linia que es veu, serveix perque quan un usuari canvii la seva contrasenya, s'actualitzi automaticament al servidor LDAP sense que l'hagi de teclejar dues vegades.

<img width="560" height="362" alt="image" src="https://github.com/user-attachments/assets/c1f8beab-69ea-48d5-b795-e5cf52e23324" />

Ara modificariem i ficariem el seguent al fitxer **/usr/share/ligthdm/lightdm.conf.d/50-ubuntu.conf** per 

<img width="559" height="111" alt="image" src="https://github.com/user-attachments/assets/6a1dcfc2-ec1b-4108-84c9-953dd2b8415e" />

Una vegada fet tot aixo, ja podriem surtir del nostre usuari, i iniciar per l'usuari nou que hem creat que es diu **alu1**.

<img width="468" height="573" alt="image" src="https://github.com/user-attachments/assets/6622b21f-43f3-4dfb-9b2c-a1fd8196be19" />
