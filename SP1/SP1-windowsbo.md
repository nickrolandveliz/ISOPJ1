---
layout: custom
title: "Sprint 1: Instal·lació i Configuració Inicial – Windows"
---

Crear màquina virtual per instal·lar un Windows 11 Pro i dur a terme la configuració inicial del sistema.

---

# Fase 1 – Instal·lació del sistema operatiu

## Pas 1 – Crear la màquina virtual amb VirtualBox

* Crearem la nova maquina.

<img width="379" height="115" alt="1" src="https://github.com/user-attachments/assets/10655e9e-7299-47b8-bd1e-298d413c4a37" />


## Pas 2 – Assignar recursos (RAM mínima 4 GB, disc mínim 40 GB)

* Aquí assigno els recursos de maquinari a la màquina virtual:

    1. **Memòria base: 6144 MB (6 GB)** – el recomanat per a Windows 10.
    2. **Processadors: 2 CPUs** – per garantir un rendiment fluid.

<img width="717" height="163" alt="2" src="https://github.com/user-attachments/assets/d487b16c-7dc7-413c-beb8-ba3397cb95c5" />

<img width="710" height="187" alt="3" src="https://github.com/user-attachments/assets/30e2aba8-1935-4e8e-aec5-d2df7e9072a8" />

## Pas 3 – Carregar la ISO de Windows 10.

* En aquest pas fico en el meu cas la iso de Windows 10.

<img width="714" height="197" alt="4" src="https://github.com/user-attachments/assets/f8c97288-7640-4490-b397-5540315ef29a" />

* I aquest seria el resum de la maquina nova.

<img width="655" height="406" alt="image" src="https://github.com/user-attachments/assets/9a94c458-ecb0-48fe-a822-157ad9d0a122" />

## Pas 4 – Instal·lar el sistema (idioma, usuari, contrasenya)

* Començarem amb l'instal·lació, elegint l'idioma en el que el voliem fer, seguidament de tota la configuració posariem l'usuari i contrasenya que utilitzara l'equip.

<img width="488" height="247" alt="5" src="https://github.com/user-attachments/assets/0c1b2c1b-2f17-450f-be0a-08c2c6915fd4" />

<img width="588" height="405" alt="6" src="https://github.com/user-attachments/assets/6b4cafce-cb29-47b1-9e58-93f694b4e326" />

<img width="740" height="388" alt="7" src="https://github.com/user-attachments/assets/13945566-9045-489d-98a5-b7398955468d" />

## Pas 5 – Comprovar que arrenca correctament

* Quan acabessem de fer tota la configuració, veurem que inicia correctament.

<img width="722" height="264" alt="8" src="https://github.com/user-attachments/assets/75152ae0-8270-45d2-9799-fa92cac40405" />


# Fase 2 – Punts de restauració

## Pas 6 – Cercar "Crear un punt de restauració"

* Al cercador de Windows buscarem "Crear un punt de restauració", i entrarem dins d'aquest programa.

<img width="325" height="91" alt="9" src="https://github.com/user-attachments/assets/71ecec13-54a0-46a1-81c5-18a2a3a78c76" />

## Pas 7 – Activar la protecció del sistema al disc C:

* Aqui dins haurem d'activar el disc C: que apareixera previament desactivat.

<img width="408" height="461" alt="10" src="https://github.com/user-attachments/assets/14e42337-f5c5-4769-87a7-f9f0141897e1" />

## Pas 8 – Crear un punt de restauració manual

* Clico **Crear...**  per crear un nou punt de restauració manualment.

<img width="379" height="209" alt="11" src="https://github.com/user-attachments/assets/b7162ce7-3eef-4d83-998e-6fc0da3c24af" />

* Com a nom del punt ficarem aquest per exemple i el realitzem.

<img width="394" height="185" alt="12" src="https://github.com/user-attachments/assets/09084838-8a55-490d-9c40-
4b4df2ce6b01" />

<img width="337" height="113" alt="14" src="https://github.com/user-attachments/assets/c58ce58f-003e-48e4-9877-e330d4c3d8bd" />

## Pas 9 – Fer un canvi (programa)

