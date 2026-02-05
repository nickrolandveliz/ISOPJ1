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

Ara crearem una unitat organitzativa mitjançant un fitxer que ens descarregat, l'editarem per a que s'adapte als nostres parametres.

<img width="520" height="147" alt="image" src="https://github.com/user-attachments/assets/56a1b938-a9ca-4e31-bf24-a42dbecb3883" />

Per executar-lo utilitzarem aquesta comanda, que serveix per afegir contingut al servidor LDAP llegint-lo des d'un fitxer.

**ldapadd:** És l'ordre principal per afegir entrades a la base de dades LDAP.

**-c (continue):** Si troba un error (per exemple, si una entrada ja existeix), no s'atura; continua afegint la resta de coses del fitxer.

**-x:** Utilitza autenticació simple (amb contrasenya normal), en lloc de xifrats complexos.

**-D "cn=admin...":** És l'usuari amb qui t'identifiques per fer els canvis (el login). Aquí estàs entrant com a admin del domini nick.cat.

**-W:** Et demana la contrasenya després de prémer Intro (per seguretat, perquè no quedi guardada a l'historial de comandes).

**-f uo.ldif:** Indica el fitxer d'on ha de llegir les dades que vols afegir (en aquest cas, el fitxer uo.ldif).

<img width="559" height="61" alt="image" src="https://github.com/user-attachments/assets/b86f4ea6-1103-4a17-9e9d-ff1a77cd4a4d" />



