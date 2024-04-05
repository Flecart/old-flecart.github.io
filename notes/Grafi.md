---
layout: page
permalink: notes/grafi
tags: en
title: Grafi
---

Ripasso Prox: 3
Ripasso: May 20, 2022
Ultima modifica: May 19, 2022 12:48 PM
Primo Abbozzo: May 3, 2022 11:31 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

## Rappresentazione e terminologia

- Operazioni importanti

    <img src="/images/notes/image/universita/ex-notion/Grafi/Untitled.png" alt="image/universita/ex-notion/Grafi/Untitled">

### Definizione di grafo
È un insieme di nodi e di archi. (prendili da insiemi corretti)

### Metodi di rappresentazione
#### Liste di incidenza

(In pratica numero tutti gli archi e storo il valore dell'arco incidente per ogni nodo)

#### Liste di adiacenza

Classico usato per cp, si storano direttamente pointer a nodi di interesse

#### Matrici di adiacenza

Se esiste un arco fra due nodi, metto un uno in questa posizione (si può utilizzare una cosa simile per mantenere il peso di un arco)

### Termini importanti

Cammino, cammino semplice, ciclo, ciclo semplice, fortemente e debolmetne connesso. grafo completo, aciclico

#### Cammino e cammino semplice

#### Ciclo

#### Componente debolmente connessa
#### Grafo completo
#### Grafo aciclico


# Algoritmi sui grafi
## Algoritmi di visita

### BFS

### DFS

### Ordinamento topologico

È una dfs 😀è utile poi per utilizzare

`

### Componenti fortemente connesse

È una relazione di equivalentz la raggiungibilità (anche per grafi indiretti) e quindi per connessione debole

Si può utilizzare l'algoritmo di Tarjan (credo si chiami cosi) per le SCC. si fa in m + n

## Minimum Spanning Tree

### Definizione di MST

Un sottografo di un grafo che prenda tutti i vertici, tale per cui la somma del peso degli archi presi sia la minima possibile.

**Taglio di un grafo**

**Regole per l’intuizione della sol greedy**

- da libro

    <img src="/images/notes/image/universita/ex-notion/Grafi/Untitled 1.png" alt="image/universita/ex-notion/Grafi/Untitled 1">


### Kruscal

Si utilizza la union find,

### Prim

Solo sulla frontiera, si espande usando la regola del taglio

## Cammini minimi

### Proprietà (sottostruttura e esistenza per connettività)

1. Se ho un cammino minimo, allora anche un suo sotto cammino a un sottonodo è un cammino minimo
2. Se ho un grafo connesso, allora esistono cammini minimi fra due nodi connessi
3.

### Condizione di Bellman

Questa è una condizione sul valore della distanza fra i nodi dei grafi:

Se ho $$d_{xy} \leq d_{xp} + w(p, y)$$, ovvero la distanza fra due nodi, è sempre minore o uguale alla distanza fra un nodo intermedio e l'arco fra questo nodo a y. È uguale se è il cammino minimo.

Da questa osservazione di può definire una **condizione di rilassamento** di un arco.
Gli algoritmi di rilassamento partono da una condizione grossolana, poi approssimano qualcosa sempre meglio, volta dopo volta.

### Algoritmo di Bellman-ford

Il pensiero per ricordarsi questo algoritmo è questa osservazione:

Suppongo di conoscere il cammino minimo da un vertice di partenza e un vertice di arrivo, allora sarebbe facile percorrerlo e conoscerne i costi. Noto che se provo a rilassare ogni singolo arco, allora dovrei aver almeno trovato il costo per il primo nodo del cammino. Continuo a fare così, con rilassamenti successivi finché non arrivo a uno stadio stabile.

Cerco di rilassare ogni arco finché qualcosa cambia, se cambia vuol dire che non ho ancora finito tutti i rilassamenti possibili.

- Algoritmo

    <img src="/images/notes/image/universita/ex-notion/Grafi/Untitled 2.png" alt="image/universita/ex-notion/Grafi/Untitled 2">


**Nota:**

Questo algoritmo è buono perché trova il cammino minimo anche per archi negativi 🌠

### Algoritmo di Dijkstra

Questo algoritmo funziona solamente nel caso in cui non ho archid i peso negativo.

- Lemma fondamentale per comprendere Dijkstra

    <img src="/images/notes/image/universita/ex-notion/Grafi/Untitled 3.png" alt="image/universita/ex-notion/Grafi/Untitled 3">

- Algoritmo in pseudocodice generico

    <img src="/images/notes/image/universita/ex-notion/Grafi/Untitled 4.png" alt="image/universita/ex-notion/Grafi/Untitled 4">

- Algoritmo in pseudocodice con strutture di dati

    <img src="/images/notes/image/universita/ex-notion/Grafi/Untitled 5.png" alt="image/universita/ex-notion/Grafi/Untitled 5">


### Algoritmo di Floyd-Warshall

Utilizziamo la programmazione dinamica per calcolare tutti i percorsi minimi.

L'idea è calcolare ad ogni step, una matrice di percorsi che passano per un certo specifico vertice.

- Algoritmo in pseudocodice (si può ottimizzare lo spazio in questo)

    !<img src="/images/notes/image/universita/ex-notion/Grafi/Untitled 6.png" alt="image/universita/ex-notion/Grafi/Untitled 6">