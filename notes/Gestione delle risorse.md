---
layout: page
permalink: notes/gestione-delle-risorse
tags: italian
title: Gestione delle risorse
---

Ripasso Prox: 14
Ripasso: May 21, 2023
Ultima modifica: May 16, 2023 1:56 PM
Primo Abbozzo: March 22, 2023 9:20 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# Gestione delle risorse

## Introduzione

### Definizione classe, fungibilità 🟩

**Classe di risorse** sono un insieme di risorse fra loro equivalenti (nel senso ch euno può rimpiazzare l’uso dell'altro), anche detti fungibili.

### Statico o dinamico 🟩

Anche in economia ci sono tali definizioni! Queste risorse possono essere allocate staticamente o dinamicamente, in modo simile a quanto abbiamo detto in [Gestione della memoria](/notes/gestione-della-memoria).

Statico quando già in fase di compilazione del processo, o di avviamento del processo gli dò la memoria, e quella sarà per tutti il tempo della sua vita.

Mentre dinamico quando gli dò cose pezzo per pezzo quando è vivo

### Tipologia di richieste e risorse (4) (!!!) 🟩

**MULTIPLO O SINGOLO**

Si può dire che il programma può chiedere risorse, e le tipologie che puoi richiedere sono **multiplo o singole**.

Il significato sembra abbastanza simile:

- Singola per singola classe di risorsa
- Multipla richiesta per tante classi (la differenza principale è **l’atomicità della richiesta,** nel secondo caso, faccio singola richiesta per molteplici classi, o li prendo tutti o zero).

**BLOCCANTE O NON BLOCCANTE**

Si può anche dividere per **richiesta bloccante o meno**, e anche questo è molto simile a quanto abbiamo fatto in [Programmi Concorrenti](/notes/programmi-concorrenti). Quindi bloccante come le IO, quando mi metto ad aspettare che finisca, oppure la comunicazione sincrona del [Message Passing](/notes/message-passing).

Non bloccante come il send della comunicazione asincrona,  ma anche solo una notifica dell mancato svoglimento, come credo faccia il message passing completamente asincrono.

**CONDIVISIBILE O NON-CONDIVISIBILE**

Si può anche dividere in **risorse condivisibli o meno**, nel senso che una risorsa possa essere utilizzata da più processi contemporaneamente (come i file di sola lettura (o qualunque cosa di solo lettura, perché non ho problemi di RW).

Esempi di non condivisibil sono le cose hardware, processori, stampanti, o anch ele sezioni critiche, versioni software.

**PREEMTABLE O NON-PREEMTABLE**

**Risorse preemptable**, ossia prelasciabili, quando posso forzare la rimozione della risorsa all'utilizzatore.

> una risorsa si dice prerilasciabile se la funzione di gestione
può sottrarla ad un processo *prima* che questo l'abbia effettivamente rilasciata
>

ovviamente non vorrei che continuasse senza questa risorsa (quindi la stoppo)

non posso cambiare lo stato!! nel senso delle preemptable, se glielo tolgo, lui si aspetta di ricevere la risorsa quando torna a runnare allo stesso stato con cui è stato tolto! Diciamo è come se prendo in prestito un tuo giocattolo a forza e poi te lo distruggo, invece te lo vorrei ridare sano, normale diciamo.

## Il Deadlock

Già studiato molto in precedenza, vorremmo caratterizzare le condizioni necessarie per i deadlock all'interno dei sistemi operativi.

### Condizioni necessarie e sufficienti per DL (4) 🟩-

- Slide Necessario e sufficiente per Deadlock
	!<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled">
    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 1.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 1">


Quindi abbiamo caratterizzato con le proprietà dei Deadlock! Quando ho tutte le 4 suddette cose, allora ho deadlock.

### Grafo di Holt 🟩

Questo è un sistema utilizzato per traccare tutte le dipendenze delle risorse, che possono finire a creare deadlock.

- Caratteristiche di grafo di holt

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 2.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 2">


**GRAFO DI HOLT GENERALE**

Lo rapresento come classe il quadrato e i puntini come singola risorsa, poi ho altre politiche per fare le frecce

- Slide grafo di holt generale

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 3.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 3">

- Esempi di holt

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 4.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 4">

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 5.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 5">


**NOTE IMPLEMENTATIVE**

Come facciamo a rappresentare nella memoria questo sistema? Alla fine è un grafo **pesato**!

- Slide implementazione grafo

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 6.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 6">


### Riduzione di grafo di holt 🟩

> un grafo di Holt si dice **riducibile** se esiste almeno un nodo processo con solo archi entranti.
>

Questo nodo eventualmente rilascia la risorsa, quindi posso posso riassegnare la risorsa!,

In questo modo faccio finta che la risorsa sia già stata rilasciata.

- Riassegno tutti gli archi del processo riducibile agli altri. (non ci importa quale ordine rilasciare)

COMPLETA RIDUCIBILITÀ

> lo stato non è di deadlock se e solo se il grafo di Holt è **completamente
riducibile**, ossia quando non ho più archi nel grafo
>

i.e. esiste una sequenza di passi di riduzione che elimina tutti gli archi del grafo

Ad intuito quando ho ancora degli archi, vorrà dire che c’è una attesa circolare, ossia:

- non tutti i nodi processo hanno tutte le risorse che gli servono
- Non c’è modo di acquisire la risorsa perché anche un altro sta aspettando la stessa cosa

In questo senso si crea l’attesa circolare, ed assumendo le altre 3 condizioni di sopra ho deadlock.

### Deadlock detection introduttivo (sola risorsa) 🟩

**Th sola risorsa per classe**

> se le risorse sono a richiesta bloccante, non condivisibili e non prerilasciabili, lo stato è di deadlock se e solo se il grafo di Holt **contiene un ciclo**.
>

Genero il **grafo wait-for** (chiusura transitiviva degli archi delle risorsa, cioè se ho P che vuole risorsa, e risorsa assegnata a P2, allora ho P to P2), che in pratica mi genera l'attesa circolare (la 4 condizoine necessaria che lo rende sufficiente), e esiste il ciclo.

- Slides del th

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 7.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 7">

- Esempi

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 8.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 8">


**RILEVAMENTO PER PIÙ RISORSE PER CLASSE**

Questo è il caso anche più reale, e ci è molto più utile questo caso. Costruiremo questo caso passo per passo con le definizioni che seguono.

### Insieme di raggiungibilità e Knot 🟩

> dato un nodo n, l'insieme dei nodi raggiungibili da n viene detto **insieme di
raggiungibilità** di n (scritto R(n))
>

E si può definire **knot** molto simile a uno strongly connected component, ma diversa:

> un **knot** del grafo G è il sottoinsieme (non banale) di nodi M tale che per ogni
n in M, R(n)=M
>
- Esempio di knot

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 9.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 9">


### Th deadlock detection con knot 🟨

> Dato un grafo di Holt con una sola richiesta sospesa per processo se le risorse sono a richiesta bloccante, non condivisibili e non pre-rilasciabili, allora il grafo rappresenta uno stato di deadlock se e solo se esiste un knot
>

Quindi riusciamo a detectare l'esistenza in questo modo!

Anche se non abbiamo la dimostrazione formale, intuitivamente possiamo dire che se tutti possono raggiugnere tutti, implica l'attesa circolare!

### Recovery deadlock (2) 🟨—

*Checkpoint e rollback*

L'idea è molto semplice, praticamente ogni tot si guarda lo stato attuale del progetto, e si tenta di ripartire da lì, è lo stesso concetto del backup (però si spera che gli effetti dal backup al deadlock, siano effetti di poco costo),
e.g. se stampo di nuovo stampa di nuovo, ma non sarebbe buono per cose come la banca.

*Terminazione di processi*

Per certe tipologie di processi è molto molto costoso terminarle:

1. Esempio centro di ricerca beowulf ci mette 6 mesi a ripartire
2. Terminare in modo brutale può lasciare risorse in modo invalido.

### Deadlock prevention 🟥+

SPOOLING

Faccio finta a credere di avere già la risorsa. Un esempio è lo spool di stampa, nel senso che tutti pensano di avere questa risorsa. (questo funziona bene per la stampante però!)

Non risolve il problema perché è **come spostare il problema in altro punto, e NON SEMPRE APPLICABILE**.

- Process table no
- Dischi no.

*Richiesta bloccante O PRERILASCIO*

nel senso che tutto quello che mi serve all'inizio, lo richiedo subito, così non mi blocco mai!

Ad esempio i sistemi a real time, che richiedono proprio allocazione totale.

Il problema è che non è sempre possibile fare questo. E poi è molto inefficiente perché se lo tengo per tutto l’utilizzo del nostro programma, ma alla fine solamente un piccolissimo momento lo utilizzo, inefficienza al più!

**ATTESA CIRCOLARE**

- Slide allocazione gerarchica

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 10.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 10">


Posso solamente richiedere risorse di classi superiori (in modo che non abbia cicli, quindi diciamo che vada solamente a un verso, e non ho mai modi per avere dei knot).

- Analisi finale allocazione gerarchica, totale

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 11.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 11">

- Riassunto dei metodi di prevention

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 12.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 12">


## Banchiere, DL avoidance

### Algoritmo del banchiere 🟩

Dijkstra (1965)

> il nome deriva dal metodo utilizzato da un ipotetico banchiere di provincia che
gestisce un gruppo di clienti a cui ha concesso del credito; non tutti i clienti
avranno bisogno dello stesso credito simultaneamente
>
- Descrizione del problema

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 13.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 13">

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 14.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 14">

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 15.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 15">

- Dati in input

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 16.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 16">


### Stato safe e unsafe 🟩

- Slide stato safe

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 17.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 17">


Detto in soldoni, lo stato è safe quando il credito del tizio che chiede è minore di tutti i soldi che possiedo. Se non esiste nessuna sequenza che mi garantisca quella cosa sono unsafe!

unsafe è necessario ma non sufficiente per DEADLOCK.

**Buona sequenza con ni CRESCENTI**.

- Esempio di banchiere safe

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 18.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 18">

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 19.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 19">

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 20.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 20">

- esempio di unsafe

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 21.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 21">

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 22.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 22">


Il fatto che sia safe o meno è utile per capire se si può accettare la richiesta o meno!

### Banchiere multi-valuta

- Dati del banchiere multi-valuta

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 23.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 23">


Purtroppo se teniamo come i vettori non possiamo ordinare :(. Quindi vorremmo **andare passo passo**, e ogni volta aggiungere qualcosa di soddisfacibile.

### Teorema dell'algoritmo del banchiere 🟩—

- Slide algoritmo del banchiere

!<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 24.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 24">

- Dimostrazione correttezza

    !<img src="/images/notes/image/universita/ex-notion/Gestione delle risorse/Untitled 25.png" alt="image/universita/ex-notion/Gestione delle risorse/Untitled 25">


Questo mi permette di dire che non importa scegliere qualcosa con logica, se ho una sequenza che va continuerà ad andare sempre! Mi permette di scegliere a caso.

### Perché non è utilizzato

Semplicemente tutte le ipotesi dell’algoritmo del banchiere non sono spesso soddisfatte nel momento in cui si prova veramente a metterlo in pratica. Poi gli ingegneri dicono che spesso se un deadlock esiste una volta in 5 anni, per la maggior parte delle applicazioni diventerebbe una cosa tollerabile.

1. Si assume che il numero dei processi sia noto all’inizio
2. Si assume che le risorse necessarie al processo siano note
3. Si assume che le risorse saranno sempre quelle (invece si potrebbero rompere a caso)