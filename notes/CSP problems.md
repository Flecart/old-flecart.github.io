---
layout: page
permalink: notes/csp-problems
tags: italian
title: CSP problems
---

Ripasso Prox: 5
Ultima modifica: December 29, 2022 3:24 PM
Primo Abbozzo: July 11, 2022 11:15 AM
Stato: 🌕🌕🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

- Non ti ricordi le tecniche di backtracking belle per avere un buon CSP.

# 3 CSP Problems

Costraint Satisfaction Problems.

## Definizione

### Caratteristiche

1. **Variabili**
2. **Dominio** per ogni variabile
3. **Costraints** per ogni variabile

Queste tre sono elementi che definiscono un problema di soddisfazione delle restrizioni, una soluzione è un assegnamento di variabili che **soddisfi** ogni restrizioone e sia all’interno del dominio

## Consistenza

Vogliamo andare a limitare il dominio valutando le consistenze possibili

### Consistenza del punto

Si può dire che un punto sia consistente se le sue variabili possibili non viola nessuna restrizione unaria: eg. se ho N e ho la restrizione n ≥ 0, allora avere tutto N è inconsistente nel punto.

### Consistenza ad arco

Questo tratta delle restrizioni binarie: una coppia di punti si dice che è arco consistente se per ogni variabile nel primo dominio esiste sempre una variabile nel secondo dominio che mi soddisfa la restrizione.

### k-consistenze

Si può estendere il concetto della consistenza per avere un numero arbitrario di nodi, questo dovrebbe causa però un costo del calcolo molto maggiore.

### AC-3 algorithm

Questo è un algoritmo per forzare la consistenza ad arco, praticamente va di **forza bruta** a imporre la consistenza su un arco, se i domini vengono aggiornati gli archi vicini vengono rimessi in coda, in modo da essere sicuri che restino ancora consistenti (infatti eliminando certe variabili potrebbero aver perso di consistenza)

<img src="/images/notes/image/universita/ex-notion/CSP problems/Untitled.png" alt="image/universita/ex-notion/CSP problems/Untitled">

## La ricerca di una soluzione

### Backtracking

<img src="/images/notes/image/universita/ex-notion/CSP problems/Untitled 1.png" alt="image/universita/ex-notion/CSP problems/Untitled 1">

### Euristiche della scelta dei valori

**Minimum remaining Values**

vorremmo che la ricerca della variabile non assegnata fallisca il prima possibile, quindi scegliamo la variabile con più vincoli, o meno valori assegnabili.

**Least  constraining value**

Se vogliamo una unica soluzione che soddisfa vogliamo scegliere variabili che hanno meno probabilità di fallire.

**Forward check**

Abbastanza simile ad AC-3, toglie dei valori che non possono esserci??? boh cose simili.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
lità di fallire.

**Forward check**

Abbastanza simile ad AC-3, toglie dei valori che non possono esserci??? boh cose simili.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |