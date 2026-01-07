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




