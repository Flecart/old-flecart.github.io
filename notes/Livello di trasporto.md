---
layout: page
permalink: notes/livello-di-trasporto
tags: en
title: Livello di trasporto
---

Ripasso Prox: 21
Ripasso: June 3, 2023
Ultima modifica: May 14, 2023 6:13 PM
Primo Abbozzo: March 18, 2023 9:23 AM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

Guardare la parte equivalente in Note Esame che è simile.

# Livello di trasporto

Si parla di **livello logico** di trasporto, ma gran parte ne abbiamo già parlato in [Livello applicazione e socket](/notes/livello-applicazione-e-socket) di UDP, TCP e Socket. **trasporto end-to-end**, nel senso che livello traporto viene visto solamente ad inizio e alla fine, in tutti i nodi intermedi non è visto sto pacchetto.

### UDP (3) 🟩-

- Slide UDP

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled">

1. Classico inizio e fine porta del socket.
2. Lunghezza, si può vedere che massimo è 2 alla 16, e poi il checksum per vedere se è comunicato bene.
3. 8 byte di header, quindi molto efficiente!

- Sposto a livello applicazione il check al mancato pacchetto. (esempio DNS)
- Oppure casi in cui perdere pacchetti non è molto importante.

CARATTERISTICHE UDP

1. Nessun controllo del flow, senza handshake, e per questo motivo possiamo dire che non sia connection oriented (l'affidabilità della connessione può essere spostata al livello superiore)
2. **Stateless**
3. Velocità di invio, 8 byte di overhead contro i 20 di TCP

Per maggiori informazioni e confronto con TCP (il fatto di connectionless etc) guardare [Intro TCP (3) e UPD 🟩](/notes/intro-tcp-(3)-e-upd-🟩).

### TCP struttura pacchetto 🟩

In cui c'è molto di più.

- TCP segment structure

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 1.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 1">


La nota importante oltre le flag, e altre cose è

- Acknoledgement del pacchetto precedente è messo nell’header!

### Internet checksum 🟩

- Slide internet checksum

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 2.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 2">


Stile dell’algoritmo:

1. Incolonnati a 16 bit,
2. faccio la somma di tutit i bit.
3. Somma del riporto **wraparound**.
4. Complemento a uno del risultato precedente

Si ricordi che questo è un metodo utile per capire se ci sono errori di trasmissione, ma non è molto buono per difendersi da attacchi umani.

## Costruzione protocollo di trasporto reliable

Vogliamo cercare di costruire un protocollo ground up, cioè assumento piano piano, errore per errore e fixare ogni errore.

Alla fine il protocollo così creato sarà

### Affidabilità del trasferimento di dati

Vorremo creare **l’equivalente di un canale di strasferimento affidabile**, cosa che non è internet, quindi vogliamo aggiungere altre cose per rendere questa interfaccia:

- Slide RDT (Reliable data transfer)

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 3.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 3">


Permetto di creare interfaccie come

1. `rdt_send()`
2. `udt_send()` unreliable data transfer, che è quello offerto dalla rete.

Stessa cosa per il lato di ricezione, ricevo da cosa unreliable, processo e li passo sopra.

Esempi sono numerazione di pacchetti e resend di pacchetti chei non sono stati ricevuti, questi sono modi per rendere affidabili.

### Passo passo, 3 problemi

1. Resistente alla corruzione dei pacchetti
2. Corruzione dei pacchetti ACK
3. Resistente alla perdita di pacchetti

**RETE RELIABLE**

- Slide rete reliable

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 4.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 4">


È la cosa più stupida, si assume subito che sia reliable

**RETE CORRUTTIBILE**

Si utilizza un sistema ACK, NACK per vedere se arriva o meno il pacchetto

- Slide rete corruttibile

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 5.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 5">


Se dal lato ricevente, viene inviato il messaggio che è arrivato sbagliato.

**CORRUZIONE DEI NAK e ACK**

Che succede con l’esempio sopra se si possono corrompere anche ACK e NACK? Facciamo ack e nack sui numeri pacchetto!

- Slide ack e nak

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 6.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 7.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 7">


**SENZA NAK**

- Slide senza nak

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 8.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 8">


Basta mandare l'ack al pacchetto corretto! Non abbiamo più bisogno che si mandi nak quando arriva il pacchetto brutto.

**PERDITA DI PACCHETTI**

In questo caso includiamoil timeout.

- Slide timing

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 9.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 9">


- Esempio di rdt3 in azione

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 10.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 10">

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 11.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 11">


**ANALISI DELLE PERFORMANCE**

- Slide performance rdt3.0

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 12.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 12">


Si può notare che l'utilizzo della rete è pochissimo! 0.027 % di utilizzo in questa analisi.

Dovremo cercare di parallellizzare il processo utilizzato per mandare e riceve

### Pipelining (2) 🟩—

È un metodo per mandare più pacchetti contemporaneamente.

Ci sono due metodologie principalemente, **go back N,  selective repeat**.

- Pipelined protocols

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 13.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 13">


**GO BACK N**

Significa che con gli ultimi n ack sono stati ricdevuti correttamente, quindi col singolo ack, mi dice da dove posso cominciare a ripartire a mandare. Ma manda un sacco di pacchetti, quindi può congestionare la rete, con il vantaggio che non mi devo memorizzare.

- Automa Go back N (NON FARE)

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 14.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 14">

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 15.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 15">

- Esempio di GBN

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 16.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 16">

- il destinatario non deve memorizzare nel buffer i pacchetti che giungono fuori sequenza. (risparmio in memoria)
- Maggiore onere alla rete, che deve ritrasmettere alcuni pacchetti anche se vengono ricevuti correttamente.

**SELECTIVE REPEAT**

Perché ti faccio ripetere in modo selettivo.

- Meno lavoro dei router
- Overhead maggiore per i RTT per gli ACK, cosa che alla fine rallenta la prestazione della rete.
- Più memoria per mantenere tempi per tutti i pacchetti.

## Approfondimento TCP

### TCP trip time

- Slides

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 17.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 17">

    <img src="/images/notes/image/universita/ex-notion/Livello di trasporto/Untitled 18.png" alt="image/universita/ex-notion/Livello di trasporto/Untitled 18">


Si utilizza una tecnica di media esponenziale presente anche in [Scheduler](/notes/scheduler) ma qui facciamo anche un **safety margin** per essere sicuri e molto conservativi parti a 4 deviazioni (quindi molto! affinché scada deve succedere veramente qualcosa di brutto).

### Ack e numeri di sequenza (no) 🟩

Il libro dice che in fase di handshaking vengono stabiliti numeri di sequenza random, questo per evitare il fatto che lo 0 rappresenti una nuova sequenza, se in precedenza si è già connessi.

Poi cosa, TCP utilizza un ack cumulativo, sul numero di byte, e il numero di sequenza è sempre fatto sul numero di byte inviati e ricevuti.

**NOTA:** grandezza della finestra pipelining e il numero di sequenza, si osservi che se abbiamo troppi pochi numeri di sequenza, allora potremmo conseguire nell’ambiguità del fatto che un pacchetto non si può distinguere se sia un pacchetto nuovo oppure una ripetizione di un vecchio pacchetto.

> la finestra deve avere ampiezza inferiore o uguale alla metà dello spazio dei numeri di sequenza dei protocolli SR. per non incorrere ai problemi di ambiguità. ~libro
>

### Il resend (2) 🟩

**TIMEOUT**: è molto speciale per il TCP, invece di calcolare il timeout con la formula con l’estimated time, con la media esponenziale e con 4 volte la deviazione standard, viene semplicemente *raddoppiato* il tempo, ogni volta che scade. Probabilmente si pensa che la rete sia congestionata, quindi si aspetta un pò.

Importante notare che questo ack cumulativo non è presente in selective repeat, quindi è più simile a GBN, però allo stesso tempo se scade il timeout, che è messo solamente sul base (quindi il pacchetto più vecchio che è stato mandato, non su tutti a differenza di SR) non vado a rimandare

**FAST RESEND**: Quando ricevo 3 acks con lo stesso numero di sequenza, assumo che è stato perché il paccketto con il numero di base è stato perso. Con questa assunzione provo a rimandare il pacchetto di base.

### Controllo del flusso (no) 🟩

il mittente non vuole mandare così tanti bytes da saturare il buffer del ricevente, per questo motivo il ricevente manda in un certo campo dell’header anche l’ampiezza del buffer che può ancora ricevere, e solitamente il mittente cerca di stare all'interno di quel buffer, in modo che la richiesta possa sempre essre elaborata.

Se il l'ampiezza è 0 non voglio stopparmi! voglio sempre mandare almeno un singolo byte di dati, altrimenti rischierei una starvation, anche se il ricevente può ricevere cose.

### Controllo della Congestione (!) 🟨++

Vengono define tre fasi per il controllo della congestione, le prime due più importanti mentre l’ultima è facoltativa diciamo.

1. **Slow start** Questa è la fase che abbiamo già studiato in precedenza, in pratica si parte con un MSS (maximum segment size) e si raddoppia fin quando continuano ad arrivare gli ACK (in pratica aggiungi 1MSS per ack).
Quando perdo un pacchetto, o per il timeout o per il triplo ack, allora torno a 1 MSS, e mi setto un massimo numero di pacchetti (la metà di quando è successo la perdita)
2. **Congestion avoidance** Sono in questa fase quando ho raggiunto il numero massimo di pacchetti inviati. Quando sono in questa fase allora aumento di 1/[pacchetti trasmessi] ad ogni ACK, in pratica cresco in modo lineare, molto più lento, fino a quando non perdo di nuovo un pacchetto.
Se lo perdo per timeout torno a 1 e sono a slow start, altrimenti alcuni pacchetti sono comunque giunti al destinatario, quindi reiverto in modo molto più soft, in pratica dimezzo la mia window e vado in fast recovery.
3. **Fast recovery** nella fast recovery aumento di 1 se l’ack è per il pacchetto che ho perso, quando arriva l’ack per il segmento perso stesso rientro in quella fase, questo mi fa crescere linearmente e mi permette di partire molto più in fretta.
Esempio: se ero a 32 pacchetti, vi vengono 3 ack per pacchetto 1, dimezzo e assumo che il pacchetto 2 sia perso, e aumento di 3 (perché sono venuti 3 acks), sono a 19, mi arrivano altri ack di 1, aumento di 1, quando arriva il 2 entro in Congestion avoidance.