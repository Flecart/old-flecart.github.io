---
layout: page
permalink: notes/garbage-collection
tags: en
title: Garbage Collection
---

Ripasso Prox: 10
Ripasso: May 20, 2023
Ultima modifica: May 11, 2023 8:17 PM
Primo Abbozzo: April 17, 2023 11:10 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Garbage Collection

## On dangling pointers

### Tombstones 🟩

- Slides tombstones

    <img src="/images/notes/image/universita/ex-notion/Garbage Collection/Untitled.png" alt="image/universita/ex-notion/Garbage Collection/Untitled">


Quando alloco, alloco anche una tombstone, e tutti i riferimenti passano per quella. (quindi ho due dereference per l’accesso) quando vado a deallocare segno la tombstone come RIP, NULL.

Dopo molto tempo ho il problema del cimitero che diventa molto grande. Anche se non punta più a niente, il cimitero.

### Keys and locks 🟩

Un pò di overhead in più dal punto di vista della memoria, che è doppio

## On GC

### Reference counting 🟩

Quando alloco, mi tengo anche un **contatore di riferimenti**, ossia puntatori che fanno riferimento a questo blocco. Quando arriva a zero dealloco. Questo è una variabile privata del GC, non è accessibile da nessuna parte dall’esterno.

Come fare per riferimenti ricorsivi? Se avessimo due elementi che si puntano fra di loro ma non sono accessibili tramite stack?

Con questa tecnica **non è possibile risolverlo** bisogna utilizzare il metodo successivo.

### Mark and sweep 🟩

- Slide tecnica mark and sweep

    <img src="/images/notes/image/universita/ex-notion/Garbage Collection/Untitled 1.png" alt="image/universita/ex-notion/Garbage Collection/Untitled 1">


Definito in due parti:

1. Fase di **detection**, in cui parto marcando tutto, poi se riesco a raggiungerlo tolgo il mark.
2. **remotion** vado a rimuovere tutti quelli marcati (alla fine è la stessa cosa marcare non marcare, basta invertire), in questo modo riconosco tutti i pezzi i memoria non raggiungibili e so cosa andare a togliere.

Svantaggio principale:

Non so quando andare a fare mark and sweep:

1. Ogni tot tempo
2. Quando finisco la memoria (ogni tot memoria).
3. Quando fa GC devo **fermare il programma (stop the world)** perché non ha senso che inserisco cose quando vado a marcare (pensala come modify list quando ci scorri).
4. Per sistemi realtype non funziona proprio, perché non posso permettermi di bloccare la computazione.

### Implementazione: invesione dei puntatori 🟨+

Come facciamo ad implementare questa tecnica quando magari è invocata solamente quando ho finito lo spazio? Non possiamo utilizzare la stack, perché la memoria è finita.

Si utilizza la tecnica di **inversione dei puntatori**:

- Slide inversione dei puntatori

    <img src="/images/notes/image/universita/ex-notion/Garbage Collection/Untitled 2.png" alt="image/universita/ex-notion/Garbage Collection/Untitled 2">


### Stop and copy

- Slide tecnica stop and copy

    <img src="/images/notes/image/universita/ex-notion/Garbage Collection/Untitled 3.png" alt="image/universita/ex-notion/Garbage Collection/Untitled 3">


La heap è divisa in due regioni differenti, quando una è piena (credo) copio tutto nell'altra zona. Questo è buono quando ho pochi blocchi ancora buoni, perché ci metterei molto meno a spostare e emttere nell’altra.y

## Borrow checking (non fatto)

Questa è la cosa nuova introdotta da Rust.

### Ownership

### Lifetimes