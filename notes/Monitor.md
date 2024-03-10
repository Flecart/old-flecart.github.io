---
layout: page
permalink: notes/monitor
tags: italian
title: Monitor
---

Ripasso Prox: 70
Ripasso: June 10, 2023
Ultima modifica: April 1, 2023 9:09 AM
Primo Abbozzo: November 9, 2022 11:31 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Monitor

Questo è un modo di più alto livello per creare programmazione concorrente.

## Introduzione

Questo costrutto per la programmazione concorrente, prende molto dalla programmazione agli oggetti, abbiamo delle variabili presenti al monitor, **private** solamente accessibili ad essa, tramite procedure che sono **mutex** automaticamente!

### Elementi costituenti 🟩

- Dati locali
- Sequenza di inizializzazione
- Procedure di entrata

Appena provo a chiamare una procedura, questa è fatta già in mutua esclusione!.

E **possono modificare dati locali** solo tramite chiamate a sue procedure

- Cose in slide

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled.png" alt="image/universita/ex-notion/Monitor/Untitled">


### Variabili di condizione 🟩

Queste sono variabili utilizzate per **sincronizzare l’accesso**,

- Strutture classiche

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 1.png" alt="image/universita/ex-notion/Monitor/Untitled 1">


### Politica del signal urgent (!) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 2.png" alt="image/universita/ex-notion/Monitor/Untitled 2">


L’idea è molto simile a quanto fatto per i signal presenti in [Semafori](/notes/semafori), se qualcuno è in attesa, dai subito il bastone a lui, altrimenti non fai niente.

Questa è la politica di signalling che **viene usata implicitamente in esame**.

### Altre politiche di signalling (3) 🟨

- Slide

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 3.png" alt="image/universita/ex-notion/Monitor/Untitled 3">


### Differenze con semafori (3) 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 4.png" alt="image/universita/ex-notion/Monitor/Untitled 4">


Sembrano simili la Wait e la signal con P e la V, ma sono cose totalmente diverse!!!!.

- Signal non ha nessun effetto se non ci sono processi in attesa, mentre V memorizza sempre
- Wait è sempre bloccante! mentre P no…
- Il processo risvegliato è sempre eseguito per primo! (signal urgent).

### Implementazione dei semafori con monitor 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 5.png" alt="image/universita/ex-notion/Monitor/Untitled 5">


È una implementazione molto facile! Per questo motivo ci piace abbastanza 😀

### Implementazione monitor con semafori 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 6.png" alt="image/universita/ex-notion/Monitor/Untitled 6">


## Problemi classici con monitor

### Readers and writers 🟨+

la parte difficile di questa parte è scrivere bene le invarianti, quindi è molto più facile scrivere una soluzione una volta che si sa.

- Driver code

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 7.png" alt="image/universita/ex-notion/Monitor/Untitled 7">

- ReaderWriter controller

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 8.png" alt="image/universita/ex-notion/Monitor/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 9.png" alt="image/universita/ex-notion/Monitor/Untitled 9">

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 10.png" alt="image/universita/ex-notion/Monitor/Untitled 10">

- Versione senza starvation !!!

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 11.png" alt="image/universita/ex-notion/Monitor/Untitled 11">


### Producer and consumers 🟩

- Soluzione producer and consumers

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 12.png" alt="image/universita/ex-notion/Monitor/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 13.png" alt="image/universita/ex-notion/Monitor/Untitled 13">


### Buffer limitato 🟩

- Sol

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 14.png" alt="image/universita/ex-notion/Monitor/Untitled 14">


Questa soluzione con i semafori è molto più clean rispetto a quello dei semafori!

basta andare a verificare che le invarianti siano soddisfatte, riguardanti la possibilità di scrittura e la possiblità di lettura.

### Filosofi a cena

- Sol

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 15.png" alt="image/universita/ex-notion/Monitor/Untitled 15">

- Driver code, dal punto di vista del filosofo

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 16.png" alt="image/universita/ex-notion/Monitor/Untitled 16">

- Without deadlock

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 17.png" alt="image/universita/ex-notion/Monitor/Untitled 17">

- Without deadlock, all destri!

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 18.png" alt="image/universita/ex-notion/Monitor/Untitled 18">

- Soluzione con chopsticks

    <img src="/images/notes/image/universita/ex-notion/Monitor/Untitled 19.png" alt="image/universita/ex-notion/Monitor/Untitled 19">


una cosa molto bella è che che non è deadlock nemmeno se sono tutti destri! il motivo è che l'accesso è sempre in mutua esclusione, il primo che va a prenderli è buona roba.

- Ulteriori delucidazioni su questa roba

    Supponiamo per assurdo che ci sia deadlock per la versione in cui i filosofi sono tutti destri. Supponiamo che siamo al filosofo $$i$$, questo prende la sua bacchetta, e deve aspettare la bacchetta successiva, fino a creare il ciclo. fino a qui abbiamo enunciato quello che deve succedere affinché ci sia deadlock. Ma questo non può succedere perché ogni filosofo guarda da solo se può prenderlo o meno (mi sembra che questa soluzione sia un poco meno efficiente rispetto a quello con i semafori, perché solamente un filosofo può prendere…)


# Registro ripassi

| 25/11/22 | Più o meno, questi monitor essendo costrutti leggermente più ad alto livello è molto più facile comprenderli, però anche dalla mia parte dovrei sforzarmi un pò di più nel carpire parti di implementazione! |
| --- | --- |
| 27/01/23 | Apposto direi, anche post esame nessun problema, solo semmai utilizzare meglio le condizioni e coscienza sulle politiche di signalling. |
| 01/04/23 | Nessun problema, mi sembra ancora di sapere come è fatto un monitor. |
solo semmai utilizzare meglio le condizioni e coscienza sulle politiche di signalling. |
| 01/04/23 | Nessun problema, mi sembra ancora di sapere come è fatto un monitor. |