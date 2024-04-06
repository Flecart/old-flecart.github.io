---
layout: page
permalink: notes/teorema-di-lagrange
tags: en
title: Teorema di Lagrange
---

Ripasso Prox: 2
Ripasso: April 30, 2022
Ultima modifica: June 29, 2022 9:42 AM
Primo Abbozzo: March 23, 2022 10:33 AM
Stato: 🌕🌕🌑🌑🌑
Studi Personali: No


## Classi laterali

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled">

- Dimostrazione dei lemmi sopra.
    <img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 1.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 2.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 2">

La cosa interessante di questa parte è possiamo usare una classe laterale per partizionare il gruppo iniziale!
## Il teorema di Lagrange

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 3.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 3">
Dividere significa che **partiziona** l'insieme iniziale in alcuni insiemi distinti.
L'insieme $$G:H$$ è l'insieme che contiene tutti i cosets, credo.

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 4.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 4">


### |G:H|  = |G|/|H|

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 5.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 5">

### |a| divide |G|

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 6.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 6">

Ossia un corollario dopo il teorema di Lagrange. La cosa citata è dimostrata in [Gruppi ciclici e permutazioni#Criterio $$a {i} = a {j}$$](/notes/gruppi-ciclici-e-permutazioni#criterio-$$a-{i}-=-a-{j}$$).


### I gruppi di ordine primo sono ciclici

Se ho un gruppo di ordine primo, per il teorema di Lagrange non posso avere sottogruppi propri, perché l’ordine di questi dovrebbe dividere l’ordine del gruppo di partenza. Per questo motivo ho un unico gruppo. Ossia ogni elemento genera l’intero gruppo

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 7.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 7">


### a elevato all’ordine del gruppo è uguale ad e

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 8.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 8">

- Dimostrazione
    L’ordine dell’elemento a deve dividere l’ordine di |G| per Lagrange, quindi, in simboli

$$
|a| =n, |G| = m, n \mid m \implies m = nj, a^{|G|} = a^{nj} = e ^j = e
$$



### Il piccolo teorema di fermat

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 9.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 9">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 10.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 10">
Solitamente si usa la versione

$$
a^{p - 1} = 1 \mod  p
$$

E la cosa comoda è che $$a^{p - 2}$$ è l'inversa di quello.

### Teorema di Eulero
Proof. [http://www.fen.bilkent.edu.tr/~franz/nt/ch7.pdf.](http://www.fen.bilkent.edu.tr/~franz/nt/ch7.pdf.)

Questa è una generalizzazione di [#Il piccolo teorema di fermat](#il-piccolo-teorema-di-fermat).
Afferma che $$\forall n \in \mathbb{N}$$ vale che

$$
a^{\varphi(n)} = 1 \mod n
$$


Questo è molto più complesso da descrivere e dimostrare. Bisognerebbe per esempio anche definire proprietà della funzione di Eulero.

### Classificazione dei gruppi di ordine 2p

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 11.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 11">

SCHIVA STO TEOREMA CHE NON MI SERVE A NUCAZZU

- Idee della dimostrazione
    1. Dividere la discussione con la presenza o meno di elementi di ordine 2p
    2. Caso in cuinon ci sono elementi di ordine 2p
        1. Dimostrare che esiste almeno un elemento di ordine p, perché se fossero tutti di ordine 2, riesco a crearmi (in modo creativo) un sottogruppo di ordine 4 a piacere, molto simile al gruppo quaternione.
        2. Avendo un sottogruppo di ordine p, questo quozienta l’insieme G per il teorema di lagrange, ho solamente un altro insieme che posso scrivere come
        *elemento_fuori_a * gruppo_generato_da_a_di_ordine_p*
        3. Dimostro che l’ordine dell’elemento fuori da a deve essere necessariamente di ordine 2. (in qualche modo che non ho compreso)
- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 12.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 12">


## Stabilizzatore e orbita

### Stabilizzatore

<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 13.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 13">

### Orbita

!<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 14.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 14">

### Teorema orbita stabilizzatore

!<img src="/images/notes/image/universita/ex-notion/Teorema di Lagrange/Untitled 15.png" alt="image/universita/ex-notion/Teorema di Lagrange/Untitled 15">



# References