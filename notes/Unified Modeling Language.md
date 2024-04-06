---
layout: page
permalink: notes/unified-modeling-language
tags: italian
title: Unified Modeling Language
---

#### Cosa è
**UML** è un linguaggio di modelling (molto vecchio) ma ancora di continua evoluzione, da 
un punto di vista storico è nato insieme ai concetti di **Object Oriented Programming** che ora è molto presente all'interno dell'industria, descritto bene in [Classi OOP](/notes/classi-oop), anche se in questa occasione sviluppata in maniera molto più intuitiva (grafica).
#### Perché serve 🟩
Per cercare di **comunicare** quanto necessario riguardo struttura e dinamicità dell'architettura.

### Struttura di UML
#### Structural Diagram 🟨++
These diagrams focus on representing the **static structure of a system**. They help depict the components, classes, objects, and their relationships in a system. Some common structural diagrams in UML include:
- Class Diagram: Shows the classes in a system and their relationships, attributes, and methods.
- Object Diagram: Represents instances of classes and their relationships at a specific point in time.
- Component Diagram: Illustrates the physical components of a system and their dependencies.
- Package Diagram: Organizes classes and other elements into packages to show their relationships.

#### Behavioral diagrams (4) 🟩--
These diagrams focus on illustrating the **dynamic aspects of a system**, including how it behaves and interacts over time. They are used to model the interactions between objects, the flow of control, and the system's behavior. Common behavioral diagrams in UML include:
- Use Case Diagram: Depicts the interactions between actors (users or external systems) and the system to achieve specific goals or functions.
- Sequence Diagram: Shows the chronological sequence of messages exchanged between objects over time.
- Statechart Diagram: Represents the various states an object or system can be in and how it transitions between those states.
- Activity Diagram: Describes the flow of activities or processes within a system.

### Main relationships
Queste sono anche chiamate le freccie, ossia le **tipologie di relazioni** che possono esistere fra entità diverse.

#### Le relazioni esistenti
1. **Association:** An association is a basic relationship that represents a link between two or more classes or objects. It indicates that instances of one class are related to instances of another class. In a graph context, you can think of associations as edges connecting nodes in a graph. Associations can have multiplicities to specify how many instances are involved in the relationship (e.g., one-to-one, one-to-many).
2. **Aggregation:** Aggregation is a specialized form of association that represents a *whole-part relationship*. It indicates that one class (the whole) is composed of or contains instances of another class (the part). In a graph, aggregation can be seen as a hierarchical relationship, where nodes at one level represent composite objects made up of nodes at another level.
	Esempio di aggregazione:
	<img src="/images/notes/Unified Modeling Language-1696933376777.jpeg" alt="Unified Modeling Language-1696933376777">

3. **Composition:** Composition is a stronger form of aggregation, indicating a strict ownership relationship. It means that the whole class has exclusive responsibility for the existence and lifetime of its parts. In a graph, composition is similar to aggregation but with a stronger emphasis on the containment of parts within the whole.<img src="/images/notes/Unified Modeling Language-1696933472558.jpeg" alt="Unified Modeling Language-1696933472558">
4. **Inheritance (Generalization):** Inheritance, represented by a *solid arrow with an open triangle*, signifies an "is-a" relationship. It is used to model the inheritance hierarchy in object-oriented programming, where one class (the subclass or derived class) inherits attributes and methods from another class (the superclass or base class). In graph terms, it represents a **hierarchy**, with edges pointing from subclasses to their superclass.
5. **Realization (Interface Implementation):** Realization is used to show that a class or component implements a specific interface or fulfills a particular contract. It indicates a relationship between a classifier and an interface. In graph theory, this can be seen as a form of dependency or connection between nodes representing classes and interfaces.
6. **Dependency:** Dependency is a relationship that indicates that *one element relies on another element*. It can be used to represent various forms of relationships, such as method dependencies, parameter dependencies, or simple associations between classes. In a graph, dependencies are akin to edges indicating connections or reliance between nodes.

