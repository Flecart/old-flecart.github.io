---
layout: page
permalink: notes/project-management
tags: italian
title: Project Management
---

#### Project, product management, project management
Bisogna capire queste definizioni.
Vedere [https://dynamik.vercel.app/ingegneria-del-software/lucidi/13-gestione-del-progetto.pdf?from=informatica,](https://dynamik.vercel.app/ingegneria-del-software/lucidi/13-gestione-del-progetto.pdf?from=informatica,) slide 5 per definizione

1. Progetto: inizia e finisce in tempo preciso.

È importante comunque ricordare gli steps principali per il progetto ossia ideazione, creazione, mantenimento, rilascio, e poi morte, questo in genere è per qualunque progetto.


### Project Manager

#### Compiti principali (costi e risorse)
1. Vedere se il progetto è fattibile
2. Allocare risorse
3. Monitorare come sta andando. (preventivo e consuntivo).
<img src="/images/notes/Project Management-1701099646139.jpeg" alt="Project Management-1701099646139">
### Work Breakdown structure

#### Descrizione WBS
È una suddivisione del progetto in piccoli sottoparti che si possono gestire in modo autonomo.
>   
A Work Breakdown Structure (WBS) is a hierarchical decomposition of a project into phases, deliverables, and work packages. It is a visual representation that helps project managers and teams organize and define the scope of work required to complete a project. The WBS breaks down the project into smaller, more manageable components, making it easier to plan, execute, and control.

[https://chat.openai.com/share/1d74fa24-d198-4c17-9fbe-1c8cc93333d4](https://chat.openai.com/share/1d74fa24-d198-4c17-9fbe-1c8cc93333d4)

Si può rappresentare con un **grafico di Gantt** (vedi [Scheduler#Diagramma di Gantt](/notes/scheduler#diagramma-di-gantt)). Perché così so quando ogni singola attività inizia e finisce.

#### Milestone e percorso critico
#### Debito tecnico
> Il debito tecnico è una stima del costo di futuro sforzo addizionale causato da una soluzione prematura adottata oggi pur di consegnare un prodotto con qualche valore (lo sforzo futuro andrà ripagato con gli interessi)

Il costo di versioni successive, è costo in debito tecnico, per questo motivo è maggiore. E si dovrebbe dare valore prima.

## Misura dei costi di sviluppo

### Misura nel software
#### costo e valore del software
Valore è sul ricavo -> numero di utenti * ricavo medio.
Mentre il costo del software e tempo persona.

Per stimare il costo usiamo 4 cose:
1. Costo hardware
2. Costo sviluppo del software
3. Costo risorse umane
4. Durata del progetto.

#### Metodi generici di stima (4)
<img src="/images/notes/Project Management-1701102596412.jpeg" alt="Project Management-1701102596412">

Design-to-cost nel senso che chi è in industria fa prodotto tailored al costo.
L'ultima è funzionale


#### Linee di codice (fisiche e logiche)
Fisiche sono quelle effettivamente presenti nel codice, invece le linee logiche sono quelle che contengono istruzioni base (per base intendo quelli C like).
Se si riesce a fare una stima dell'architettura del progetto, e poi delle linee logiche necessarie per fare questo sviluppo, possiamo tenere conto di una *media di numeri giornalieri*, e possiamo calcolare cose come costo totale del software avendo una media per riga.
Chiaramente mi sembra che questa stima sia fortemente imprecisa.

#### Vantaggi e svantaggi di LOC
La cosa carina di questo metodo è che è **facile** da fare.
Poi abbiamo metriche derivate molto semplici da intendere come:
1. Bugs per kLoC. 
2. la produttività è una cosa molto facile.
3. Il costo per linea di codice
Sono certe metriche che potrebbero servire lato business, però sono abbastanza senza senso per quanto riguarda features date al cliente.
Mi sembra il caso in cui una metrica può diventare facilmente l'oggetto (massimizzare per cosa sbagliata dico), e non una linea guida

Però
- dipende dal linguaggio
- quasi nessuna correlazione con la qualità del software (quindi produce bloatware per dire), non viene prodotto software conciso o efficiente.
- **Non tiene conto della complessità**, certe istruzioni possono fare un sacco di cose, a seconda del livello di astrazione.
- Non possiamo distinguere bene le linee logiche con quelle fisiche, non abbiamo un metodo per contarle per dire.

### Function point

#### Idea principale del metodo
> L’analisi Function Point enumera le funzionalità di un sistema dal punto di vista **utente**

Elaborata da un certo Dr. Allan Albrecht in 1979, sono il numero di features fatte, che l'utente può utilizzare (e questa stima mi piace molto di più rispetto a quello di linee di codice).
Cerchiamo di analizzare il software tramite le funzionalità nuove che possono venire offerte.

L'idea è partire da quello che è necessario all cliente, quelli che chiamiamo **functional requirements** trattati a [Requisiti e backlog del software](/notes/requisiti-e-backlog-del-software).
Insieme a questi sono collegati i *non functional requirements* che sono features necessarie a sviluppatori, e non utenti.

#### UFC e TFC

Ufc è **Unadjusted Function Count** che è la somma semplice di tutte le funzionalità su tutti i lati in cui potrebebro essere necessità di function points.

### Cocomo e modelli di costo
Non fatti.

# References