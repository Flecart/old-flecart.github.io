---
layout: page
permalink: notes/design-patterns
tags: italian
title: Design patterns
---

### Introduction to design patterns

#### Introduzione personale 🟩
I design patterns sono simili a dei *plug and play*, ossia delle **soluzioni che hanno funzionato bene** in passato e che sono ora riutilizzati.
Solitamente dovrebbe essere una **abilità implicita**, cioè un buon programmatore è in grado di fare senza pensarci, dovrebbe essere automatico. Infatti quando uno fa il design non lo fa esplitamente seguendo un certo modello, ma farlo solitamente risulta utile per guidare il processo.

#### Definizione design pattern 🟨++
> Descriptions of communicating objects and classes that are customized to solve a general design problem in a particular context

> A Pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice

### Common OO patterns

#### Singleton 🟩
Questa la sai. Provi a ritornare un oggetto già inizializzato che vive per tutto il tempo del tuo programma. È il singoletto, qualcosa che esiste solamente una volta.
Un pattern solito con questo è il check dell'esistenza del valore statico, e il **getter di istanza**.

#### Composite 🟩

In pratica è un **albero** in cui **solamente le foglie sono operazioni**.
è stato utilizzato nelle slides per modellizzare un oggetto **composto** che deve semplicemente eseguire il codice dei figli (quindi diciamo un qualcosa di mezzo per poter dare in modo chiaro l'operazione corretta).

<img src="/images/notes/Design patterns-1698181120455.jpeg" alt="Design patterns-1698181120455">

#### Iterator pattern 🟨++
Viene utilizzato per **scorrere** qualcosa di generico, in C++ per esempio è utilizzato in moltissime librerie standard. in Python è possibile definire due metodi `__next__` e `__iter__` e anche in rust è molto molto usato questo pattern. 

<img src="/images/notes/Design patterns-1698181226541.jpeg" alt="Design patterns-1698181226541">

### Creational

#### Perché creational? (2) 🟩--
Sono i pattern utilizzati per creare nuovi oggetti in modo sostenibile.
- Astrarre la creazione del singolo oggetto
- Incapsulamento, quindi voglio limitare l'accesso a informazione a solamente certi metodi ben definiti.

#### Builder 🟨+
[https://refactoring.guru/design-patterns/builder](https://refactoring.guru/design-patterns/builder)

In questo caso abbiamo un **director** che in pratica orchestra la costruzione dei componenti reali.
E singole componenti in cui sono specificati esattamente cosa fare.
È utile soprattutto quando ho qualcosa di molto complesso da costruire, che può cambiare in molti modi.
Un esempio è il build di Zig credo.

<img src="/images/notes/Design patterns-1698181474071.jpeg" alt="Design patterns-1698181474071">

#### Abstract factory 🟩--
[https://refactoring.guru/design-patterns/abstract-factory](https://refactoring.guru/design-patterns/abstract-factory)

Serve soprattutto come **interfaccia comune** per andare a creare qualcosa di concreto (nel nostro caso una factory concreta).
Ricorda l'esempio di sedia, tavoli, e stili diversi! 
Avere l'abstract factory ti permette di utilizzare la stessa interfaccia, quando nel concreto puoi produrre cose diverse. (dal punto di vista del cliente è sempre la stessa cosa).

<img src="/images/notes/Design patterns-1698181758178.jpeg" alt="Design patterns-1698181758178">

#### Factory Method 🟩
[https://refactoring.guru/design-patterns/factory-method](https://refactoring.guru/design-patterns/factory-method)

Da un punto di vista intuitivo, questo è solamente quando si utilizzano le classi virtuali.
In C++ li abbiamo usati, vengono utili soprattutto quando la stessa funzione viene chiamata, la semantica è uguale, ma l'implementazione cambia a seconda del tizio che la vuole usare tipo.
Un esempio è la funzione attacco dei mostri, che possono attaccare in molti modi, ma quello che vogliono fare è attaccare.


<img src="/images/notes/Design patterns-1698182346876.jpeg" alt="Design patterns-1698182346876">

#### Prototype

### Structural

Sono utilizzati come **interfacce** utili per far funzionare delle cose assieme.
#### Adapter and Bridge
Adapter viene utilizzato per problemi di nome, bridge per **nascondere l'interfaccia**
<img src="/images/notes/Design patterns-1699958186148.jpeg" alt="Design patterns-1699958186148">
<img src="/images/notes/Design patterns-1699958196691.jpeg" alt="Design patterns-1699958196691">

#### Decorators
Sono delle funzioni che ritornano altre funzioni con delle **funzionalità aggiunte** (e sono comode) se lo hai visto in python o JS lo conosci senza problemi. Per linguaggi statici tipo C è più difficile da mettere.

#### Proxy pattern
Invece di accedere qualcosa in modo diretto usiamo una altra classe od oggetto che si occupa di **controllare l'accesso**, un esempio guardare i permessi, controllare altro, fare log o simili...
<img src="/images/notes/Design patterns-1699958735041.jpeg" alt="Design patterns-1699958735041">

### Behavioural
I patter comportamentali definiscono quali sono le **classi di responsabilità** per una classe e una altra, e gli *algoritmi* da utilizzare.


#### Visitor
È tipo una visita dfs, bfs, prende informazioni in modo strutturato **senza cambiarne la struttura**.
<img src="/images/notes/Design patterns-1699959417127.jpeg" alt="Design patterns-1699959417127">

#### Strategy
È un pattern che specialmente per librerie di python si vede spessissimo, si utilizza un identificatore e un dispatcher all'algoritmo corretto.
<img src="/images/notes/Design patterns-1699959627562.jpeg" alt="Design patterns-1699959627562">
#### Chain of responsibility
È una suddivisione di classi di responsabilità, come se fosse una catena di montaggio.
Una cosa comune è l'albero, e il responsabile diretto è il suo parente, che magari deve gestire altro, non lo so.
Se in un certo punto un check fallisce, la cosa non continua, ma viene cestinata.

<img src="/images/notes/Design patterns-1699959712333.jpeg" alt="Design patterns-1699959712333">


#### Mediator
Mi sembra simile alla reificazione che abbiamo studiato per la prima volta (in logica un po' ma di più in) [Design del database](/notes/design-del-database). ossia invece di avere $$N^{2}$$ collegamenti, basta avere un punto intermedio di comunicazione e abbassi di una potenza. È la potenza del mediatore.

<img src="/images/notes/Design patterns-1699960130989.jpeg" alt="Design patterns-1699960130989">

## Note di ripasso
Devi avere in mente le note principali e un esempio concreto di ogni metodo.

| Data | Commenti |
| ---- | -------- |
|      |          |