* Com a canvi del sistema, he descarregat un arxiu que seria el de LibreOffice. Amb la protecció activa al disc C:, Windows pot revertir aquest canvi si es fa una restauració.

<img width="321" height="175" alt="15" src="https://github.com/user-attachments/assets/7efec49c-6bea-4d1c-af5c-c4b04e7e7c64" />

## Pas 10 – Restaurar i comprovar

* Clico **Restaurar sistema...** per iniciar el procés de restauració al punt creat prèviament.

<img width="402" height="218" alt="16" src="https://github.com/user-attachments/assets/f25ae7c3-5f47-49f2-bad3-6c4c519a7a86" />

* Seleccionarem el punt que haviem creat que sera l'unic, el triem.

<img width="557" height="207" alt="17" src="https://github.com/user-attachments/assets/0635db65-b315-41bd-a31f-ad303345cab3" />

* Confirmarem que estigue tot be.

<img width="522" height="249" alt="18" src="https://github.com/user-attachments/assets/70ba373e-da88-414a-898c-8e6915f3bc12" />

* I deixarem que carrege i acabi de fer la restauració.

<img width="495" height="204" alt="19" src="https://github.com/user-attachments/assets/f5a1ece6-6db0-49e8-b199-014f5b896f18" />

* Fins que acabi i quan tornessim a buscar el programa que haviem descarregat no surtira ja.

<img width="399" height="151" alt="20" src="https://github.com/user-attachments/assets/7119be1d-e076-4537-b0a5-42a041e1503b" />

<img width="334" height="157" alt="21" src="https://github.com/user-attachments/assets/1af29be1-12d6-4eb3-bd97-f10c989ee62f" />

# Fase 3 – Llicències de Windows

## Pas 11 – Obrir Configuració → Sistema → Activació

* Obro **Configuració** i vaig a **Sistema** ① → **Activació** ② per consultar l'estat de la llicència de Windows.

<img width="444" height="224" alt="22" src="https://github.com/user-attachments/assets/76d1cc0b-e152-42f7-8611-99e5ee7306a8" />

## Pas 12 – Veure si Windows està activat

Com a la captura anterior podem veure que no esta activat.

<img width="444" height="224" alt="22" src="https://github.com/user-attachments/assets/c32283b1-b711-43ea-94cc-4fab57e7131d" />

## Pas 13 – Executar al CMD: `slmgr /xpr`

* Obro el symbol del sistema i executo la comanda `slmgr /xpr`. Apareix una finestra de **Windows Script Host** que indica: *"Windows(R), Professional edition: Windows está en modo de notificación"*. Això confirma que Windows funciona però sense llicència activa.

<img width="615" height="317" alt="24" src="https://github.com/user-attachments/assets/a20519ba-dbb9-494b-8f78-6e897e1ba0f8" />

## Pas 14 – Tipus de llicenciament de Windows

> **Tipus de llicències de Windows més habituals:**
>
> | Tipus | Descripció |
> |---|---|
> | **OEM** | Preinstal·lada per fabricants (Dell, HP...). Lligada al maquinari, no es pot transferir. |
> | **Retail** | Comprada per l'usuari directament. Es pot transferir entre equips. |
> | **Volume (MAK/KMS)** | Per empreses amb molts equips. S'activen contra un servidor intern o clau mestra. |
> | **Digital License** | S'associa al compte Microsoft. S'activa automàticament al connectar-se. |
>
> En aquest cas el sistema es troba en **mode de notificació** (sense llicència vàlida), cosa habitual en entorns de laboratori i instal·lacions de prova.


## Pas 15 – Preu aproximat d'una llicència Windows

> **Preus oficials de Microsoft (abril 2026):**
>
> | Edició | Preu aprox. (web oficial) |
> |---|---|
> | Windows 11 Home | ~115 - 145 € |
> | Windows 11 Pro | ~199 - 259 € |
> | Llicencie OEM (claus digitals) | ~15 - 45 € |
>
> Tot i que Microsoft prioritza la venda de Windows 11, encara es poden trobar llicències de Windows 10 a botigues com Amazon o minoristes de programari. Les llicències OEM solen ser molt més econòmiques perquè es vinculen definitivament a la placa base de l'ordinador on s'activen per primer cop.


# Fase 4 – Gestor d'arrencada

## Pas 16 – Obrir Command Prompt com a administrador

* Al cercador de Windows busco **"cmd"** (Símbolo del sistema) i clico **"Ejecutar como administrador"** per tenir tots els permisos necessaris per executar `bcdedit`.

<img width="356" height="200" alt="25" src="https://github.com/user-attachments/assets/9624442f-1a3a-411f-8ed7-5060a2e0af2c" />

## Pas 17 – Executar bcdedit

* Executo la comanda `bcdedit` que mostra la configuració completa del gestor d'arrencada de Windows (BCD – Boot Configuration Data).

<img width="507" height="516" alt="26" src="https://github.com/user-attachments/assets/f94c5439-b147-4efe-acdc-a5714d235703" />

## Pas 18 – Identificar els blocs Boot Manager i Boot Loader

A la sortida de `bcdedit` s'identifiquen dos blocs principals:

**Bloc 1 – Administrador de arranque de Windows (Boot Manager):**
```
Identificador    {bootmgr}
device           partition=\Device\HarddiskVolume1
description      Windows Boot Manager
default          {current}
timeout          30
```

**Bloc 2 – Cargador de arranque de Windows (Boot Loader):**
```
Identificador    {current}
device           partition=C:
path             \WINDOWS\system32\winload.efi
description      Windows 11
```

---

## Pas 19 – Interpretar dades concretes

> **Del bloc Boot Manager:**
>
> | Camp | Valor | Significat |
> |---|---|---|
> | `default` | `{current}` | El sistema que arrenca per defecte és el Windows 11 actual |
> | `timeout` | `30` | Espera 30 segons al menú d'arrencada abans d'iniciar automàticament |
>
> **Del bloc Boot Loader:**
>
> | Camp | Valor | Significat |
> |---|---|---|
> | `device` | `partition=C:` | Windows està instal·lat a la partició C: |
> | `path` | `\WINDOWS\system32\winload.exe` | Fitxer que carrega el sistema operatiu |
> | `description` | `Windows 11` | Nom del sistema operatiu |

---

## Pas 20 – Respostes a les preguntes curtes

> **Quin sistema s'està arrencant?**
> → **Windows 10** (identificador `{current}`).
>
> **A quin disc o partició està instal·lat?**
> → A la partició **C:** del primer disc dur.
>
> **Quant temps espera abans d'arrencar?**
> → **30 segons** (`timeout 30`).
>
> **Quin fitxer inicia Windows?**
> → `\WINDOWS\system32\winload.exe`

---

## Pas 21 – Interpretació final

> **Qui decideix l'arrencada (Boot Manager):**
> El **Windows Boot Manager** (`bootmgr`) és el responsable de mostrar el menú d'arrencada i decidir quin sistema operatiu s'iniciarà, en funció de la configuració del BCD.
>
> **Qui carrega el sistema (Boot Loader):**
> El **Windows Boot Loader** (`winload.exe`) és el fitxer que realment carrega el nucli de Windows a la memòria i inicia el sistema operatiu un cop el Boot Manager ha pres la decisió.

---

# Fase 5 – Xarxa bàsica

## Pas 22 – Obrir la configuració de xarxa

* Obro **Configuració > Red e Internet** ① i entro a **Ethernet** ② per veure i modificar la configuració de la connexió de xarxa.

<img width="695" height="386" alt="27" src="https://github.com/user-attachments/assets/9cc709f4-b501-4151-a3eb-f3629e926ea3" />

## Pas 23 – Consultar la IP amb `ipconfig`

* Obro el CMD i executo `ipconfig`. Es mostren les dades de la interfície Ethernet:
    - **Adreça IPv4:** `10.0.2.15`
    - **Màscara de subxarxa:** `255.255.255.0`
    - **Porta d'enllaç (gateway):** `10.0.2.2`

<img width="543" height="203" alt="28" src="https://github.com/user-attachments/assets/04700c53-8cdd-4389-a95d-c8df3a8b90f4" />

## Pas 24 – Configurar IP dinàmica (DHCP automàtic)

* A la configuració d'Ethernet, verifico que l'assignació d'IP és **Automático (DHCP)**. Amb DHCP, el router assigna automàticament una IP al dispositiu cada vegada que es connecta, sense necessitat de configuració manual.

<img width="364" height="152" alt="29" src="https://github.com/user-attachments/assets/c20f044c-16f8-4c1b-a132-65c1e1b0632a" />

## Pas 25 – Configurar IP fixa (manual)

* A la pantalla d'informació de l'adaptador Ethernet, es pot veure la configuració actual obtinguda per DHCP que establiré de forma estàtica:
    - **IP:** `10.0.2.16`
    - **Màscara:** `255.255.255.0` (prefixe /24)
    - **Gateway:** `10.0.2.2`
    - **DNS:** `8.8.8.8`

  Per configurar una IP fixa, des d'aquest panell es pot clicar **Editar** als camps "Asignación de IP" i canviar-ho a **Manual**, introduint els mateixos valors però de forma estàtica.

<img width="330" height="224" alt="30" src="https://github.com/user-attachments/assets/f7a297fe-7609-4e34-97b2-83c1e066658f" />

## Pas 26 – Comprovar la connexió amb `ping google.com`

* Executo `ping google.com` al CMD. El resultat mostra que els 4 paquets enviats han estat rebuts amb 0 pèrdues i un temps de resposta d'aproximadament **12 ms**, confirmant que la connexió a Internet és correcta.

<img width="530" height="212" alt="31" src="https://github.com/user-attachments/assets/319c6046-d9ff-4ae3-b41c-cbc0d65fd582" />

# Fase 6 – Comandes generals

## Pas 27 – Obrir PowerShell

* Busco **"Windows PowerShell"** al cercador i el selecciono per obrir-lo.

<img width="309" height="146" alt="32" src="https://github.com/user-attachments/assets/7785df58-af7a-4bce-835d-ac8fe5f5cd1a" />

## Pas 28 – Diferenciar CMD i PowerShell

> | Característica | CMD (Símbol del Sistema) | PowerShell |
> |---|---|---|
> | **Propòsit** | Comandes bàsiques i clàssiques de Windows | Automatització avançada i scripting |
> | **Objectes** | Traballa amb text pla | Treballa amb **objectes** .NET |
> | **Potència** | Limitada, herència de MS-DOS | Molt potent, permet pipelines d'objectes |
> | **Scripts** | Arxius `.bat` | Arxius `.ps1` |
> | **Exemple** | `dir`, `copy`, `del` | `Get-ChildItem`, `Copy-Item`, `Remove-Item` |
>
> **Quan usar cadascun:**
> - **CMD** → Per a tasques ràpides, scripts simples o compatibilitat amb aplicacions antigues.
> - **PowerShell** → Per automatitzar tasques, gestionar el sistema, treballar amb serveis, registres i objectes complexos.

## Pas 29 – Comandes bàsiques (provades)

* Executo `dir` per veure els fitxers i carpetes del directori arrel `C:\Users\nicksist\Documents`. Es mostra el fitxer prova.txt que he creat abans.

<img width="421" height="134" alt="33" src="https://github.com/user-attachments/assets/38f7eaf4-3d77-4c4f-881a-9c91f1321915" />

* Executo `cd C:\Users\nicksist\Documents` per moure'm a la carpeta de documents que tenia el fitxer, `mkdir prova` per crear una nova carpeta i `echo hola > fitxer.txt` per crear un fitxer de text.

<img width="385" height="32" alt="34" src="https://github.com/user-attachments/assets/1c8f3c56-b9f5-493b-8d90-597dfeb8470b" />

<img width="396" height="135" alt="35" src="https://github.com/user-attachments/assets/f02fd037-9dd8-470a-8c26-37943177587c" />

* Torno a executar `dir` per confirmar que tant la carpeta **prova** com el fitxer **fitxer.txt** (14 bytes) han estat creats correctament.

<img width="436" height="344" alt="36" src="https://github.com/user-attachments/assets/616d9ff2-0fcd-4287-a372-1c101f1999c0" />

* Finalment executo `del fitxer.txt` per eliminar el fitxer i torno a fer `dir` per confirmar que ja no apareix al llistat.

