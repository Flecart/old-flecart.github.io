---
layout: page
permalink: notes/tecniche-algoritmiche
tags: italian
title: Tecniche algoritmiche
---

Ripasso Prox: 3
Ultima modifica: May 8, 2022 11:57 AM
Primo Abbozzo: April 12, 2022 12:50 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# 10 Tecniche Algoritmiche

[13-DivideEtImpera.pdf](Tecniche%20algoritmiche%200bb8874d51fd470896a78cb2a0b1c748/13-DivideEtImpera.pdf)

## 10.1 Divide et impera

### 10.1.1 Introduzione

Abbiamo già visto L'utilizzo di questa tecnica per quick e merge sort in [Algoritmi di ordinamento](/notes/algoritmi-di-ordinamento)

Questa tecnica si focalizza in tre passi fondamentali:

1. Dividere il problema in sotto-problemi
2. Risolvere il sotto-problema
3. Mergiare le soluzioni di questi sotto-problemi.

Questa è più una tecnica che si impara di più con la pratica, andremo a fare un problema che utilizza questa tecnica

### 10.1.2 La torre di Hanoi

- Storia sotto

    <img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled">


- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 1.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 1">

- Soluzione con ricorsione

    <img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 2.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 2">


### 10.1.3 Moltiplicazione fra interi

Si utilizza una tecnica divide ed impera per moltiplicare assieme i due numeri.

Quindi divido il numero in parte superiore e parte inferiore...

- Prima applicazione

    <img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 3.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 3">

    Ma si potrà notare che questo metodo non porta a migliroamenti

- Moltiplicazione più efficiente

    <img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 4.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 4">


### 10.1.4 Sottovettore di valore massimo

Questo è un problema classico che ho già riscontrato in [maximum subarray su](https://cses.fi/problemset/task/1643)m.

**Algoritmo banale**

Va a guardare tutte le sottosequenze possibili, che sono O(N2) perché è uguale al numero di coppie di indici (ordinate) che si possono prendere.

**Algoritmo Divide et Impera**

Si nota che la massima sottosequenza è o nella parte destra o sinistra, oppure in mezzo, quindi si conside

- Algo

    <img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 5.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 5">


## 10.2 Greedy

Greedy è buono quando si può **Dimostrare** (e se non lo dimostri perdi un sacco di tempo a implementare una soluzione che non è nemmeno giusta) e si basa sui sottoproblemi ottimali.

### 10.2.1 Problema del resto

In cui basta scegliere la moneta migliore ogni volta (perché sicuramente(con piccolo ragionamento) ci vorranno meno monete rispetto a usare altre)

<img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 6.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 6">

Un osservazione è che può fallire in sistemi non CANONICI.

### 10.2.2 Job scheduling

Si avrà che basta ordinare secondo la lunghezza minore (perché si guadagna sempre in questo caso)

<img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 7.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 7">

### Huffman coding

Si crea un albero di codifica che sia il meno profondo possibile, in questo modo ho un modo più formale per giustificare il fatto di avere la minima codifica.

<img src="/images/notes/image/universita/ex-notion/Tecniche algoritmiche/Untitled 8.png" alt="image/universita/ex-notion/Tecniche algoritmiche/Untitled 8">

- Pseudocodice per l’albero di huffman.

    ```cpp
    Huffman(real f[1..n], char c[1..n]) → Tree
    Q ← new MinPriorityQueue()
    integer i;
    for i ← 1 to n do
    	z ← new TreeNode(f[i], c[i]);
    	Q.insert(f[i], z);
    endfor
    for i ← 1 to n – 1 do
    	z1 ← Q.findMin(); Q.deleteMin();
    	z2 ← Q.findMin(); Q.deleteMin();
    	z ← new TreeNode(z1.f + z2.f, '');
    	z.left ← z1;
    	z.right ← z2;
    	Q.insert(z1.f + z2.f, z);
    endfor
    return Q.findMin();
    ```


## Programmazione dinamica

Abbiamo risolto fibonacci, Maximum subarray sum con la programmazione dinamica, entrambi in O(n).

Ora andiamo a parlare del problema più importante per la programmazione dinamica, il problema dello zaino

### Knapsack problem

z

### Distanza di levenstein

### Seam Carving

# 11 Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
ante per la programmazione dinamica, il problema dello zaino

### Knapsack problem

z

### Distanza di levenstein

### Seam Carving

# 11 Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |