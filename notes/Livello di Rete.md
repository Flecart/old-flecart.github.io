---
layout: page
permalink: notes/livello-di-rete
tags: en
title: Livello di Rete
---

Ripasso Prox: 50
Ripasso: June 14, 2023
Ultima modifica: May 13, 2023 11:59 PM
Primo Abbozzo: October 12, 2022 9:50 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Reti di Reti

Le parti importanti per questo sono [Data Plane](/notes/data-plane) e [Control Plane](/notes/control-plane) (che ha saltato quasi tutto, ma almeno dijkstra lo dovresti fare bene)

## Introduzione (puoi skippare 🟩)

La puoi skipppare perché tratta in modo molto generare parti che saranno trattati in modo più approfondito in seguito. La parte importante forse è il riassunto di cosa faccia questo livello.

### Discussione rete locale globale

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled.png" alt="image/universita/ex-notion/Livello di Rete/Untitled">


> No, non è possible creare una connessione globale utilizzando le tecnologie locali, come hub, switch e simili, perché causerebbe **flooding** e impedirebbe scalabilità e crescita dinamica che è classica della rete
>

Se i milioni di calcolatori oggi connessi a Internet fossero tutti organizzati secondo i protocolli e gli schemi visti finora per le reti locali, la comunicazione tra due calcolatori su Internet richiederebbe di passare per migliaia di calcolatori intermedi, switch, bridge, segmenti di rete, ognuno dei quali aggiungerebbe ritardi di gestione, complessità, rischi di errore. Il **problema dell’instradamento** dei frame (routing), ovvero il decidere da che parte o su che segmento deve essere inoltrato un frame per raggiungere il destinatario finale, richiederebbe in ogni dispositivo una lista completa (tabella di instradamento) di tutti gli indirizzi MAC dei dispositivi nel mondo, con a fianco l’indicazione della direzione di inoltro. Ovviamente questo limiterebbe in modo *critico* la scalabilità e la crescita di Internet. Inoltre **causerebbe flooding** perché praticamente ogni pacchetto di ogni computer rete di internet dovrebbe passare da ogni computer.

Una soluzione semplice consiste nell’elezione di un **rappresentante per ogni rete locale** X (e indichiamo con la rete sotto di essa come **dominio di rete locale**) (il router di X), incaricato di ricevere tutti i pacchetti dati destinati a uno dei calcolatori della rete locale (es. mac1 di X, mac2 di X, ecc.). Ricevuti i pacchetti destinati alla rete locale, il router potrebbe occuparsi di recapitare alla rete locale i pacchetti, come se si trattasse di un frame a livello
MAC/LLC destinato all’indirizzo MAC del destinatario. Allo stesso modo, ogni router dovrebbe farsi carico di inoltrare tutti i pacchetti uscenti dalla propria rete locale, verso i router delle reti di destinazione. Per rispettare le direttive dettate dallo standard ISO/OSI, il livello di indirizzamento e la gestione dell’instradamento dei pacchetti tra i router vengono gestiti al terzo livello (rete) della gerarchia dei protocolli di Internet.

Per ciò che riguarda i router, tuttavia, lo scambio diretto tra router di pacchetti destinati alle rispettive reti locali potrebbe ridurre molto la complessità dell’instradamento. I router comunicano quindi attraverso collegamenti dati molto veloci, dette **dorsali (backbone)**. Ogni router deve ricordare in una **tabella di instradamento (forwarding table)** solo quale sia il primo router
intermedio per raggiungere ogni altro router. La visione del sistema al terzo livello (Rete) da parte dei router è quindi simile alla visione che appare a destra nella figura. Si nota come tutti i dettagli delle reti locali siano di fatto nascosti dai router a questo livello.

Il router deve avere una mappa fra gli indirizzi IP e i mac!

### Obiettivi generali del livello (6) (!) 🟥+

**Sintassi**

1. Struttura gerarchica fra dominio e host (per facilitare l’invio)
2. Busta a livello arancione, terzo livello.

**Semantica**

1. Frammentazione dei dati
    1. Questa parte non è più esistente per gli IPv6, perché è un overhead in più che non si vuole dare ai router
2. Si occupa **solamente di inviare**. Un motivo per cui succede è l’efficienza, tenere in memoria questa cosa è molto costosa. I router devono solamente tritare pacchetti!
    1. Forwarding dei pacchetti, inoltramento dei pacchetti
    2. O ricezione del pacchetto se è giusto.
    3. Non si occupa di affidabilità del trasporto (di cui si occupa il livello mac e trasporto)

**Hardware (operazionale credo)**

1. Dispositivi fisici di questo livello, come i router (quindi tabelle di instradamento e protocollo di instradamento e aggiornamento)

### Protocollo di rete

