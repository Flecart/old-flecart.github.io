---
layout: page
permalink: notes/fn-ordine-superiore
tags: en
title: Fn Ordine superiore
---

Ripasso Prox: 30
Ripasso: May 18, 2023
Ultima modifica: April 22, 2023 11:23 AM
Primo Abbozzo: March 25, 2023 11:49 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# Fn Ordine superiore

Questa parte è strettamente collegata conl a parte di [Astrazione sul controllo](/notes/astrazione-sul-controllo).

Si parla di **passare le funzioni come dati**. e quindi possono essere passati come se fossero dei parametri.

> un linguaggio di programmazione è di ordine superiore qualora
ammetta funzioni sia come parametro che come risultato di altre funzioni.
>

La parte molto simile alla precedente è il fatto di **valutare** la funzione nell'ambiente iniziale, quindi bisogna utilizzare un sistema simile a quello del passaggio per nome.

### Deep and shallow binding 🟩

- Esempio di passaggio di funzione

    <img src="/images/notes/image/universita/ex-notion/Fn Ordine superiore/Untitled.png" alt="image/universita/ex-notion/Fn Ordine superiore/Untitled">


Si noti che questa distinzione fra scope statico e dinamico è indipendente da queste regole di shallow e deep binding, queste regole qui ci dicono quale ambiente scegliere per la valutazione, mentre le altre ci dicono in che modo percorrere le catene, se andare per catena dinamica o statica.

**DEEP BINDING**

In questo caso viene associato alla funzione la x presente al **momento di creazione del binding.** Nell’esempio di sopra la x in riga 11. se ho **scope dinamico**, invece quello a riga 2 se ho **scope statico**

**SHALLOW BINDING**

In questo caso l’ultimo binding possibile, quando sono proprio dentro la funzione (quindi la x attiva in quell’ambiente). Nell’esempio di sopra la x in riga 5. Quindi si valuta la funzione **al momento della chiamata**.

### Implementazione del shallow binding 🟩

Questa è l'implementazione semplice, praticamente uguale allo scope dinamico in [Nomi e Scope](/notes/nomi-e-scope). Quindi **cerco l’ultima istanza presente** fra tutte quelle presenti (se voglio scope statico, risalgo catena statica, altrimenti risalgo catena dinamica). Esattamente come si faceva per lo scope dinamico, infatti si potrebbe dire che è più naturale utilizzare scope dinamico con questo, anche se si potrebbe senza problemi utilizzare scope statico!.

Questo perché l’ultima presente era quella ancora presente nell’ambiente di chiamata!

### Implementazione del deep binding 🟩

Abbiamo detto che vogliamo valutare il deep binding seguendo la sua struttura (in questo caso **statico**, oppure nello scope di chiamata, in quel caso dinamico).

Questo è easy, si segue direttamente lo stesso sistema fatto per il nome e per la catena statica, passando una coppia **(funzione, ambiente**) chiamata **chiusura** della funzione, la funzione sarà il puntatore al codice, mentre l'ambiente è determinato così:

**STATICO**

In questo caso devo mettere nel puntatore d’ambiente in cui la nostra funzione è dichiarata, questo si può avere a tempo di compilazione, perché conosco il livello di annidamento della funzione, e anche al momento della creazione del binding, quindi utilizzo un sistema simile in [Nomi e Scope](/notes/nomi-e-scope). (quindi scorrere la catena statica con la differenza che conosco, oppure display).

**DINAMICO**

In questo caso basta mettere l'ambiente in cui metto creo il binding fra parametro formale e attuale.

### Il caso del C 🟩

In C non abbiamo cose come i lambda, non abbiamo quindi problemi di risoluzione di ambienti, perché tanto non posso dichiarare funzioni in ambienti non locali.

Semplicemente in C tutte le funzioni passate come parametro vengono risolte nell'ambiente globale. Non c'è proprio la necessità di utilizzare la catena statica! Tutto risolto a compile-time.

### Funzioni come ritorno di funzione 🟩

Quello che viene ritornato è una **chiusura**, ma come valutare una chiusura in un ambiente che è già scomparso :O  ?? Scomparso nel senso che non l’avremmo più sulla stack sto ambiente! Non possiamo fare altro che utilizzare un ambinete illimitato di vita. E dare la responsabilità al garbace collector l'onere di liberare questo ambiente.



# References