## Structural diagrams
### Class diagrams
Descrivo in che modo le varia classi sono relazionati fra di loro (ad esempi con l'albero di ereditarietà)


## Types of behavioral diagrams (5)

### Use cases (!) 🟨+

#### Structure of use case diagrams

> A use case is a concept in software engineering and system design that describes a specific **interaction or set of interactions** between a *system* (usually software) and its *external actors*

1. **Goal-Oriented:** Use cases are centered around achieving specific goals or objectives. Each use case represents a particular task, process, or scenario that an external actor wants to accomplish using the system.
2. **Actor:** An actor is any external entity that interacts with the system. Actors can be users, other software systems, hardware devices, or any external entity that initiates a use case. Actors are defined based on their roles and responsibilities in the system.
3. **Flow of Events:** A use case typically includes a description of the *main flow of events*, which outlines the steps or interactions involved in achieving the desired goal. It can also include alternative or exceptional flows to cover various scenarios.
4. **Preconditions and Post-conditions:** Use cases may specify conditions that must be met before the use case can be initiated (preconditions) and the state of the system after the use case has been successfully completed (post-conditions). (ossia ciò che abbiamo bisogno, e ciò per rendere deterministico questo processo).

Quindi è utilizzato per modellare in che modo *chi usa* dovrebbe interagire con il nostro sistema, e ciò che il nostro sistema ha bisogno per funzionare.

Esempio:
<img src="/images/notes/Unified Modeling Language-1697540836732.jpeg" alt="Unified Modeling Language-1697540836732">

#### More on actors

#### Use case modelling and diagrams 🟥
1. **Use Case Diagrams:** Use cases are often visualized using diagrams called use case diagrams. These diagrams *show the relationships between actors and use cases*, helping to provide a high-level overview of the system's functionality.
2. **Use Case Modeling:** Use case modeling is a technique used during the early stages of system design to identify and define the various use cases that the system will support. It helps in understanding and documenting user requirements and system behavior.
### State-chart diagrams

#### Notazione sugli stati (4) 🟨+
<img src="/images/notes/Unified Modeling Language-1697538887281.jpeg" alt="Unified Modeling Language-1697538887281">
#### Notazione delle transizioni 🟩-
In modo simile agli automi a stato finito, definisco gli stati (in questo caso aggiungo anche una semantica per gli stati, e poi una possibile transizione all'interno di quelli).
<img src="/images/notes/Unified Modeling Language-1697538824092.jpeg" alt="Unified Modeling Language-1697538824092">

#### Perché utilizzare state-chart 🟩
- Descrizione di **cambi di stato**, in modo a simile a quanto si farebbe per automata per esempio.
- Descrizione di **campi statici** presenti negli oggetti per esempio.
È contrapposto con gli **interaction diagrams** che racconta in che modo cose differenti comunicano fra di loro, questo state-chart è utilizzato per definire in modo statico se succede cosa, cosa cambia.

#### Esempi di state diagrams
<img src="/images/notes/Unified Modeling Language-1697537984771.jpeg" alt="Unified Modeling Language-1697537984771">
In pratica è un grafico più rilassato di Deterministic Finite Automata [Grammatiche Regolari](/notes/grammatiche-regolari)

Si può usare anche in modo innestato come in seguito
<img src="/images/notes/Unified Modeling Language-1697538082674.jpeg" alt="Unified Modeling Language-1697538082674">

### Activity diagrams
#### Cosa descrivono le activity diagrams 🟩
- **Workflows**, ossia in che modo il sistema agisce, ad alto livello per poter a
- **Parallelizzazione**, se devono essere eseguite più cose allo stesso tempo, è molto comodo.
- **Sincronizzazione**, quindi anche per logica con async ha senso

<img src="/images/notes/Unified Modeling Language-1697537692099.jpeg" alt="Unified Modeling Language-1697537692099">


### Sequence diagrams

**Interaction diagrams**
Cercano di modellare in che **modo comunicano** fra l'uno e l'altro, serve per fare cose complesse
Un esempio sono i sequence diagrams
#### Perché sequence diagrams? 🟩
>Shows object interactions **arranged in time sequence**

Un esempio di utilizzo comune è per i **protocolli**, dato che il tempo è importante è molto facile comunicare esattamente cosa viene scambiato.
Quindi utile per rappresentare in che modo chi chiama cosa **nel tempo**.
<img src="/images/notes/Unified Modeling Language-1697537346445.jpeg" alt="Unified Modeling Language-1697537346445">

Altro esempio, un po' più complesso
<img src="/images/notes/Unified Modeling Language-1697538337917.jpeg" alt="Unified Modeling Language-1697538337917">
#### Descrizione della struttura 🟩
In alto abbiamo degli **oggetti** oppure degli agenti differenti, poi col tempo questi oggetti diversi scambiano messaggi, in questo caso è **chiara sequenza dei messaggi**, che è il vantaggio principale di questi diagrammi.

- Asincroni
- Sincroni
- Non bloccanti, esattamente gli stessi che abbiamo visto in sistemi

### Collaboration diagrams
#### Descrizione collaboration diagrams 🟩
Uguale ai sequence diagrams, ma esprime **messaggi possibili** fra una classe e una altra e *non esprime il tempo* durante una singola comunicazione.

Un altro aspetto è che la **sequenza dei messaggi è identificata da numeri**

#### Confronto con i diagrammi di sequenza 🟩
- Facile vedere **messaggi che vengono scambiati** da enti differenti, quindi organizzazioni diciamo.
- Si perde però **informazione sul tempo**

Per il resto è molto simile rispetto ai [#Sequence diagrams](#sequence-diagrams) perché anche in questo caso si scambiano messaggi, solo che non è ben definito il tempo. (viene *marcato con un numerino*).

Un esempio:
<img src="/images/notes/Unified Modeling Language-1697538360271.jpeg" alt="Unified Modeling Language-1697538360271">




# References