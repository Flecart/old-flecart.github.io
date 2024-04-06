---
layout: page
permalink: notes/semafori
tags: italian
title: Semafori
---

Ripasso Prox: 120
Ripasso: September 28, 2023
Ultima modifica: May 19, 2023 10:28 AM
Primo Abbozzo: October 15, 2022 10:22 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Semafori

## Introduzione

### Concetto principale 🟩-

È sempre stato introdotto da Dijkstra, 1965 (Cooperating Sequential Processes) utilizzato come strumento di cooperazione semplice

Questo è un sistema fortemente ispirato dai semafori che regolano gli incroci stradali.

> due o più processi possono cooperare attraverso semplici
segnali, in modo tale che un processo possa essere bloccato
in specifici punti del suo programma finché non riceve un
segnale da un altro processo
>

### Primitive dei semafori 🟩-

Il semaforo solitamente è una **variabile intera non negativa**.

**V** anche chiamao *sem_wait*.

Da *verhogen* utilizzata per **rilasciare una risorsa**. Di solito è implementata *aumentando* il valore di un semaforo.

**P**, anche chiamato *sem_post*.

Da *proberen* per attendere evento o rilascio di una risorsa. Di solito è implementata *decrementando*  il valore del semaforo **solo se è positivo non nullo**.

**Invarianti per i semafori  (!!!)**

- Slide invarianti

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled.png" alt="image/universita/ex-notion/Semafori/Untitled">


### Implementazione classica della CS 🟩

- Programma concorrente con semafori per CS

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 1.png" alt="image/universita/ex-notion/Semafori/Untitled 1">

- Implementazione classica di P e V (ricordare da metterle nella CS)

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 2.png" alt="image/universita/ex-notion/Semafori/Untitled 2">


Si può notare che tutte le 4 proprietà espresse per la concorrenza sembrano essere soddisfatte.

Oltre a questo bisogna avere una **struttura di dati (Queue)** che tenga conto dei processi che stanno aspettando la risorsa dietro questo semaforo, in modo da poter ricominciare.

Si potrebbe in questo caso anche disabilitare l'interrupt! Perché tanto ora non è dentro lo scope del programmatore, è dentro lo scope del semaforo! Per i multicore si possono utilizzare le soluzioni trattate in parti precedenti.

### Vantaggi dei semafori 🟩

- Fairness data dalla politica FIFO utilizzata per la struttura di dati della coda
    - Slide

        <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 3.png" alt="image/universita/ex-notion/Semafori/Untitled 3">

- Busy waiting molto minore

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 4.png" alt="image/universita/ex-notion/Semafori/Untitled 4">

- Interleaving controllato? Boh non ho capito il concetto di questa frase

## Semafori binari

### Descrizione generale 🟩

Sono semafori che possono solamente avere come valore 0 e 1.

TODO: dire anche cosa succede per l’attesa dei due…

### Implementazione 🟩-

- Implementazione semaforo binario

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 5.png" alt="image/universita/ex-notion/Semafori/Untitled 5">


I semafori binari ci **garantiscono mutua esclusione**

### Semafori binari equiv. semafori normali 🟩

- Implementazione dei semafori con semafori binari 🟩

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 6.png" alt="image/universita/ex-notion/Semafori/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 7.png" alt="image/universita/ex-notion/Semafori/Untitled 7">

- Implementazione di semafori binari con semafori 🟩

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 8.png" alt="image/universita/ex-notion/Semafori/Untitled 8">


## Problemi classici

### Producer consumer 🟩

Abbiamo due agenti, un programma che produce una risorsa e un agente che la consuma. Questa comunicazione di disponibilità di un valore avviene attraverso una **singola variabile condivisa.**

**Proprietà importanti**

- Producer non può scrivere la zona di memoria comune prima che il consumer l'abbia consumato
- Consumer non deve leggere due volte la stessa cosa.
- No deadlock né starvation

In questo caso sono come delle sezioni critiche alternate  **passing the baton** perché è come se passasse il testimone, e vanno avanti in modo alternato.

