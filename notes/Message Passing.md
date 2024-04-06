---
layout: page
permalink: notes/message-passing
tags: italian
title: Message Passing
---

Ripasso Prox: 70
Ripasso: July 22, 2023
Ultima modifica: May 19, 2023 9:25 AM
Primo Abbozzo: November 23, 2022 1:32 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# Message passing

ora abbiamo alcune primitive per passarci i messaggi, vogliamo creare metodo in modo che i processi si possano sincronizzare mandando messaggi.

la memoria **è sempre privata**.

## Primitive

<img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled.png" alt="image/universita/ex-notion/Message Passing/Untitled">

### Send e receive 🟩

**Send**

- Spedizione del messaggio
- input deve avere un **identificato al processo su cui spedire.**

Se si vuole espandere si possono avere **multicast e broadcasting** ma non li studieremo in questo corso.

**Receive**

Ricevi messaggi

## Tassonomia dei message passing (!)🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled 1.png" alt="image/universita/ex-notion/Message Passing/Untitled 1">


**Sincrono**

In questo caso **entrambi send e receive** sono bloccanti, quindi non possono andare avanti finché non è mandato e finché non è ricevuto!

**Asincrono**

Simile al precedente, solo che il **send non aspetta** che il ricevente prenda il messaggio!

**NOTA:** non si aspetta che il receiver riceva il messaggio!

**Completamente asincrono**

nessuno di due aspetta, il receive se nessuno ha inviato non riceve niente!

### Thoth

proponeva 3, **reply receive send**, principalmente solo la reply è bloccante.

più o meno tutti gli autori avevano una sintassi diversa per il message passing

## Equivalenza fra sincrono asincrono

Si può vedere che questi due metodi si possono rivelare equivalenti

### Sincrono dato quello asincrono 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled 2.png" alt="image/universita/ex-notion/Message Passing/Untitled 2">


Per bloccare il asendodevo fare un areceive per un ack, così lo blocco

NOTA: ed è esattamente questo, un ack aggiuntivo che hai fatto all’esame che ti ha fatto perdere tipo 2 punti, stai attento!

### Asincrono dato quello sincrono 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled 3.png" alt="image/universita/ex-notion/Message Passing/Untitled 3">


Si vede che il sincrono non è espressivo tanto l’asincrono perché abbiamo bisogno di far uso di un altro processo server.

## Problemi classici 🟨

### Filosofi a cena

- Slide

    <img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled 4.png" alt="image/universita/ex-notion/Message Passing/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled 5.png" alt="image/universita/ex-notion/Message Passing/Untitled 5">


Basta ricordarsi di fare anche il filosofo mancino e poi siamo apposto! Sarebbe poi la stessa soluzione proposta in [Semafori](/notes/semafori)

### Producer consumer

- Slide

    <img src="/images/notes/image/universita/ex-notion/Message Passing/Untitled 6.png" alt="image/universita/ex-notion/Message Passing/Untitled 6">




# References