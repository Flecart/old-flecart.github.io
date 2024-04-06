---
layout: page
permalink: notes/alberi-bst-e-avl
tags: en
title: Alberi BST e AVL
---

Ripasso Prox: 35
Ripasso: June 20, 2022
Ultima modifica: May 19, 2022 12:52 PM
Primo Abbozzo: March 18, 2022 9:59 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Analisi sull’altezza dell’albero di fibonacci
- I tipi di sbilanciamento, e fare degli esempi di inserimento e deletion di questi alberi che sono la cosa che ti potrebbe chiedere
- Inserire esercizi per il MINIMAX che potrebbe chiedere.

# 4 Alberi BST e AVL

[06 - Alberi binari di ricerca.pdf](Alberi%20BST%20e%20AVL%209baa15ae9efa4a879dbd730afb540b55/06_-_Alberi_binari_di_ricerca.pdf)

[07 - Alberi AVL.pdf](Alberi%20BST%20e%20AVL%209baa15ae9efa4a879dbd730afb540b55/07_-_Alberi_AVL.pdf)

## 4.1 Alberi binari di ricerca (BST)

Queste sono delle varianti rispetto all'albero, descritto in modo molto sommario sopra (binario perché ogni nodo ha al massimo due figli, mentre l'albero può averne quanti se ne vuole).

### 4.1.1 Introduzione

La caratteristica principale dell'albero di ricerca è una condizione sulle chiavi (che hanno i figli).

Infatti questo albero binario di ricerca si può vedere come una implementazione della struttura astratta del dizionario. (che ricordiamo, è un struttura in cui a ogni nodo sono presenti due valori, una chiave (tute differenti) e un dato, e sono definite tre operazioni principali, possiamo vederla come interfaccia).

1. Al massimo due figli per nodo. (albero binario)
2. Il dizionario, quindi che ogni nodo abbia chiave.
3. I figli di sinistra hanno chiavi minori del genitore, a destra maggiore.

### 4.1.2 Prototipo

Possiamo definire alcune operazioni principali per l'albero di ricerca:

1. Le tre standard che sono presenti per il dizionario. (search, insert e delete)
2. Max e Min.
3. Predecessor e successor

Saltiamo le note di implementazione di questi algoritmi :D  perché sono già triti e ritriti.

Una nota su predecessor:

Per l'operazione di delete abbiamo solamente considerato il caso di predecessor quando il nodo da considerare possedeva il figlio giusto.

Ma è possibile che non lo abbia, allora è molto simile, ma opposto (invece di scendere continuamente a destra, salgo continuamente a sinistra, con continuamente nel senso finché c'è ancora il nodo).

## 4.2 Alberi AVL

Questi sono alberi AVL (il cui nome deriva dal nome dei creatori, come RSA), alberi bilanciati secondo l'altezza dei sottonodi. La cosa buona è che avendo i bilanciamenti abbiamo un altezza logaritmica. in particolare possiamo dire che questi siano **autobilancianti**.

Introduciamo ora alcuni concetti importanti per comprendere il bilanciamento

### 4.2.1 il concetto di bilanciamento

**Il fattore di bilanciamento**

Cerchiamo di considerare un fattore di bilanciamento che si ottiene con

 con h una funzione che mi ritorna l'altezza. (da notare che è l'altezza, non la funzione).

E l'altezza parte da 0


$$
\beta = fattore\_bilanciamento = h(sinistra) - h(destra)
$$


**Bilanciato in altezza**

Consideriamo un albero bilanciato in altezza se  $$|\beta| \leq 1$$

### 4.2.2 Altezza di un albero di fibonacci

L'albero di fibonacci è molto interessante da studiare dal punto di vista dell'altezza, infatti possiede il massimo sbilanciamento possibile

- Intuizione dell'albero (dalla costruzione puoi dimostrare la sua altezza in modo intuitiva)

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled">

- Numero di nodi nell'albero di fibonacci

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 1.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 1">

- Conclusione sull'altezza

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 2.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 2">


### 4.2.3 Operazioni elementari (rotazione e altezza)

**Altezza**

Possiamo definire un algoritmo per definire il fattore di bilanciamento e l'altezza di un sotto-albero (da sapere bene, fare attenzione ai casi null)

- Algoritmo (fattore bilanciamento e update altezza di un nodo)

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 3.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 3">


**Operazione di rotazione**

Una rotazione è una operazione elementare di su un albero che mi riposiziona alcuni figli e genitori di un nodo.

- Esempi di rotazione semplice

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 4.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 5.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 6.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 6">

- Pseudocodice della rotazione

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 7.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 7">


### 4.2.4 Risoluzione degli sbilanciamenti

Possiamo catalogare le possibili tipologie di sbilanciamento in 2 macrogruppi di 2 (sono simmetrici destra e sinistra), questi saranno risolvibili tramite rotazioni, che, come vedremo, hanno la proprietà di diminuire l'altezza del nodo di rotazione di 1.

- Tipi di sbilanciamento

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 8.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 8">

- Sbilanciamento di tipo SS (simmetrico DD)

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 9.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 9">

- Sbilanciamento di tipo DS

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 10.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 10">

- Pseudocodice per risolvere sbilanciamento

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 11.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 11">


### 4.2.5 Note su inserimento e rimozione

Queste due operazioni sono le uniche che possono cambiare il bilanciamento dell'albero.

Si può dimostrare che l'inserimento sbilancia al massimo un nodo, per cui una unica rotazione è sufficiente per il tutto.

Mentre la rimozione può sbilanciare tutto il percorso fino la radice come questa operazione:

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Alberi BST e AVL/Untitled 12.png" alt="image/universita/ex-notion/Alberi BST e AVL/Untitled 12">


# 5 Registro ripassi

| 09/04 | Non sapresti esattamente riscrivere il pseudocodice come nel momento in cui lo hai studiato,ma riesci a descrivere con buona esattezza le caratteristiche delle operazioni |
| --- | --- |
| 20/04 | Inizialmente come prima, ma riguardandoti le slides sembra più chiaro. |
|  |  |
o,ma riesci a descrivere con buona esattezza le caratteristiche delle operazioni |
| --- | --- |
| 20/04 | Inizialmente come prima, ma riguardandoti le slides sembra più chiaro. |
|  |  |

# References