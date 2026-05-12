# Sprint 2 – Windows: Discs, Quotes, Scripts, Processos i ACLs

---

## Fase 1 – Preparació del sistema

### Pas 1 – Afegir un nou disc virtual a la màquina virtual

Per ampliar l'emmagatzematge de la màquina virtual cal afegir un nou disc des de la configuració de VirtualBox. Accedim a **Configuració → Emmagatzematge** de la màquina virtual "Windows 10 Pro". Fem clic a la icona per afegir un nou disc dur virtual i seleccionem **Crea un nou disc**.

En aquesta captura podem veure que s'ha creat el fitxer `Projecte 2 SP1_1` (el segon disc), amb una mida virtual de **5,00 GB** i format **VDI (Normal)**. Apareix connectat al controlador SATA al port SATA 2, just a sota del disc principal del sistema.

> 💡 Un disc VDI d'ubicació dinàmica ocupa molt poc espai real al host fins que s'hi escriu informació.

<img width="531" height="234" alt="1" src="https://github.com/user-attachments/assets/899cc626-c352-4d95-8fb9-0ebc31f6cddb" />


---

### Pas 2 – Iniciar Windows i obrir Gestió de discs

Un cop afegit el disc a VirtualBox, iniciem la màquina virtual amb Windows 10. Per gestionar els discs des de Windows, executem `diskmgmt.msc` (o clic dret al menú d'inici → **Gestió de discs**).

En la captura s'observa que el sistema reconeix el nou **Disc 1** (5 GB) amb tot l'espai **No asignat**. Això confirma que Windows l'ha detectat correctament, però encara no s'ha inicialitzat ni creat cap partició.

> ℹ️ Quan un disc és nou, Windows el detecta però cal inicialitzar-lo (triar GPT o MBR) abans de poder-hi crear particions.

<img width="747" height="574" alt="2" src="https://github.com/user-attachments/assets/2aaa6a9c-fbe2-44c3-a301-15cceb0f94a8" />


---

### Pas 3 – Inicialitzar el disc i crear dues particions: Dades (NTFS) i Portable (FAT32)

#### Crear la partició Dades (NTFS)

Fem clic dret sobre l'espai no asignat del Disc 1 i seleccionem **Nou volum simple…**

<img width="405" height="247" alt="3" src="https://github.com/user-attachments/assets/c9bb1dde-8f64-4cd7-a24a-e6726bc8e2da" />


S'obre l'assistent per crear el volum. Introduïm **3000 MB** (3 GB) com a mida per a la primera partició, deixant la resta per a la segona.

<img width="491" height="390" alt="4" src="https://github.com/user-attachments/assets/5163e6a2-fc43-493b-9adc-5bc652c043cb" />


Assignem la lletra d'unitat **E:** a aquesta partició perquè sigui accessible des de l'Explorador de Windows.

<img width="488" height="387" alt="5" src="https://github.com/user-attachments/assets/0f9a2fd4-0470-4bdc-879e-e5717cc45b21" />


Formatem la partició amb el sistema de fitxers **NTFS**, que és el format natiu de Windows i l'únic que suporta quotes de disc i permisos ACL avançats. L'etiqueta del volum serà **Dades**.

<img width="483" height="383" alt="6" src="https://github.com/user-attachments/assets/8a037cc0-4da9-4d64-96ab-bc5d31707bab" />

El resum final de l'assistent mostra tota la configuració seleccionada: 3000 MB, unitat E:, NTFS, etiqueta "Dades". Fem clic a **Finalizar** per crear la partició.

<img width="495" height="380" alt="7" src="https://github.com/user-attachments/assets/c5e8e057-997a-4da9-a41b-2f46add7b39d" />

#### Crear la partició Portable (FAT32)

Amb l'espai restant del Disc 1 (2,07 GB aproximadament), creem una segona partició. Clic dret → **Nou volum simple…**

<img width="708" height="207" alt="8" src="https://github.com/user-attachments/assets/a7545f94-2826-4586-ab00-13b71ac8c97e" />


Usem tot l'espai disponible (2117 MB) per a aquesta partició, que simularà un dispositiu portàtil.

<img width="488" height="389" alt="9" src="https://github.com/user-attachments/assets/f3983cef-00a2-4b06-bbea-721319f6c800" />

Assignem la lletra **F:** per a la partició Portable.

<img width="488" height="379" alt="10" src="https://github.com/user-attachments/assets/6d4de20a-6ee0-47dd-b5ef-4bff18dfcf6f" />

Formatem aquesta partició com a **FAT32** amb l'etiqueta **Portable**. FAT32 és compatible amb la majoria de dispositius (càmeres, consoles, etc.) però té la limitació de no poder emmagatzemar fitxers de més de 4 GB.

| Característica      | NTFS          | FAT32                  |
|---------------------|---------------|------------------------|
| Mida màx. fitxer    | Il·limitada   | 4 GB                   |
| Permisos ACL        | ✅ Sí         | ❌ No                  |
| Quotes de disc      | ✅ Sí         | ❌ No                  |
| Compatibilitat      | Windows/Linux | Universal              |
| Journaling          | ✅ Sí         | ❌ No                  |

<img width="487" height="376" alt="11" src="https://github.com/user-attachments/assets/d6cb4448-50d0-4703-83de-32d1ba7f76fa" />

El resum final confirma la creació de la partició Portable: 2117 MB, unitat F:, FAT32. Fem clic a **Finalizar**.

<img width="487" height="376" alt="12" src="https://github.com/user-attachments/assets/2501d668-fe24-44a7-85a3-c9b43e06d0b8" />

---

### Pas 4 – Assignar lletres i comprovar amb diskpart la configuració

Per verificar la configuració de manera exacta, obrim una consola CMD com a administrador i executem `diskpart` seguit de les comandes de llistat:

```
DISKPART> list disk
DISKPART> sel disk 1
DISKPART> list part
DISKPART> list vol
```

La captura mostra el resultat complet. Podem confirmar:

- **Disc 0 (50 GB)**: disc principal del sistema amb la partició C: (NTFS, 49 GB).
- **Disc 1 (5 GB)**: el nou disc amb dues particions:
  - **Partició 2** → Volum 4 · Lletra **E:** · Etiqueta **Dades** · NTFS · 3000 MB ✅
  - **Partició 3** → Volum 5 · Lletra **F:** · Etiqueta **PORTABLE** · FAT32 · 2117 MB ✅

<img width="645" height="460" alt="13" src="https://github.com/user-attachments/assets/d752cbef-2776-438a-8fc3-4d87ccd773b2" />

---

## Fase 2 – Quotes i usuaris

### Pas 5 – Activar quotes de disc a la partició Dades (NTFS)

Les **quotes de disc** a Windows permeten limitar l'espai que cada usuari pot usar dins d'una partició NTFS. Per activar-les, obrim l'Explorador de Windows, clic dret sobre la unitat **Dades (E:)** i seleccionem **Propietats**.

<img width="624" height="201" alt="14" src="https://github.com/user-attachments/assets/f647e124-a977-405c-8621-041da057bdbf" />

A la finestra de propietats ens dirigim a la pestanya **Cuota** i fem clic a **Mostrar configuració de cuota**.

<img width="334" height="198" alt="15" src="https://github.com/user-attachments/assets/9a58ee1e-2196-40d1-9d18-f16d4f8ae5d2" />

---

### Pas 6 – Establir límit de 300 MB per usuari, amb notificació d'advertència

Dins del panell de configuració de quotes, activem les opcions:

- ✅ **Habilita la administración de cuota**: activa el sistema de quotes.
- ✅ **Denegar espacio en disco a usuarios que superen el límite**: bloqueja l'escriptura quan se supera el límit.
- 🔘 **Limitar espacio en disco a**: **300 MB**
- ⚠️ **Establecer el nivel de advertencia en**: **150 KB** (l'usuari rebrà un avís quan quasi ompli el límit)
- ✅ **Registrar un evento cuando algún usuario supere su límite de cuota**
- ✅ **Registrar un evento cuando algún usuario supere su nivel de advertencia**

> ⚠️ Amb el limit establert a 300 MB, cap usuari podrà escriure més dades un cop superi aquesta mida. L'advertència a 150 KB és inusualment baixa (seria recomanable posar-la a uns 250 MB), però serveix per il·lustrar el funcionament.

<img width="357" height="438" alt="16" src="https://github.com/user-attachments/assets/766c4f94-8a52-48da-b984-c2e9a5f40570" />

---

### Pas 7 – Crear dos usuaris locals: alumne1 i alumne2

Per crear usuaris locals a Windows, executem `lusrmgr.msc` (Gestió d'usuaris i grups locals) des de la finestra **Executar** (Win + R).

<img width="391" height="195" alt="17" src="https://github.com/user-attachments/assets/0cc0e944-129d-47ee-b4c3-841aef4abdf7" />


Dins de la consola, fem clic dret sobre **Usuaris → Usuari nou…**

<img width="265" height="80" alt="18" src="https://github.com/user-attachments/assets/1e3c2892-2028-4b3f-993f-ae164fd2c790" />

Creem l'usuari **alumne1** amb la contrasenya corresponent. Activem l'opció **La contrasenya mai expira** per evitar problemes en les proves.

<img width="404" height="376" alt="19" src="https://github.com/user-attachments/assets/dc31d6c1-b986-49f5-8d39-0c33b494e39c" />

De la mateixa manera, creem l'usuari **alumne2** amb la mateixa configuració.

<img width="410" height="376" alt="20" src="https://github.com/user-attachments/assets/000d0f4b-de48-48ff-ba19-8ffd43284af6" />

---

### Pas 8 – Afegir-los a un grup nou anomenat Limitats

Dins de `lusrmgr.msc`, fem clic sobre la carpeta **Grupos** per veure tots els grups existents. Clic dret en un espai buit de la llista → **Grupo nuevo…**

<img width="567" height="458" alt="21" src="https://github.com/user-attachments/assets/664634cf-d5e9-46b5-9a3a-faa920da186d" />

Introduïm el nom del grup **Limitats** i afegim els dos usuaris creats (`alumne1` i `alumne2`) com a membres. Fem clic a **Crear** per finalitzar.

<img width="407" height="374" alt="22" src="https://github.com/user-attachments/assets/a33b9bb9-6fe2-4672-b40c-2e82af9e7151" />

---

### Pas 9 – Provar la còpia de fitxers a Dades per veure com actuen les quotes

Per comprovar que les quotes funcionen correctament, iniciem sessió com a **alumne1** i intentem crear fitxers de diverses mides a la partició `E:\` amb la comanda `fsutil file createnew`:

```
fsutil file createnew E:\prova.dat 350000000   → Error 112: Espai insuficient (supera els 300 MB)
fsutil file createnew E:\prova.dat 150000000   → Fitxer creat (150 MB)
fsutil file createnew E:\prova.dat 150000000   → Fitxer creat (re-escriu el mateix)
fsutil file createnew E:\prova2.dat 50000000   → Fitxer creat (50 MB)
fsutil file createnew E:\prova3.dat 50000000   → Fitxer creat (50 MB)
fsutil file createnew E:\prova4.dat 50000000   → Fitxer creat (50 MB)
fsutil file createnew E:\prova5.dat 50000000   → Error 112: Espai insuficient (ja s'han superat els 300 MB)
```

La captura mostra clarament com el sistema **nega l'accés** quan l'usuari intenta superar els 300 MB assignats per la quota. L'error **112** és el codi de Windows per "espai en disc insuficient", que en aquest context és provocat artificialment per la quota, no per la mida real del disc.

<img width="564" height="478" alt="23" src="https://github.com/user-attachments/assets/43af1a00-f7d1-4f1f-bc52-6a86f8556a92" />


---

## Fase 3 – Script de còpia i automatització

### Pas 10 – Afegir tercer disc virtual, formatar-lo en NTFS com a Backups

Des de la configuració de VirtualBox, afegim un **tercer disc** (`Projecte 2 SP1_2.vdi`) de 5 GB connectat al port SATA 3. Servirà com a unitat de còpies de seguretat.

<img width="663" height="325" alt="24" src="https://github.com/user-attachments/assets/bcb3c20f-5489-449a-8a8f-d12c96b20cc2" />

Un cop dins de Windows, obrim la **Gestió de discs** i localitzem el nou **Disc 2** (4,98 GB, no asignat). Clic dret → **Nou volum simple…**

<img width="500" height="114" alt="25" src="https://github.com/user-attachments/assets/276a1e72-e309-45d7-bb9b-06c475c8c8b7" />

Formatem tot el disc com a **NTFS** i li posem l'etiqueta **Backups**. Assignem la lletra **B:**.

<img width="491" height="386" alt="26 1" src="https://github.com/user-attachments/assets/5c1e03ec-6959-4680-97ee-0f8cd2c9416e" />

<img width="488" height="382" alt="27" src="https://github.com/user-attachments/assets/a679e30e-6860-411d-bd91-ea77ce851306" />


---

### Pas 11 – Crear carpeta CòpiesUsuaris dins Backups

Un cop creat i muntat el disc Backups (B:), creem manualment la carpeta `CòpiesUsuaris` dins de la unitat B:. Aquesta carpeta actuarà com a contenidor principal on l'script crearà una subcarpeta per cada usuari.

La captura confirma que la carpeta `CòpiesUsuaris` ha estat creada correctament a `B:\`.

<img width="236" height="86" alt="28" src="https://github.com/user-attachments/assets/51e5354d-9aff-4b83-8367-24e196c9e442" />

---

### Pas 12 – Crear un script .bat que copiï C:\Users\%USERNAME% a B:\CòpiesUsuaris\%USERNAME%

Creem un fitxer `script.bat` (per exemple a `C:\Users\aaron\Documents\script.bat`) amb el contingut següent:

```bat
@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y
```

**Explicació de la comanda:**

| Paràmetre | Significat |
|-----------|------------|
| `@echo off` | Silencia la sortida de les comandes a la consola |
| `xcopy` | Copia fitxers i directoris (inclou subdirectoris) |
| `%USERNAME%` | Variable d'entorn que s'expandeix automàticament amb el nom de l'usuari actiu |
| `/E` | Copia tots els subdirectoris, fins i tot els buits |
| `/I` | Si la destinació no existeix, la crea com a directori |
| `/Y` | Sobreescriu fitxers existents sense demanar confirmació |

<img width="508" height="126" alt="29" src="https://github.com/user-attachments/assets/92aeb210-8edb-4692-a27d-dffa4c86bef8" />

---

### Pas 13 – Obrir gpedit.msc → Configuració d'usuari → Scripts → Inici de sessió

Per assignar l'script perquè s'executi automàticament en iniciar sessió, obrim l'**Editor de directrius de grup local** executant `gpedit.msc` des de la finestra **Executar** (Win + R).

<img width="391" height="186" alt="30" src="https://github.com/user-attachments/assets/25666e0b-ae71-4f23-b82c-86790b7c9c96" />

Dins de l'editor, naveguem per l'arbre de directives:

**Configuració d'usuari → Configuració de Windows → Scripts (inici de sessió o tancament de sessió)**

Fem doble clic sobre **Iniciar sessió** per obrir la finestra de propietats.

> ℹ️ La distinció entre **Configuració d'equip** i **Configuració d'usuari** és important: les directives d'equip s'apliquen al sistema sencer (independentment de qui hi ha iniciat sessió), mentre que les d'usuari s'apliquen per sessió d'usuari.

<img width="662" height="324" alt="31" src="https://github.com/user-attachments/assets/71d4800c-6dd9-4b59-be56-1512f23b79e7" />

---

### Pas 14 – Assignar l'script perquè s'executi automàticament en iniciar sessió

A la finestra de propietats d'**Iniciar sessió**, fem clic a **Agregar…** i introduïm la ruta completa al nostre script:

`C:\Users\aaron\Documents\script.bat`

Fem clic a **Aceptar** per confirmar.

<img width="651" height="443" alt="32" src="https://github.com/user-attachments/assets/0bf0be9e-5186-4863-acd3-790dda896eb0" />

> ⚠️ **Nota important sobre `gpedit.msc` i usuaris locals:** La directiva de grup local s'aplica a **tots** els usuaris del sistema (excepte administradors, en alguns casos). Per controlar l'script específicament per a `alumne1` i `alumne2`, una alternativa és copiar l'script a la carpeta de Documents de cada usuari i registrar-lo individualment. En aquest cas, l'script funciona de manera global per a qualsevol usuari que iniciï sessió.

---

## Fase 4 – Verificació i documentació

### Pas 15 – Comprovació: l'script fa la còpia a Backups

Iniciem sessió amb l'usuari **alumne1**. L'script s'executa automàticament a l'inici de sessió i copia el contingut de `C:\Users\alumne1` a `B:\CòpiesUsuaris\alumne1`.

La captura del Explorador de Windows confirma que la còpia s'ha realitzat correctament: es veuen totes les carpetes del perfil d'alumne1 (`Contacts`, `Desktop`, `Documents`, `Downloads`, etc.) dins de `B:\CòpiesUsuaris\alumne1\`, amb data del 29/04/2026.

<img width="1024" height="658" alt="image" src="https://github.com/user-attachments/assets/bc70621e-19e3-4f8a-9e16-a2a0e7b895bd" />


---

## Fase 5 – Gestió de processos i serveis

### Pas 19 – Llistar processos actius

Iniciem sessió com a **alumne1**, obrim la consola (CMD) i executem `tasklist` per obtenir la llista de tots els processos actius, amb el seu PID, sessió i ús de memòria.

<img width="372" height="391" alt="49" src="https://github.com/user-attachments/assets/50fff54a-27c2-48ec-bafd-0d7885508eb5" />

```
C:\Users\alumne1> tasklist
```

La captura mostra processos típics del sistema: `System Idle Process`, `System`, `Registry`, `smss.exe`, `csrss.exe`, `wininit.exe`, `services.exe`, `lsass.exe`, `svchost.exe` (múltiples instàncies), etc.

<img width="615" height="377" alt="33" src="https://github.com/user-attachments/assets/9cb69050-328e-40b5-b1c8-402182748706" />

Redirigim la sortida a un fitxer de text per poder-la analitzar:

```
C:\Users\alumne1> tasklist > C:\Users\%USERNAME%\processos_inici.txt
```

La captura mostra que la comanda s'ha executat correctament i que el fitxer `processos_inici.txt` (12.950 bytes) s'ha creat al directori de l'usuari `alumne1`. Fem `dir` per confirmar-ho.

<img width="532" height="417" alt="34" src="https://github.com/user-attachments/assets/9c5137ae-3747-4c59-bb11-fc3e3e4c0b6c" />

Comprovem alguns processos clau usant `findstr` per filtrar del fitxer guardat:

```
findstr explorer.exe C:\Users\%USERNAME%\processos_inici.txt
findstr SearchIndexer.exe C:\Users\%USERNAME%\processos_inici.txt
findstr OneDrive.exe C:\Users\%USERNAME%\processos_inici.txt
```

- **explorer.exe** (275 MB) → Gestor del sistema de fitxers i escriptori.
- **SearchIndexer.exe** (42 MB) → Servei d'indexació per a la cerca de Windows.
- **OneDrive.exe** (133–135 MB) → Sincronització al núvol de Microsoft; prescindible en entorns de laboratori.

<img width="745" height="191" alt="35" src="https://github.com/user-attachments/assets/76639080-f8e5-4f9d-9a88-dacae9b39941" />

---

### Pas 20 – Identificar processos prescindibles

Filtrem el `tasklist` per trobar processos no essencials per a l'usuari en un entorn educatiu:

```
C:\Users\alumne1> tasklist | findstr "OneDrive.exe Teams.exe SkypeApp.exe"
```

La captura mostra que **OneDrive.exe** s'executa en dues instàncies (PID 4272 i 1480), consumint uns 133-135 MB de RAM en total.

<img width="691" height="58" alt="36" src="https://github.com/user-attachments/assets/46917d8f-8caa-4404-aa18-2fa7aafcd10a" />

**Taula de processos prescindibles identificats:**

| Nom del procés | Memòria aprox. | Justificació per eliminar |
|----------------|----------------|---------------------------|
| `OneDrive.exe` | ~135 MB | Sincronització al núvol innecessària en un entorn de VM sense connexió a internet real |
| `Teams.exe` | ~150-400 MB | Client de videoconferència no necessari per a tasques d'aula |
| `SkypeApp.exe` | ~80-150 MB | Aplicació de comunicació no requerida en l'entorn de laboratori |

> 💡 En màquines virtuals amb pocs recursos (4 GB de RAM), eliminar aquests processos pot alliberar entre 200-700 MB de memòria, millorant notablement el rendiment del sistema.

---

### Pas 21 – Eliminar processos manualment

Executem `taskkill` per finalitzar el procés d'OneDrive forçosament:

```
C:\Users\alumne1> taskkill /IM OneDrive.exe /F
```

La captura mostra el resultat:
- El procés amb PID 4272 **no s'ha pogut terminar** (accés denegat, possiblement perquè és un procés del sistema o un usuari diferent).
- El procés amb PID 1480 **s'ha terminat correctament**.

Comprovem amb `tasklist | findstr OneDrive.exe` que ara només en queda una instància (PID 4272).

<img width="692" height="132" alt="37" src="https://github.com/user-attachments/assets/a2475cf2-3b55-4764-bb5c-c9e593b7dd94" />


> ⚠️ **Nota:** En alguns casos, un procés amb protecció de Windows (com alguns serveis de sistema o processos protegits) no pot ser terminat ni amb el flag `/F`. Això és un mecanisme de seguretat del sistema operatiu.

---

### Pas 22 – Automatitzar-ho a l'inici de sessió

Modifiquem l'script `script.bat` per incloure les comandes `taskkill` que eliminaran automàticament OneDrive i Teams cada vegada que un usuari iniciï sessió:

```bat
@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y

taskkill /IM OneDrive.exe /F
taskkill /IM Teams.exe /F
```

<img width="501" height="138" alt="38" src="https://github.com/user-attachments/assets/cc496db9-9643-41c1-9dd6-e98374a2d56f" />


Per verificar que funciona, iniciem sessió com a **alumne2** i comprovem que OneDrive no s'executa:

<img width="354" height="387" alt="52" src="https://github.com/user-attachments/assets/7f025452-3af7-49b8-9cce-6f0d851c77a7" />

```
C:\Users\alumne2> tasklist | findstr OneDrive.exe
(cap resultat)
```

La consola no retorna cap resultat, cosa que confirma que **OneDrive.exe no s'està executant** per a `alumne2` gràcies a l'script d'inici de sessió.

<img width="387" height="52" alt="39" src="https://github.com/user-attachments/assets/bc7cd190-708f-457b-8b12-79c2a10b0934" />

---

### Pas 23 – Documentació: tasklist, anàlisi de processos crítics i rendiment

#### Fitxer de processos i anàlisi

El fitxer `processos_inici.txt` generat per `tasklist` conté la llista completa de processos en el moment d'inici de sessió. S'ha adjuntat a la documentació com a evidència.

#### Què passa si mates un procés crític com explorer.exe?

`explorer.exe` és el gestor de l'escriptori i de l'Explorador de fitxers de Windows. Si l'eliminem:

1. L'escriptori desapareix completament (barra de tasques, icones, fons).
2. No podem obrir cap finestra ni accedir a cap fitxer via GUI.
3. El sistema NO es penja: el kernel i els serveis segueixen funcionant.
4. Per recuperar-lo: `Ctrl + Alt + Supr → Administrador de tasques → Arxiu → Executar nova tasca → explorer.exe`

> ⚠️ **Prova controlada:** En un entorn de laboratori, eliminar `explorer.exe` és reversible. En un entorn de producció caldria anar amb molta cura, ja que l'usuari quedaria sense interfície gràfica.

#### Com millora el rendiment en VMs?

| Acció | Recursos alliberats |
|-------|---------------------|
| Matar OneDrive.exe | ~135 MB RAM, CPU esporàdica |
| Matar Teams.exe | ~150-400 MB RAM, CPU i xarxa |
| Deshabilitar SearchIndexer | ~40 MB RAM, I/O disc reduït |
| Total estimat | +300-600 MB RAM disponible |

En màquines virtuals amb 4 GB de RAM, alliberar 300+ MB pot significar la diferència entre un sistema fluid i un de lent.

---

## Fase 6 – Gestió de permisos (ACLs)

### Què són les ACLs i com funcionen a Windows

A Windows, cada fitxer i carpeta té una **llista de control d'accés (ACL, Access Control List)**. Aquesta llista defineix qui pot fer què amb aquell recurs.

Cada entrada d'una ACL es diu **ACE (Access Control Entry)** i indica:
- Quina **identitat** (usuari o grup) està afectada
- Quins **permisos** té (lectura, escriptura, execució, control total, etc.)
- Si el permís és **Permetre** o **Denegar**

**Permisos disponibles a Windows:**

| Permís | Descripció |
|--------|------------|
| Control total (F) | Accés complet: llegir, escriure, modificar, eliminar i canviar permisos |
| Modificar (M) | Llegir, escriure i eliminar fitxers, però no canviar permisos |
| Lectura i execució (RX) | Obrir fitxers i executar programes |
| Mostrar contingut | Llistar el contingut d'una carpeta |
| Lectura (R) | Obrir fitxers en mode només lectura |
| Escriptura (W) | Crear fitxers i subcarpetes |

**Herència:** Els permisos d'una carpeta pare es propaguen automàticament a les subcarpetes i fitxers. Quan es desactiva la herència, cal decidir si es conserven o descarten les entrades heretades.

---

### Pas 24 – Crear la carpeta Projectes

Iniciem sessió com a **administrador** i creem la carpeta `Projectes` dins de la partició Dades (E:). La carpeta s'ha creat correctament a `E:\Projectes`.

<img width="583" height="78" alt="40" src="https://github.com/user-attachments/assets/db7fe323-16fb-4f21-87d4-739e5d9f9c1d" />


---

### Pas 25 – Assignar permisos normals al grup Limitats

Fem clic dret sobre `E:\Projectes → Propietats → Seguretat`. Veiem els permisos actuals (heretats de `E:\`): Usuaris autenticats, SYSTEM, Administradors i Usuaris.

Fem clic a **Opciones avanzadas** per accedir a la configuració avançada de permisos.

<img width="771" height="1024" alt="image" src="https://github.com/user-attachments/assets/ee0cc03b-fe61-42fe-9929-c5d8e41b7ef7" />


A la finestra d'opcions avançades veiem que els permisos estan **heretats** des de `E:\` (columna "Heredada de"). Fem clic a **Deshabilitar herencia** per trencar la herència i poder gestionar els permisos de forma independent.

<img width="359" height="476" alt="44" src="https://github.com/user-attachments/assets/cc70c9d6-f4a2-4452-94ed-f5e607948f8a" />


Eliminem l'entrada de **Usuarios (DESKTOP-EQI6OGD\Usuarios)** per netejar els permisos per defecte que no necessitem. Seleccionem l'entrada i fem clic a **Quitar**.

<img width="724" height="393" alt="47" src="https://github.com/user-attachments/assets/36b01016-87bb-48cb-a564-a98816ed964a" />


Ara afegim el grup **Limitats** amb **Control total**. Fem clic a **Agregar**, introduïm `Limitats`, i marquem tots els permisos bàsics (Control total, Modificar, Lectura i execució, Mostrar el contingut de la carpeta, Lectura, Escriptura).

El tipus és **Permitir** i s'aplica a **Esta carpeta, subcarpetes y archivos** per garantir herència cap avall.

<img width="564" height="394" alt="46" src="https://github.com/user-attachments/assets/f94d0370-5f20-489d-b168-7c0090e51512" />


La captura de la configuració avançada final mostra el resultat: la columna **"Heredada de"** ara diu **"Ninguno"** per a totes les entrades, confirmant que la herència s'ha desactivat. El grup **Limitats (aaron\Limitats)** apareix amb **Control total**.

<img width="724" height="393" alt="47" src="https://github.com/user-attachments/assets/6b899e3d-6b82-464a-b6c1-4713b0abe195" />

---

### Pas 26 – Comprovar accés amb alumne1

Iniciem sessió com a **alumne1** (membre del grup Limitats). Creem un fitxer de text `hey.txt` a `E:\Projectes` amb el contingut "hola".

La captura confirma que alumne1 ha pogut crear i escriure el fitxer sense cap problema, tal com s'esperava (té **Control total** hereta del grup Limitats).

<img width="268" height="94" alt="50" src="https://github.com/user-attachments/assets/1e4ec27d-9238-4be0-929a-5480cc86d886" />


El fitxer `prova` s'ha creat correctament a `E:\Projectes` i conté el text "hola prova".

<img width="180" height="74" alt="51" src="https://github.com/user-attachments/assets/fbd718af-5684-42fe-add1-4cae439452b7" />

---

### Pas 27 – Aplicar excepció per alumne2 (només lectura)

Tornem a iniciar sessió com a **administrador** i executem la comanda `icacls` per aplicar una excepció específica per a `alumne2`:

```
icacls "E:\Projectes" /grant:r alumne2:(R)
```

**Explicació:**
- `/grant:r` → Substitueix (reset) qualsevol permís existent per a aquell usuari.
- `alumne2:(R)` → Assigna **només lectura (R)** a l'usuari alumne2.

La sortida confirma: *"Se procesaron correctamente 1 archivos"*. Ara `alumne2` té **només lectura**, tot i ser membre del grup Limitats que té Control total (la entrada explícita de l'usuari té **prioritat** sobre la del grup).

<img width="550" height="63" alt="48" src="https://github.com/user-attachments/assets/a97d8e52-ca0f-45f9-8e02-3ec1de258b47" />

---

### Pas 28 – Comprovar l'excepció amb alumne2

Iniciem sessió com a **alumne2** i accedim a `E:\Projectes`. La captura mostra que la carpeta apareix **buida** per a alumne2 (no veu el fitxer creat per alumne1, o la carpeta s'ha estat modificada entre captures).

Quan alumne2 intenta crear un fitxer nou o modificar algun existent, rep un missatge de **denegació d'accés**.

<img width="460" height="109" alt="54" src="https://github.com/user-attachments/assets/78d25f28-c3e8-485a-99c4-ef0848d0e219" />


Tornem a iniciar sessió com a alumne1 i comprovem que pot llegir i veure el fitxer `hola.txt` creat a la sessió anterior.

<img width="295" height="94" alt="53" src="https://github.com/user-attachments/assets/be4f55d0-5079-4b70-a54b-7f33ceebdd36" />



---