<img width="429" height="328" alt="37" src="https://github.com/user-attachments/assets/44bc395e-ef66-4132-9c6d-1c1be8b3b665" />


## Pas 30 – Comandes útils del sistema

* `tasklist` → Mostra tots els **processos actius** al sistema amb el seu PID, sessió i consum de memòria. Es poden veure processos com `System`, `svchost.exe`, `wininit.exe`, etc.

<img width="542" height="309" alt="38" src="https://github.com/user-attachments/assets/95639aa0-9639-4880-9a83-2dd0408eaffe" />

* `taskkill /IM notepad.exe /F` → Força el tancament del procés **Notepad**. El sistema confirma: *"se terminó el proceso Notepad.exe con PID 7540"*.

<img width="422" height="34" alt="39" src="https://github.com/user-attachments/assets/ef553a8e-db5a-4920-a73d-5e7facfc283e" />

* `systeminfo` → Mostra informació detallada del sistema: nom de l'equip (**DESKTOP-EQI60GD**), sistema operatiu (**Windows 10 Pro**), fabricant (**VirtualBox**), memòria, processador, data d'instal·lació, etc.

<img width="768" height="693" alt="40" src="https://github.com/user-attachments/assets/2a9549a9-c1cf-49e6-a4f3-e500aef72660" />

* `hostname` i `whoami` → `hostname` retorna el nom de l'equip (**DESKTOP-EQI6OGD**) i `whoami` retorna l'usuari atual (**DESKTOP-EQI6OGD\nicksist**).

<img width="217" height="32" alt="41" src="https://github.com/user-attachments/assets/d10094d4-c2e9-495e-99f5-9024d3281e14" />

<img width="200" height="32" alt="42" src="https://github.com/user-attachments/assets/46a435b3-d3bd-44fb-8303-28304011caee" />

## Pas 31 – Comandes de xarxa

* `ipconfig` mostra la configuració IP de l'adaptador Ethernet: **IP 10.0.2.16**, màscara **255.255.255.0** i gateway **10.0.2.2**.

  `ping google.com` envia paquets a Google i el resultat confirma connexió a Internet amb **0% de pèrdua** i temps de resposta ~12 ms.

<img width="474" height="174" alt="43" src="https://github.com/user-attachments/assets/706b45f9-5982-43fb-bd5f-51db33b3ede4" />

<img width="467" height="184" alt="44" src="https://github.com/user-attachments/assets/d851e4eb-374e-41a6-ba1c-825013d07a85" />

* `netstat -an` mostra totes les **connexions de xarxa obertes** al sistema, tant les que estan en estat LISTENING (escoltant) com les ESTABLISHED (connectades). És útil per detectar connexions actives o ports oberts.

<img width="468" height="311" alt="45" src="https://github.com/user-attachments/assets/f325c536-5684-4aba-83f0-27fb022e85bb" />

## Pas 32 – Comandes interessants (avançades)

* `tree` → Mostra l'estructura de carpetes en forma d'arbre des del directori actual. En aquest cas mostra totes les subcarpetes de l'usuari nicksist com `Desktop`, `Documents`, `Downloads`, `prova`, etc.

<img width="310" height="298" alt="46" src="https://github.com/user-attachments/assets/5669036b-bbde-4a39-9138-cd2116a9a915" />

* `cls` → Neteja completament la pantalla del terminal. La pantalla queda buida i el cursor torna a l'inici.

<img width="188" height="17" alt="47" src="https://github.com/user-attachments/assets/ac940c19-ad5b-431c-a513-904aff890897" />

* `help` → Mostra el sistema d'ajuda de PowerShell amb informació sobre els cmdlets, funcions i conceptes disponibles.

<img width="739" height="464" alt="48" src="https://github.com/user-attachments/assets/84427f0c-e643-4034-aadf-42ac1662a5a6" />

> **Nota sobre `shutdown /s /t 0`:** Aquesta comanda apaga l'equip immediatament (temps = 0 segons). No he fet captura per evitar apagar la màquina virtual durant la sessió de treball.

## Pas 33 – Mini interpretació

