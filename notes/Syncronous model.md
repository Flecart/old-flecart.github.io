---
layout: page
permalink: notes/syncronous-model
tags: en
title: Syncronous model
---

Ripasso Prox: 20
Ultima modifica: February 1, 2023 4:21 PM
Primo Abbozzo: December 30, 2022 9:40 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Syncronous model

## Introduction

Da ricordare il "The State Machine Replication (SMR) Problem" che è importantissimo per comprendere questa parte.

1. Storia locale
2. Transazioni al singolo noto

Problema del sync fra tutti questi nodi.

### Goal of SMR solution in blockchains

Andiamo a considerare alcune proprietà di safety e liveness [Programmi Concorrenti](/notes/programmi-concorrenti)

1. **Consistenza** i nodi devono essere daccordo su quale transazione mettere prima e dopo → stessa storia per tutte le transazioni. (con la possibilità di alcuni nodi che siano indietro, ma solo prefisso!).
2. **Liveness** che vogliamo dire che tutte le transazioni valide devono essere aggiunte alla fine

### Assunzioni per sincrono (4)

1. **Permissioned**, ossia i nodi del nostro modello sono fissi, non possiamo averne di più, non possiamo averne di meno e sono conosciuti.
2. **Public key infrastructure**, Ogni nodo ha una coppia pubblica e privata.
3. **Synchronous**,
    1. esiste una sorta di stato globale, e tutti i nodi condividono questa informazione.
    0, 1, … t.
    2. I messaggi sono tutti mandati bene, e arrivano esattamente uno step dopo. (mandato al tempo t, arriva a t + 1).
4. **Onestà** di tutti i nodi (sarà droppato subito questa assunzione).

4’. Una percentuale dei nodi è bizantina.

Altre di base trattate prima

1. esistenza di internet
2. Esistenza di crittografia

Si può notare che le ultime due assunzioni sono le stesse più generali definite in [Consensus protocols](/notes/consensus-protocols), andremo negli appunti in seguito solamente a rilassare alcune assunzioni di 1 e 2.

La 1 è stata storicamente molto sensata, dato che era pensata per database che comunicassero fra di loro, e chiaramente quello era un settings più controllato, per blockchain vorremmo anche provare rilassare questo.

## Bizantine broadcast problem

Questo è un problam molto simile a SMR, tanto che si potrà dimostrache che risolvere SMR si può ridurre a dimostrare BB. Andremo quindi a descrivere questo problema

### Faulty/Bizantine Nodes

Alcuni nodi falliscono, anche se non intenzionalmente, per esempio con errori di hardware.

> Un nodo che non è onesto (comporta come si dovrebbe comportare) è **faulty**.
>

**Motivi di errore possibile**

1. Crash fault (errore del software oppure dell’hardware).
2. Omission fault (in cui la trasmissione di informazione importante è fallita, può essere intenzionale o meno)
3. Bizantine fault (un certo insieme di nodi fa come gli pare)

È molto importante comprendere questo concetto, dato che sarà di base nell’analisi della costruzione di protocolli che funzionino per BB.

In modo intuitivo possiamo intendere un nodo come bizantino sse non si comporta come dovrebbe. E lì vengono descritte anche 3 cause per il suo non-comportamento corretto.

### Descrizione del problema

Un nodo leader e n - 1 nodi non leader. Il leader ha una informazione privat a $$v ^*$$ che deve mandare a tutti.

Una soluzione del problema deve soddisfare queste tre caratteristiche

1. **Validità** ossia se il nodo sender (leader) è onesto, gli altri devono essere daccordo che il messaggio è  $$v^*$$
2. **Terminazione** non di deve essere deadlock, i nodi devono terminare con qualche risultato.
3. **Agreement** quando termina, tutti i nodi onesti devono essere d’accordo sullo stesso risultato.

### SMR si riduce a BB

Prenderemo in questa soluzione l’idea presente in Round-Robin leaders, ad avere ad ogni momento un leader.

Allora dato questo leader, utilizziamo BB con leader = sender, e gli altri nodi per mandare il messaggio privato.

Allora questo algoritmo possiede sia liveness che consistency. Liveness per stesso motivo di prima, prima o poi un nodo diventa un leader, quindi riesce ad aggiungere la sua informazione privata.

Consistency perché perla soluzione di BB, ogni nodo onesto alla fine sarà d’accordo su quanto deve aggiungere alla sua lista privata. In particolare se il leader è onesto sarà esattamente quanto mandato dal sender.

- Slides

    <img src="/images/notes/image/universita/ex-notion/Syncronous model/Untitled.png" alt="image/universita/ex-notion/Syncronous model/Untitled">

    <img src="/images/notes/image/universita/ex-notion/Syncronous model/Untitled 1.png" alt="image/universita/ex-notion/Syncronous model/Untitled 1">


## Alcune soluzioni

### Lazy SMR

Se ogni nodo non comunicasse, ma aggiungesse alla propria lista privata la transazione, questo non funziona. Non c’è proprio la consistenza. Non ci si può aspettare che il nodo esterno, la transazione riesca a richiedere allo stesso tempo a tutti i nodi.

Da qui concludiamo che **i nodi devono comunicare fra di loro** (che è una cosa molto banale).

### Round-Robin leaders

Questà è una idea che ogni nodo diventa **leader** e si mette a coordinare i nodi a turni, in un certo senso è molto simile all’idea presente in [Architettura e livelli 1, 2](/notes/architettura-e-livelli-1,-2)  riguardo le reti ad anello e il passaggio del testimone.

**Funzionamento**

I nodi diventano leader aseconda del tempo globale.

Il nodo leader manda a tutti gli altri la sua lista, gli altri aggiungeranno al proprio alla fine, all’inizio metto le propria (quindi).

**Correttezza**

Sia consistenza sia liveness vengono soddisfatti. La liveness è soddisfatta perché prima o poi il nodo n sarà il leader, allora avrà l’occasione di aggiungere alla catena i suoi dati privati.

La consistenza viene soddisfatta perché sotto le assunzioni che abbiamo i messaggi vengono mandati e ricevuti esattamente in uno step di tempo, quindi ogni nodo riesce ad aggiungere alla sua lista privata quello che gli è di interesse.

**Necessità dell’onestà**

Se un nodo non onesto diventa leader, potrebbe mandare un pò della sua lista ad lacuni nodi e niente ad altro (omission fault) e quindi questo rompe tutta la consistenza! Quindi questo metodo funziona solamente nel caso in cui nessun nodo fallisca. Vorremmo però resiste anche al fallimento!

## Dolev-Strong protocol

L’idea generale di questo protocollo è capire se il sender è onesto o meno. Se si riesce a capire questa cosa, allora se è onesto prendo il suo valore, altrimenti metto bottom sulla mia pila

### Convincing messages

- Definizione in slide

    <img src="/images/notes/image/universita/ex-notion/Syncronous model/Untitled 2.png" alt="image/universita/ex-notion/Syncronous model/Untitled 2">


### The protocol

<img src="/images/notes/image/universita/ex-notion/Syncronous model/Untitled 3.png" alt="image/universita/ex-notion/Syncronous model/Untitled 3">

Quel mandare cose è più o meno cercare di capire se il nodo sender ha mandato messaggi contraddittori.

### Proof of correctness

## PKI (Hexagon proof)

Pease, Shostak, and Lamport [PSL80], and later the proof was simplified by Fischer, Lynch, and
Merritt [FLM85].

Questa è una dimostrazione molto importante per quanto riguarda questo modello. Mostra che ci sono delle limitazioni pesanti riguardanti il modello. Come si vedrà in seguito anche in [Asynchronous model](/notes/asynchronous-model), ci saranno delle limitazioni in praticamente qualunque modello.

### Enunciato

Siano n nodi all’interno di un modello a comunicazione sincrona in cui **non è presente un setting PKI** (chiave privata e pubblica), se i nodi bizantini sono $$f \geq n / 3$$, allora non è possibile avere contemporaneamente terminazione, safety e liveness.

### Dimostrazione

Dimostreremo solamente il caso in cui n = 3, poi si dovrebbe estendere senza molto sforzo al caso maggiore generico.

Questa dimostrazione va a contraddizione. Supponiamo di avere un setting a 6 nodi come in figura

<img src="/images/notes/image/universita/ex-notion/Syncronous model/Untitled 4.png" alt="image/universita/ex-notion/Syncronous model/Untitled 4">

I nodi F sono i sender, mentre M e L sono le altre cose.

Ora da notare è che **il procollo può eseguire su questo sistema**, cioè anche se era inteso per essere eseguito nel caso $$n = 3$$, le uniche cose di cui ha bisogno il protocollo è

1. Sapere se è un sender o meno
2. Il messaggio da inviare se è il sender
3. I suoi n - 2 vicini (quindi sapere a chi mandare).

Quindi sotto queste assunzioni il protocollo può eseguire

Allora andiamo a considerare 3 scenari possibili:

**Scenario 1 F bizantino**

Supponiamo di essere in un sistema a 3, con L, M, F, ma F è il nodo bizantino. F dato che è bizantino può fare cose arbitrarie, in particolare facciamo finta che simuli i nodi F’, M’, L’, F collegati come di sopra.

Allora dato che il nosto protocollo deve soddisfare consistenza, ossia tutti i nodi onesti devono finere per essere d’accordo su qualcosa, deve essere che nel sistema l’output di L = M

**Scenario 2 L bizantino**

Sistema a 3 dato da L, M, e F’, ma in questo caso ora il nodo M simula i nodi M, L, F, M’. Per validità del protocollo deve essere che L è d'accordo con l’output 1, del sender F’.

**Scenario 3 M bizantino**

Simile al siste a tre nel primo caso, ora L simula L, F’, M’, L’. Quindi per validità M dà in output F.

ma allora bbiamo un assurdo perché L dovrebbe essere uguale a M, invece l'output è diverso. Quindi questo scenario non può succedere.



# References