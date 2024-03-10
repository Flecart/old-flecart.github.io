---
layout: page
permalink: notes/notazione-asintotica
tags: italian
title: Notazione Asintotica
---

Ripasso Prox: 31
Ripasso: May 28, 2022
Ultima modifica: April 28, 2022 5:07 PM
Primo Abbozzo: February 24, 2022 9:19 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- funzione di costo
- Vecchi ripassi
    - Analisi ammortizzata

# 1 Notazione asintotica

## 1.1 Introduzione

### 1.1.1 Obiettivi

Cercare di definire il tempo impiegato da una funzione per essere eseguita **in termini di DIMENSIONE dell'input**. **(il numero di bit a livello basso basso)

Ma abbiamo il problema di misura, in quanto dobbiamo considerare delle variabili che siano indipendenti rispetto alla macchina.

### 1.1.2 Caratteristiche della notazione

Vogliamo considerare una notazione asintotica (che guarda quanto fa il comportamento verso l'infinito)

<img src="/images/notes/image/universita/ex-notion/Notazione Asintotica/Untitled.png" alt="image/universita/ex-notion/Notazione Asintotica/Untitled">

### 1.1.3 Funzione di costo

<img src="/images/notes/image/universita/ex-notion/Notazione Asintotica/Untitled 1.png" alt="image/universita/ex-notion/Notazione Asintotica/Untitled 1">

## 1.2 Modelli asintotici

### 1.2.1 O-grande

### 1.2.2 o-piccolo

### 1.2.3 Theta

### 1.2.4 Omega-grande

### 1.2.5 omega-piccolo

## 1.3 Costo e Complessità computazionale

### 1.3.1 Definizioni

<img src="/images/notes/image/universita/ex-notion/Notazione Asintotica/Untitled 2.png" alt="image/universita/ex-notion/Notazione Asintotica/Untitled 2">

## 1.4 Analisi ammortizzata

### 1.4.1 Introduzione

Questa è una tecnica che trova il **costo medio** di un algoritmo. La differenza con il calcolo del costo medio classico è che questo calcolo mi trova il costo medio per una *sequenza di operazioni* mentre il classico mi trova il costo medio per una singola operazione

### 1.4.2 Casi di utilizzo

Di solito è utile utilizzare questo metodo di analisi in queste condizioni

1. Caso pessimo non frequente (quindi per dire che nella media un algoritmo è molto più efficiente)
2. Semplificare l'analisi del caso medio

### 1.4.3 Aggregazione

Vogliamo cercare un limite superiore su n operazioni, poi dividere il tutto per n.

Questo è più utile quando il costo **totale è conosciuto**

### 1.4.4 Accantonamenti

Questo è basato sulla contabilità, ho un certo credito iniziale, posso utilizzare tutto, ma non posso mai andare in negativo.

Questo è utile quando **ci sono diverse operazioni**.

Un esempio di analisi ammortizzata utilizzando gli accantonamenti è la doubling and halving in cui 3 monete per ogni operazione di inserimento bastano poi per ricopiare ed espandere o diminuire il tutto a piacere (quindi 3n , si ha un costo costante).
menti è la doubling and halving in cui 3 monete per ogni operazione di inserimento bastano poi per ricopiare ed espandere o diminuire il tutto a piacere (quindi 3n , si ha un costo costante).