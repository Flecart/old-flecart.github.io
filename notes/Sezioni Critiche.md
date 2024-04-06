---
layout: page
permalink: notes/sezioni-critiche
tags: italian
title: Sezioni Critiche
---

Ripasso Prox: 80
Ripasso: May 21, 2023
Ultima modifica: March 12, 2023 10:00 AM
Primo Abbozzo: October 8, 2022 11:30 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# 2 Sezioni Critiche

## Introduzione

> La parte di un programma che utilizza una o più risorse
condivise viene detta sezione critica (critical section, o CS)
>

Andiamo in questa altra parte a valutare certe soluzioni:

### Programma d’esempio 🟩

<img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled">

Vorremmo garantire che **a = b invariante.** (espressione logica verificata nell'esecuzione di questo programma). quindi una coerenza di uno prima dell'altro vogliamo.

Non funziona lasciare la gestione dell'invarianza al sistema operativo o al compilatore perché manca questa informazione (quindi non abbiamo potere per la gestione dell’ordine in questo caso.

### Requisiti per le CS (5) 🟩——

Vogliamo ora cercare di listare le proprietà delle critical sections in modo teorico, per implementare un programma che riesca ad implementare la critical section.

- Slide requisiti

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 1.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 1">


**Safety**:

1. Mutua esclusione, solo uno all'interno della CS
2. No deadlocks

**Liveness**:

1. Un processo fuori dalla CS non dovrebbe ritardare l’entrata di un altro programma
2. Un processo eventualmente deve entrarci

Altro:

1. Nessun processo può terminare in una critical section (secondo me perché si porterebbe la risorsa critica con sé, nel senso che nessun altro programam può utilizzarlo, suppongo. Questo si può associare al principio 4 di Liveness.

## Algoritmo di Dekker

Listo qua in breve le idee principali che daranno vita all’algoritmo

1. Turni per disambiguare chi può entrare e chi vuole entrare
2. Booleani per esprimere il concetto di voler entrare.
3. Dare la precedenza all’altro.

### Soluzioni provate e non funzionanti 🟩- (prolly non richiede)

- Soluzione 1 (busy waiting esterno con i turni)

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 2.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 2">

    Non è buona perché **viola il principio 3** del non rallentamento. Può succedere che nessuno è dentro la sezione critica, ma uno non ci può entrare finché l’altro non ci entra ed esce (ma può essere che l’altro sia molto più lento!)

- Soluzione 2 (busy waiting esterno con 2 booleani)

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 3.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 3">

    Il problema è che possono entrambi entrare nella soluzione critica, quindi **non è mutex** e quindi non è una soluzione

- Soluzione 3 (2 booleani, assegnamento prima)

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 4.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 4">

    Può accadere un deadlock, **viola principio 4**

- Soluzione 4 (livelook, assegnamenti nel busy waiting)

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 5.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 5">

    Può accadere **starvation** in questo problema nel requisito 4, ossia uno non entra mai.


### l’algoritmo 🟨

Questo è un algoritmo che funziona per implementare le sezioni critiche.

Andremo in questa parte a considerare moltissime soluzioni che non soddisfano i requisiti esplicitati precedentemente, fino a raggiungere l’algoritmo di dekker. (Questo è proprio il processo seguito da Dijkstra nel raggiungimento della soluzione!)

- Algoritmo di Dekker

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 6.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 6">


### Dimostrazione correttezza di Dekker 🟩-

**Mutua esclusione**

- Mutua esclusione

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 7.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 7">


In pratica si riduce che in un certo momento deve esserci un momenti in cui uno è nella critical section, e il valore di need associato deve essere falso. Ciò è impossibile, devo essere eseguite entrambe le istruzioni di uscita!

**Assenza di deadlock**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 8.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 8">


**Assenza di ritardi**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 9.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 9">


**Assenza di starvation**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 10.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 10">


## Algoritmo di Peterson

### Descrizione dell’algoritmo 🟩—

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 11.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 11">


### Algortitmo generalizzato 🟥

- Slide peterson generalizzato (non so perché funzioni, comunque il prof. lo ha saltato).

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 12.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 12">


TODO: se vuoi fare bene questo pezzo sarebbe anche Peterson

È una cosa molto più compatta rispetto Dekker, e l'idea principale è che il turno è stabilito prima di entrare nel while

### Dimostrazione correttezza di Peterson 🟩

**Mutua esclusione**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 13.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 13">


**Assenza deadlock**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 14.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 14">


È quasi ovvio perché **turn non può avere due variabili diverse**

**Assenza di ritardi**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 15.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 15">


**Assenza di starvation**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 16.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 16">


## Soluzioni hardware

### Perché è meglio di software (3) 🟨-

Si preferirebbero delle soluzioni hardware perché tutte le soluzioni software fanno utilizzo di busy waiting che è molto dispendioso.

- Dispendioso dal punto di vista della CPU per il busy waiting
- Difficile da implementare senza bug (difficile da testare)
- Gestione delle responsabilità a livello software (cosa che non si vuole)

### Disabilitazione interrupt (2) 🟩

Così non posso passare ad un altro processo all'inizio di una sezione critica. (ma c'è il problema dei multicore perché dovrei disabilitarlo per tutti!).

Ci sono altri motivi per cui questa è una brutta soluzione:

- Lasciare la gestione degli interrupt ai programmi perché agisce sull'intera macchina, ma non dovrebbe avere questo diritto.
- Multicore dovrebbero essere sincronizzati su questo aspetto (quindi **difficoltà di parallelizzazione**). Quindi non posso essere interrotto
- Non funziona su multicore perché anche se li disabilito su entrambi, può esser che due processi lavorano sempre con la stessa sezione critica

### Test & set (spin lock) 🟩-

L’hardware ha delle istruzioni in più che aiutano a creare l’implementazione per le sezioni critiche.

<img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 17.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 17">

- Programma con test e set

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 18.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 18">


- Dimostrazione di correttezza (senza starvation)

    <img src="/images/notes/image/universita/ex-notion/Sezioni Critiche/Untitled 19.png" alt="image/universita/ex-notion/Sezioni Critiche/Untitled 19">


Oltre a questo si può implementare con altre istruzioni atomiche come  fetch and set, compare and swap.

### CS con swap e divisione 🟩-

- Protocollo entrata con swap

    ```cpp
    lock = 0;
    do {
    	v = 1;
    	swap(v, lock);
    } while(v);
    ```

    Chiaramente posso entrare quando lock è 0, altrimenti lock è sempre 1.

- Protocollo entrata con divisione

    ```cpp
    lock = 2
    do
    	v = < lock /= 2 >
    while (v != 1)
    ```


Con questo abbiamo raggiunto una notevole semplificazione nella programmazione (ed anche della generalizzazione di questa soluzione), ma non sono risolti i problemi di starvation né busy waiting, ancora fortemente inefficiente.



# References