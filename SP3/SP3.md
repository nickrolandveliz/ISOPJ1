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


## Gestió del domini mitjançant comandes

Per aquest apartat he utilitzat aquesta activitat.

<img width="736" height="495" alt="Captura de pantalla de 2026-02-20 08-44-06" src="https://github.com/user-attachments/assets/5f834da8-86e0-400e-b672-c7db03dc4d4b" />

### Requisits previs

* Fes un dpkg-reconfigure slapd al servidor per tal de deixar la base de dades buida i només amb el domini l’usuari admin creat. Comprova-ho amb un slapcat.

<img width="762" height="177" alt="2026-02-20_08-55" src="https://github.com/user-attachments/assets/400fae27-894c-4b4e-a29a-0faf500c713c" />

<img width="505" height="306" alt="2026-02-20_08-57" src="https://github.com/user-attachments/assets/caf7e644-af67-4baa-9ab1-0f5a70df8026" />

* Descarrega l'arxiu dades_pt10.ldif del moodle i amb la comanda ldapadd carrega els usuaris, grups i uos (Compte que el domini és vesper.cat, hauràs de modificar-lo pel teu)

<img width="522" height="312" alt="2026-02-20_09-03" src="https://github.com/user-attachments/assets/128dff1e-5d9e-4ad1-902c-f9c534c5d87e" />

I afegim el **.ldif** amb **ldapadd**.

<img width="808" height="421" alt="2026-02-20_09-06" src="https://github.com/user-attachments/assets/16d6b624-a920-4ebd-bd1f-c2f9c4db43e2" />

* Fes un altre slapcat per tal de comprovar que les dades s'han carregat correctament.

<img width="508" height="530" alt="2026-02-20_09-09" src="https://github.com/user-attachments/assets/12e342aa-852d-43a9-8e5c-1e971f7f7163" />

### Activitats

* Quantes uos hi ha? **Hi ha 2 UO** Quants usuaris hi ha al domini? **Hi ha 3 usuaris**

<img width="818" height="200" alt="2026-02-20_09-11" src="https://github.com/user-attachments/assets/0d7578bc-ebb0-4918-bb87-f073dc1e1e5b" />

* Crea una nova uo anomenada asix

<img width="809" height="181" alt="2026-02-20_09-13" src="https://github.com/user-attachments/assets/e5dd5039-ceac-4d64-9893-5e41f006814b" />

* Esborra l’atribut roomnumber i homeDirectory de l’usuari ejohnson

Amb aquest cas no existeix cap usuari **ejohnson** i cap dels usuaris te assignat roomNumber i homeDirectory per tant primer ho afegiré i despres ho esborraré.

Com que l'usuari esta present no permet eliminar el homeDirectory pero si el seu roomNumber.

<img width="532" height="125" alt="2026-02-20_10-30" src="https://github.com/user-attachments/assets/a6c8978e-2bf1-4914-a9b9-e182881f729f" />

Aqui ja l'hauriem creat que es podria veure.

<img width="504" height="491" alt="2026-02-20_10-33" src="https://github.com/user-attachments/assets/3d17e869-a38d-4608-8cd5-0657848129d3" />

Executariem la seguent comanda.

<img width="767" height="86" alt="2026-02-20_10-31" src="https://github.com/user-attachments/assets/0e0be5b2-0f41-4c7e-b91c-464dcb0de0c7" />

I ja s'hauria esborrat.

<img width="509" height="466" alt="2026-02-20_10-33_1" src="https://github.com/user-attachments/assets/f394b8ef-4149-40c8-9421-b94756cf9c7c" />


* L’usuari kvaughan en quants grups el trobem com a uniqueMember i quins són?

Utilitzant l’usuari xavier com a substitut de kvaughan:

Nombre de grups: 1

Grups on apareix com a memberUid: informatica

<img width="790" height="93" alt="2026-02-20_10-36" src="https://github.com/user-attachments/assets/287b4384-6da7-44c3-8968-ad0c114d59d3" />

* Trau de la uo People a 3 usuaris i afegeix-los a la uo asix

Aquest seria el fitxer que he creat.

<img width="527" height="405" alt="2026-02-20_10-52" src="https://github.com/user-attachments/assets/06204ee9-fd6d-49c6-a4eb-aaad367cb923" />

Amb la seva comanda per executar-lo.

<img width="773" height="178" alt="2026-02-20_10-52_1" src="https://github.com/user-attachments/assets/05280bc2-649a-4bea-b107-289f68999d07" />

Comprovacio:

<img width="504" height="464" alt="2026-02-20_10-55" src="https://github.com/user-attachments/assets/2781f875-988f-4e7a-9401-e4811f470774" />

* Quants grups hi ha dintre de la uo Groups?

Amb aquest cas 0

<img width="787" height="94" alt="2026-02-20_13-16" src="https://github.com/user-attachments/assets/1650532b-4e81-4738-937c-c7a13c497e38" />

* Esborra la uo People

En aquest cas esborraria la "uo" de "rrhh" ja que la de "People" no existeix.

<img width="774" height="71" alt="2026-02-20_13-24" src="https://github.com/user-attachments/assets/47bf9f35-5ef7-4751-ba71-15bf04f74061" />

* Modifica el uid de l’usuari hmiller a hamiller

Com que el usuari hamiller no exiteix ho faré amb l'usuari xavier, amb aquest fitxer.

<img width="528" height="115" alt="2026-02-20_13-26" src="https://github.com/user-attachments/assets/079f0cfa-3ad1-417e-bce4-eb1ebe8346b9" />

I aquesta comanda.

<img width="778" height="96" alt="2026-02-20_13-27" src="https://github.com/user-attachments/assets/72ec3db5-033a-4bbd-9109-11429d887d76" />

Comprovació:

<img width="507" height="467" alt="2026-02-20_13-27_1" src="https://github.com/user-attachments/assets/747d973b-e62f-4df3-b888-e10ba0f1ecef" />


* Crea un nou usuari amb dos atributs opcionals per a  la classe posixAccount, ho fare amb aquest fitxer.

<img width="512" height="373" alt="2026-02-20_13-30" src="https://github.com/user-attachments/assets/e21f32e7-1016-4b56-bef3-a816428498e0" />

Comanda:

<img width="776" height="87" alt="2026-02-20_13-30_1" src="https://github.com/user-attachments/assets/182df6d1-c05a-4888-a471-e64e16e1f2c8" />

* Afegeix un parell més d’opcionals a l’usuari anterior

<img width="509" height="181" alt="2026-02-20_13-32" src="https://github.com/user-attachments/assets/f351ba9f-a495-4d43-8934-d4c12a8d6626" />

Comanda:

<img width="772" height="90" alt="2026-02-20_13-32_1" src="https://github.com/user-attachments/assets/35924df9-7f1e-49bb-88bc-245c2ee14436" />

* Modifica el mail de l’usuari jburrell per jburrell@gmail.com

Com que el usuari jburrell no existeix ho he fet amb ramon.

<img width="497" height="115" alt="2026-02-20_13-34" src="https://github.com/user-attachments/assets/e875b1da-b991-4fe5-a4a2-9f47b2da16bf" />

Comanda:

<img width="778" height="88" alt="2026-02-20_13-34_1" src="https://github.com/user-attachments/assets/2d58fe02-fa0b-4513-8861-f3adf4f2221c" />

Comprovació:

<img width="277" height="72" alt="2026-02-20_13-35" src="https://github.com/user-attachments/assets/bf626264-87a0-40f8-816d-455d4a8f7d70" />

* Crea un nou grup dintre de la uo Groups i afegeix 3 usuaris

Com que prèviament he mostrat que no existeix la UO Groups ho faré sobre la de asix.

<img width="514" height="202" alt="2026-02-20_13-36" src="https://github.com/user-attachments/assets/f8194083-3222-4dc3-b982-3e57224f9294" />

Comanda:

<img width="780" height="89" alt="2026-02-20_13-36_1" src="https://github.com/user-attachments/assets/a81e19c8-ab5b-4af7-8678-256c3f763588" />

Comprovació:

<img width="787" height="391" alt="2026-02-20_13-38" src="https://github.com/user-attachments/assets/0e9fbfbb-22ec-4fef-b080-bb715d847ca3" />

* Treu del grup creat anteriorment a un usuari

<img width="533" height="109" alt="2026-02-20_13-39" src="https://github.com/user-attachments/assets/93ca45c3-0a10-44ec-9774-cc6f98bf2f06" />

Comanda:

<img width="781" height="96" alt="2026-02-20_13-40" src="https://github.com/user-attachments/assets/d2751a0c-4a96-43f9-9ace-2ae59cf5830f" />

