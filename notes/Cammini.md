---
layout: page
permalink: notes/cammini
tags: en
title: Cammini
---

Ultima modifica: October 17, 2021 10:38 AM
Primo Abbozzo: October 16, 2021 5:16 PM
Studi Personali: No

# Elementi di ripasso

# 1 Cammini

## 1.1 Il cammino minimo

### 1.1.1 Definizione e caratteristiche

### 1.1.2 Costi negativi

Sono cose molto brutte

### 1.1.3 Cammino minimo semplice

### Costruzione di cammini minimi

## 1.2 Vertici

### 1.2.1 definizione distanza fra due vertici

Costo del cammino minimo che li connette

### Condizione di bellman

### Albero dei cammini minimi

## Rilassamento

### Definizione

Si va a vedere dove non funziona la disuguaglianza triangolare, se localmente non funziona ovvero se per esempio succede $$D_{xu} + \omega(u,y) < D_{xy}$$ per qualche vertice all'interno del grafo, so di per certo che la distanza $$D_{xy}$$ non è una distanza, quindi possiamo riassegnarla in modo che verifichi la disuguaglianza

### Bellman ford

Questo algoritmo parte definendo tutti i vertici a distanza infinita, riassegna i valori partendo da un vertice prefissato.

Questo ragionamento è solamente possibile con l'osservazione che il cammino è minimo se tutti i suoi sottocammini lo sono, quindi mi sto costruendo cammini minimi da zero.

Sto riassegnando valore a tutti gli archi piano piano...

### Rilassamento topologico

### Bellman-ford con ordinamento

Permette di non ripetere l'ordinamento di n vertici

## Grafi Aciclici

### Ordinamento topologico

### Dijkstra

**Lemma sull'espansione del grafo di esplorazione**
 ordinamento

Permette di non ripetere l'ordinamento di n vertici

## Grafi Aciclici

### Ordinamento topologico

### Dijkstra

**Lemma sull'espansione del grafo di esplorazione**

# References