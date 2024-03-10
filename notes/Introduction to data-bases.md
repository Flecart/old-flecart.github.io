---
layout: page
permalink: notes/introduction-to-data-bases
tags: italian
title: Introduction to data-bases
---

## Basi di dati
### Cosa è un database? (2) 🟩
Si potrebbe intendere come un **insieme** di dati **strutturato**, *utili* per certi obiettivi di enterprise, aziende pubbliche o simili (uno delle necessità che la rivoluzione informatica ha più contribuito diciamo.)

Un altro significato più importante è
> Un insieme di dati gestito da un Database Management System

Tristemente con questa definizione anche excel è un DBMS...

Solitamente sono utilizzati per gestire **grandi quantità di dati**.

### Il sistema informativo 🟩
> Componente di una istituzione

Si potrebbe dire che sia una base utile alle organizzazioni per gestire l'informazione, questi sistemi erano già presenti molto prima rispetto alla creazione dei sistemi dell'informazione moderni, per esempio registri e tavole venivano utilizzate in questo senso, ossia come sistemi per registrare alcuni strumenti utili per il nostro enterprise.
Quindi storicamente c'è molta necessità, è solamente con la rivoluzione storica che abbiamo nuove cose.


### Necessità dell'informazione 🟨++
Ci sono alcuni aspetti che possiamo dire molto comuni quando mettiamo mano ai dati e sono tipo:

- Collezionare i dati
- Filtrare i dati e *memorizzarli*
- elaborare i dati
- Restituire e visualizzare i dati

## Database Management System
#### Caratteristiche generali dei DBMS (5) 🟩

Le slides affermano che i dati in questione devono essere:
1. Grandi dimensioni (righe)
2. Persistenti
3. Condivisi
4. efficienti
5. efficaci
Io aggiungerei anche **strutturati** perché se sono dati non strutturati è difficile che vengano messi in un DBMS.

Comunque commentiamo ora pezzo per pezzo il motivo per cui abbiamo bisogno di queste caratteristiche per i DBMS:
1. Grandi dimensioni perché vogliamo che sia efficiente anche su questi (soprattutto su questi, quando tengono dati di tante cose rimanendo comunque organizzati diciamo)
	1. Terabyte e terabyte di data secondo le slides (500 TB per dati scientifici :O)
2. Persistenti perché non avremmo bisogno di un database se tutto rimanesse in RAM... I dati sono più longevi dei computer che li ospitano diciamo.
3. Così abbiamo un unico punto di sicurezza in cui molte persone possono affidarsi per avere una fonte di verità diciamo (questo forse ne parlava in the manga introduction to databases)
4. Efficienti si parla da solo, dato che vogliamo che sia effettivo a prendere i dati non vorremmo aspettare tanto
5. Efficace perché deve fare il suo lavoro di renderci la vita più facile nella gestione dei documenti e dei dati :)
### Altro
#### Comparazione con File System 🟩--
Sembra che anche i file-system siano in grado di svolgere il lavoro di DBMS, infatti potremmo vedere il DBMS come un file-system allargato, con più funzionalità.
Infatti possiamo anche in questo caso tenere un file-system distribuito, e affidarci ad esso per 
1. gestire una grandissima mole di dati (perdiamo sulle garanzie di integrità), 
2. gestione dell'accesso (e quindi di privacy),
3. pone interfaccia per accedere velocemente al supporto fisico sottostante. 
4. Diciamo che fa bene il suo lavoro. (efficace)

In un certo senso si può paragonare a tenere i dati su excel, funziona, però non è il massimo, non si hanno garanzie che si vorrebbero avere, i check automatizzati diciamo.

