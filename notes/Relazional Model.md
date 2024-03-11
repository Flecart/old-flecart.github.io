---
layout: page
permalink: notes/relazional-model
tags: italian
title: Relazional Model
---

This is the classical format that we encounter, it is the format used for relational databases introduced in [databases course introduction](/notes/introduction-to-data-bases), introduced in @coddRelationalModelData1970. 

### Introduzione, i modelli di dati
#### Lista modelli di dati (4)
Nel tempo sono stati sviluppati molti modelli di dati:
1. **Relational Data Model:** This is the most common data model and uses tables to represent data. It organizes data into rows and columns, where each row represents a record, and each column represents an attribute of that record. Relationships between data are established through keys.
    
2. **Entity-Relationship Model:** This model focuses on the relationships between entities, which are objects or concepts, and how they relate to each other. It is often used in the design of databases.
    
3. **NoSQL Data Model:** NoSQL databases use various data models, such as document, key-value, column-family, or graph, to store and manage data. These models offer more flexibility than the traditional relational model.
    
4. **Hierarchical and Network Data Models:** These older models organize data in a tree or graph structure, which was common in early database systems.

In questa sezione andiamo ad analizzare il primo. (anche perché quello storicamente più rilevante, e ancora (tristemente) più utilizzato).

Altri modelli come reticolare e gerarchico erano famosi all'inizio, ma si è scelto di andare sul modello relazionale col tempo

#### Vantaggi relazionale 
1. @coddRelationalModelData1970 è stato un contributo fondamentale, la separazione fra layer logico e fisico è stato proprio necessario per fare questi modelli
2. Rappresenta solamente ciò che è importante
3. Semplicità del passaggio per valori.


## Il modello relazionale
We can represent each row of a table as a **partial function**, in the domain of the headers,
### Domini e attributi
#### Schemi e istanze di relazione e di basi di dati 🟩
Potremmo definire in maniera lasca, che una base di dati a modello relazione è un insieme di relazioni, che possono avere schemi diversi.
Ad alto livello possiamo dire che uno schema è la descrizione matematica dei domini, mentre l'istanza è una serie di dati che rispettano quello schema.
In matematichese possiamo vedere in immagine:

<img src="/images/notes/Relazional Model-1700136703747.jpeg" alt="Relazional Model-1700136703747">

#### Introduzione concetti fondamentali 🟩
In pratica abbiamo $$D_{1}, \dots D_{n}$$ **domini** a cui spesso sono associati dei nomi, chiamati **attributi** che spiegano l'interpretazione di questo dominio, che vengono rappresentati come gli *headers* o nomi delle colonne.
Un campione di questo dataset non è altro che un cittadino nell'insieme $$D_{1} \times \dots \times D_{n}$$, in cui non importa né l'ordine dei singoli elementi all'interno della tupla, ma non importa per gli elementi fra una tupla e una altra.

Nel caso in cui la posizione degli attributi non è importante (quindi posso mischiare una colonna a una altra) si dice che il database è **non-posizionale**
![ 350](/notes/modello-relazionale-1695508072434.jpeg-)
Le due colonne scambiate non ci fanno differenza dal punto di vista logico.

#### Schemi matematici o relazionali 🟩
In matematica la tupla ha un uso posizionale, nel senso che la posizione al suo interno è importante, mentre noi abbiamo *dati omogenei* per questo motivo definiamo che le tuple sono identificate da **attributi** diversi fra di loro.
Gli attributi sono delle funzioni che mappano a un dominio (es. stringhe, numeri o simili). 

$$
dom: X \to D,,,, A \in X
$$

E si può introdurre una notazione simile per le tuple $$t$$ su una certa relazione, che permette di prendere il valore di quella tupla, scegliendo una relazione specifica.

#### Condizioni necessarie per relazione (3) 🟩
1. Devono esserci tutti i dati (colonne) per ogni riga.
	- Quindi *non vengono ammesse NaN*
2. Tutte le righe sono elementi diversi (questa non la ho capita bene, perché necessariamente devono essere tutti diversi?)
	- Le tipologie di valori per colonna sono **omogenee**

3. Domain integrity, Relational Integrity

### Chiavi e vincoli
#### Keys and superkeys 🟩
**Superkeys**
Sono il *subset degli attributi* utili a identificare in modo univoco un sample.

**Candidate Keys**
Sono il subset minimo di chiavi utilizzati per identificare un record

Primary keys sono solo dei candidate keys identificati da un designer.

Possiamo proprio dare una definizione formale del concetto di chiave, come l'insieme di cardinalità minima degli attributi superchiave.

Cosa succede invece nel momento in cui includiamo la possibilità che certi valori possano essere nulli nel nostro schema? Chiaramente se una chiave diventa nulla *diventa impossibile identificare il valore* di essa! Per questo motivo dobbiamo mettere un constraint e dire che non può esserlo, in questo modo possiamo identificare in modo univoco ogni entry.


#### Foreign Key and  Referential integrity (!) 🟩
È un attributo del nostro schema che si **riferisce a una primary key esterna**.
Anche chiamato *referential integrity constraint*.

Definizione:
> fra un insieme di attributi $$X$$ di una relazione
$$R_{1}$$ e un’altra relazione $$R_{2}$$ è soddisfatto se i valori su $$X$$ di ciascuna tupla dell'istanza di $$R_{1}$$ compaiono come valori della chiave (primaria) dell’istanza di $$R_{2}$$


Se ho una foreign key, non avrebbe senso se il valore a cui si riferisce non esistesse!

#### Vincoli

I vincoli servono per imporre dei limiti tali per cui i dati abbiano un senso nel nostro dominio, possono essere di tipi specifici, come *di tupla* e in genere sono intra-relazionali, ossia non hanno bisogno di andare su altre relazioni, oppure inter-relazionali, se prendono più relazioni.

#### Database schema
> The schema of a relation refers to its logical design, while an instance of the
relation refers to its contents at a point in time. The schema of a database and
an instance of a database are similarly defined. The schema of a relation in-
cludes its attributes, and optionally the types of the attributes and constraints
on the relation such as primary and foreign key constraints.

<img src="/images/notes/Relazional Model-1698225348130.jpeg" alt="Relazional Model-1698225348130">

## Standardization
Da questa parte trattiamo meglio quando parliamo di forma Normale in seguito
Abbiamo detto che il dataset relazionale ha un formato preciso [#Condizioni necessarie per relazione (3)](#condizioni-necessarie-per-relazione-(3)) espresso in questo punto, ma ci sono alcuni formati comuni che non lo sono, andiamo a vedere come si possono riportare nel formato standard
### Unnesting 
Per questo riguarda questo un

### Partial information
Non sarebbe sensato utilizzare elementi che siano dentro il nostro dominio della colonna per rappresentare un dato che manca.
Per questo motivo si utilizza **NULL** che rappresenta proprio il dato mancante, e il dominio della colonna sarebbe sempre esteso con NULL (almeno ché esplicitamente vietato).
#### Types of Nulls (3)
- **Unknown**
- **Inexistant**
- **Uninformative**
Ma nei DBMS non si fa distinzione, quindi si utilizza un **unico null type**.