> **Què mostra `tasklist`?**
> → Mostra tots els **processos actius** en el moment d'executar la comanda, amb el nom del procés, el seu **PID** (identificador de procés), la sessió on s'executa i el consum de memòria. Permet veure quins programes estan en marxa i consumint recursos.
>
> **Què mostra `ipconfig`?**
> → Mostra la **configuració de xarxa** de totes les interfícies del sistema: adreça IP, màscara de subxarxa, porta d'enllaç predeterminada i adreces IPv6. Molt útil per diagnosticar problemes de connectivitat.
>
> **Què mostra `systeminfo`?**
> → Mostra un **resum complet de la informació del sistema**: nom de l'equip, versió del sistema operatiu, fabricant del maquinari, quantitat de RAM, processador instal·lat, data d'instal·lació de Windows i molt més. Equivalent a "Sobre aquest equip" però molt més detallat.

# Fase 7 – Instal·lació d'aplicacions

## Pas 34 – Descarregar un programa des del navegador (VS Code)

* A la pàgina oficial `code.visualstudio.com/Download` selecciono la versió per **Windows (Windows 10, 11)** i inicio la descàrrega de l'instal·lador.

<img width="879" height="377" alt="50" src="https://github.com/user-attachments/assets/7c24bf27-8564-4548-ac65-b1f0592c0984" />

## Pas 35 – Instal·lar seguint l'assistent

* Segueixo l'assistent d'instal·lació. Primer accepto el **acord de llicència** de Microsoft per a VS Code i clico Següent.

<img width="589" height="459" alt="51" src="https://github.com/user-attachments/assets/d6596886-2277-43e2-b9f0-526790578ae7" />

* Confirmo la **carpeta de destinació** on s'instal·larà VS Code: `C:\Users\nicksist\AppData\Local\Programs\Microsoft VS Code` (requereix mínim 576,5 MB).

<img width="587" height="208" alt="52" src="https://github.com/user-attachments/assets/2269871a-4e1d-4f3b-b9c2-412f64091f50" />

Estaria ja per instalar i clicariem a "Instalar".
<img width="591" height="464" alt="53" src="https://github.com/user-attachments/assets/c590c040-11fe-4ec6-a454-833a4407b549" />

## Pas 36 – Obrir i comprovar que funciona

* **Visual Studio Code** s'obre correctament i mostra la pantalla de benvinguda amb les opcions de **Walkthrough: Setup VS Code**. L'aplicació funciona perfectament a Windows 11.

<img width="1018" height="239" alt="54" src="https://github.com/user-attachments/assets/02a280a4-ddd8-4297-a7de-c08b0a6ec2de" />

## Pas 37 – Instal·lar una aplicació des de Microsoft Store

* Obro la **Microsoft Store** i instal·lo **Spotify**  Clico **Obtener** per instal·lar-lo.

<img width="569" height="342" alt="55" src="https://github.com/user-attachments/assets/6f7f5729-3f8a-47ff-81e0-417c0c42dcca" />

## Pas 38 – Obrir i comprovar el funcionament

* Un cop instal·lat, obro l'aplicació de "Spotify".

<img width="1014" height="606" alt="56png" src="https://github.com/user-attachments/assets/55182e26-5778-484a-b2c3-5b6b35b5456a" />

## Pas 39 – Desinstal·lar una aplicació

* Obro **Configuració > Aplicaciones** ① i clico **Aplicaciones instaladas** ② per veure la llista de programes instal·lats.

* Al menú desplegable selecciono **Desinstalar** per iniciar el procés d'eliminació de VS Code.

<img width="456" height="474" alt="57" src="https://github.com/user-attachments/assets/92cfaeb7-19c2-4aee-a222-8924adc23292" />


## Pas 40 – Verificació: comprovar que ja no apareix al sistema

* Faig una cerca de **"Spotify"** al cercador de Windows. Abans apareixia Spotify com a millor coincidència; ara ja **no apareix cap aplicació instal·lada**, només suggeriments de cerca web. Això confirma que Spotify ha estat desinstal·lat correctament.

<img width="515" height="487" alt="58" src="https://github.com/user-attachments/assets/0fcdfc70-b9bd-4217-aafa-4e09c06b8de1" />
