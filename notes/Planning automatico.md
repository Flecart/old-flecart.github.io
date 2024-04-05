---
layout: page
permalink: notes/planning-automatico
tags: en
title: Planning automatico
---

Ultima modifica: December 29, 2022 3:24 PM
Primo Abbozzo: August 14, 2022 4:14 PM
Stato: 🌑🌑🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

# Planning Automatico

Vogliamo andare a creare un programma che sia in grado di creare un piano per fare una azione, andiamo in questo capitolo gli algoritmi storicamente migliori adatti a risolvere questo problema

## Il problema di pianificazione

Andiamo a rappresentare il nostro problema di pianificazione con un linguaggio molto simile alla [Logica del Primo ordine](/notes/logica-del-primo-ordine).

È il PDDL ossia il **Planning domain definition language**

### PDDL

Questo linguaggio è definito da

1. Una serie di predicati in FOL iniziali
2. Una serie di predicati in FOL di arrivo
3. Una serie di azioni
    1. Con una serie di precondizioni
    2. E una serie di effetti



Il nostro obiettivo sarà principalmente raggiungere un obiettivo finale, utilizzando le azioni per cambiare lo stato attuale

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Planning automatico/Untitled.png" alt="image/universita/ex-notion/Planning automatico/Untitled">

    In cui si può notare che una soluzione di questo problema è molto semplice:

    <img src="/images/notes/image/universita/ex-notion/Planning automatico/Untitled 1.png" alt="image/universita/ex-notion/Planning automatico/Untitled 1">


## Algoritmi generali

Gli algoritmi principali per risolvere la PDDL sono di due tipologie

1. **Forward search**
2. **Backward search**

Entrambe dovrebbero avere delle euristiche molto forti per funzionare in un ambiente reale. (nota: essendo questa poi una rappresentazione fattorizzata del mondo, si possono creare delle euristiche indipendenti dal dominio molto forti!).

**Sulla soddisfacibilità booleana**

Si può anche trasformare il problema di pianificazione in un problema di logica proposizionale da dare in pasto ad un sat solver. Con lo stato attuale dei sat solver questo potrebbe anche essere considerato una soluzione possibile interessante.

**Altri metodi da almeno tenere in mente i nomi**

Planning graph

Situation calculus **praticamente sat-plan ma con la FOL

Partial ordering planning, molto figo perché ci fanno i rover per andare su marte questo 😀, è usato perché puoi vedere in modo molto chiaro il motivo per cui ha scelto questo piano.

### Backward search

Vogliamo partire dall’obiettivo, dal nostro goal, ed andare indietro fino a trovare uno stato che sia adatto allo stato iniziale.

Per fare questo vogliamo cercare azioni che siano **rilevanti**, ossia le cui precondizioni non siano assurde con quello che avremmo già. Questo aiuta moltro a diminuire il fattore di branching.

Per maggiori dettagli su come si faccia l’update dello stato andare a vedere sul libro.

### Forward search

Praticamente andiamo a guardare tutte le soluzioni, è la stessa cosa di un [Problemi di ricerca](/notes/problemi-di-ricerca) ed è quindi facilmente attaccabile (se non per la grandezza dello spazio di ricerca) dagli algoritmi lì studiati. Il più importante dei quali resta sempre A* con una buona euristica.

###