- Slide1

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 1.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 1">

- Slide2

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 2.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 2">


In questa parte iniziamo ad analizzare il concetto di **rete globale**, ossia non è più locale!

Il livello rete di Internet si basa sul protocollo IP (Internet Protocol). Il protocollo IP definisce un nuovo schema di indirizzamento globale e gerarchico, che permette di **identificare univocamente** tutti i dispositivi di rete e allo stesso tempo la loro rete locale di appartenenza. Gli indirizzi usati permettono di identificare intere reti locali come un riferimento singolo nella gestione dell’instradamento dei pacchetti. Questo fatto semplifica molto la visione della rete che appare al livello Rete. Al protocollo IP, si possono associare **protocolli di instradamento** dei pacchetti dal mittente al destinatario finale (forwarding), originando servizi di trasmissione a pacchetto di tipo connectionless. Il protocollo IP richiede l’adozione di nuovi dispositivi amministratori dell’inoltro dei pacchetti a livello Rete, detti router.

### Router

I router sono forniti di **tabelle di instradamento** che illustrano la topologia della rete vista al livello dei router stessi (quindi non è necessario conoscere gli indirizzi dei calcolatori di una LAN al di fuori della LAN stessa. I router devono implementare protocolli di aggiornamento delle tabelle di instradamento (detti protocolli di routing). Ulteriore compito dei router è la **gestione della frammentazione dei dati** da spedire nei pacchetti, e la creazione della busta di livello rete con gli indirizzi del router mittente e destinatario di ogni pacchetto inoltrato.

Sono improntate alla efficienza! Principalmente è solo hardware che è in grado di far arrivare e partire un pacchetto a ogni ciclo di clock.

### Non self-similar 🟩

Si è tentato di cercare di predire i dati futuri pensando a quanti dati ho ora. Ma si è scoperto che non è proprio possibile, perché ci sono dei **burst** di richieste, dipendenti dalle richieste delle singole applicazione, per questo motivo sembra che sia un sistema caotico (esempio della farfalla). Principalmente perché questo è dipendente dai media (es. youtube).

## Indirizzo IP

> Gli indirizzi IP sono una nuova specie di indirizzi rispetto al MAC, necessari per il Protocollo omonimo;
>

### Header IP 🟨++

- Slide del formato IP

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 3.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 3">


Questo è il bellissimo pacchetto di livello trasporto 🙂. NOTA: vedi che contiene il pacchetto dello stato superiore.

1. Version sono 4 bit per la versione.
2. Dimensione dell'header in byte (che il campo options lo rendere variabile).
3. Il campo Type of Service, o TOS, definisce il **valore di priorità**, di cui abbiamo parlato [Scheduling dei routers (3+) 🟩](/notes/scheduling-dei-routers-(3+)-🟩). Che è principalmente utilizzato in internet due (basta un router che  non lo sia e fa droppare le garanzie). (solitamente è ignorato).
4. 16 bit per la lunghezza, quindi al massimo posso mandare 65k nel payload.
5. L’identificazion di 16 + cose bits è per capire la targa, meglio per la frammentazione (quel sistema per spezzattare file lunghi e inviarli a pezzetti), sono ricomposti a destinazione, il router lo ignora 🙂, l'ultimo ha flag a 0, e offset più lungo
6. Time to live è una cosa che viene decrementata ad ogni router e viene dropatto il pacchetto se vado a 0
7. Upper layer è il protocollo di livello 4 da utilizzare.
8. Per verificare se non ci sono stati errori di trasmissione. (Che è molto facile da manipolare, però buono per errori a caso di trasmissione).

Alcune opzioni tipo la rotta da prendere (tipo i router da visitare), itmestamp,  La cosa è che questa parte è variabile.

C'è un over**head di 40 bytes!**.

### Frammentazione e Reassembly 🟩

Per questa parte concetti importanti da comprendere sono:

1. Perché si fa frammetnazione (MTU) e perché si riassembla solamente alla fine.
2. Campi dell’header IP utili alla frammentazione e perché vengono utilizzati.

Non ha molto senso fare reassembly in mezzo, perché il pacchetto potrebbe fare una altra strada, sono indipendenti una volta spediti.

- poi si potrebbero fare fragmentation anche in un router intermedio, si potrebbero fare fragmentation ancora dopo!

Frammentazione è necessaria se il pacchetto è più grande del **MTU Maximum Transfer Unit.**

- Slide esempio di fragmentazione

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 4.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 4">


### Struttura IPv4 🟩

Un indirizzo IPv4 è un valore espresso su **32 bit (4 Byte)**, e può essere espresso anche come sequenza di 4 valori decimali, separati da punto. Ogni valore decimale può essere compreso tra i valori 0 e 255. Un esempio di indirizzo IP valido è (130.136.250.1).

Ogni indirizzo IP è sempre composto da due parti:

1. numero della rete IP alla quale appartiene la scheda (**network number**),
2. numero dell’interfaccia di rete (**host number**) all’interno della rete IP.

Esistono dei numeri speciali per ogni rete:

Host tutti 0 e tutti 1

- Tutti 0 → indica la rete stessa
- Tutti 1 → indica l’indirizzo di broadcast

### Datagramma IPv6

- Slide IPv6

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 5.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 5">


IL nextheader dice il protocollo che sta sopra, stesso di upper level di sopra

- Il campo priority è siile al Type of service, ci da la priorità del flusso di dati
- Flow label identifica il flusso di dati (infatti non c’è la frammentazione), anche se non è ben definito il concetto di flusso.
- Hop limit è la stessa cosa del time to live.
- Flow label (questo è molto importante!, se il flusso identifica una comunicazione, non ho bisogno di indirizzi sorgente, finale, porta etc., per questo motivo posso compattare le informazioni!)

## Struttura delle reti

### Univocità e statico/dinamico 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 6.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 6">

- Esempio slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 7.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 7">


Attualmente usati si riferiscono al protocollo IP versione 4, (IPv4). Un indirizzo IP viene associato a una e una sola (**univoca**) interfaccia di rete (scheda di rete). Potrebbe essere contemporaneamente identificato da più di un indirizzo IP nel caso in cui ci siano più interfaccie di rete (e più MAC). Se l’associazione univoca tra indirizzo MAC dell’interfaccia di rete e l’indirizzo IP rimane sempre lo stesso, allora si parla di I**P statico**. In caso contrario, se può cambiare l’associazione MAC-IP a seconda di vari fattori, si parla di **IP dinamico**. (cambio da dove mi connetto!).

Quando è statico è utile quando stiamo ad offrire dei servizi, così non devo fare aggiornamenti, i computer sanno che strada devono fare per raggiungere un certo computer.

### Classi di rete 🟩

Sono definite tre classi di reti IP, che si differenziano sulla base del numero massimo di host supportabili. Il valore dell’indirizzo IP determina la classe della rete: A,B,C (vedere figura).

Le reti di **classe A** sono al massimo 126 e ognuna può contenere fino a oltre 16 milioni di host. Per le reti di classe A, il byte di indirizzo più significativo (a sinistra) ha sempre il primo bit uguale a zero, e può assumere i valori da 1 a 126 (network number) rispetto ai 128 valori possibili. I tre byte rimanenti possono assumere oltre 16 milioni di combinazioni, ognuna associabile a un host della rete. 0XXXXXXX.xxxxxxxx.xxxxxxxx.xxxxxxxx

Una nota particolare è l'indirizzo 127 che è un indirizzo di **loopback** perché fa finta di uscire, e poi all’ultimo rientra. Questo indirizzo è utile per testare protocolli di rete.

Le reti di **classe B** sono al massimo 16.382 e ognuna può contenere fino a oltre 64.000 host. Per le reti di classe B, il network number è dato dai due byte di indirizzo più significativi (a sinistra), che hanno sempre i primi due bit uguali alla coppia (uno,zero). I network number di classe B possono assumere i valori da 128.0. a 191.255. I due byte rimanenti (host number) possono assumere oltre 64.000 combinazioni, ognuna associabile a un host della rete.

forma di 10XXXXXX.XXXXXXXX.xxxxxxxx.xxxxxxxx

Le reti di **classe C** sono oltre 2 milioni, e ognuna può contenere fino a 254 host. Per le reti di classe C, i tre byte di indirizzo più significativi (a sinistra) rappresentano il network number, e hanno sempre i primi tre bit uguali alla terna (uno,uno,zero). I network number di classe C possono assumere i valori da 192.0.0 a 223.255.255. Il byte rimanente (host number) può assumere 254 combinazioni utili, su 256 possibili, ognuna associabile a un host della rete.

110XXXXX.XXXXXXXX.XXXXXXXX.xxxxxxxx

**Convenzione** l’ultimo IP disponibile per l’Host di solito è dato al Router.

### Sottoreti e netmask !!! (3) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 8.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 8">

    La figura mostra a sinistra uno schema gerarchico di strutturazione di una rete di classe B. A partire dall’alto troviamo il router principale (default router) della rete 130.136, il cui indirizzo IP è nell’esempio 130.136.0.254. Alla rete 130.136 appartengono anche tre router subordinati, con IP 130.136.1.254, 130.136.2.254, 130.136.3.254 rispettivamente amministratori delle sottoreti (130.136.1.), (130.136.2.) e (130.136.3.).


**Netmask**

Il Netmask identifica nelle zone in cui è settato 1 l'indirizzo di rete e sottorete, dove è 0 l’indirizzo di host. Quindi ci dice ìl modo con cui si interpreta un byte di rete. **Obbligatoriamente** deve essere in questa forma ($$1^n0^m: n + m = 32$$ se vogliamo utilizzare una sintassi più famigliare da Linguaggi di programmazione).

Il concetto di creare sottoreti si può riassumere in **frazionare** l’host in altre due parti che rappresentano l’indirizzo di sottorete e l’host. Queste sono nuove **componenti logiche**.

Facendo questa operazione abbiamo $$nreti \times(nhost - 1)$$, mentre prima era  $$nhostgrosso$$. Alla fine se si svolge questo calcolo sono stesso numero di host, (magari perdo nreti numero di host per i router, però la ho gerarchizzata meglio).

Esiste una notazione molto più carina per i netmask che è il **CIDR** (Classless Interdomain ROuting) in pratica stai dicendo quanti bit sono messi a 1

**Creazione sottoreti**

In questo modo è possibile creare **una gerarchia di sottoreti**, ognuna delle quali è amministrata da un router (il default router). Esempio: data la rete di classe B 130.136. per semplicità decidiamo di considerare possibili 256 sottoreti: netmask 255.255.255.0.

Il numero della sottorete è quindi fornito dai primi tre byte dell’indirizzo IP, es. 130.136.1. è la sottorete 1, 130.136.2. è la sottorete 2, mentre ad esempio 130.136.1.22 è l’host 22 della sottorete 1, 130.136.3.48 è l’host 48 della sottorete 3, e così via. (quindi un router sottorete ora prende IP del genere 130.136.1.254, perché indica la sottorete 1 della rete di classe B che si possiede).

Per istruire ogni router subordinato sulla dimensione e sull’interpretazione degli indirizzi IP da amministrare, ogni router subordinato deve essere fornito di una maschera di rete (netmask), evidenziata a destra.

**Elementi fondamentali per il Protocollo IP**

Senza questi tre elementi il protocollo IP non funziona proprio. Quindi è la prima cosa da fare per configurarlo.

1. Maschera di rete
2. Indirizzo IP
3. Indirizzo default di router (il primo router sopra la gerarchia, che è a chi mandare quando non so a chi mandare). (può essere che con dispositivi stupidi abbiamo solamente l’indirizzo del router).

La maschera di rete serve per capire

**Netmask**

In particolare rileviamo qui 2 funzionalità principali per questo netmask:

1. Dire quanti subnet esistono, oltre alla rete principale
2. Far sapere all’host a quale rete appartiene

È quindi una quantità fondamentale per configurare la regte

### Classless Inter Domain Routing 🟩

Questo nuovo modo per fare netmask (nuovo rispetto gli anni 80) è un modo per avere tagli di rete più efficienti, nel senso che se prima la C non bastava, ti davano una B( Renzone a unibo ha avuto in questo modo una classe B). Ora possono avere molta più disponibilità per i tagli negli indirizzi di rete. Questa cosa permette anche un concetto di **supernetting**. (in cui ho un insieme condiguo di classi più piccole, e così mi creo una rete maggiore, più grosso delle classi, così ho maggiore dinamicità).

**Esempio forwarding dei Pacchetti**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 9.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 9">

- Slide esempio

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 10.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 10">

    La figura mostra un esempio di instradamento su rete IP. Esistono tre router Ry, Rz e Rk rispettivamente amministratori delle reti (140.217.), (190.89.), e (130.136.). Il router Ry è connesso a Rz, e Rz è connesso a Rk. Tale informazione risulta dalle tabelle di instradamento di Ry, Rz, Rk. La rete del router Ry include due sottoreti (140.217.1.) e (140.217.2), amministrate dai rispettivi default router 140.217.1.254 e 140.217.2.254 . La rete del router Rk include tre sottoreti (130.136.1.), (130.136.2.) e (130.136.3.), amministrate dai rispettivi default router 130.136.1.254, 130.136.2.254 e 130.136.3.254 . Un pacchetto IP spedito dall’host 140.217.2.10 all’host 130.136.2.33 deve compiere il seguente tragitto: passa per il default router di sottorete 140.217.2.254 che, notando che il destinatario non appartiene alla sottorete, lo inoltra al default router del livello superiore di rete: 140.217.0.254. Il default router di rete controlla la propria tabella di forwarding e scopre che per raggiungere la destinazione il pacchetto deve essere inoltrato al router intermedio 190.89.0.254. Il router intermedio riceve il pacchetto, verifica la propria tabella di forwarding, scopre che il prossimo destinatario intermedio è il router 130.136.0.254, al quale inoltra il pacchetto. Il router 130.136.2.254 riceve il pacchetto e verifica che appartiene alla propria rete, inoltrando quindi il pacchetto internamente. Il router di sottorete 130.136.2.254 riceve il pacchetto e scopre che appartiene alla propria sottorete, inoltrando il pacchetto internamente. Finalmente, l’host 130.136.2.33 riceve il pacchetto a lui destinato. Si possono notare alcuni aspetti importanti: malgrado il numero elevato di host che potrebbero essere parte del sistema considerato, il processo di instradamento permane molto semplice, composto da piccole e semplici operazioni di base. Le tabelle di instradamento sono limitate agli elementi che agiscono allo stesso livello, e quindi l**’instradamento è gerarchico**.


### Routing 🟨

Si parlerà molto meglio del routing in [Data Plane](/notes/data-plane) e [Control Plane](/notes/control-plane)

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 11.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 11">


Il problema del routing può essere definito come il problema di mantenere l’aggiornamento delle tabelle di forwarding in tutti i router della rete.
Questo problema può essere a volte molto complesso, a causa di frequenti modifiche forzate dei cammini per i pacchetti in rete. Le cause di tali modifiche possono essere dovute a molti fattori, ad esempio: la mobilità degli host in reti senza fili, guasti di mezzi trasmissivi, interruzione delle linee, guasti di router, nuove politiche e accordi per lo scambio dei dati tra gestori di dorsali
e sistemi autonomi.

Un **sistema autonomo** (AS) è sinonimo di una grossa rete, o una collezione di reti, soggetta a una comune politica di amministrazione. Gli accordi commerciali tra gestori di AS possono modificare i cammini consentiti per lo scambio dei pacchetti di dati.
Per realizzare un parallelo intuitivo, gli AS si comportano come nazioni che permettano o meno il passaggio di pacchetti, analoghi a voli aerei, sul loro suolo nazionale.
Ogni volta che si verifica uno dei problemi citati, esistono router che hanno indicazioni errate nelle loro tabelle di forwarding. Tutto ciò può causare la perdita di pacchetti, oppure può determinare un disordine nell’arrivo di pacchetti che hanno seguito strade diverse. Ecco quindi una causa del servizio connectionless ottenuto dal livello rete basato solo sul protocollo IP. I router hanno bisogno di aggiornare al più presto le loro tabelle, per evitare malfunzionamenti del servizio.

In pratica fanno lo stesso modo per decidere dove mandare, cioè hanno lo stesso protocollo, ma dato che si trovano in parti diverse avranno poi tabelle di instradamento diverse.

la **Core network** è molto veloce nel trovare il percorso giusto (è molto più fisso, e sa più o meno dove mandare le cose).

I **protocolli di routing** hanno la funzione di richiedere e scambiare informazioni per trovare cammini alternativi (idealmente il cammino migliore tra le possibili alternative), tra mittenti e destinatari dei pacchetti, e consentire quindi l’aggiornamento delle tabelle di forwarding.
A puro titolo informativo, si citano alcune sigle di protocolli di routing adottati in Internet: Routing Information Protocol (RIP), Open Shortest Path First (OSPF), Border Gateway protocol (BGP).
Questi algoritmi sono tutti utilizzati in locale. La cosa brutta è che il cammino ottimo cambia nel tempo (anche nell’ordine dei secondi), quindi gli algoritmi si devono abituare dinamicamente a questi nuovi dati.

**Note sistemi distribuiti o centralizzati**

Il centralizzato è bello perché è chiaro a chi chiedere per andare poi a mandare il pacchetto dove si vuole, il problema è che se il nodo centrale fallisce, cade l'intera rete.

Distribuito è bello perché risolve il problema del single point of failure però dall’altra parte ogni nodo non ha una visione globale quindi non può fare altro che andare a massimizzare localmente, che spesso non è la cosa migliore.

**Wikipedia sui sistemi autonomi**

[Link](https://it.wikipedia.org/wiki/Sistema_autonomo), in pratica singola autorità amministrativa è la parola chiave.

## Protocolli basati su IP

### Protocollo ICMP (6) 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 12.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 12">


ICMP (**Internet Control Message Protocol**) è un protocollo standard definito per supportare i messaggi di controllo per la **gestione della rete** al livello 3. ICMP viene usato da semplici host, da router e persino da gateway (router speciali con ulteriori funzioni) per scambiare informazioni utili alla gestione del livello Rete. Le informazioni scambiate sono trasferite sotto forma di pacchetti IP. Utile per stabilire una **sintomatologia** dei problemi di reti.

Alcuni esempi di messaggi ICMP che possono essere scambiati indicano, ad esempio:

1. situazioni di rete di destinazione irraggiungibile (possibile sintomo di problemi di routing, o di rottura di un router).
    1. In questo caso può convenire andare a cercare il problema di rete, che può essere fisico, e fixarlo in questo modo
2. rete di destinazione sconosciuta (possibile sintomo di indirizzo IP di rete male specificato)
    1. In questo caso il router non sa a chi mandare, quindi alcuni fix sono 1. aggiornare tabelle di instradamento, o provare altre strade.
    2. Ossia nessuno conosce l’indirizzo della rete locale
3. host di destinazione non raggiungibile (possibile sintomo che l’host sia spento o il cavo di connessione sia male collegato).
Questo è un problema che non ci riguarda, quindi probabile che l’host si sia sconesso.
Per questo significa che **la rete è conosciuta!**, quindi problema di rete locale!.
4. host di destinazione sconosciuto (possibile sintomo di host number del’indirizzo IP male specificato, malgrado la rete indicata esista e sia raggiungibile).
problemi con indirizzo IP
5. protocollo richiesto non disponibile (sintomo di un tentativo di dialogo tra dispositivi male configurati, che non forniscono i servizi richiesti). (come se stessi provando ad accedere a un servizio in una porta sbagliata, o versione IP sbagliata o simili).
6. ricerca di cammino alternativo (può essere usato per risolvere i problemi di routing).

Anche chi riceve il messaggio, può rispondere in modo preinpostato a quelle richieste. (e dato che è preimpostato non c'è bisogno di avere un frame grosso!).

### Applicazioni su ICMP (2) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 13.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 13">


Le applicazioni sono utilizzate solitamente per la verifica delle cause o del semplice sospetto di problemi di rete.
L’applicazione **PING** permette di testare la connessione tra due host: eseguendo il comando “ping <indirizzo IP di host2” da un host1 qualsiasi (mittente) connesso in rete, l’applicazione invia una richiesta ICMP di eco, alla quale l’host2 indicato risponde con una risposta ICMP (eco della richiesta). Dopo l’invio della richiesta, host1 fa partire un timer. In caso di successo, viene
calcolato il tempo di andata e ritorno dei pacchetti (durata o Round Trip Time, RTT), mentre in caso di insuccesso viene indicato che il timer per la richiesta inviata è scaduto senza ottenere risposta (secondo esempio della prima figura).
Al termine dei tentativi, viene mostrato un elenco di statistiche sul numero di richieste andate a buon fine e i tempi medi stimati di andata e
ritorno dei pacchetti.

L’applicazione Traceroute (**tracert**) permette di verificare la lista di tutti i router attraversati da una richiesta ICMP inviata da host1 a host2. Il comando “tracert <indirizzo IP di host2>” eseguito da host1, causa l’invio di una sequenza di richieste ICMP verso host2, per le quali viene fissato il numero massimo di router da attraversare (numero di passaggi o tempo di vita, TTL), a valori crescenti da 1 in poi. Ogni router a distanza TTL risponde con un messaggio ICMP di errore (tempo di vita scaduto) attraverso il quale è possibile risalire al suo indirizzo IP (ognuno mostrato su righe successive).

### Protocollo ARP e RARP 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 14.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 14">

- Slide immagine

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 15.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 15">


Il protocollo **Address Resolution Protocol (ARP)** aiuta a gestire l’associazione tra indirizzo IP di un dispositivo a livello rete e il suo indirizzo MAC a livello MAC/LLC .
Quando un router riceve un pacchetto a livello IP destinato alla sua sottorete (es. 130.136.2.33) esso verifica se a tale IP risulti o meno associato un indirizzo MAC.
In caso contrario, il router spedisce sui segmenti della rete locale un frame in *broadcast* (cioè ricevuto da tutti i dispositivi) contenente il codice di richiesta ARP, e l’indirizzo IP del destinatario del pacchetto. Tutti i riceventi vanno a confrontare, e se matcha risponde.

- Intuiviamente

    Tale frame equivale quindi al rivolgere a tutti i dispositivi la domanda: “quale indirizzo MAC ha il dispositivo corrispondente al seguente indirizzo IP”? Il dispositivo in questione, se esiste, risponde con un frame indirizzato all’indirizzo MAC del router, contenente il codice di risposta ARP, e con allegato l’indirizzo MAC richiesto.
    A questo punto il router può quindi preparare e spedire la busta di livello MAC/LLC, indirizzata al MAC del dispositivo destinatario del pacchetto IP, contenente il pacchetto IP incapsulato all’interno. Il destinatario riceve il frame e risponde con il frame di conferma per il sottolivello LLC.


Quando è risposto possiamo andare a mappare l’IP con il MAC locale. Chi ha il MAC corrispondente può rispondere col proprio IP.

Esiste anche una versione analoga del protocollo ARP, detta **Reverse-ARP**, che risponde alla domanda: “quale indirizzo IP corrisponde al dispositivo con questo indirizzo MAC”?.
Può essere utile ad esempio se mi arriva un pacchetto a un IP nella mia sottorete, ma non so a quale host è destinato.

### Protocolo DHCP 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 16.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 16">

- Slide di immagine

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 17.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 17">


Questo protocollo è utilizzato per assegnare un IP in modo dinamico. **porta 67**, unico all'interno della rete, chi non ha un servizio lì aperto droppa il messaggio.

**Introduzione: assegnazione IP**

I numeri di rete delle classi A, B e C, ovvero la parte sinistra degli indirizzi IP vengono assegnati da enti internazionali quali RIPE, ICANN, ARIN, APNIC a enti, aziende, consorzi e imprese che ne fanno richiesta motivata. Un problema molto più pratico riguarda il modo in cui un nuovo dispositivo che venga connesso a una rete esistente, veda associare al proprio indirizzo MAC un indirizzo IP della rete stessa. Il numero di rete o di sottorete viene automaticamente determinato dall’appartenenza alla rete, ovvero alla presenza al di sotto del dominio di gestione di un router.

**Soluzioni**
La prima, ovvia alternativa (molto usata) è quella di avere un amministratore di rete che assegna manualmente uno dei numeri di host disponibili al nuovo indirizzo MAC. In questo modo l’associazione indirizzo MAC e indirizzo IP può essere mantenuta per un tempo indeterminato, e quindi si considera l’indirizzo IP come statico.

La seconda alternativa, molto usata in reti senza fili, in reti locali e nei collegamenti domestici a Internet Service Provider (ISP) via Modem o ADSL consiste nell’utilizzare un server per Dynamic Host Configuration Protocol (**DHCP**).
Il server DHCP è dotato di una lista di numeri di host liberi per la sottorete amministrata, che provvede ad associare su richiesta agli indirizzi MAC dei dispositivi che lo richiedono. Tale associazione dipende spesso dalla disponibilità degli indirizzi già assegnati in precedenza, quindi allo stesso indirizzo MAC possono essere associati di volta in volta indirizzi IP diversi, e si parla in questo caso di indirizzi IP dinamici. E’ possibile configurare attraverso DHCP anche altri parametri di rete, come la maschera di rete, il defaul router e il server DNS (che vedremo dopo).
Il servizio DHCP equivale spesso al concetto di rete “**plug and play**”, ovvero rete in cui basta connettere il dispositivo al medium e non c’è bisogno di nessuna configurazione manuale aggiuntiva. È questo è quasi un must per le reti wireless! Sarebbe improponibile che ci fosse un sistemista ad assegnare un indirizzo IP per ogni dispositivo che si connette!

**In breve:**

1. Host che assegna IP a chi lo richiede
2. Gestione degli IP liberi e associazione ai MAC
3. Questa è chiaramente una forma di **indirizzamento dinamico** discusso in Univocità e statico/dinamico 🟩

Ogni tot di tempo è fatto un **ping** se la macchina risponde è ancora lì, altrimenti libera l’IP.

**MAGGIORE DETTAGLIO 4passi**

- Slides

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 18.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 18">


È importante avere 4 passi, perché l’HOST deve rispondere con la scelta del DHCP, nel caso in una sottorete ci siano molto DHCP.

ma **Non esiste nessuna autenticazione**, quindi è molto fragile ad attacchi (uno si potrebbe impersonare a DHCP senza problemi). I primi due passaggi sono facoltativi, ma lo rendono più solido contro possibilità di avere 2 DHCP server.

NOTA: comuqnue non è un protocollo per dare IP a dispositivi mobili che si spostino.

### IPv6 e tunnelling 🟩

- Slide

    https://www.notion.so

- Immagine

    Nella figura viene mostrato come sia possibile spedire pacchetti IPv6 tra due router IPv6 passando per cammini che includono router IPv4, attraverso il tunnelling IPv6 in IPv4. Il pacchetto IPv6 viene incapsulato dai ogni router IPv4 in pacchetti IPv4, in modo da poter essere instradato lungo la rete di router IPv4. Uscito dal tunnel IPv4 il pacchetto IPv6 prosegue il suo inoltro fino alla destinazione IPv6 finale.

    <img src="/images/notes/image/universita/ex-notion/Livello di Rete/Untitled 19.png" alt="image/universita/ex-notion/Livello di Rete/Untitled 19">


Il motivo principale della necessità di IPv6 è la necessità di altri indirizzi IP.  IPv6 perché hanno tentato di fare un IPv5 in molti modi ma sono caduti in disuso.

**Non c'è frammentazione**, con IPv6, mentre IPv4 ha bisogno… questo toglie il lavoro del router, e quindi rende tutto più veloce.

Dal 1990 è stato avviato un progetto di definizione e sviluppo di una nuova versione del protocollo IPv4, denominato versione IPv6. In seguito all’esplosione del collegamento di calcolatori in rete, e quindi dell’utilizzo di indirizzi e reti IP, le proiezioni mostrano che al ritmo attuale gli indirizzi IPv4 saranno esauriti nel decennio 2008-2018.
Brevemente, le caratteristiche salienti di IPv6 vanno nella direzione di ovviare a questo problema, oltre a migliorare alcuni aspetti di IPv4.
La caratteristica fondamentale di IPv6 è la definizione di nuovi indirizzi IPv6 composti da 128 bit (16 byte), cioè ben quattro volte la dimensione degli indirizzi IPv4. Questo incredibile numero di indirizzi potrebbe consentire di avere circa 15000 indirizzi IPv6 per dispositivi diversi su ogni metro quadrato di superficie dell’intero pianeta, oceani inclusi.

Sono inoltre stati ridefiniti i campi che costituiscono la busta dei pacchetti di livello IPv4, aggiungendo ad esempio parametri per la gestione di flussi di pacchetti IP con diversi livelli di priorità. Purtroppo la definizione di IPv6 nella maggioranza dei casi non permette di continuare a usare i vecchi router IPv4, e quindi non è compatibile con l’attuale struttura di Internet.

**Tunnelling**

Il tunnelling è **fondamentale per la compatibilità** fra IPV4 e IPv6

La sperimentazione e lo sviluppo di IPv6 sta procedendo su reti IPv6 separate, che possono in certi casi integrarsi alle reti IPv4 usando la tecnica del **tunnelling** dei pacchetti IPv6 in IPv4. Quindi wrappo con un pacchetto IPv4 i router che capiscono solo IPv4.

Si chiama tunnelling perché il wrap ci assomiglia tanto!

### NAT

# Cose vecchie

### Confronto col MAC

L'indirizzo Internet Protocol è il protocollo internet a *livello 3* più utile per la comunicazione fra reti locali diverse. Una delle caratteristiche che la contraddistingue dal MAC è il fatto che sia **gerarchico**, ossia c'è una sorta di indirizzo generale, indirizzo specifico e indirizzo della rete locale!. Oltre al fatto che è gerarchico **non è univoco**, perché può succedere molto spesso che viene riassegnato.

### Caratteristiche IP (3)

- **Globale** perché non esiste rete connessa ad Internet che non abbia indirizzo IP;
- **Strutturato** perché è diviso in due parti, una per l’indirizzo della rete locale e l’altro per l’indirizzo della scheda di rete interna alla rete locale;
- **Gerarchico** perché appunto le due parti di indirizzo sono in ordine gerarchico (rete locale > scheda di rete).

### Indirizzamento IP

Se succede che due IP sono uguali, questo succede **solamente a rete locale** perché anche la prima parte dell’IP deve essere uguale, quindi se ne accorge il Router e risolve questo.

**Staticità e dinamicità**

Statico → IP associato a MAC

Dinamico → IP che cambia, quindi è più difficile

### Classi di rete

Dividiamo l’IP in 3 classi principali **A, B, C** a seconda di quanti IP riescono a supportare

**Classe A**

Il bit più significativo è 0. Quindi la prima sezione va da 1 a 126, perché 0 è utilizzato per l’identificazione. Sono quelle più prezione perché possono avere più host ($$2^{24}$$  host).

**Classe B**

Hanno i primi due bit come valore 10. e vanno da 128 a 191,

**Classe C**

## Router

I router ricevono pacchetti e guardano la parte di rete locale, se matcha è OK, viene inoltrato ad altri router della rete locale per smistare ulteriormente, altrimenti inoltra ad altri router in altre reti, attraverso i collegamenti chiamati **dorsali**.

### Tabelle e protocollo di instradamento

Queste sono tabelle che hanno un utilizzo molto simile a quanto utilizzato per lo switch, che mappa una porta a un indirizzo MAC. In questo caso mappa la tolopogia di rete (che non so in che modo sia intesa questa mappa). Di solito il router è collegato a **un solo altro router** che viene chiamato **default gateway**.

Il protocollo, invece, si occupa di aggiornare questa tabella secondo le occorrenza (TODO, non so su quali regole).

### Protocollo di routing

Questo protocollo che si occupa di trovare il percorso più breve, e di **frammentare** il messaggio originale in pacchetti più piccoli, ma senza fare controlli su un arrivo corretto di queste informazioni. Quind fa una scelta per capire che strada fare

### CIDR Classless Inter Domain Routing

Si utilizza una scrittura molto compatta per