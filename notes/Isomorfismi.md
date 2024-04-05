---
layout: page
permalink: notes/isomorfismi
tags: en
title: Isomorfismi
---

Ripasso Prox: 4
Ripasso: April 30, 2022
Ultima modifica: June 29, 2022 9:42 AM
Primo Abbozzo: March 22, 2022 9:19 AM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

# 3 Isomorfismi

Gli isomorfismi sono delle proprietà fondamentali per stabilire una sorta di equivalenza fra i gruppi. Utilizziamo questi isomorfismi per parlare della stessa cosa ma in modi diversi.

## 3.1 Introduzione

### 3.1.1 Definizione

Un gruppo si dice isomorfo rispetto ad un altro gruppo se, in paroloni semplici, esiste una funzione bigettiva tale che preservi l'operazione del gruppo.

In altre parole


$$
\phi:A \to B,\phi(ab) = \phi(a)\phi(b)
$$


### 3.1.2 Step di dimostrazione

Esiste un modo preciso per dimostrare se due gruppi sono isomorfi. In particolare:

1. Trovare la funzione per l'isomorfismo
2. Dimostrare che è iniettiva
3. Dimostrare che è suriettiva
4. Dimostrare che preserva la struttura del gruppo

## 3.2 Ogni gruppo è in isomorfismo con un gruppo di permutazione

Questo è uno dei teoremi principali per classificare i gruppi

<img src="/images/notes/image/universita/ex-notion/Isomorfismi/Untitled.png" alt="image/universita/ex-notion/Isomorfismi/Untitled">

- Dimostrazione (left cosets as permutation groups)

    <img src="/images/notes/image/universita/ex-notion/Isomorfismi/Untitled 1.png" alt="image/universita/ex-notion/Isomorfismi/Untitled 1">


### 3.2.1 Note storiche su questo teorema

Storicamente parlando si è iniziati a studiare la teoria dei gruppi dal punto di vista delle permutazioni, questo teorema è ciò che ha permesso una maggiore astrazione rispetto al concreto gruppi delle permutazioni, permettendo lo sviluppo di questo campo in modo tale.

## 3.3 Proprietà dell'isomorfismo sugli elementi

Abbiamo una unica slide che riassume tutte le proprietà. Non dovrebbe essere molto difficile dimostrare il tutto.

<img src="/images/notes/image/universita/ex-notion/Isomorfismi/Untitled 2.png" alt="image/universita/ex-notion/Isomorfismi/Untitled 2">

### 3.3.1 Preservazione dell’elemento neutro

### 3.3.2 Preservazione della potenza

### 3.3.3 Coimplica la commutatività

### 3.3.4 Coimplica la ciclicità

### 3.3.5 Stesso ordine

### 3.3.6 Preservazione del n_sol per equazioni del gruppo

### 3.3.7 Preservazione dell’ordine degli elementi

## 3.4 Proprietà dell’isomorfismo sui gruppi

<img src="/images/notes/image/universita/ex-notion/Isomorfismi/Untitled 3.png" alt="image/universita/ex-notion/Isomorfismi/Untitled 3">

### 3.4.1 La funzione inversa è un isomorfismo

### 3.4.2 Coimplica abelianità

### 3.4.3 Coimplica la ciclicità

### 3.4.4 L'immagine di un sottogruppo è un sottogruppo (del gruppo di arrivo)

## 3.5 Automorfismi

### 3.5.1 Definizione

Un automorfismo di gruppo è solamente un isomorfismo con una funzione che parte da sé ed arriva a sé stesso.

Un esempio di automorfismo è la permutazione (che mi scambia gli elementi, ma alla fine è una funzione da sé in sé).

### 3.5.2 Automorfismo interno

L'automorfismo interno rispetto a un gruppo è una specie di congiunzione:

$$G_a(x) = axa^{-1}$$ si può dimostrare che questo è effettivamente un isomorfismo.

### 3.5.3 Aut(Zn) ha stesso ordine di U(n)

<img src="/images/notes/image/universita/ex-notion/Isomorfismi/Untitled 4.png" alt="image/universita/ex-notion/Isomorfismi/Untitled 4">

Gli unici isomorfismi di Zn a se stesso sono gli elementi che sono coprimi con zn, in quanto solo questi possono generare l'intero gruppo (ed essere generatore quindi...) Questo è lo stesso numero di elementi con U(n). Ad alto livello è questo è il motivo per cui vale questo teorema.

- Dimostrazione

    !<img src="/images/notes/image/universita/ex-notion/Isomorfismi/Untitled 5.png" alt="image/universita/ex-notion/Isomorfismi/Untitled 5">