Col database abbiamo 
1. garanzie in più su uniformità e relazione dei dati con un **Data Model**
2. velocità di accesso a query classiche
3. Non limitazione ad aprire e chiudere file (prende o l'intero file o niente col file system)

#### Architettura ANSI/SPARC (3) 🟩
Introduzione a basi di dati-1695506718147.jpeg | 300|Introduzione a basi di dati-1695506718147.jpeg | 300
- **Schema logico** descrive *come dovrebbero essere i dati* ossia la struttura logica dei dati
- **Schema interno** come sono rappresentati i dati, potremmo dire l'implementazione del livello logico dei dati.
- **Schema esterno** che a volte è chiamata anche *view*, ossia come gli utenti hanno bisogno di vedere i dati

La cosa interessante di questa parte, è che vorremmo che i dati siano **indipendenti** (sia il fisico dal logico, sia il logico dall'esterno) rispetto a come sono rappresentati, una idea molto importante introdotta per la prima volta da @coddRelationalModelData1970.

Credo anche sia la stessa idea, che sta alla base del processo di astrazioni comunissimo in informatica è l'idea di **interfaccia**, un qualcosa che espone solamente la parte logica di quale sarà l'effetto dell'operazione, ma ne nascone le operazioni effettive, che chiamiamo interne. 
Per i database forse questa cosa era nuova.

#### Tipologie di modelli logici (5) 🟨+
Nel tempo sono stati creati molti modelli possibili dello strato logico del database
Una lista di modelli presenti è 
1. Gerarchici
2. Grafo (network based)
3. Relazional Model|relazionali|Relazional Model|relazionali
4. Object Oriented
5. XML-based

Quello studiato in questo corso è il modello relazionale di database management

### Problemi classici (2) 🟨--
- Ridondanza e coerenza per questo
	- **Sync** dei valori che possono essere presenti in macchine anche molto distanti
- Availability
	- È un grande problema se un database va giù...
- **Privacy** e gestione dei permessi, perché dato che sono *shared*, non vogliamo però che uno possa accedere a dati di altri.
TODO
### Caratteristiche dei dati  (3)
vogliamo che i dati all'interno dei DBMS soddisfino certe desiderata al fine di garantire il buon servizio:
1. Privacy
2. Reliability
3. Availability
E parte di queste desiderata sono le stesse che abbiamo anche richiesto all'interno di [Sicurezza OS](/notes/sicurezza-os) quando abbiamo parlato degli attacchi che era possibile fare ad un sistema informativo.

Per gestire la *reliability* ossia la tolleranza a fallimenti hardware e software, e la possibilità di garantire anche la ridondanza si utilizzano le **transazioni**

### Transactions (3)  (non fare)
Questa parte è trattata leggermente meglio quando andiamo a parlare di SQL transactions in [Structured Query Language](/notes/structured-query-language)
Anche in [Advanced SQL](/notes/advanced-sql)
- Atomiche
- Concorrenti
- Permanenti 

Le facciamo per benino in [The Database Management System](/notes/the-database-management-system)

### Pros and cons
#### Pros (5) 🟨+
Introduzione a basi di dati-1695507029821.jpeg | 350|Introduzione a basi di dati-1695507029821.jpeg | 350
1. È necessario, molto più efficiente nel caso quella stessa informazione venga utilizzata anche da dipartimenti diversi
2. È chiara la comunicazione e la struttura, che è sempre **una fonte di verità**
3. vabbé ovvio
4. Questo è molto importante, ci sono stati un sacco di danni che ci sono stati a causa di inconsistenza, come nei file di excel
5. Questo è ancora una delle radici presenti nell'informatica, l'indipendenza del software dall'implementazione concreta dei dati, oppure dalla rappresentazione hardware.


#### Cons (2) 🟩
Introduzione a basi di dati-1695507057166.jpeg | 350|Introduzione a basi di dati-1695507029821.jpeg | 350
Io aggiungerei anche il livello di astrazione (quindi magari tempo di implementazione delle cose) in più, che poi si riguadagna indietro con la facilità di gestione dell'infrastruttura

1. C'è un grande overhead per mettere su un DBMS
2. questo è ovvio come con.
## Basi di dati attive

Finora i database "passivi" non fanno niente finché non c'è interazione con query o richiesta.

#### Il comportamento reattivo 🟩
In sql ci sono dei checks a reference di integrità, che vengono attivati su update o deletions. La capacità di reagire ad eventi è importante.

#### Event-Condition-Action (ECA) 🟩
Questo è il costrutto principale dei database attivi, devono essere **in grado di reagire ad eventi** in modo reattivo. 

Quindi possiamo dire che il database è attivo quando esistono dei triggers, regole che vengono eseguite in un certo momento.

Oracle è stato uno dei primi che si è accorto di questa necessità (infatti è anche l'azienda che ha fatto questo, e l'ha chiamato **stored procedures**)
Però aspetti negativi sono:
1. Linguaggio procedurale (impendance mismatch con SQL)
2. Non standarizzato


#### Trigger, granularità e modalità 🟩
Esiste un comando SQL, nella DDL, che mi permette di definire in modo esplicito i trigger.

**Granularità**:
- Tupla (attivazione per ogni tupla)
- Operazione, a singola operazione

**Modalità**:
- Immediato
- Dilazionato.
Questi si possono rappresentare anche con semantica differente.

## Note di ripasso
### Domande importanti
- Cosa è un DBMS?
- Cosa è un database?
- Cosa è uno schema?
- In che modo si divide il database?
- Quali sono le caratteristiche importanti per i databases?

| Data | Commenti |
| ---- | ---- |
| 20/10/2023 | Molto molto male, praticamente non sapevi niente di questa parte introduttiva del corso |
| 05/01/2024 | Devo farlo meglio, rileggendomi il primo capitolo di questo per esempio. (anche se probabilmente questo è solamente introduttivo, quindi molto poco importante per comprendere l'argomento direi). |
| 12/01/2024 | Inutile questo capitolo credo. |