* Mostra tots els usuaris de la uo Asix que el seu uid comenci per la lletra x i formin part també de la uo Recursos Humans

<img width="783" height="108" alt="2026-02-20_13-40_1" src="https://github.com/user-attachments/assets/49e827cd-3a63-4a5a-8736-4abdac833e28" />

* Mostra tots els usuaris del domini on el seu uidNumber estigui entre 1010 i 1030 (inclosos). Quants en son?

<img width="788" height="119" alt="2026-02-20_13-42" src="https://github.com/user-attachments/assets/96f7d159-bd9d-4d80-897b-9bab8deeed92" />

* Usuaris on el seu telèfon acabi en un 2 o el seu cognom en una n. Quants?

Amb aquest cas son 0 usuaris.

<img width="776" height="71" alt="2026-02-20_13-42_1" src="https://github.com/user-attachments/assets/48a7c46b-4072-4898-ab7d-04fa69412a53" />

* D’un sol cop, a l’usuari que tu vulguis, esborra un atribut, afegeix-ne un altre i modifica un tercer.

<img width="515" height="314" alt="2026-02-20_13-44" src="https://github.com/user-attachments/assets/75c71516-cbc6-49dc-a78e-7ef9cce7eae9" />

Comprovació:

<img width="776" height="89" alt="2026-02-20_13-45" src="https://github.com/user-attachments/assets/c2e3a892-d6e1-4f27-95ef-692d83c12361" />


## Entorn grafic

<img width="733" height="196" alt="2026-02-18_17-21" src="https://github.com/user-attachments/assets/2e67a43a-7ae1-421d-9c12-90c343c3a69c" />

<img width="734" height="134" alt="2026-02-18_17-23" src="https://github.com/user-attachments/assets/4f8f4c3b-7e2f-4b3d-ab51-56dd18ea5d0a" />

<img width="735" height="131" alt="2026-02-18_17-24" src="https://github.com/user-attachments/assets/cf3658e4-0da9-4c6f-b9ff-3510e2f024fd" />

<img width="693" height="401" alt="2026-02-18_17-27" src="https://github.com/user-attachments/assets/ecbd687c-afe4-442e-af19-12fdb5106fde" />

<img width="791" height="527" alt="2026-02-18_17-41" src="https://github.com/user-attachments/assets/105f0a65-aa52-4feb-9230-21765132fabb" />

<img width="440" height="338" alt="2026-02-18_17-42" src="https://github.com/user-attachments/assets/c78f32b8-1756-4669-bebc-466c336f6554" />

<img width="787" height="455" alt="2026-02-18_17-42_1" src="https://github.com/user-attachments/assets/1cf79ab5-4dca-4981-885a-95744a8505cd" />

<img width="621" height="353" alt="2026-02-18_18-00" src="https://github.com/user-attachments/assets/f7f2eaee-9f3b-472a-adcd-c57aaa0c7a56" />

<img width="816" height="477" alt="2026-02-18_18-04" src="https://github.com/user-attachments/assets/157aa314-e1d0-45d0-b1b8-b30798c30442" />

<img width="700" height="267" alt="2026-02-18_18-06" src="https://github.com/user-attachments/assets/9f9a40db-6f54-4ff1-ad7d-7fe0878d9f7c" />

<img width="826" height="368" alt="2026-02-18_18-11" src="https://github.com/user-attachments/assets/2900ac29-6e4e-4c2e-8b69-0d84b6ab9ea0" />

<img width="389" height="312" alt="2026-02-18_18-18" src="https://github.com/user-attachments/assets/6b005c3f-aff0-49b6-8b59-2929a11b307f" />

<img width="1073" height="545" alt="2026-02-18_18-18_1" src="https://github.com/user-attachments/assets/cc7177d7-9757-4061-8fb3-2dece95f9b86" />

<img width="356" height="236" alt="2026-02-18_18-20" src="https://github.com/user-attachments/assets/f71694c9-d757-46cf-a677-24a63484e4ae" />

<img width="1015" height="209" alt="2026-02-18_18-20_1" src="https://github.com/user-attachments/assets/76341059-402a-41f2-ae37-33f436ec313d" />

<img width="344" height="152" alt="2026-02-18_18-21" src="https://github.com/user-attachments/assets/5590605c-da92-4c54-925f-4cc3d6ab326c" />

<img width="449" height="130" alt="2026-02-18_18-21_1" src="https://github.com/user-attachments/assets/38fe7d4a-8637-4a21-a180-386ae6089c67" />

