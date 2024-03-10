---
layout: page
permalink: notes/livello-os
tags: italian
title: Livello OS
---

Ripasso Prox: 12
Ripasso: December 23, 2021
Ultima modifica: March 23, 2023 2:12 PM
Primo Abbozzo: November 15, 2021 2:16 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Come funzionano esattamente gli algoritmi di paginazione?
- Quali sono i problemi principali della paginazione?
- Come funziona la MMU (ossia come faccio a trovare un indirizzo reale per ogni indirizzo virtuale?)

# 9 Livello sistema operativo

## 9.1 Caratteristiche

Il sistema operativo non ha sempre avuto una interfaccia grafica.

### 9.1.1 In generale

Principalmente è un **gestore delle risorse** come il disco, la CPU, l'output e l'input.

È qualcosa che si infrappone come interfaccia fra le applicazioni e quello che è presente sotto.

### 9.1.2 Ambiti principali

<img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled.png" alt="image/universita/ex-notion/Livello OS/Untitled">

## 9.2 Paginazione

Al programma non interessa se effettivamente è presente in memoria fisica questa quantità di memoria, si di solito basta sempre.

Ci sono 3 casi:

1. se la necessità di memoria è anche superiore alla memoria virtuale esistente allora c'è l'errore out-of-memory
2. Se è maggiore della fisica ma minore, dovrà essere gestita dalla paginazione e simili.
3. Se è minore della memoria fisica allora tutto ok!

### Implementazione

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 1.png" alt="image/universita/ex-notion/Livello OS/Untitled 1">


### 9.2.1 Indirizzi virtuali e paginazione

Vogliamo utilizzare tutti i bit per l'indirizzamento, anche se questi superano effettivamente la memoria effettiva, questa astrazione permette di facilitare al programma la comprensione di tutto. (ma il programma è molto più lento perché ogni volta doveva ricaricare la pagina di memoria).

### 9.2.2 Hit and fault

Si ha un page hit se la pagina è caricata, altrimenti è page fault e si deve ricaricare tutta la memoria per il programma.

### 9.2.3 Memory Management Unit

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 2.png" alt="image/universita/ex-notion/Livello OS/Untitled 2">


Questo è il chip che si differenzia dalla cache. Una pagina virtuale può essere messo in qualunque pagina reale.

**Tabella** gestita dal sistema operativo che tiene in memoria le pagine che sono usate e quelle no.

quindi se è 1 (in memoria) si chiama working set.

### 9.2.4 Algoritmi di paginazione (2)

Ci dicono quale pagina togliere dalla memoria principale per sapere quale rimpiazzare con la nuova pagina.

I principi che sono presenti per questi algoritmi di paginazione, sono molto simili ai principi della località spaziale e temporale presenti per la Cache

Quelle presentate sono **LRU e FIFO**, si può dire che il primo funziona meglio mentre il secondo è più veloce, quindi bisogna vedere i tradeoff.

Questi algoritmi (in particolare La Least Recently Used è utilizzata anche in [Memoria](/notes/memoria) per la cache).

### 9.2.5 Dirty bit

Si aggiunge un bit che ci dice se una pagina è stata sporcata o meno (così possiamo decidere se scrivere in memoria o no).

### 9.2.6 Frammentazione interna

Non vorremmo sprecare un pezzo del blocco, sprecheremmo mezzo blocco.

Per ovviare a questo (il fatto di non utilizzare l'intero blocco si dice frammentazione interna)

## 9.3 Segmentazione

### 9.3.1 Problemi della paginazione

Questa opzione non è più presente nella realtà, dato che si utilizza sempre la paginazione.

Problemi della paginazione

- Evitare la frammentazione interna
- Le pagine sono scollegati dai programmi (potrebbe essere che un array sia scollegato in più pagine, ho mano manovra).

Si divide la memoria in segmenti che vengono dati a parti del processo (esempio i/o ) e altro a seconda dello scopo

### 9.3.2 In memoria: frammentazione esterna

Dato che i segmenti non sono della stessa grandezza, c'è un pò di complicazione mentre si trattano queste cose. ecco che si ha il fenomeno di frammentazione esterna in questo caso.

L'operazione di compattare la memoria è moolto costosa...

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 3.png" alt="image/universita/ex-notion/Livello OS/Untitled 3">


### 9.3.3 Scelta del "buco" (2)

Ci sono due modi principali per scegliere la zone in cui mettere il programma

1. Best Fit: (ci metto più tempo perché devo cercare il buco migliore, ma poi trovo quello più economico in cui c'è meno spazio inusato)
2. First fit: è il più veloce perché metto subito sul primo blocco, però grande spazio potrebbe essere inutilizzato

### 9.3.4 Combinazione segmentazione e paginazione

Si possono mischiare: una parte per la segmentazione e poi la pagina per il segmento e da questo si raggiunge un blocco.

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 4.png" alt="image/universita/ex-notion/Livello OS/Untitled 4">


## 9.4 Gestione del linking !

### 9.4.1 il file oggetto

Ogni file viene compilato assumendo che parta dall'indirizzo zero, poi questi vengono riorganizzati con successo da linker

<img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 5.png" alt="image/universita/ex-notion/Livello OS/Untitled 5">

- Esempio

### 9.4.2 Esempio

<img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 6.png" alt="image/universita/ex-notion/Livello OS/Untitled 6">

### 9.4.3 La rilocazione

La rilocazione per chiamate di funzioni esterne (di sistema è semplice), poi bisogna rilocare anche pointers e branches., si utilizza un **dizionario di rilocazione**.

### 9.4.4 Indirizzamento dinamico

Viene compilato normalmente, e viene linkato nel momento di esecuzione grazie al sistema operativo

- Esempio

    <img src="/images/notes/Livello OS/Untitled 7.png" alt="Livello OS/Untitled 7">
Indirizzamento dinamico

Viene compilato normalmente, e viene linkato nel momento di esecuzione grazie al sistema operativo

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Livello OS/Untitled 7.png" alt="image/universita/ex-notion/Livello OS/Untitled 7">