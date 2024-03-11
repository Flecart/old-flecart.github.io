---
layout: page
permalink: notes/norme-e-condizionamento
tags: italian
title: Norme e Condizionamento
---

Ripasso Prox: 30
Ripasso: December 24, 2022
Ultima modifica: January 9, 2023 3:28 PM
Primo Abbozzo: September 28, 2022 4:34 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Errore inerente

Bisogna cercare di generalizzare il concetto di errore e lo si fa con la norma

## Norma vettoriale

È una funzione da $$f: \R ^n \to \R$$ indicata con due barrette, questa funzione mi dà un concetto di distanza.

### Proprietà 🟨+

<img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled">

### Norma p 🟩-


$$
(\sum_{i = 1}^{n}|x_i|^p)^{1/p}
$$


Nel caso in cui $$p = 2$$ si chiama norma euclidea o viva

Nel caso  $$p = 1$$ è la distanza di manhattan

### Norma di chebichev 🟨

quando ho  $$p = +\infty$$ è definita come  $$\max_{1\leq i \leq n} |x_i|$$ e si indica con $$||x||_\infty$$

### Equivalenza fra le norme 🟩

Questo è un teorema che ci permette di asserire che più o meno tutte le norme hanno la stessa proprietà di definire il concetto di distanza fra due punti poiché

Siano $$||\cdot||, ||\cdot||_x$$ due norme differenti, allora  $$\exists m, M : m ||\cdot|| \leq || \cdot || _x \leq M||\cdot ||$$, ma questo vale solo se siamo in un campo finito.

## Norma matriciale

### Proprietà 🟩

Vogliamo riprendere tutte le propreità descritte per la norma vettoriale, in più vogliamo andare ad aggiungere un quinto punto ossia

<img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled 1.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled 1">

### Norma naturale (o indotte) 🟨—


$$
||A|| = \sup_{x \neq 0} \dfrac{||Ax||}{||x||} = ||Ay||, y = \dfrac{x}{||x||}
$$


Considero solamente le righe, come se compattassi tutte le colonne in una


$$
||A||_\infty = \max_{1 \leq i \leq m} \sum_{j = 1}^n|a_{ij}|
$$


La norma-1 indotta è molto simile, solo che ora compatto sulle colonne


$$
||A||_1 = \max_{j} \sum_{i = 1}^n|a_{ij}|
$$


Norma 2, o **norma spettrale**:


$$
||A||_2 = \sqrt{\Lambda(A^TA)}
$$


Con $$A^TA$$ simmetrica e semidefinita positiva. con $$\Lambda$$ gli autovalori di $$A^TA$$

Se $$A$$ ha rango massimo allora è definita positiva, che è il rango qui?

Le norme dell’identità in tutte queste cose indotte è 1

### Norma di frobenius


$$
||A||_ F = \sqrt{\sum_{i = 1}^m \sum_{j = 1}^n a^2_{ij}}
$$


$$||I||_F = \sqrt{n}$$

- Slide relazione fra le norme matriciali

    <img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled 2.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled 2">


## Condizionamento

Vogliamo andare a definire il concetto di condizionamento per il sistema lineare.

Ossia vorremmo valutare quanto un piccolo cambiamento della matrice influisca sul risultato finale.

- Slide esempio condizionamento

    <img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled 3.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled 3">


Chiamiamo come **errore inerente** la distanza fra il risultato vero e il risultato perturbato. Questo errore dipende fortemente da una natura dei dati in input (che sono mal condizionati)

### Mal condizionamento 🟩

si verifica quando a piccoli cambi della matrice di partenza, si ha un grande errore nel risultato (potremmo dire ordini di grandezza diversi, solitamente questo è una cosa che non vorremmo che ci fosse)

E la differenza fra i risultati è un errore inerente, che dipende dai dati, ma non dall’algoritmo

### Perturbazione e n-condizionamento 🟩

Vogliamo ora vedere quanto siano grandi gli effetti di una perturbazione su una matrice. si può dimostrare che


$$
\dfrac{||\Delta x||}{||x||} \leq k(A) \dfrac{||\Delta A|| }{||A||}
$$


Con $$k(A)$$ il **numero di condizione** della matrice, solamente più è grande più l'errore viene amplificato., se questo  valore è sempre maggiore o uguale a 1 è non singolare.


$$
k(A) = ||A||\cdot||A^{-1}|| \geq ||AA^{-1}|| = ||I|| = 1
$$


- Slide ricavo relazioni condizionamento

    <img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled 4.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled 5.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Norme e Condizionamento/Untitled 6.png" alt="image/universita/ex-notion/Norme e Condizionamento/Untitled 6">