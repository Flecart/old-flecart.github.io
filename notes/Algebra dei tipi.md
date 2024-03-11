---
layout: page
permalink: notes/algebra-dei-tipi
tags: italian
title: Algebra dei tipi
---

Ripasso Prox: 19
Ripasso: May 22, 2023
Ultima modifica: May 6, 2023 5:58 PM
Primo Abbozzo: April 3, 2023 1:22 PM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Elementi di ripasso

# Algebra dei tipi

- Slide introduzione algebra dei tipi

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled">


### Equivalenza dei tipi (2) 🟩

Quando possiamo dire che due tipi siano uguali? Solitamente vengono utilizzati due metodi:

**EQUIVALENZA NOMINALE**

Quando un nuono tipo introduce un nuovo nome diverso fra tutti i presenti. Credo così vada golang.

Quindi in questo caso si può dire che un tipo **è equivalente solamente a sé stesso**.

Vogliamo fare in questo modo perché se definiamo un nuovo tipo solitamente dovrebbe avere funzioni diverse, quindi è giusto che sia diverso da uqello iniziale.

- Slide equivalenza nominale

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 1.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 1">


**EQUIVALENZA DI STRUTTURA**

Ossia quando **tutte le operazioni, strutture e sottoelementi sono uguali** possiamo andare a definire una equivalenza di struttura. (vado anche di più a guardare come vengo utilizzati, a tempo di compilazione).

In un modo forse più intuitivo possiamo dire che abbiamo una equivalenza di struttura quando tutti i campi all’interno della struttura sono gli stessi.

- Slide equivalenza di struttura

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 2.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 2">


Possiamo anche utilizzare una forma più lasca (molto ispirata dal duck typing) chaichiamo questa la **compatibilità di tipo**).

### Duck typing e confronto equivalenza 🟩

Questo è molto simile a quanto si fa in **duck typing** in slide

- Slide duck typing

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 3.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 3">


> If it walks like a duck, and it quacks like a duck, then it must be a duck. ~**a duck**
>

- Slide confronto fra i tipi di equivalenza

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 4.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 4">


In pratica possiamo dire che l’equivalenza nominale porta vantaggi rispetto a quello strutturale.

- Notazione molto più chiara per tipi ricorsivi.
- Di solito si utilizza una cosa di messo, tipo una parte nominale per dichiarare, e poi fare un controllo strutturale in secondo momento.
- Controllo del sottotipaggio è molto più semplice dal punto di vista nominale.

### Compatibilità dei tipi (3) 🟨++

> Diciamo che il tipo T è compatibile con il tipo s, se un valore di tipo T è ammesso in un qualsiasi contesto in cui sarebbe richiesto un valore di tipo s.
>

Questo è abbastanza naturale, la compatibilità essendo anche simmetrica, sussume anche un ordine parziale (riflessivo e transitivo) su questo possiamo andare ad avere tipi compatibili con l’iniziale (quindi convertibili, o se parli con set theory li puoi vedere uguali).

- Slide compatibilità dei tipi

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 5.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 5">


Quando ho queste proprietà:

1. Abitanti di un tipo sono anche abitanti di tipo2 (ad esempio in rust andiamo a definire le traits sulle structs).
2. Ci sono le stesse operazioni
3. Conversioni canoniche, o arbitrarie.

Allora potrei prendere il primo tipo e considerarlo come del secondo, in questo senso posso dire che sono dei tipi compatibili fra di loro.

### Conversione di tipi🟩-

- Slide conversione dei tipi

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 6.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 6">


Può essere **silente o espicito**, se il silente non è controlalto potrebbe dare dei bugs.

Importante sottolineare la differenza fra conversione **sintattica** che in pratica è solamente una interpretazione diversa della zona di memoria (stessa grandezza credo) oppure proprio da una funzione che applichi questa conversione.

Quando faccio una conversioen diretta sto facendo una **coercizione**, ossia una conversione diretta seguendo un certo modo, anche detto marshalling).

### Type inference

*Type inference*

- Slide type inference

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 7.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 7">


Quando con il parsing riesco ad **accumulare informazioni** irguardo un certo tipo o operazione, quindi riesco ad assegnare un tipo senza che sia stato specificato in modo esplicito.

Alla fine vado a risolvere una specie di equazioni con i tipi. Se non è possibile avere abbastanza informazioni per escludere tutto si ritorna un errore. (semmai con una proposta di segnatura, o signature)

- Slide algoritmo di unificazione (non si fa credo)

    <img src="/images/notes/image/universita/ex-notion/Algebra dei tipi/Untitled 8.png" alt="image/universita/ex-notion/Algebra dei tipi/Untitled 8">