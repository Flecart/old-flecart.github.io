---
layout: page
permalink: notes/system-design
tags: italian
title: System Design
---

NOTA: tolgo dalle note perché non mi sembra importante.
### Introduction to system design
#### Packages vs diagrams 🟩-
- Packages **fisica implementazione**, perché è una cosa utile per lo sviluppo
- Diagrams **logica visualizzazione** perché aiuta solamente a comprendere meglio come funziona il sistema in toto.

### Components

#### What is a component (3) 🟨
È una **entità totalmente indipendente** che funziona a sé, un esempio è il *dll, dynamically loaded libraries* presente nei sistemi di windows.
Una cosa è che **espongono interfacce** per interagirci, e questi possono essere utilizzati per creare sistemi complessi.

Quindi riassumendo:
1. Indipendenza da altri software (almeno è contenuto)
2. Presenza di interfacce per interagirci
3. Risolvono un certo problema specifico (appunto isolato)

Se ho questo allora posso **rappresentare la struttura in esecuzione** con i diagrammi di sopra, a seconda di come li carico scarico e simili.


#### Difference with collaboration diagrams 🟥+
nel nostro caso è una **dipendenza esterna** non è una estensione ereditaria come potrebbe sembrare se lo analizziamo come class diagram.

Ci permette lo stesso di creare diagrammi che rappresentano in che modo i singoli oggetti comunicano con altri.

<img src="/images/notes/Unified Modeling Language-1697541168878.jpeg" alt="Unified Modeling Language-1697541168878">
#### Stereotypes 🟥
Capire un po' meglio questa parte.

<img src="/images/notes/Unified Modeling Language-1697541340381.jpeg" alt="Unified Modeling Language-1697541340381">

### Node
#### What is a node 🟩
Sono una **risorsa computazionale**, quindi con CPU e memoria per poter eseguire qualcosa.
Un esempio sono micro-controllori per temperatura, smart-home e simili. Questo è qualcosa di base se vogliamo andare ad analizzare cose come sistemi distribuiti e nodi di computazione in quel punto.

<img src="/images/notes/Unified Modeling Language-1697541598371.jpeg" alt="Unified Modeling Language-1697541598371">

#### Difference with components (1) 🟩
I componenti rappresentano **il pacchetto logico** per una esecuzione, quindi sono più strutturali, astratti, rappresentano **in che modo esegue** un certo sistema.
Mentre i nodi sono **rappresentazione fisica esecuzione**, in cui effettivamente eseguono qualcosa, prima solo per rappresentarlo, quindi **deployment** di ciò

### Real Time UML
Una delle caratteristiche fondamentali dei real time è che hanno **garanzia di esecuzione entro tot tempo**, questa è una cosa anche indagata per gli schedulers, vedi [Scheduler#SISTEMI A REALTIME (non fare)](/notes/scheduler#sistemi-a-realtime-(non-fare))

#### Time events (3) 🟨
- **Change event**: rappresentano il momento in cui una azione è avvenuta e quindi probabilmente deve essere gestito un cambio di stato in questo caso.
- **Time Event**: descrivono *quanto* deve essere fatto un evento, per esempio
	- Fra 5 minuti
	- alle 12 P.M.
- **Timing costraints** entro quanto tempo deve essere fatto (o ogni quanto).
	- Solo che manca un linguaggio per esprimere questi constraints.

Esempio:
<img src="/images/notes/Unified Modeling Language-1697541728317.jpeg" alt="Unified Modeling Language-1697541728317">

### Object Contraint Language
#### Introduzione a OCL🟥
è un **linguaggio di modellazione** utilizzato per modellare in modo *non ambiguo* tutte le **pre e post condizioni** per un linguaggio.
È un **linguaggio puro**. Secondo Succi è utile quando facciamo i test durante il progetto.



# References