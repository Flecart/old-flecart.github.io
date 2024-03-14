---
layout: page
permalink: notes/gruppi-ciclici-e-permutazioni
tags: italian
title: Gruppi ciclici e permutazioni
---

Ripasso Prox: 14
Ripasso: April 30, 2022
Ultima modifica: June 29, 2022 9:42 AM
Primo Abbozzo: March 20, 2022 4:36 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Gruppi ciclici e permutazioni

## Il gruppo ciclico

### Definizione gruppo ciclico

Abbiamo definito in [Gruppi](/notes/gruppi) per la prima volta il significato di gruppo ciclico generato da un elemento del gruppo, questo insieme si è poi dimostrato essere un sottogruppo del gruppo

Un gruppo $$G$$ è chiamato *ciclico* se esiste un $$a \in G$$ tel per cui 

$$
G = \left\{ a^{n} \mid n \in \mathbb{Z} \right\} 
$$

Dove **a** è chiamato **elemento generatore**.

Scriviamo $$G = \langle a \rangle$$ per dire che $$G$$ è generato dall'elemento $$a$$.
L'ordine del gruppo è la cardinalità:

$$
ord(G) = \lvert \langle a \rangle  \rvert 
$$


### Criterio $$a^{i} = a^{j}$$

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 1.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 1">
Probabilmente ha qualche relazione con [Teorema di Lagrange](/notes/teorema-di-lagrange).

- note sull'enunciato
    entrambe le frecce $$\impliedby$$ sono abbastanza ovvie.

    Ragionando sul primo caso, nel caso in cui è infinito, se succedesse che $$a^i = a^j \land i \neq j$$ si avrebbe che l'ordine è finito, perché si ripeterebbe ogni tot, quindi dimostri così. Nel secondo caso credo sia così, ma non saprei come formalizzare la cosa.

- Dimostrazione
    Come si può notare, mi sto riducendo a una classe di resto con l'algoritmo di euclide nel secondo caso.

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 2.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 2">


Questo è un teorema molto importante nei gruppi finiti, soprattutto, perché mi sta dicendo che ci possiamo sempre ridurre a una classe di resto per l'esponente.

**Corollario 1**
$$\text{ Per ogni elemento di gruppo A, si ha che: } |A| = |\langle A\rangle|$$

**Corollario 2**

$$a\in G, |a| = n \in \mathbb{N}, k \in \mathbb{Z}, a^k = e_g \implies n \mid k$$

**Osservazione**

Questo fatto che la moltiplicazione fra due elementi funziona come una addizione fra due elementi in $$\Z_n$$ ci fa intuire come sia possibile un isomorfismo fra questi due gruppi.

Infatti esiste, dimostreremo poi che per ogni gruppo ciclico finito di ordine n esiste un isomorfismo con Zn (credo)

### Relazione fra ordine $$n, e$$ un $$k$$ in $$\mathbb{Z}$$ e $$gcd(n,k)$$

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 3.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 3">

- Dimostrazione
    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 4.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 4">


Questo teorema ci è molto utile per **ridurre il generatore di un gruppo in un altro più gestibile** o più semplice da manipolare

**Corollario 1**

In un gruppo ciclico, l'ordine di un elemento divide l'ordine del gruppo.

In simboli


$$
a\in G, |a| =k, |G| = n,\implies k \mid n
$$


(da notare l'ordine opposto dei divide rispetto al corollario 2 del teorema precedente)

**Corollario 2 criterio |ai| = |aj|**

Questo è molto simile al teorema precedente, ma ora stiamo parlando di ordine.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 5.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 5">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 6.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 6">


**corollario 3 Generatori di gruppi ciclici finiti**

Questo è un corollario del corollario 😂. In pratica afferma che

Il gruppo generato da $$\langle a \rangle$$ è uguale a $$\langle a^j \rangle$$ sse $$gcd(n, j) = 1$$ con n l'ordine di a.
cosa simile con $$|a| = |a^j| \iff gcd(n,j) = 1$$

E avendo questo possiamo definire con concretezza di generatori del gruppo finito Zk

**Corollario 4 Generatori di Zn**

sia $$k \in \mathbb{Z}_n$$, k è un generatore sse $$gcd(n,k) = 1$$.

la dimostrazione segue dal fatto che 1 è un generatore di Zn, e vogliamo che il gruppo generato da 1 e k sia lo stesso.

## Classificazione di sottogruppi di gruppi ciclici

### Teorema fondamentale dei gruppi ciclici

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 7.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 7">

- Dimostrazione
    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 8.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 8">


**Corollario Sottogruppi di Zn**

Dal teorema fondamentale dei sottogruppi di gruppi ciclici abbiamo una caratterizzazione precisa dei sottogruppi presenti in Zn, sono in particolare tutti i **divisori di n**.

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 9.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 9">

### Numero di elementi di un un certo ordine in un gruppo ciclico

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 10.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 10">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 11.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 11">

Questo è anche una dimostrazione per [Teorema di Lagrange#Teorema di Eulero](/notes/teorema-di-lagrange#teorema-di-eulero).

**Corollario 1 Numero di elementi di ordine d**

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 12.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 12">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 13.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 13">


## Gruppi di permutazione

### Decomposizione in cicli

Esiste una sintassi per scrivere le permutazioni con una notazione a cicli. Vogliamo dimostrare ora che questa sintassi è sempre possibile (quindi corrisponde a una equivalenza)

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 14.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 14">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 15.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 15">

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 16.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 16">


La dimostrazione procede per via costruttiva, proponendo una specie di algoritmo per trovare tutti i cicli fino ad esaurimento di elementi nell’insieme.

### Commutatività di cicli disgiunti

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 17.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 17">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 18.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 18">


Una volta letta la dimostrazione sembra una cosa ovvia, ma probabilmente l’idea è sulla scelta degli elementi iniziali?

### Ordine di una permutazione (scomposizione con ordine di sottocicli)

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 19.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 19">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 20.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 20">


### Decomposizione in permutazioni bicicle

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 21.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 21">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 22.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 22">


**Proposizione**

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 23.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 23">

Questo lemma si può estendere a un caso più generale, dove si possono iniziare a distinguere permutazioni pari e dispari. Vedremo che avranno certe proprietà (legate alle matrici poi anche).

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 24.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 24">

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 25.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 25">


### Parità e disparità di 2-cicli

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 26.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 26">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 27.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 27">


### L’insieme di permutazioni pari è un sottogruppo di Sn

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 28.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 28">

- Dimostrazione

    Siano a, b due elementi di questo insieme, vogliamo dimostrare che $$ab^{-1} \in S$$ notiamo che per il teorema 5.5  $$b^{-1}$$ deve essere pari, perché altrimenti avrei che $$e = bb^{-1}$$ sarebbe scrivibile come un prodotto di permutazioni 2-cicle dispari. Inoltre, chiaramente un prodotto di 2 permutazioni pari è ancora pari (basta concatenare queste, che poi al massimo si eliminano a  due a due). Ecco il sottogruppo.


### Il gruppo alternante di n ha ordine n! 

L’enunciato è proprio questo titolo, quindi non lo riporto (sul libro è il numero 5.7).

Invece riporto la definizione di gruppo alternante:

<img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 29.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 29">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 30.png" alt="image/universita/ex-notion/Gruppi ciclici e permutazioni/Untitled 30">
## Residui Quadratici
Si dice che $$x \in G$$ è un residuo quadratico nel suo gruppo se ha una radice quadrata in quel gruppo, ossia un $$a \in G$$ tale per cui $$a^{2} = x$$.
Questo è di particolare interesse per robe di Crypto.

### Simbolo di Legendre
È il valore 

$$
x^{(p - 1)/2}
$$

E ha delle proprietà carine che non conosco