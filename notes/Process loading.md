---
layout: page
permalink: notes/process-loading
tags: italian
title: Process loading
---

Ultima modifica: December 6, 2021 2:49 PM
Primo Abbozzo: December 1, 2021 6:54 PM
Studi Personali: No

# Elementi di ripasso

# 2 Caricamento dei processi

## Processo (6)

Il processo possiede tutte queste caratteristiche:

<img src="/images/notes/image/universita/ex-notion/Process loading/Untitled.png" alt="image/universita/ex-notion/Process loading/Untitled">

Ci possono essere molti processi che vengono eseguiti in ogni momento.

### Creazione del processo

Il processo viene creato per *mitosi!* in modo simile alla biologia, un processo deve avere un processo parente.

Quando chiamo /bin/sh  sto facendo un fork della bash! che poi si **rimpiazza con il processo** da eseguire, così funzionano le famiglie delle chiamate exec, (molti comandi simili).

### Caricamento del processo

1. Il processo ha bisogno di un interprete per funzionare. Questo è comunicato dalla `#!` all'inizio del programma. (e riesegue il programma con l'interprete. la cosa può essere ricorsiva. )
2. Se è assente va in automatico a cercare un file di sistema per vedere se il programma matcha un formato o non (è /proc/sys/fs/binfmt_misc in linux).
    - Esempio di cosa è presente in binfmt_misc

        <img src="/images/notes/image/universita/ex-notion/Process loading/Untitled 1.png" alt="image/universita/ex-notion/Process loading/Untitled 1">

        Si va a vedere il magic del file.

        Ci può essere anche una bitmask per matchare.

3. Se è una D-L ELF il kernel di linux va a vedere l'interprete definito nell'elf, lo carica e lascia che questo interprete esegua il programma.

**Caricamento per D-L ELFs**

- In breve

    <img src="/images/notes/image/universita/ex-notion/Process loading/Untitled 2.png" alt="image/universita/ex-notion/Process loading/Untitled 2">


Utilizza 3 variabili d'ambiente per loaddare il processo (Importa librerie utili, se queste sono rotte può rompere l'intero sistema, quindi fai molta attenzione!)

Tutto è caricato nella **memoria virtuale**, in cui tutto è caricato. (utile per isolare i processi fra di loro) È una cosa di sicurezza!

- Memoria virtuale

    <img src="/images/notes/Process loading/Untitled 3.png" alt="Process loading/Untitled 3">

    ### Initializzazione

    Costruttori, sono delle funzioni che vengono eseguite prima che il programma (main) venga caricato. (quindi se crei un costruttore nel preload che possa esser eseguito va!)

    ### Lancio

    __libc_start_main() chiama il main del nostro programma

    Syscall program → OS, and signal is OS→process

    ### Terminazione

    Il programma puo`terminare in due modi (solamente questi due modi!)

    1. Signal
    2. Exit syscall
rogram → OS, and signal is OS→process

    ### Terminazione

    Il programma puo`terminare in due modi (solamente questi due modi!)

    1. Signal
    2. Exit syscall