<img width="549" height="320" alt="2026-02-18_18-22_1" src="https://github.com/user-attachments/assets/af0a0b76-c244-42b9-9b14-3c372b5a19d5" />

<img width="905" height="269" alt="2026-02-18_18-30" src="https://github.com/user-attachments/assets/2364fdff-a0e6-46cf-88d0-6174f670778a" />

<img width="715" height="171" alt="2026-02-18_18-31" src="https://github.com/user-attachments/assets/2ba32186-af59-4d43-b134-a955fb8fe001" />

<img width="889" height="341" alt="2026-02-18_18-31_1" src="https://github.com/user-attachments/assets/9e0e1286-b179-408d-8bd6-ce75bc0b177f" />

<img width="298" height="66" alt="2026-02-18_18-32" src="https://github.com/user-attachments/assets/4df0d191-0c57-4d8e-b335-8407ca67ad4f" />

<img width="848" height="426" alt="2026-02-18_18-32_1" src="https://github.com/user-attachments/assets/dff5a5c2-0367-4f98-99d8-59748dfe6eb1" />

<img width="809" height="285" alt="2026-02-18_18-34" src="https://github.com/user-attachments/assets/0d47e2ab-0aed-4c68-8976-13811276b2e5" />

<img width="811" height="276" alt="2026-02-18_18-35" src="https://github.com/user-attachments/assets/49aba089-4f8a-438e-8c74-1917f0f6f710" />

<img width="1082" height="355" alt="2026-02-18_18-36" src="https://github.com/user-attachments/assets/10285577-8690-4372-a351-9efe85094e08" />

<img width="683" height="423" alt="2026-02-18_18-37" src="https://github.com/user-attachments/assets/3ea00955-bde9-4848-8651-89fa37c525d4" />

<img width="676" height="155" alt="2026-02-18_18-38" src="https://github.com/user-attachments/assets/1240daec-b4d5-4e44-bd81-d1d9c69e44b4" />

<img width="856" height="456" alt="2026-02-18_18-38_1" src="https://github.com/user-attachments/assets/790f3576-958d-4aeb-8401-3b505e829020" />

<img width="512" height="67" alt="2026-02-18_18-41" src="https://github.com/user-attachments/assets/151d46b3-81bd-4ae1-acb2-98e6223bee15" />



## Servidor Samba

<img width="703" height="155" alt="image" src="https://github.com/user-attachments/assets/3cbde56f-b1f3-4b70-b3eb-324d4d48ed76" />

<img width="604" height="202" alt="image" src="https://github.com/user-attachments/assets/1cebacd2-3e71-4a7e-ac6f-711db3fe35f0" />

<img width="562" height="304" alt="image" src="https://github.com/user-attachments/assets/40433e5a-d777-442a-b67e-a162f2970699" />

<img width="333" height="292" alt="image" src="https://github.com/user-attachments/assets/732d6887-6da7-4272-8e70-b8f8a5960f74" />

<img width="494" height="377" alt="image" src="https://github.com/user-attachments/assets/ebdfe297-c9ca-491a-bcc8-95adc2d3c96f" />

<img width="697" height="393" alt="image" src="https://github.com/user-attachments/assets/b237032d-2590-45d2-bf9f-0655f9bb4984" />

<img width="627" height="247" alt="image" src="https://github.com/user-attachments/assets/6b247cf5-9c9b-4c71-bb17-37fcdc317169" />

<img width="607" height="154" alt="image" src="https://github.com/user-attachments/assets/7e04ced9-4fbf-4d32-86dd-8be3c7b87685" />

<img width="463" height="437" alt="image" src="https://github.com/user-attachments/assets/fb849993-4bf2-4554-b008-bb6d308d19d8" />

<img width="436" height="127" alt="image" src="https://github.com/user-attachments/assets/589511c5-4f21-4a4c-bc69-024c098bc898" />

<img width="251" height="142" alt="image" src="https://github.com/user-attachments/assets/4cca0f9a-53ee-43a5-ad3b-f5f88feaa2da" />

<img width="261" height="260" alt="image" src="https://github.com/user-attachments/assets/9e3a2c98-11de-41e3-85c5-25ae746493a2" />

<img width="469" height="429" alt="image" src="https://github.com/user-attachments/assets/d43f61a2-0339-4dac-9c7e-8bb924459bd7" />