- Soluzione

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 9.png" alt="image/universita/ex-notion/Semafori/Untitled 9">


### Limited Buffer  🟩

La descrizione del problema è molto simile, la differenza è che si utilizza un **buffer condiviso** per lo scambio di informazioni, non una singola variabile, il resto delle proprietà è molto simile.

- Soluzione

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 10.png" alt="image/universita/ex-notion/Semafori/Untitled 10">


**Osservazioni personali**

- Non c'è deadlock perché si bloccherebbero assieme solo se sia empty sia full sono 0, ma questo sarebbe un problema di inizializzazione.

### Dining philophers 🟩-

Ho 5 filosofi intorno a una tavola che devono acquisire le due bacchette (risorse condivise) per mangiare, altrimenti pensano.

- Invarianti

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 11.png" alt="image/universita/ex-notion/Semafori/Untitled 11">


**Resource hierarchy solution**

- Soluzione

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 12.png" alt="image/universita/ex-notion/Semafori/Untitled 12">


In questa soluzione si crea una gerarchia di priorità per chi deve acquisire la fork, con una rottura di simmetria per l’ultima.

Il problema è che non è libero da starvation.

Pagina [wiki]([https://en.wikipedia.org/wiki/Dining_philosophers_problem](https://en.wikipedia.org/wiki/Dining_philosophers_problem)#Resource_hierarchy_solution)

- Altre soluzioni

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 13.png" alt="image/universita/ex-notion/Semafori/Untitled 13">


**Osservazioni personali**

Credo ci sia starvation perché non c'è niente che mi garantisca che non ci sia.

- Roba da buttare, riguardo dining

    ```cpp
    Pseudocodice per il problema dei dining filosophers che utilizza il token, e la
    struttura ad anello

    inizializza 5 semafori, solo uno sarà a 1 sarà quello attivo direi.
    5 booleani che indicano la disponibilità.
    inizializzo 5 numeri che identificano il numero delle volte che si ha mangiato
    Alla fine di ogni ciclo di mangiata viene incrementato il numero, e questo numero viene
    incrementato solamente da un unico thread, quello di un certo filosofo, quindi
    non devo metterci il mutex, o forse sì??.
    Quindi fra gli attivi voglio solamente chi ha il token e chi può mangiare.

    bool done = false;

    while (!done):
    	waiting_for_token = true, // anche done può essere utilizzato come waiting for token.
    	[enter CS]
    	if (disponibile left):
    		prendi left
    		if (disponibile right):
    			prendi right
    			waiting_for_token = false; // done = true qui, invece che sotto.
    			make calls to take left and right.
    		else:
    			release left
    	[exit CS]

    	if (has both forks):
    		eat()
    		releaseLeft()
    		signal left is available
    		releaseRight()
    		signal right is available
    		done = true;
    	else:
    		go to sleep (try again lather, if not done))
    	passtoken to next waiting for token.
    - somebody is waiting for token if
    1. Is not eating
    2. Has not finished
    Quindi ci metto il check booleano sopra.



    ```


### Readers and writers 🟩-

Questo è uno dei problemi più importanti, adremo in seguito a sviluppare il concetto di awaiting.

Ci sono due tipi di processi che devono leggere un database. I lettori accedono al database per leggerlo, gli scrittori per scriverlo, fatto è che i lettori possono leggere quanto vogliono, quando però uno ci vuole scrivere, nessun altro ci può andare a leggere.

- Un solo scrittore, che blocca tutti
- Se nessuno scrive tutti possono leggere.
- Invarianti da rispettare

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 14.png" alt="image/universita/ex-notion/Semafori/Untitled 14">

- Soluzione Readers and Writers con semafori

    **Starvation degli scrittori**

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 15.png" alt="image/universita/ex-notion/Semafori/Untitled 15">

    Questa soluzione ha il drawback del fatto che **starvation** per i scrittori.


Questa è una soluzione che funziona ma vorremmo trovare un metodo per descrivere tutti i problemi con await, in modo molto clean.

### Priorità ai scrittori con await framework 🟨+

Vogliamo in questa parte trattare di una soluzione che non metta in starvation gli scrittori, ma mette in starvation i lettori in questo caso.

- Slide soluzione

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 16.png" alt="image/universita/ex-notion/Semafori/Untitled 16">


La soluzione è quasi la stessa, ma si cambia la condizione di entrata per i lettori che sarà quando non c'è nessun scrittore che sta scrivendo e **nemmeno** nessuno che sta aspettando di scrivere.

Scegliere quale soluzione utilizzare dipende molto dall’ambiente in cui stiamo, dipende se vogliamo più gente che scriva o più gente che legga (di solito per un database c'è molta gente ch elegge e poca che scrive).

### Problema del barbiere addormentato

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 17.png" alt="image/universita/ex-notion/Semafori/Untitled 17">


## Framework per semafori

Andiamo in questa parte a creare un framework generale per la discussione di problemi con await con i semafori.

### Framework semafori Andrews (4) 🟨-

<img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 18.png" alt="image/universita/ex-notion/Semafori/Untitled 18">

### Notazione con Await (2) 🟨+

- Notazione (andrews Await)

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 19.png" alt="image/universita/ex-notion/Semafori/Untitled 19">


Quindi la sintassi diventa di due parametri in particoalre

1. Statement atomico
2. Statemento atomico con await su una condizione booleana.

Molto interessante notare che è questo ciò che stato implementato con Javascript! Ed è una cosa molto clean questo paradigma :D.

- Soluzione readers and writers con await (generale)

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 20.png" alt="image/universita/ex-notion/Semafori/Untitled 20">


Si noti che questa soluzione è equivalente alla soluzione dei semafori, ma è scritta in modo molto più clean.

### Implementazione await con semafori 🟩

- Note sulle variabili di implementazione

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 21.png" alt="image/universita/ex-notion/Semafori/Untitled 21">


Le note principali sono i semafori e i waiting.

- Implementazione in slide

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 22.png" alt="image/universita/ex-notion/Semafori/Untitled 22">

    i quadrati sono degli if non deterministici, nel senso che posso riordinarli come mi pare e sarebbe comunque apposto


**Su signal**, ci dà un idea di quanti processi possono andare avanti dato un cambiamento di stato.

La modifica sul waiting[i]- - non è un write non protetto??? No perché sempre passaggi di testimoni! Siamo sempre in una sezione critica, ma divisa fra più processi grazie a questo meccanismo passing the baton.

Infatti è per questo che possono fare waiting[i]- - senza apparentemente essere in mutua esclusione!.

Nota che sembra interessante è che questo baton viene continuamente passato da processo a un altro da signal ad un altro finché non posso più fare signal.

**Nota sui passaggi di testimoni**

La mutex è sempre rilasciata attraverso la tecnica del passing the baton, in qui il mutex è rilasciato da processi diversi, si può espandere su molti processi diversi la mutua esclusione… Cavolo però credo sia molto difficile sbagliarci qualcosa no? boh.

### Readers and writers con await (!) 🟨-

- Slide soluzione

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 23.png" alt="image/universita/ex-notion/Semafori/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 24.png" alt="image/universita/ex-notion/Semafori/Untitled 24">

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 25.png" alt="image/universita/ex-notion/Semafori/Untitled 25">

- Soluzione in singola slide (e con signal ottimizzato)

    <img src="/images/notes/image/universita/ex-notion/Semafori/Untitled 26.png" alt="image/universita/ex-notion/Semafori/Untitled 26">


## Considerazioni finali (3) 🟨

I semafori pongono **forti problemi di leggibilità** dato che sono costrutti a basso livello sparsi in mezzo al codice.

È possibile inoltre compiere **errori stupidi** in modo molto facile, come scambiare P o V, omettere Po V.

E pone un **sacco di responsabilità sul prorammatore** che deve gestire lui in modo corretto le risorse e definire gli accessi.



# References