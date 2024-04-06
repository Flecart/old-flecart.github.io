---
layout: page
permalink: notes/design-del-database
tags: en
title: Design del database
---

### Processo design del database

#### Il design

#### Some design steps (3) (non impo)

##### How to gather requirements? 🟨+
Come si può raccogliere i dati degli utilizzatori?
- parlare col il personale che dovrà utilizzare questi sistemi
- Documentazione esistente
- Interview di persone che dovrà utilizzare queste risorse
- O Moduli per fare sampling

##### Top-down approach
La cosa brutta è che questi requisiti non possono essere standardizzati, ci sono molte necessità, molto diverse fra i loro, quindi è utile andare a parlare con gli esperti e capire cosa abbiano bisogno per i dati.
Consiglio del prof. è partire dai senior e poi scendere, perché quelli in alto hanno un punto di vista *più ampio ma con meno dettagli* diciamo.

##### How to ask the requirements
È molto facile non capire un interlocutore, basta usare il gergo specifico di quell'ambito. Anche i maranza per esempio hanno il proprio gergo che non è comprensibile.
Bisogna chiedere cosa hai bisogno, secondo le necessità soprattutto! Esempi possono semplificare un sacco.
Una cosa molto importante è **mantenere il linguaggio semplice** e fare le domande giuste (dividere le domande funzionali con le domande di dati utili da memorizzare).
È difficile sapere cosa è importante mantenere per una istituzione. Solitamente se usano un gergo specifico è bene provare a comprendere cosa significhi la parola specifica. Un bias comune è che le persone tendono a parlare di problemi recenti, che non potrebbero riflettere le necessità a lungo termine per i dati.

Un **glossario** dei termini è molto importante per stabilire il significato in quel contesto.

##### How to create entities and relations? (4)
<img src="/images/notes/Design del database-1699532722803.jpeg" alt="Design del database-1699532722803">
##### Storicizzazione (!)
Può essere fatta in due modi, o con due relazioni, oppure con una generalizzazione.

### Metodi di modellazione

#### Top down 🟩
Parto dai requisiti e provo a raffinarli passo passo fino ad avere uno schema finale
<img src="/images/notes/Design del database-1699533321514.jpeg" alt="Design del database-1699533321514">
#### Bottom up 🟩
Parto dalle specifiche e costruisco i singoli componenti fino ad arrivare a schemi collegati assieme
<img src="/images/notes/Design del database-1699533308444.jpeg" alt="Design del database-1699533308444">
#### Inside out 🟩
Parto da un requisito chiaro, che costruisco e poi inizio a costruire gli altri secondo quando bene ho capito sono relazionati.
	
<img src="/images/notes/Design del database-1699533371441.jpeg" alt="Design del database-1699533371441">

##### Steps per design concettuale
Per il prof. si può passare al design logico subito se si è molto bravi, però il suo consiglio è sempre partire da alto livello e poi andare a definire tutte le relazioni.
<img src="/images/notes/Design del database-1700046625648.jpeg" alt="Design del database-1700046625648">
## Entity-Relationship model

### Introduction to modeling phases

#### The conceptual modelling phase 🟩
It's a **data representation** is *independent* from the system, but it's useful to show how are the different entities connected to each other.

Questa è la prima fase del processo di design di un database, nasce principalmente da una inefficacy of the relational structure (too much information), quindi si vuole usare come via di alto livello per analizzare la struttura!
- Visual documentation that is useful for docs.

#### Other modelling phases (2) 🟩
Logico, ne parliamo in [Database logical design](/notes/database-logical-design) e poi il fisico non viene trattato in questo corso, e dovrebbe essere bene astratto.

### Entity

#### Definition of entity 🟩
An **entity** represents a *class of "objects" sharing common properties, but still having an autonomous existence*.
It is clearly heavily linked to the concept of object in OOP (see [Classi OOP](/notes/classi-oop)), that is the framework where the ER model was born.

#### Entity identifier, internal 🟩
NOTA: queste non sono chiavi! Si chiamano in modo diverso!
It could be an **internal identifier** formed by the attributes of the single relationship, or external if it is identified by some kind of relationship.
<img src="/images/notes/Design del database-1698926495504.jpeg" alt="Design del database-1698926495504">

#### External identifier 🟩
<img src="/images/notes/Design del database-1698926478009.jpeg" alt="Design del database-1698926478009">
#### Generalization and specialization 🟩
One entity $$E$$ could be composed by many components $$E_{1}, E_{2}, \dots E_{N}$$, this is a **generalization** relationship,
the inverse is a a specialization. There are also some properties to consider:
- Every property in $$E_{i}$$ is used in some way in $$E$$
- Every instance of $$E_{i}$$ is an instance of $$E$$ too.
<img src="/images/notes/Design del database-1698926764938.jpeg" alt="Design del database-1698926764938">


#### Types of generalization (2) 🟩
It could be **total**/**partial** or **disjoint**/**Overlapped**.
It is total if the parent is totally composed by the child entities, otherwise it's partial.
A total relationship has a full arrow, while a partial has an outlined arrow as pointer.

It is disjoint if the children doesn't have anything in common (property-wise) and overlapped otherwise.

#### Data dictionary (3) 🟩
The data dictionary is a quick way to represent the conceptual model, some examples are given down there.
There are also some **non-expressible constraints** that in the example is not reported, but are the cardinality or other types of constraints that the model has.
<img src="/images/notes/Design del database-1698927106733.jpeg" alt="Design del database-1698927106733">
<img src="/images/notes/Design del database-1698927097783.jpeg" alt="Design del database-1698927097783">

### Relationships
#### Definition of relationships 🟩
A **relationship** is a *connection* between two or more entity types.
Usually is given a name to the relationship, that summarizes his **semantic** meaning.
Singular nouns are preferred.

Example of relationship:
![ 500](/notes/design-del-database-1698924834575.jpeg-)

#### Arity of relationship 🟩
A relationship is not limited to connect two entity types, it can connect more, and this value defines the arity of the relationship.
In each case the relationship is represented as a **tuple**, that is **unique**, meaning that more instances of the same type could not exist: You can't have the same tuple within the relationship.

#### Relationship promotion to entity 🟩
Sometimes a relationship is not enough to model some constraints, in these cases it is useful to use an entity instead.

Example:
<img src="/images/notes/Design del database-1698925199874.jpeg" alt="Design del database-1698925199874">
#### Cardinality of relationship 🟩--
This is different from the arity. It's a constraint that defines the *minimum and maximum* value that a relationship can have.
There is a convention to use $$N$$ if we don't have an upper limit

<img src="/images/notes/Design del database-1698925934115.jpeg" alt="Design del database-1698925934115">


#### Types of relationship cardinality (3) 🟩
The classical classification is
- Many-to-many
- One to many
- 1 to 1

It's clear what they mean, it's a cardinality relation, for example current_spouse relationship is a 1-1 in the modern society, schools frequented could be one to many, the exams taken by a student in the course entity is a many to many.


### Attributes
#### Definition of attributes 🟩
> Sono **proprietà** o di entità o associazioni, che assumono valori da un certo **dominio**

#### Composite attributes 🟩
They are used to **group together** different attributes to the same class or relationship. This is useful if different attributes share the same semantic meaning.

In the example in the image it's the address.
<img src="/images/notes/Design del database-1698925756436.jpeg" alt="Design del database-1698925756436">
#### Cardinality of attributes 🟩
It is possible to define a cardinality for single attributes, because an employee could have more phone numbers, or the driving licence is optional (not everybody has it!)

<img src="/images/notes/Design del database-1698926543311.jpeg" width="400" alt="Design del database-1698926543311">



# References