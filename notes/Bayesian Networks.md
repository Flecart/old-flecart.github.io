---
layout: page
permalink: notes/bayesian-networks
tags: en
title: Bayesian Networks
---

Ripasso Prox: 3
Ultima modifica: December 29, 2022 3:24 PM
Primo Abbozzo: August 20, 2022 1:31 PM
Stato: 🌕🌕🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

# Networks Bayesiani

Questi network bayesiani sono proprio dei grafi, che permettono una migliore comprensione delle relazioni causali o diagnostici fra le probabilità

- Esempio rete bayesiana

    <img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled">


## Note generali

### Introduzione alla rete classica

Una rete bayesiana ci permette di semplificare di molto il calcolo della full disjoint probability table, rendendola in questo modo

<img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled 1.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled 1">

Ossia andiamo a utilizzare una **probabilità locale, o sparsa** per fare i conti, cosa che semplifica molto, e quindi velocizza il calcolo. v

### Conditional probability table

Ogni nodo deve avere anche una tabella per i valori di probabilità condizionale.

<img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled 2.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled 2">

### Il mantello di Markov

> Il mantello di un nodo nell rete è l’insieme dei genitori, dei figli, e dei genitori dei figli, costituisce l’insieme per cui il nodo attuale è condizionalmente indipendente da tutti gli altri nodi.
>

È una nozione molto forte questa, che ha implicazioni molto profonde, un esempio è Karl Friston che lo usa per fare delle argomentazioni forti sull’origine della vita dalla zuppa primordiale.

### Rete con variabili continue

In cui servirebbe una base di analisi molto forte e anche di probabilità e statistica (quindi conoscere anche dal punto di vista matematico cosa sia la distribuzione normale etc).

## Inferenza esatta

Possiamo andare ad utilizzare le reti per calcolare il **valore di probabilità di un evento,** in questa parte si vede come.

### Per enumerazione

Si va con la classica definizione di probabilità, andiamo a contare tutto, e ciò ci comporta un tempo esponenziale di calcolo.

<img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled 3.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled 3">

- Pseudocodice

    <img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled 4.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled 4">


### Eliminazione di variabili

Con il metodo precedente, può succedere che facciamo lo stesso calcolo molteplici volte, questa è una chiarissima inefficienza. Si può risolvere facendo una eliminazione di variabili in modo tale:

- Pseudocodice

    <img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled 5.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled 5">


### Algoritmi di clustering

L’idea principale di questo è raggruppare dei nodi in un nodo più grosso.

- Esempio di clustering

    <img src="/images/notes/image/universita/ex-notion/Bayesian Networks/Untitled 6.png" alt="image/universita/ex-notion/Bayesian Networks/Untitled 6">


## Sampling (inferenza approssimata)

ora andiamo ad utilizzare un metodo di **monte carlo,** che abbiamo visto per la prima volta (se non c’è è perché sono stato pigro e non l’ho scritto) in [Adversarial Search](/notes/adversarial-search).

Praticamente andremo a fare sampling di un evento tante volte, e cercheremo di carpirne delle informazioni con cui aggiornare il nostro modello.

### Sampling diretto

(classico)

### Sampling con rifiuto

Se non è consistente con il modello di probabilità, allora rifiuta un assegnamento…

### Importance sampling

## Simulazione con catene di Markov



# References