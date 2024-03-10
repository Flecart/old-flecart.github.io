---
layout: page
permalink: notes/linux-command-line
tags: italian
title: Linux command line
---

Ultima modifica: December 1, 2021 6:53 PM
Primo Abbozzo: December 1, 2021 6:52 PM
Studi Personali: No

# **PWN COLLEGE NOTES**

> Note per il sito pwn.college
>

Per andare sulle challange [dojo.pwn.college](https://dojo.pwn.college/)

## **Program Interaction**

### **Linux Command Line**

### **Symlink**

I symlink possono essere di due tipi, *hard* e *soft*.Definiamo ora la differenza fra i due. Per far ciò presentiamo come vengono salvati i file nel file system a grandi linee.

- **File** : nel file system i file sono semprati tra blocchi di contenuto (diretti o indiretti) e **inode**
    - **inode**: contiene le infomazioni del file (Grandezza dei file, timestamps, permessi, Mode ) e gli indirizzi dei blocchi diretti e indiretti; Non contiene il nome del file o il contenuto

    - Una serie di blocchi di data ad indirizzamento indiretto
    - **indirizzamenti indiretti** sono dei blocchi che contengono gli indirizzi di blocchi diretti in cui e splittato il contenuto del file originale (sono creati perchè file abbastanza grossi non riescono a essere immagazzinati in un solo blocco di memoria e devono essere separati)
    - **indirizzamenti diretti**: è un blocco di byte corrispondente al contenuto (o una parte) del file, e non a una altra tabella di indirizzi.
- Directory: Tengono una tabella con l’inode e il rispettivo nome del file (EVRYTHING IS A FILE anche le directory)

- **hard**: è visto dal file system come lo stesso file, ovvero condivide lo sesso inode del file originale
    - L’inode contiene un counter per gli hard link, quando questi arriva a zero il file è eliminato nel filesystem.
    - Due directory che contengono due hard link dello stesso file potrebbero registrare nomi differenti ma i nomi puntano allo stesso inode
    - Non si possono fare hard link delle directory perchè comprometterebbero il sistema
    - Per creare un hard link `ln <fileoriginale> <hardlink>`
- **soft**: è un collegamento a un altro file, senza condividere lo stesso inode dell’originale.
    - Dal file system è visto come *file differente* ossia possiede un inode proprio, senza condividerlo con il file originale.
    - Non condividendo l’inode è possibile *collegare in filesystem diversi*.
    - Essendo solamente un collegamento ha un peso quasi nullo all’interno del filesystem.
    - Per creare un soft link `ln -s <fileoriginale|directory> <softlink>`

> Notai link possono essere relativi rispetto alla directory in cui sono stati creati.
>

### **Tipi di file**

### **Pipes**

Esistono due tipi di pipes:

- **Named**: TODO:deve farlo angelo
- **Unnamed**: sono dei canali per trasferire informazioni tra i processi (es. `echo "prova"|cat` )

[Named pipes tutorial in C]([https://jameshfisher.com/2017/02/17/how-do-i-call-a-program-in-c-with](https://jameshfisher.com/2017/02/17/how-do-i-call-a-program-in-c-with)-pipes/)

### **Binary Files**

Andremo in questi appunti a studiare gli

**ELF**

, il formato eseguibile per Linux.

Riassunto da questa immagine:

### **Headers**

Gli header contengono informazioni necessarie per l’esecuzione del file, come il linking e le istruzioni per caricare l’eseguibile in memoria, e metadata.**Program headers**:

- **LOAD** contiene istruzioni che definiscono quali parti del file sarano caricate in memoria.
- **INTEPR** definisce la libreria che dovrebbe essere utilizzata per caricare l’eseguibile in memoria

**Section Headers**:TODO: noiosi, una lista di nomi :P

### **Symbols and Relocations**

Le informazioni simboliche sono i nomi che diamo alle variabili (funzioni, variabili locali, globali).**Symbol Table**

- È una sezione dell’eseguibile (non necessaria per l’esecuzione del programma) che contiene mapping dei nomi simbolici con i nomi fisici (l’indirizzo di memoria)
- È utile per il debugging, così come al compilatore nel momento di compilazione del programma…
- *Meccanismi di anti-analisi* di programmi possono interagire con la symbol table eliminandola interamente dal programma, o swappando alcuni indici della tabella.

### **Linux Process Loading**

### **Linux Process Execution**

# **Link Utili**

[Cheatsheet pwn tools](https://gist.github.com/anvbis/64907e4f90974c4bdd930baeb705dedf), in modo molto conciso vengono presentate le funzionalità maggiori di pwntools **con esempi**
et [pwn tools](https://gist.github.com/anvbis/64907e4f90974c4bdd930baeb705dedf), in modo molto conciso vengono presentate le funzionalità maggiori di pwntools **con esempi**