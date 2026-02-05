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



