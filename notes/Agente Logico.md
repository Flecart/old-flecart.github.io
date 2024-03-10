---
layout: page
permalink: notes/agente-logico
tags: italian
title: Agente Logico
---

Ripasso Prox: 5
Ultima modifica: December 29, 2022 3:24 PM
Primo Abbozzo: July 30, 2022 4:16 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

# Agenti Logici

## Introduzione

### Nozioni base

Questi sono le parole chiave di questo capitolo, ci permettono di parlare con chiarezza riguardo l’agente logico.

**Sentence**

**Knowledge Base**

**Axiom**

**Inference**

**background knowledge**

**Knowledge representation language**

**Knowledge level**

**Implementation level**

- Esempio generale di agente logico

    <img src="/images/notes/image/universita/ex-notion/Agente Logico/Untitled.png" alt="image/universita/ex-notion/Agente Logico/Untitled">


## Logica proposizionale

### Sintassi del linguaggio

Descrivere la BNF della logica proposizionale.

per sapere cosa sia la BNF di questo è molto più facile rifarsi agli appunti di logica presi durante l’anno di corso 2021/2022 [Logica Proposizionale](/notes/logica-proposizionale).

### **Deduzione o derivazione**

Abbiamo ora un algoritmo (stupido) di verifica sul fatto se valga o meno $$KB \vDash \alpha$$, ovvero vogliamo sapere se alpha si può derivare dal nostro modello

- Algoritmo di derivazione

    <img src="/images/notes/image/universita/ex-notion/Agente Logico/Untitled 1.png" alt="image/universita/ex-notion/Agente Logico/Untitled 1">


### **Inferenza → (sound and complete inference methods)**

### Risoluzione

La risoluzione è una operazione che si può avere fra due clausole, come se fosse una regola di derivazione, come vedremo ci sta molto comodo, anche se non l’abbiamo mai fatta a lezione.

In breve:

> Consiste di eliminare qualche caso banale negli OR e.g. se ho a or b or c, e ho anche not a, allora posso dedurre b or c.
>

Sono interessanti soprattutto perché è una operazione **completa**, cioè che è in grado di derivare tutto il derivabile (quindi se gli dai 2 clausole random, $$\alpha, \beta$$ riesce *sempre* a determinare se vale o meno $$\alpha \vDash \beta$$.

oltre a ciò sono anche **sound**, ossia quello che deducono è corretto (non fanno mai teoremi sbagliati).

**Perché funziona**

In pratica prova a dimostrare che not tesi→ assurdo. e questa è gestibile perché è in forma congiuntiva normale, che permette di utilizzare la risoluzione

- Algoritmo per la risoluzione

    <img src="/images/notes/image/universita/ex-notion/Agente Logico/Untitled 2.png" alt="image/universita/ex-notion/Agente Logico/Untitled 2">


### Check del modello

## Modelli di inferenza

### Conjunctive Normal Form

Quando abbiamo delle clausole, ossia delle *disgiunzioni di letterali,* possiamo cercare di trasformare questa nella sua forma congiuntiva normale. Questo è possibile perché **ogni proposizione si può ridurre a And e Or**.

- BNF della CNF

    <img src="/images/notes/image/universita/ex-notion/Agente Logico/Untitled 3.png" alt="image/universita/ex-notion/Agente Logico/Untitled 3">


Andare a vedere questo per un algoritmo che utilizzi questa forma per runnare.

### Forward Chaining

### Horn Clauses

Una horn clause è una proposizione composta di and, in cui al messimo un singolo valore è vero.

Si è scoperto che esiste un algoritmo molto efficiente per checkare se una proposizione è vera in un modello (che *eseguen in O(n)*)

In pratica è una cosa molto simile in **And-or search** presentato in [Problemi di ricerca](/notes/problemi-di-ricerca).

**Algoritmo in breve**

Praticamente è una BFS che prende come queue iniziale tutte le proposizioni atomiche che sono date per vere.

Una volta poppati questi vanno a diminuire il conteggio degli implica che lo hanno come ipotesi. Se il singolo implica ha questo counter del numero di ipotesi necessarie che va a 0, allora si hanno nuove ipotesi.

Da notare che questo **funziona solamente per HORN CLAUSES** perché ci fa molto comodo avere un unico effetto derivato da una serie di di ipotesi in AND iniziali.

- Algoritmo

    <img src="/images/notes/image/universita/ex-notion/Agente Logico/Untitled 4.png" alt="image/universita/ex-notion/Agente Logico/Untitled 4">


## Agente logico

### Frame problem

## Conclusione

### Creazione di Plan con SAT solvers

### Incapacità della logica proposizionale col tempo

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
### Frame problem

## Conclusione

### Creazione di Plan con SAT solvers

### Incapacità della logica proposizionale col tempo

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |