---
layout: page
permalink: notes/python-and-java-notes
tags: italian
title: Python and java notes
---

#### Referential immutability/transparency
In python alcuni valori classici sono immutabili e le variabili assumono solamente una reference ad essa.
In versioni vecchie del compilatore venivano allocati interi oggetti per questi, perché dal punto di vista della semantica denotazionale è la stessa. Quella operazionale (quindi esattamente come gestire questo assegnamento) è diverso.
Questo è l'aspetto funzionale del linguaggio.


#### Inner and nested classes
Servono per nascondere alcune funzioni all'esterno e raccoglierle assieme per un utilizzo.
- Each instance has an enclosing instance, and can use its members
- Inner classes cannot have static members
- Inner classes cannot have the same name as the enclosing class
- If an inner class is a local class (see later), it has access to the members of the enclosing class, final local variables and parameters
- Inner classes can also be anonymous classes (see later), i.e., unnamed classes defined within an expression They are similar to local classes but can have only one instance
#### Local classes
Local classes are very useful when we need code and data structures to perform specific tasks inside a function, but we don’t want to make them available to the outside world

#### Interfacce
- Scopo delle interfacce
- Differenza con oggetti e classi.

#### Anonymous classes
Sono delle classi senza nome, solitamente classi locali, che però vengono **utilizzate una singola volta **