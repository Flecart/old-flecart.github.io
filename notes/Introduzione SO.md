---
layout: page
permalink: notes/introduzione-so
tags: italian
title: Introduzione SO
---

Ripasso Prox: 40
Ultima modifica: April 9, 2023 9:36 AM
Primo Abbozzo: September 21, 2022 11:15 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Introduzione a SO

## Intro

### Scopi del sistema operativo 🟩

Un sistema operativo è una **astrazione sul HW** che permette di

- Gestire l’esecuzione di più programmi assieme (concorrenza), tramite virtualizzazione CPU e Memoria
- Gestire le risorse (Quindi I/O, RAM, Memoria, Networking)
- Fornisce una interfaccia di programmazione (API) molto più generale e potente, in grado di astrarre da dettagli di livello basso, vicini all’Hardware (come device drivers).

Quindi in breve il SO è n **programma** che crea un ambiente civile per i programmi in cui interagire, e facilita molto il lavoro al programmatore per la sua interfaccia nuova. (si potrebbe dire che sia una macchina virtuale con un suo linguaggio (che è l’API) se seguiamo la terminologia di [Macchine Astratte](/notes/macchine-astratte))

### Vantaggi principali 🟩

Col sistema operativo abbiamo ora una **astrazione sull’HW**che ci permette di interagire con queste in modo molto più facile (molto molto).

Quindi

- Indipendenza dall’hardware (i dettagli nascosti sotto le interfacce)
- Programmabilità e comodità di Uso per le API che sono presenti.

Un buon sistema operativo deve essere quindi semplice per l’utilizzo ed efficiente nell’utilizzo delle risorse che ha disponibili.

## Sistemi paralleli ↩️

Sistemi paralleli sono dei sistemi che possono eseguire più istruzioni allo stesso momento (quindi hanno più centri computazionali diciamo.

### **Tassonomia sulla struttura**

Questo sono stati citati in [CPU e storia degli elaboratori](/notes/cpu-e-storia-degli-elaboratori).

- SIMD, come le GPU.
- MIMD, multicore, quelli che ci sono anche nelle GPU.

### **Tassonomia sulla dimensione**

- Basso parallelismo, quando ho poche CPU potenti.
- Sistemi massicciamente paralleli, ho tante CPU, anche normali.

### Tipologie di **Coupling**

Tight quando ho CPU su MEMORIA CONDIVISA

Loose quando ho CPU su memoria privata, che possano comunque comunicare fra di loro.

### **Alcune tipologie di sistemi paralleli**

Symmetric multiprocessing: quando hanno la stessa struttura di dati per ogni processore.

Questo rende più semplice un pò la gestione delle strutture di dati, che sono le stesse.

**Asymmetric multiprocessing** quando c’è un unico processo che dà da fare un compito specifico a certi processi (quindi ho una asimmetria

## Sistemi realtime

> Quando il valore di output dipende non solo dal valore, ma anche dall’**istante** in cui il valore viene prodotto.
>

### Hard and soft real-time

Hard quando può avere effetti catastrofici, come controllo velivoli o Nucleari.

Soft quando ho solo disservizi.

# Vecchia roba

### Hardware e Software

Il professore fa una distinzione molto strana fra software e hardware (ricorda teatrino dei limoni che ha fatto in classe).

In soldoni hardware è tutto quello che è composto da mero hardware. Il software è la conoscenza, qualcosa che si distingue molto facilmente perché è facilmetne copiabile, e distribuibile

### Informazione

qualche conoscienza che è utile. Ha 3 problemi principali

1. **Elaborazione**, che risolve il problema della trasformazione di un informazione in un altra forma che possa risultare utile (es bites in suoni che si possono sentire).
2. **Memorizzazione** che risolve il problema di trattenimento dell’informazione nel tempo.
3. **Comunicazione** che risolve il problema di comunicazione dell’informazione in due luoghi diversi (protocolli)

### Cosa fa un informatico secondo il prof.

Studia un problema, da una descrizione della soluzione in modo preciso e dettagliato che un calcolatore si ain grado di eseguire la soluzione (e replica questo pensiero umano).

### Sulle graffette

esempio che ha fatto il prof riguardo le graffette. Afferma in soldoni che la scuola uccida la creatività perché si trovano molti meno modi di utilizzare la creatività, e sembra ch ela causa principale di questo sia la scuola. Ma è davvero così???

A me sembra che sia il processo di crescita normale in cui si impara cosa servno di solito a cosa, quindi si spendono meno risorse per cose comuni. È una cosa normale nell’essere umano che una cosa comune sia poco interessante. È interessante un modo nuovo e utile del suo utilizzo, ma il raggio di soluzioni è vasto. Le cose comuni è difficile che servano per soluzioni innovative, senza nessuna base: eg. se voglio fare maetematica non vado certo a considerare una graffetta, ci vorrebbero altri episodi serendipici che possano fare una associazione, cosa direi che non accadrebbe mai