<img width="433" height="113" alt="image" src="https://github.com/user-attachments/assets/6ee1f356-c671-4e98-86ff-f3dce4145ac3" />

<img width="240" height="140" alt="image" src="https://github.com/user-attachments/assets/4d0112ca-4f97-4c38-a86e-779daf2f0748" />

<img width="466" height="429" alt="image" src="https://github.com/user-attachments/assets/457724ab-ef5e-4057-965a-aa287b3b732d" />

<img width="424" height="119" alt="image" src="https://github.com/user-attachments/assets/415a7a89-0d63-440c-bd44-d53e07249033" />


## NFS


### 1 exercici nfs sense ldap 

<img width="803" height="238" alt="2026-02-10_12-50" src="https://github.com/user-attachments/assets/be38697b-61f7-43e2-b3f8-41886a244f46" />

<img width="708" height="219" alt="2026-02-10_12-50_1" src="https://github.com/user-attachments/assets/48d5b0d9-8c9a-4982-8f5c-547c53d813ed" />

<img width="632" height="180" alt="2026-02-10_12-53" src="https://github.com/user-attachments/assets/17215ed7-922b-4686-86b4-b7d49a086eef" />

<img width="507" height="310" alt="2026-02-10_12-57" src="https://github.com/user-attachments/assets/8b0dc7a1-c06e-4bf5-971f-d58e9d3c5b20" />

<img width="809" height="268" alt="2026-02-10_12-58" src="https://github.com/user-attachments/assets/9ea595ec-0125-4bf8-8b7c-56010b3f9131" />

<img width="359" height="58" alt="2026-02-10_13-00" src="https://github.com/user-attachments/assets/3ce9553d-93d1-4404-9ddb-98e26fc5a809" />

<img width="802" height="262" alt="2026-02-10_13-01" src="https://github.com/user-attachments/assets/defc13af-f667-4220-818f-1d943742b764" />


<img width="642" height="178" alt="2026-02-10_13-03" src="https://github.com/user-attachments/assets/fa5ca1eb-1728-4cef-b7ff-c2292e3fa016" />

<img width="597" height="198" alt="2026-02-10_13-09" src="https://github.com/user-attachments/assets/d37a100c-4231-4079-90b2-f2c0d5d33007" />

<img width="623" height="204" alt="2026-02-10_13-10" src="https://github.com/user-attachments/assets/60cd3a43-a916-46f2-b0fe-5f8b8255d8a6" />

<img width="917" height="356" alt="2026-02-10_13-23" src="https://github.com/user-attachments/assets/4d42a169-bb0f-4fae-85aa-221d550d09ef" />

<img width="290" height="46" alt="2026-02-10_13-16_1" src="https://github.com/user-attachments/assets/2dfff157-33cb-47b2-a83e-ad2070582c8d" />

<img width="336" height="70" alt="2026-02-10_13-20" src="https://github.com/user-attachments/assets/136d4a63-b6ea-44f0-b797-d207a753bbc9" />

### 2 exercici

<img width="413" height="156" alt="2026-02-10_13-51" src="https://github.com/user-attachments/assets/6a237ed6-da20-4b4b-935f-c8ae490b63ce" />

<img width="508" height="324" alt="2026-02-10_13-53" src="https://github.com/user-attachments/assets/cda2076d-3900-4af4-9a52-47da22df2ed1" />

<img width="917" height="369" alt="2026-02-10_13-57" src="https://github.com/user-attachments/assets/19bc5eff-9ec5-4346-9aea-c1071de95ff2" />

<img width="290" height="92" alt="2026-02-10_13-58" src="https://github.com/user-attachments/assets/ce2d63b1-a10d-4530-9a0d-a42a65a86186" />

<img width="572" height="387" alt="2026-02-10_14-01" src="https://github.com/user-attachments/assets/fc2b2906-963c-40c1-b0c9-ca329ae7abd9" />

<img width="805" height="96" alt="2026-02-10_14-04" src="https://github.com/user-attachments/assets/d9122bd4-d208-4280-8436-1d45a32fdc75" />

<img width="615" height="155" alt="2026-02-18_10-32" src="https://github.com/user-attachments/assets/79826dc5-79b1-4dfc-87dc-628452b0fc31" />

<img width="524" height="67" alt="2026-02-18_10-32_1" src="https://github.com/user-attachments/assets/18da9858-f630-4765-b20d-4e8d89038a1d" />

