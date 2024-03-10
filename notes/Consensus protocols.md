---
layout: page
permalink: notes/consensus-protocols
tags: italian
title: Consensus protocols
---

Ripasso Prox: 7
Ultima modifica: January 27, 2023 2:29 PM
Primo Abbozzo: December 29, 2022 3:49 PM
Studi Personali: No

# Elementi di ripasso

# Consensus protocols

## Introduzione

Vogliamo tenere in modo sincronizzato alcune macchine, questo è il nostro obiettivo. Questo è un problema abbastanza difficile… Come tenere in sinc se ci sono alcuni nodi maligni o la rete che non è bona?

### Assunzioni principali (2)

1. **Esiste internet**
2. **Esiste Crittografia**

Queste sono le assunzioni che non saranno mai rilassate per l’intero corso, diciamo che sono la nostra base su cui possiamo andare a costruire la base per il nostro studio.

## Digital signature scheme

Vorremmo avere un sistema per firmare alcuni documenti online, e possiamo dividere questa cosa in tre passi fondamentali

Questa roba esiste da molto tempo, dagli anni 80 o prima.

### Algoritmi per digital signature (3)

Una cosa importante è che questi algoritmi di signature son oefficienti.

**Generazione della chiave**

Deve essere nella forma $$s \to (pk, sk)$$, ossia seed per public e secret key.

**Firma con la chiave**

Dovrà essere una funzione nella forma $$msg + sk \to msg + sig$$. Da notare è che la signature è dipendente dal contenuto. Ma non possiamo utilizzarlo in questi ambienti elettronici perché è troppo facile copiare ed incollare una forma. Deve essere per forza che dipenda

1. Dall’identità di chi firma
2. Da cosa vuole dire il firmatario.

**Verifica della chiave**

$$msg + sig + pk \to bool$$, per capire se questa firma è valida o meno, deve solamente dirmi questo valore booleano. In particolare **la chiave è pubblica** quindi ognuno può venire a verificare un messaggio, ma può firmare solamente chi possiede la chiave privata.

### Sicurezza (3 assunzioni)

L’assunzione principale della sigurezza delle firme digitali è

> **Ideal signatures:** Se non conosci la chiave privata ⇒ non posso mai generare la coppia `msg + sig` corretta
>

Delle volte è possibile rompere questa cosa (e.g. con brute force se ci metto abbastanza poco per farlo). Però noi assumeremo che valga questo. E ha bisogno di risorse infinite per poter bruteforcare tutto se ha solamente quello come unica soluzione. Quindi una altra assunzione è che **l’avversario ha risorse finite, polinomiali**.

**Assunzione di complessità** vogliamo che non ci siano algoritmi efficienti per risolvere qualcosa in modo molto veloce

## The State Machine Replication (SMR) Problem

### Intuizione al problema

Prendiamo uno **state machine**, in modo simile a quanto fatto in Linguaggi di programmazione, che ad ogni input e output cambia lo stato interno. Uno state machine può essere un database, ma può essere anche tutto l’ambiente delle blockchain (e.g. mandare currency cambia lo stato) o un [Automi e Regexp](/notes/automi-e-regexp).

La **replica** è necessaria per la performance, in modo che ci siano più macchine uguali che rendano lo stesso servizio. Ma se ho tante macchine che fanno la stessa cosa, devo in qualche modo farci il sync, ed ecco il problema che nasce dai database, il problema dei sync write e read. Per noi la replicazione è lo stato della macchina gigante della blockchain.

**Nel contesto di blockchain**

Avremo una **lista** di transazioni, che sono niente altro che delle richieste a un certo nodo di fare qualcosa, e si stora la storia delle transazioni, è molto importate che **l’ordine sia consistente**. Il problema del consenso diventa quindi provare a **sincronizzare la transazioni**, che nota, non devo essere money! Basta richieste.

### Consistency

Questa è la proprietà che tutti i nodi sono d’accordo sulla storia, permettendo la possibilità che qualche nodo sia indietro (ma devono essere d’accordo su quella parte comune!)

### Liveness e Safety

queste sono le stesse proprietà descritte in [Programmi Concorrenti](/notes/programmi-concorrenti). Con la liveness vogliamo che non ci siano deadlocks, e blocchi con la stessa logica → **alla fine il nodo dovrà essere aggiunto!**

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
alla fine il nodo dovrà essere aggiunto!**

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |