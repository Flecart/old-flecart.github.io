---
layout: page
permalink: notes/data-plane
tags: italian
title: Data Plane
---

Ripasso Prox: 30
Ripasso: May 20, 2023
Ultima modifica: May 14, 2023 5:18 PM
Primo Abbozzo: March 10, 2023 12:10 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Data and control Plane

## Introduzione Data or Control plane

come fanno i router a fare forwarding dei pacchetti? e decidere come mandare? Come fanno a passare. Sono le tabelle di instradamento. Si può dire di **end-to-end** perché solamente il sender e receiver andranno a livello applicazione, e leggeranno le cose (se criptato veramente solo loro riescono a fare questo).

### Funzioni principali (2) 🟩

**Forwarding** che in pratica è passare il pacchetto al successivo, è parte del data plane.

Questa è una cosa molto semplice, in pratica bisogna capire da una porta di ingresso quale sarà la porta d’uscita del router. Guardando l'intestazione del pacchetto. Se non matcha nessuna riga della tabella allora manda nel router di default che avrà un reach maggiore, più probabile che sappia dove mandare.

**Routing** invece va a scrivere mappe nel grafico della rete, cioè capisce quale sia il percorso più breve all'interno della rete, è parte dle control plane.

Tutta la rete in modo coordinato prova a creare questo piano (me se stesse segnalando se una segnaletica funziona ancora, se la strada va ancora dove dovrebbe andare (e.g. se è crollato un ponte dovresti sapere se quella strada non funziona più)).

Solitamente questo è fatto con un software chiamato SDN (ma anche un umano potrebbe farle, anche se sarebbe troppo lento).

### Routing control planes (2) 🟩

La differenza fra i due è sostanzialmente architetturale, se ne parla in Architetture a livello applicazione 🟩.

**PER ROUTER CONTROL PLANE** possiamo dire che sia un modo semplice del control plane per stabilire la tabella di instradamento, in pratica listo tutti i collegamenti che ho nella tabella con i loro IP di interesse, quindi se un prefisso matcha quello allora mando lì. È strano che i router siano anche in grado di fare prefisso più lungo per matchare. In questo modo utilizzando un algoirtmo locale, distribuito, posso avere una tabella di istradamento. gli algoritmi locali possono fare scelte non coordinate, dato che può cambiare nel tempo la situazione, l'informazione locale potrebbe non essere del tutto corretta.

**LOGICALLY CENTRALIZED CONTROL PLANE** quando c'è una struttura centrale che contiene tutte le informazioni dei singoli router (o almeno quanto trasmesso), e da lì aggiorna le tabelle di instradamento dei singoli router. (Control Agent è il singolo router, che trasmette a un controllo remoto). La cosa importante è che il cos Remote Contorller è conoscente di tutti i dati principali della rete. Questo rende più efficiente, perché ha tutte le informazioni per fare le decisioni migliori.

Però ha bisogno di comunicare fra CA e RC, e se non funziona la comunicazione non avrei comunque le informazioni perfette.

Inoltre deve essere un processo bono, e si dovrebbe capire chi avrebbe la responsabiltià di pagare il remote controller, i provider? gli utenti finali?

- Immagine semplificazione Data e Control Plane

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled.png" alt="image/universita/ex-notion/Data Plane/Untitled">


### Service Model 🟩—

I modelli di servizio definiscono le caratteristiche che dovrebbe avere il servizio di trasporto end-to-end dei pacchetti. Alcune caratteristiche potrebbero esser come consegna garantita, o garantita consegna entro certo tempo, oppure il flow dei datagrammi in ordine, minima bandwidth, servizi di sicurezza sul trasporto. Ma queste caratteristiche alla fine non sono comunque mai garantite. Quindi possiamo indire un sistema **best-effort**, ma non è che sia comunque garantito qualcosa, potrei dire che una rete che non è in grado di trasportare niente sta facendo il massimo di quanto riesce a fare. Non ci aiuta molto.

**ATM (asynchronous transfer model)** è un servizio che prova a fare questo, cercare di misurare il modello di servizio del trasporto che in una specifico spazio temporale posso darti tutte le risorse, e allora avresti le garanzie dette sopra. E se non riesco a riempire tutto il canale in quel tempo, do lo spazio in più ad altri che non hanno bisogno di quella garanzia.

C’è un Overhead per la quantità di dati e la lunghezza di header (se header molto lungo, alla fine trasmetto meno percentuale di dati), però se faccio troppo lungo ci metto di più a mandare, quindi altri pacchetti potrebbero metterci molto di più ad arrivare, e perdere la garanzia sul tempo minimo di arrivare. era 32 o 64, quindi si è fatta una scelta politica che è 48 byte, e fa schifo perché non è una potenza di 2 e devi fare check leggermente più complicate.

A noi di solito non serve questa garanzia, noi utenti dico, ma al backbone di internet è importante e si sono messi così. Ci sono molti tipologie di ATM come

- constant bit rate ( voice over Ip, abbiamo biosgno di flusso costante per la voce, vogliamo real time, oppure coso di un reattore nucleare, senza nessuna congestione e con forti garanzie su loss, ordering e timing).
- Variable bit rate, come il video, perché ha bisongo di un sacchissimo di informazioni, un byte per un pixel bianco e nero, non si può trasmettere tanta roba..
- Altro che non listo
- Slide garanzie Service Models

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 1.png" alt="image/universita/ex-notion/Data Plane/Untitled 1">


## The Router

### Router architecture (4) 🟩

ci sono credo molti modi per implementare la funzione di router, in generale in un singolo ciclo di clock ti riescono a far entrare e far uscire il pacchetto, questo sarebbe il router buono

Quindi possiamo individuare

1. Porte di input
2. Un processore di routing che ti indirizza nell uscita giusta
3. Un sistema di switching fabric per poter mandare l'informazione nella porta giusta
4. Porte di uscita
- Slide sistema di routing

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 2.png" alt="image/universita/ex-notion/Data Plane/Untitled 2">


la parte del processore è molto più utilizzato nella parte di [Control Plane](/notes/control-plane)

### Forwarding (2) 🟨

Il forwarding tratta delle politiche che il processore di routing dovrebbe utilizzare per capire in quale porta di output ti potrebbe mandare

Questo può essere fatto in due tipi:

**DESTINATION BASED FORWARDING** in cui si va a guardare l'indirizzo di arrivo e si decide in questo modo come mandarti.

Vediamo un esempio di questa tipologia di forwarding.

- Slide forwarding destination based primo esempio

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 3.png" alt="image/universita/ex-notion/Data Plane/Untitled 3">


Da notare che sono degli intervalli in questo caso di esempio, ed è esattamente come avevamo diviso le subnets in un esercizio passato, in [Livello di Rete](/notes/livello-di-rete).

- Slides forwarding destination based secondo esempio

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 4.png" alt="image/universita/ex-notion/Data Plane/Untitled 4">


Questo è il più usato, è il **longest prefix match**. Questo è bello perché si possono indirizzare nelle (TCAMs Ternary content addressable memories, CISCO ha inventato sta tecnologia ed è la più forte sul mercato attualmente) che praticamente ti trova in singolo ciclo di clock quello corretto.

L’algoritmo normale per trovare l'indirizzo corretto, sarebbe comunque fatto in $$O(n)$$, ma se l’hardware riesce a fare in parallelo con tutte le tabelle in un singolo ciclo di clock allora ho un $$O(1)$$, quindi ez.

**GENERALIZED FORWARDING** Software defined networking

Generalizzato perché è **indipendente dal router che facciamo** perché è tutto gestito da un controller centralizzato.

Ogni router ha una **flow table**, la stessa cosa di cui si parla nei IPv6 in Datagramma IPv6 . Questa tabella è **costruita col routing plane centralizzato,** descritta dal software. Importante che tutta la rete sia SDN, sennò non funziona questo.

- Slide SDN

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 5.png" alt="image/universita/ex-notion/Data Plane/Untitled 5">


### Open Flow

- Slide flow table

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 6.png" alt="image/universita/ex-notion/Data Plane/Untitled 6">


Abbiamo certe **regole di gestione del pacchetto** che si basa tu match-action. Se c’è un match sugli header del pacchetto, allora faccio una azione su quel pacchetto. (come drop, forward, modify) e ci permette di fare molta roba, come le IP tables, o il NAT. Il router ora può assumere molt funzioni diverse.

Abbiamo anche una priority, mentre nella destination based è solamente longest prefix.

### Switching fabrics (3) 🟩

- Schemi libro per presentare i router

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 7.png" alt="image/universita/ex-notion/Data Plane/Untitled 7">

1. La prima è una memoria, ma è molto lento perché **ha bisogno di due copie di memoria**.
2. Ognuno può avere un bus condiviso, si sceglie a livello del sender il bus di arrivo, ma **posso far passare solamente un bus alla volta**, quindi posso avere un singolo alla volta che passa.
3. La cosa migliore è la **TRANSFER SWITCH**. Così posso far passare in parallelo dei pacchetti, però è la cosa più complessa, però è anche la cosa più efficiente, perché non devo né copiare, né avere collisioni sul bus

### Ritardi possibili 🟩

**INPUT QUEUING 2**

1. Quando due pacchetti di entrata devono andare sulla stessa uscita.
2. **Head of the line blocking**, quando ci sono più pacchetti che stanno aspettando, quello avanti è bloccato, ma quello dietro potrebbe andare.
- Slide input queuing

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 8.png" alt="image/universita/ex-notion/Data Plane/Untitled 8">


**OUTPUT**

Ho due cose **buffering** ossia quanto velocemente la switching fabric copia sui bus di uscita e **scheduling** che determina l'ordine di invio credo.

Per decidere la quantità di buffering voluta per avere un certo bandwitdth è in slide (una formula precisa): buffering delle uscite meno radice quadrata di quelle di ientrate.

- Slide buffering

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 9.png" alt="image/universita/ex-notion/Data Plane/Untitled 9">


Se il buffer di uscita diventa pieno, allora comincio a perdere i pacchetti! Posso perderlo secondo certe politiche:

1. L'ultimo che arriva
2. Cade uno a caso
3. Cado quello con meno priorità (per fare questo devi fare **hardware diverso** perché non basta un semplice hardware).

### Scheduling dei routers (3+) 🟩

Ci sono certi algoritmi di scheling banali, come il First Come First served, e poi droppo tutti quelli che stanno fuori, oppure farli droppare a caso.

- Slide priorità

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 10.png" alt="image/universita/ex-notion/Data Plane/Untitled 10">


in pratica ho un classificatore, che dice se è di priorità o meno.

Poi per mandare guardo se c'è qualcosa di priorità maggiore, se è vuoto provo a mandare quelli minori.

Ma questo può **generare starvation**.

- Slide Round Robin (che non faccia starvation)

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 11.png" alt="image/universita/ex-notion/Data Plane/Untitled 11">


In pratica provo uno per classe ad ogni ciclo.

- Slide Weighted Fair Queuing

    <img src="/images/notes/image/universita/ex-notion/Data Plane/Untitled 12.png" alt="image/universita/ex-notion/Data Plane/Untitled 12">


Tipo se ho massima priority, ne mando 4, se sono nella seconda ne mano 2, se sono nella terza ne mando 1, quindi **esiste ancora la priority** e non ho starvation perché anche nella coda brutta riesco sempre ad andare avanti.

Sul pacchetto IP [Indirizzo IP (!!!)](/notes/indirizzo-ip-(!!!)).