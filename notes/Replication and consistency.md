---
layout: page
permalink: notes/replication-and-consistency
tags: en
title: Replication and consistency
---

Ultima modifica: January 5, 2023 9:59 AM
Primo Abbozzo: January 4, 2023 10:02 AM
Studi Personali: No

# Elementi di ripasso

# Replication and consistency

## Introduzione

Ci sono due vantaggi principali nella replicazione dei dati

1. **Velocità**
    1. Vicinanza geografica (quindi meno tempo ad andare a tornare)
    2. Maggiore computazione, quindi avere molti più processori che cercano di offrire lo stesso servizio.
2. **Affidabilità**
    1. Così se una sede diventa corrotta, posso avere abbondanza, avere una copia da una altra parte, così non perdo le informazioni!
    2. Se una macchina cade in errore, ho altre macchine che lo sostituiscono! Quindi dal punto di vista dell’utente funziona ancora.

Ma provare ad avere lo stesso dato in zone diverse porta a grandi problemi riguardo la **consistenza**! Come facciamo ad avere la garanzia che due cose diverse abbiano la stessa informazione?

## Consistency

La nozione di consistenza non è che sia definito in modo molto formale, possiamo solo descriverlo in modo molto generale come un **contratto fra processo e dati** su cui opera. Si può dire che un processo è consistente se fa quello che dovrebbe fare (quindi vago vago descrizione).

### Continuous consistency

Questo è un modello molto vecchio, caduto in disuso perché principalemente pone delle **interfaccie di difficile implementazione**, nel senso che è difficile utilizzarle e definirle in casi di applicazione reale (credo un pò come se stessi utilizzando i semafori).

Il concetto principale è di **errore assoluto o relativo** di inconsistenza (→ quando l’inconsistenza supera una certa deviazione, allora si prova a rimediare e ristabilire la consistenza), che andiamo a chiamare il **conit**. A seconda di quanto conit abbiamo decidiamo o meno se propagare la consistenza. Si nota subito da qui che è difficile dare un valore di inconsistenza e quindi andiamo a disuso.

Esempi di caso d’uso sono i prezzi degli stock. Se variano di poco, non so 0.0001, allora non provo a renderlo consistente ancora (per quanto riguarda la lettura)

Per maggiori informazioni consultare il capitolo 7 sulla consistenza continua.

### Ordered consistency (2)

In questa parte trattiamo un idea presente già da tempo negli studi di parallelismo e sistemi distribuiti. L’idea principale è che cerchiamo di ordinare la sequenza di lettura e scrittura. Questo sarà la cosa comune ai vari protocolli.

**Sequential consistency**

Definito in Lamport [1979]

> The result of any execution is the same as if the (read and write) operations by all processes on the data store were executed in some sequential order and the operations of each individual process appear in this sequence in the order specified by its program
>

In questa definizione lo vediamo come ci sia il bozzolo dell’idea che il sistema distribuito sia una unica macchina un pochetto sparsa. Abbiamo che tutte le operazioni sono sequenziali, come se stessimo su una macchina! In particolare **ci basta che siano in ordine** non sappiamo però quale ordine sia.

**Causal consistency**

Questo è un tipo speciale di sequential consistency, e l’idea principale si basa sul fatto che non ha senso dare un ordine a delle cose indipendenti fra di loro, per esempio se faccio solamente dei read, non ha senso che provi a dare un ordine di lettura, tanto le cose che leggo sono le stesse.

Quindi avrebbe senso ordinare solo le read che hanno una write che la influenza quindi che sia in qualche modo causato o influenzato dalla write.

**Eventual consistency**

### Client-centric consistency

Questo è un modello che abbiamo creato principalmente per i dispositivi mobili. Vogliamo garantire **consistenza all’utente** anche quando il server non potrebbe essere pienamente consistente. Il motivo di cambiare visuale e ora metterci dal punto di vista dell’utente è che non possiamo predire lo spostamento di essa. E per esempio cambiare password in un punto. Spostarsi, e provare a loggare da un altro punto porta a un fallimento, questa non è una buona cosa. La client centric consistency prova a risolvere questo problema

**Eventual consistency**

Ossia prima o poi il dato sarà sincronizzato fra i dispositivi diversi (un giorno? due giorni? prima o poi lo fa!).

Per molte cose questo ritardo non è molto importante, per esempio i DNS.

### Read & write consistencies

**Monotonic-read consistency**

> if a process reads the value of a data item x, any successive read
operation on x by the process will always return that same value or a
more recent value
>

Ossia, una volta letto una cosa al tempo t, non posso più leggere cose al tempo < t.

Esempio: **email** , non voglio rileggere una email che ho già letto.

**Monotonic-write consistency**

> a write operation by a process on a data item x is completed before
any successive operation on x by the same process
>

Ossia se voglio scrivere cose al tempo t, devo aspettare che tutte le write prima di t finiscano per fare qualunque cosa dopo t.

Update del software, devo andare a leggere o scrivere sulla versione più recente.

**Read your writes**

> the effect of a write operation by a process on data item x will always
be seen by a successive read operation on x by the same process
>

Ossia prima scrivo poi leggo.

Es: password update. (non voglio che una password vecchia sia ancora considerata come valida dopo un cambio).

**Writes follow reads**

> a write operation by a process on data item x following a previous read
operation on x by the same process is guaranteed to take place on the
same or a more recent value of x that was read
>

Ossia quando modifico, lo faccio solo sull’ultimo valore. (cioè non posso scrivere su elementi vecchi (aka, non può succedere che il mio messaggio arrivi prima del messaggio che ho letto, dopo che c’è stato consistenza))

## Replication

Questa è una parte complicata.

**Posso replicare non solo i dati ma ANCHE i servizi**. E qui sale il problema dell’identità. Come gestire i servizi che fanno esattamente la stessa cosa?