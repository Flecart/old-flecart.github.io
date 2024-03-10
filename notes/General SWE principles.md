---
layout: page
permalink: notes/general-swe-principles
tags: italian
title: General SWE principles
---

This small note sections tries to fix 5 important concepts in software engineering

### Sub-system and modules 🟩
We need to differentiate from sub-system, which is a part of a system that tries to achieve some objective, and a **module**, which is more *language specific* way of saying imported file, or set of functions or classes.

### Information hiding 🟩
This is a very important principle present in Classi OOP |object oriented programming|Classi OOP |object oriented programming.
Within this philosophy we should **be able to access only public** methods or data, this allows the construction of *abstractions* that allow us to think at a higher level.

A good think about this is that **changing implementation** *doesn't* change the interface, this allows lower level of coupling within the system.


### Coupling
#### Meaning of coupling 🟩
Two methods are said to be highly coupled when every change to one of them, needs the other one to be changed too!
Clearly if we have a highly coupled system refactoring is a hell of a nightmare.
**Low coupling** provides **independency**, creating a easier to maintain software.

#### Coupling sources (7) 🟩
There are many coupling sources, here is a not definitive list:
- Function or method calling
- Data coupling, for example the prop drilling hell present in react, where you have to pass other data to other data on an indefinite chain.
- Hereditary coupling, where you have too long chain of sub-classes.
- OS-coupling, where you don't have an equivalent function for other OSes
- Common coupling:, e.g. global variables, config files, that are used by many files.
- Content coupling: happens when the #Information hiding is not implemented, an other module directly sees internal data-structure of another module, implying a very bad implementation!.


### Cohesion 🟩

Cohesion is a concept that similarly to Memoria#4.2 Memoria Cache, with the location principle, common functions should be grouped together, the best thing that could happen is the **functional cohesion**, where code that tries to implement the same abstraction tries to be together, another one is **content cohesion**, where code that needs same input structure is close.

A bad example is random ordering, where code with no shared meaning stays together.

### Simplicity 🟩
This is also one of the main pillars of Software engineering.
In this case it is advised not to generalize too early, probably You aren't gonna need it.

When we are talking about methods instead, you should follow the principles explained in [clean code](https://dl.acm.org/doi/10.5555/1388398), so keep the names descriptive, keep the public methods small and precise, use small functions, and keep code smell low (avoid duplicates for example).



## Note di ripasso

| Data | Commenti |
| ---- | -------- |
|10/21/2023      |Molto generale, va bene, questo modulo non è che contenga molte informazioni interessanti          |
|11/14/2023 | Questo alla fine non mi sembra per niente importante, se leggo le parole chiave riesco a motivarti a voce o per iscritto perché sarebbero importanti, però non da sapere a memoria diciamo...|
|12/06/2023 | Non c'è molto da guardare direi su questo, quindi tolgo le note |