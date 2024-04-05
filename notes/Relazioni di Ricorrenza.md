---
layout: page
permalink: notes/relazioni-di-ricorrenza
tags: en
title: Relazioni di Ricorrenza
---

Ripasso Prox: 40
Ripasso: June 24, 2022
Ultima modifica: May 19, 2022 12:48 PM
Primo Abbozzo: February 28, 2022 5:02 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# 2 Relazioni di ricorrenza

### Iterazione

Questo metodo semplicemente consiste di calcolare tutte le operazioni e scriverlo con una notazione asintotica.

- slide

    <img src="/images/notes/image/universita/ex-notion/Relazioni di Ricorrenza/Untitled.png" alt="image/universita/ex-notion/Relazioni di Ricorrenza/Untitled">


### Sostituzione (induzione)

- slide

    <img src="/images/notes/image/universita/ex-notion/Relazioni di Ricorrenza/Untitled 1.png" alt="image/universita/ex-notion/Relazioni di Ricorrenza/Untitled 1">


**Analisi della relazione di ricorrenza di fibonacci**

Si può dimostrare utilizzando l'induzione che una relazione di questo tipo


$$
T(n) = \begin{cases}
O(1) \\
T(n-1) + T(n-2) + 1
\end{cases}
$$


Si trova che è $$O(2^n), \Omega(2^{n/2})$$

Analisi finale.

Si può creare una stima corretta, utilizzando la formula per il calcolo di fibonacci (che dimostri facendo osservazioni su una funzione generatrice di essa, una serie infinita).

<img src="/images/notes/image/universita/ex-notion/Relazioni di Ricorrenza/Untitled 2.png" alt="image/universita/ex-notion/Relazioni di Ricorrenza/Untitled 2">

### Albero di ricorsione

- slide

    <img src="/images/notes/image/universita/ex-notion/Relazioni di Ricorrenza/Untitled 3.png" alt="image/universita/ex-notion/Relazioni di Ricorrenza/Untitled 3">


### Teorema dell’esperto (master)

Questo teorema permette di stabilire subito la stima asintotica per tutte le ricorrenze nella forma

$$T(n) = aT(n/b) + f(n)$$ ed è diviso in tre casi:

| 23/03 | Ricordo tutto come se fosse ieri |
| --- | --- |
| 09/04 | Non ti ricordi esattamente tutto (teoricamente albero di ricorsione, ma in pratica non lo so se lo fa) |
|  |  |
in tre casi:

| 23/03 | Ricordo tutto come se fosse ieri |
| --- | --- |
| 09/04 | Non ti ricordi esattamente tutto (teoricamente albero di ricorsione, ma in pratica non lo so se lo fa) |
|  |  |