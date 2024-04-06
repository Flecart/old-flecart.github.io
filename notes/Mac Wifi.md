---
layout: page
permalink: notes/mac-wifi
tags: en
title: Mac Wifi
---

Ripasso Prox: 5
Ripasso: May 17, 2023
Ultima modifica: May 12, 2023 12:21 PM
Primo Abbozzo: May 3, 2023 1:48 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

# Mac Wifi

## Introduzione

Ricordiamo che vogliamo cercare di **arbitrare l’accesso al canale fisico sottostante**. In questo momento andiamo ad assumere di avere già tutto l’impianto di trasmissione fisica che abbiamo in [Tecnologia Wireless](/notes/tecnologia-wireless), [Modulazione wireless](/notes/modulazione-wireless) [Fisica del Wireless](/notes/fisica-del-wireless).

### Obiettivi: 🟨—

1. Arbitraggio del singolo canale fisico (la tesi di dottorato del prof era su collision avoidance di wifi).
    1. Sia in tempo
    2. Sia in spazio (come gestire il segnale mandato nello stesso spazio)
2. Utilizzo minimo di energia
3. Quality of service
4. Adaptive behaviour (come il 6G che vuole andare ad utilizzare AI per fare predizione).
5. Evitare segnale spaghetti o jammed
    1. Collisioni fanno sprecare energia ad entrambi (sia ricevente sia sender)
    2. bisogna trovare un metodo per fare risoluzione (controllare il sender riguardo la trasmissione, in quanto non sono in grado di trasmettere e ascoltare in modo contemporaneo)
    3. Questo si lega alla parte di arbitraggio del canale

Ricordiamo che ethernet provava ad ascoltare il segnale e provare a trasmettere, si può utilizzare la stessa cosa anche qui? No, ethernet permetteva di ascolatare il segnale nel momento di generazione, mentre wifi non può, perché semplicemente il segnale prodotto localmente è molto più grande. Inoltre wifi ha anche bisogno di fare multiplexing sullo **spazio** non solo nel tempo come per l’ethernet.

### Anticollisione primo tentativo (esempio nf)

Allora, in questa parte continuiamo ad analizzare un protocollo che tenti di evitare la collisione, si può utilizzare un sistema simile ad ethernet?

1. Risposta negativa: non evita le collisioni
- Slide fenomeno

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled.png" alt="image/universita/ex-notion/Mac Wifi/Untitled">

    Nonostante i senders non sentano niente, c'è interferenza, credo si chiami anche problema del **terminale nascosto**, perché non senti l’interferenza (asimmetria di informazioni).


1. Non arbitra niente alla fine…

### Classificazione accesso multiplo MACWIFI (2+) (!) 🟩—

- Slide protocolli

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 1.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 1">

1. Senza contesa, ossia si cerca di evitare la contesa della rete wifi
    1. Centralizzati statici, con un **coordinatore statico** che dica quando puoi comunicare (prenotazioni registrate da un coordinatore) → garanzia del servizio
        1. Costo coordinatore (centralizzato, quindi se cade cade tutto, facile da attaccare)
        2. Costo allocazione statica delle risorse.
    2. **token-based** chi vuole comunicare tiene solamente il token (solo che il rischio è che si perda il token per una interferenza o simili).
2. Content, provare a prendersi il segnale, o provare finché non ci si riesce.
    1. Probabilistico è quello più sicuro dal punto di vista della sicurezza, e ha **allocazione dinamica di servizi** (provare a comunicare a tempi random, probabilisticamente parlando provandoci così prima o poi si comunicherà). Solo che ha il problema delle collissioni ,quindi sarebbe molto buono questo metodo di allocazioen dinamica con il server centrale (0 collisioni e 0tempi vuoti). Solo che il coordinatore ha un costo. → reliability della comunicazione.
    2. Deterministico (mi sono distratto a configurare alacritty e non ho capito).

Abbiamo un accesso probabilistico in cui si prova a comunciare nel vuoto (nel senso che non si può spegnere questa rete, nel caso della presenza di un accesso centralizzato allora si utilizza quella. (ma nessuno paga))

## Aloha protocol

### Funzionamento in breve 🟩

È stato uno dei primi protocolli radio presenti. Stiamo parlando di 1970, Abramson1970 era alle Hawaii e aveva solamente dispositivi radio a disposizione, sono le prime sperimentazioni.

- Slide aloha protocol

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 2.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 2">


Il round trip time veniva calcolato, se non riceve l’ack aspetta un tempo un pò random. (il seme sarà diverso, tipo l’id della scheda di rete, il tempo di backoff che coincida è abbastanza basso)

### Analisi dominio di collisione 🟩

Ci vogliamo chiedere quando è il time frame in cui può avvenire una collisione?

Siano due comunicanti, che devono entrambi trasmettere, se uno trasmette, quando non potrebbe trasmettere l áltro per evitare la connessioen? Ci interessa solamente il tempo.

La risposta è semplice, vogliamo solo che sia una dimensione di frame prima e una dimensione di frame dopo: **tempo/slot di collisione è due volte**.

- Slide intuizione dominio di collisione

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 3.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 3">


Con questa osservazione, possiamo cambiare leggermente l'algoritmo di aloha al fine di risolvere, o meglio alleviare, il problema della collisione:

### Slotted aloha 🟩

Lo slotted aloha permette solamente la trasmissione in certi slot di tempo, questo aiuta ad alleviare il problema della collisione:

Ha senso che la dimensione dello slot è **dimensione massima del frame con anche trasmission delay** vogliamo andare a contare anche il delay della trasmissione perché altrimenti due frames possono comunque influenzarsi fra di loro durante la trasmissione.

- Slide slotted aloha

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 4.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 4">


Quindi ora il tempo di vulnerabilità è ridotto a slot + propagation, invece che due slots (anche se solitamente pensavo che il tempo di propagazione è maggiore? Credo dipenda…).

## CSMA

Carrier sense multiple access

### Introduzione all'algoritmo 🟩

- Slide CSMA

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 5.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 5">


In questo caso il **FVT** (frame vulnerability time) è due volte il propagation, perché se sono dentro a questo intervallo allora non sento il segnale dell'altro, che non è ancora arrivato. Questo valore solitamente è molto più piccolo rispetto al frame size.

### Slotted CSMA 🟩

Alla fine molto simile questa idea allo slotted aloha, tutti possono trasmettere soltanto in certi slots di times

- Slotted csma

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 6.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 6">


### Throughput comparison 🟩

- Slide thorughput

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 7.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 7">


Vediamoc he il throughput cambia molto seguendo i protocolli (e va giù perché ci sono troppe collisioni se provo a trasmettere troppo.

Mi serve sapere il numero di stazioni trasmittenti, una cosa che non conosco generalmente.

## MACA

### hidden and exposed terminals 🟩—

Vogliamo cercare di limitare le trasmittenti a comunicare bene con un ricevitore (sto ragionando sull esempio di ACBD in mezzo) cioè in un caso di **hidden terminal** in cui due senders non si sentono fra di loro, ma il loro segnale potrebbe interferire in un certo punto.

Un problema opposto è il **exposed terminal** quando il sender è condiviso da più host, un host che vorrebbe comunicare, a un host diverso, non può comunicare perché sente questo.

### RTS and CTS (credo = MACA) 🟨++

- Slide RTS and CTS

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 8.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 8">


Un altro problema di hidden terminal oltre alla trasmissione su un terminale comune è il fatto che se CB provano a comunicare a persone differenti (rispettivamente ad A e D, B non può perché sente ricevere).

Una soluzione semplice è semplicemente chiedere al canale ricevente se ci sono interferenze o meno. (un pacchetto breve che si chaiama **RTS (request to send)**.) questo è un piccolo pacchetto, potrebbe interferire, si spera che faccia molti pochi interferenze.

Il ricevitore risponde con un **CTS (clear to send**) Se il cts è ricevuto allora comincia a rispondere.

→ Non ho carrier sensing qui.

### RTS and CTS drawback

Non abbiamo garanzia di comunicazione senza interferenze, questa garanzia c'è solamente quando il range di comunicazione sono uguali fra di loro, un esempio in cui non funziona è l’esempio qui sotto in cui esiste una rete grande ch epossa andare a fare interferenza con tutte.

- Slide drawback

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 9.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 9">


### MACAW

Voglio ritardare il RTS in un tempo casuale in modo che non sovrappongano fra di loro. C'è carrier sensing **per gli acks, posso spedire solo quando mando RTS così posso ricevere ack in silenzio. Gli altri quando sentono dovrebbero restare in silenzio.

- RTS
- Carrier sensing (anche questa credo sia la cosa nuova, il sistema RTS/CTS è lo stesso di MACA)
- backoff (questa è l’unica cosa nuov acredo).

L’unico che ha preso la RTS sarà l’unico a comunicare, gli altri stanno in silenzion perché sentono il canale occupato.

Si può settare il RTS threshhol superiore alla soglia per dire che non verrà mai utilizzato.

- Esempio MACAW

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 10.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 10">


Che è molto simile a un coordinator function with backoff, solo che questo è senza infrastruttura, mentre nell'altro credo ci sia.

### Ad hoc networks (non chiede)

Ci sono delle cose nuove che sono delle **veicole infrastructures** ossia in realtà non esisterebbe una infrastruttura per questa connessione, ma passa da veicolo a veicolo quindi è una comunicazione locale. fino a un certo punto in cui alla fine si comunica con una infrastruttura. Come se le auto stesse fossero diventati dei sensori del traffico (quindi molte auto ferme riescono a dire se c'è troppo traffico o meno.

non sono ancora diffusi questi servizi, ma stanno arrivanto, u n altro metodo è fare unità di ricarica per i veicoli.

C'è una trasmissione con CSMA/CA , poi c'è una **fase di contention** in cui si potrebbero trasmettere cose e cose di altro tipo. ci otrebbero essere un sacco di rts che vadano a vuoto. Ognuna delle fasi di rts è un passaggio indipendente in cui si rischia ancora la collisione.

Ma quando trasmette indietro potrei avere delle (la collisione :

1. **Fast forward intra-stream** in cui il RTS del nodo successivo è interpretato dal nodo davanti come se fosse un ACK, questo risolve il problema delle itnerferenze (la fase di contesa non ci sarebbe più). (c'è un campo che rappresenta il tipo di questo segnale, che valga sia come ack sia come rts).
2. **Quick exchange inter-stream**, se i due nodi intermedi hanno cose da scambiarsi in direzioni diverse, potrebbe essere una buonissima soluzione il fatto di scambiarsi i dati nello stesso stream di dati (dopo l'ack di una direzione viene mandato il dato dell'altra direzione).

Se uno cade allora c'è tempo vuoto e viene itnerpretato come autorizzazioen alla trasmissione

### Carrier sensing virtuale (non chiede)

Carrier sensing **virtuale** sapere che il canale sia occupato senza andare ad ascoltarlo?
Appena sentono un RTS, e se sanno la lunghezza del campo di trasmissione classico (**Network Allocation Vector NAV)** allora sicuramente nessuno ascolta il canale.

Questo fa risparmiare batteria al destinatario. E trasmettere prende un sacco di energia, anche solamente andare ad ascoltare consuma.

### FAMA (non fare)

Voglio utilizzare una solgia **adattiva** oltre la quale comincio ad utilizzare il meccanismo rts/cts. Solitamente questo mi serve quando ho troppe connessioni.

Se il frame è minore di una soglia allor anon ha bisogno di rts/cts, altrimenti ha bisogno.

Anche questo è per reti ad hoc.

## Coordinator functions

Ci sono principalemente **due meccanismi** che vanno a regolare l’accesso al canale

- Slide coordination functions

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 11.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 11">


C’è l’access point che fa un **beacon** e che rende possibile la coordinazione (cose come il nome della rete e annuncio della sua esistenza è il beacon che sempre ogni tanto manda il beacon!).

Una volta fatto una comunciazione coordinata dà il temop alla DCF. In questo momento l’AP non comunca

### Point coordination function 🟩

- Slide PCF

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 12.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 12">


Quando esiste un access point che cerchi di evitare le collisioni e governi tutto la comunicazione nel canale.

Questa cosa è bella perché funziona anche se muore l'access point. Ma alla fine l’unica cosa rimasta è la DCF, quindi abbiamo molte più collisioni. (perché creare firmware era molto costoso).

### Interframe spaces 🟩-

- Slide Interframe spaces

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 13.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 13">


Point, ditributed and short,, sono una d**durata di tempo in cui carrier sensing** deve avere vuoto prima di poter tentare di comunicare.

- SIFS tempo prima di autorizzare la comunicazione qualcuno che sa già che deve parlare a seconda del contesto (e dovrebbe essere solamente un unico host) Se non parte significa o che sia morto o non ci sia nessuno. E Questo è necessario per avere un PIFS
- PIFS questo è il tempo per far parlare **l'access point.** se nemmeno questo c'è (ad esempio se l'access point vuole permettere la comunicazione contesa) allora il tempo aumenta e diventa un difs. (può essere che trasmettino un polling, con l'id di quello che deve andare a trasmettere).
- DIFS Questo è come dire un **liberi tutti** quindi si rientra al tempo di contesa del WIFI.

### Distributed coordination function 🟩

- Slide DCF

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 14.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 14">


Spazio RTS-CTS anche adattivo con una soglia

Tempo è avoidance con carrier sensing, in un ambiente **distribuito**. In questo caso tutti provano a comunicare, finché non ci riescono.

Lo slot non è l'intero frame come in ALOHA, ma solamente il **tempo di propagazione** (esempio il tempo necessario per la luce in 100 metri), gli slots sono messi in questo senso. Nello slot successivo sicuramente il tentativo è stato ricevuto.

il backoff è basato sul numero di questi slot vuoti che abbiamo ascoltato. E se vado a 0 allora mi metto a comunicare in modo descritto da sopra.

Il numero degli slot dovrebbe dipendere dal numero di comunicanti questo non è a priori definito (e non è nemmeno possibile stimarla secondo il prof).

### Gestione del backoff 🟩

- Standard 802.11 per backoff

    <img src="/images/notes/image/universita/ex-notion/Mac Wifi/Untitled 15.png" alt="image/universita/ex-notion/Mac Wifi/Untitled 15">


Il backoff è via via crescente, si potrebbe dire che sia la come la dimensione della finestra di contesa **CW = contention window** che è diversa rispetto alla congestion window, però il signfiicato è completamente diverso! Congestion trattato in [Livello di trasporto](/notes/livello-di-trasporto) serve per mandare tot frammenti allo stesso tempo senza far esplodere il router (il livello è diverso!) mentre ora siamo a livello fisico, e si prova a comunicare localmente.

La cosa brutta è che deve andare a sperimentare contesa per sapere quanta contesa ci sia! Per questo motivo si dice che non sia efficiente: se il canale è occupato con questo metodo ci provi lo stesso e quindi vai a disturbare.

Quando va a 0 allora io faccio proprio la tramissi contione e aspetto ack, se arrivo è ok, altrimenti si aumenta timer nel backoff e si rifà. Continua finché non ce la fai.



# References