---
layout: page
permalink: notes/introduzione-a-reti
tags: italian
title: Introduzione a reti
---

Ripasso Prox: 60
Ripasso: May 18, 2023
Ultima modifica: May 12, 2023 7:59 PM
Primo Abbozzo: September 19, 2022 11:11 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Vecchi ripassi
    - Esempi di rete di calcolatori e non
    - Metodi di valutazione della qualità della rete
    - Il connettore di rete


# 0 Introduzione

## 0.1 Introduzione

### 0.1.1 Definizione di rete di calcolatori (2) 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled">


I requisiti sono principalmente 2

1. Essere autonomi nel calcolo (capacità di eseguire dei programmi)
2. Essere interconnessi (capacità di ricevere ed inviare dei segnali)

Gli scopi sono principalmente per la comunicazione fra utenti o calcolatori.

**Non-esempi**

1. Rete telefonica, *non sono autonomi*
2. Rete televisiva

**Esempi**

1. Smartphones con wi-fi
2. WWW
3. E-mail

Una rete di calcolatori è un insieme di dispositivi autonomi, cioè in grado di eseguire e svolgere autonomamente i compiti programmati di calcolo e di comunicazione, interconnessi tra loro da supporti fisici alla trasmissione di segnali. Non sono considerate reti di calcolatori, ad esempio, né le reti di comunicazione telefonica (i cui terminali telefonici non sono dispositivi autonomi), né le reti di distribuzione televisiva (in quanto i televisori non sono dispositivi autonomi in grado di comunicare informazione).
Nel prosieguo della presentazione, con il generico termine di “rete” o “rete di comunicazione” intenderemo implicitamente solo le reti di calcolatori elettronici.
Con l’avvento dei calcolatori elettronici, e con la loro diffusione tra comunità sempre più grandi di utenti, è emersa l’esigenza e l’utilità di fornire un supporto alla comunicazione tra utenti, attraverso l’uso del calcolatore, supportando innovativi servizi di comunicazione per l’utente, quali ad esempio il World Wide Web e la posta elettronica. In tempi più recenti si sono sviluppati ulteriormente i sistemi di rete includendo Internet of Things (IoT), reti senza fili (Wireless), ecc.
Le necessità di comunicare e condividere informazione sono tra i principali motivi che favoriscono la nascita e lo sviluppo di reti di calcolatori. La fruizione dell’informazione contenuta in questo corso rappresenta un esempio.
Un ulteriore aspetto che ha favorito la nascita e la diffusione delle reti di calcolatori è legato alla possibilità di condividere dispositivi costosi, altrimenti sotto-utilizzati, come ad esempio stampanti o capienti dispositivi di memorizzazione dei dati, e la possibilità di accedere e lavorare sui dati di un calcolatore, senza doversi spostare fisicamente sul calcolatore stesso.
Una rete di calcolatori può consentire di eseguire calcoli complessi in parallelo e in maniera distribuita, aumentando le prestazioni per l’ottenimento dei risultati. In tal senso, le reti rendono possibile la scalabilità dei sistemi di comunicazione e di calcolo: il numero di dispositivi usati, e l’investimento relativo, possono essere dimensionati dinamicamente in funzione delle
richieste di servizio. In tempi recenti, le reti sono utilizzate in particolare per supportare la comunicazione utente, secondo svariate forme e applicazioni, oppure per supportare la comunicazione diretta tra dispositivi pervasivi e mobili (es. Internet of Things, Wireless Networks), ecc

### 0.1.2 Classificazione delle reti (5 principali) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 1.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 1">


Una prima classificazione delle reti di calcolatori si basa sulla **dimensione delle reti stesse**.
Non esiste in generale un criterio ben definito per tale classificazione, ma ci si basa su considerazioni generali, riguardanti la dimensione dell’area di copertura geografica della rete, ovvero l’area entro la quale possano esistere dispositivi connessi.

**Le reti personali (PAN)** sono reti di comunicazione per connettere dispositivi vicini tra loro, ad esempio sul corpo di una persona o entro una stanza.
Un esempio potrebbe essere dato dalla connessione di due dispositivi indossabili, sensori e smartphone, oppure calcolatori, una stampante e un agenda elettronica. Le reti personali sono di solito finanziate e gestite dal singolo utente che le utilizza.

**Le reti locali (LAN)** sono molto spesso reti gestite e mantenute da *organizzazioni, università, enti o aziende*. Esse connettono calcolatori nel raggio di qualche centinaio di metri, ad esempio su interi edifici o campus universitari. Ad esempio, la rete delle aule del Dipartimento.

**Le reti metropolitane (MAN)** hanno connessioni in un raggio dell’ordine delle decine di chilometri, e possono connettere intere aree urbane. Esse sono mantenute e gestite da fornitori di servizi di comunicazione (provider) e gestori di servizi telefonici.

**Le reti geografiche (WAN)** sono reti in grado di coprire distanze internazionali e addirittura planetarie. Tali reti sono mantenute e gestite da enti nazionali e internazionali, oppure da grossi enti o gestori delle comunicazioni. L’organizzazione e la struttura di tali reti può essere molto complessa, e può risultare composta da diverse parti, e da diverse tecnologie, eterogenee e integrate (ad esempio, molte reti collegate tra loro con tecnologie cablate o in fibra, fino a reti basate su comunicazione satellitare senza fili).

**Internet** (inter-networking, ossia comunicazione di rete fra *rete diverse*) è una rete di reti, composta da molte reti diverse connesse tra loro, integrate grazie a un insieme di regole comuni: i protocolli della rete Internet.

- Alcuni esempi
    1. PAN
        1. Anche reti all’interno del corpo stesso! (es. per autenticazione). (qualcosa che passa da un pezzo del corpo a un altro pezzo). (molto piccola)
    2. LAN
        1. Alma-wifi (wireless) → WLAN
    3. MAN
        1. Alma-wifi, perché ce in molte parti della città (diffusa con ripetitori, che all’insieme hanno una rete metropolitana).
        2. NOTA: MAN (e più in generale le reti) si possono espandere componendo reti più piccole
        3. NOTA: la grandezza della rete influenza i problemi che la rete deve risolvere.
    4. WAN
    5. Internet
        1. C’è un problema di comunicazione, come connettere tutti i calcolatori del mondo???


### 0.1.3 Evoluzione e costi della rete (storia, non richiesta) 🟨

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 2.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 2">


Lo sviluppo delle reti di calcolatori, che ha permesso la nascita di Internet, non sarebbe stato possibile senza una distribuzione dei costi di realizzazione e gestione delle infrastrutture tra molte entità.

**Un pò di storia**
Storicamente, la prima rete di Internet nasce da un esperimento nel 1969, connettendo solo 4 calcolatori di 4 università americane (con linee di telefoni!).

Da allora molte entità hanno dato il loro contributo per lo sviluppo e la diffusione delle reti di calcolatori.
All’inizio del 2003 Internet contava oltre 172 milioni di calcolatori (fonte Internet Software Consortium). Già nel 2017 si parla di oltre 4 miliardi di dispositivi connessi (anche se non tutti connessi allo stesso momento). Entro 5-7 anni si raggiungeranno i 60 miliardi di dispositivi connessi, realizzando l’avvento dell’Internet of Things.

Poi si è sviluppata (dal primo esperimento, si racconta che HELL sia stato il primo messaggio, poi c'è stato un system crash) grazie ad ingesti investimenti militari, poi aziende private. Queste aziende private poi rivendono al cliente finale.

**Sui costi**
Per quello che riguarda i costi, la realizzazione, mantenimento e gestione dell’infrastruttura di una rete molto ampia richiede investimenti economici elevati, che possono essere maggiori a seconda del grado di avanzamento delle tecnologie e delle prestazioni richieste.

**Costi MAN e WAN**

Alcune delle infrastrutture principali delle reti estese MAN e WAN (e di Internet) hanno costi affrontabili solo attraverso un consistente investimento e una pianificazione delle ricadute commerciali da parte di consorzi o fornitori di servizi di comunicazione nazionali e multinazionali.

**Costi LAN**

Tuttavia, la maggior percentuale del complesso delle infrastrutture di rete che compongono Internet risultano essere mantenute e gestite capillarmente da piccoli gestori e piccoli gruppi, con investimenti relativamente modesti per la realizzazione di piccole reti locali (LAN). L’integrazione di un insieme molto vasto di reti grandi e soprattutto piccole reti locali, eterogenee e distribuite su tutto il pianeta, ha permesso la crescita incrementale, il successo commerciale e la esplosiva diffusione delle reti su scala globale, fino a Internet.

**Costi utente finale**

L’utente delle reti paga tipicamente per i servizi di trasmissione offerti dalle reti, con tariffe che possono essere basate sul tempo di collegamento, sulla quantità di dati.

### 0.1.4 Valutazione prestazioni della rete (2) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 3.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 4.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 4">


Per ciò che riguarda le prestazioni delle reti di calcolatori, l’utente è principalmente interessato a due indici: la capacità di trasmissione (impropriamente detta velocità della rete) e il ritardo del collegamento di rete.

1. *La capacità di trasmissione* si misura sulla base della quantità di dati che è possibile comunicare in un secondo mediante la rete. I dati digitali del calcolatore si misurano in bit o in byte (gruppi di 8 bit), e di conseguenza l’unità di misura usata tipicamente per misurare la capacità di trasmissione dei dati di una rete è il numero di bit oppure di byte trasmessi al secondo
(bit/sec, byte/sec). Spesso si usano i prefissi Kilo (K) per le migliaia, Mega (M) per i milioni e Giga (G) per i miliardi di bit o byte al secondo, Tera (T) per le migliaia di miliardi, ecc. (esempio Kbit/sec, Kbyte/sec).
2. *Il ritardo del collegamento di rete* indica il tempo necessario ai dati per transitare dal mittente al destinatario finale sulla rete.
I fattori del ritardo (non solo questi):
    - la distanza fisica del collegamento
    - i tempi necessari alla gestione delle regole dei processi di comunicazione in rete (protocolli) che i dati devono subire durante il loro tragitto. (che può essere anche fisico letterale: eg. aereo o furgone, invece che fibra o reti, questo è un protocollo 🙂).
    - Variazione del ritardo (es. coda per furgoni, congestione delle linee e simili) **Jitter** (su quale sia meglio, dipende sempre dagli utilizzi → Streaming? o semplice scaricare? a seconda di quanto ci serve è meglio la rete blu o rossa)

Ovviamente sono da preferire reti dotate di basso ritardo, in quanto ciò favorisce la rapidità e l’interattività del processo di comunicazione.
Per fare un parallelo intuitivo, pensando alle reti come a tubi che trasportano bit, la capacità di trasmissione equivale al diametro del tubo, mentre il ritardo equivale al tempo che i bit impiegano ad attraversare una serie di tubi in tutta la loro lunghezza.

## 0.2 Componenti della rete

### Introduzione generali dei componenti principali 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 5.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 5">

- Esempi di pezzi di rete

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 6.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 7.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 7">


La connessione di un calcolatore a una rete di calcolatori richiede un insieme essenziale di componenti, hardware e software, in aggiunta al calcolatore elettronico di base.

L’elemento primario da aggiungere al calcolatore è il **dispositivo (o scheda) di rete**: si tratta di un dispositivo hardware di comunicazione, fisicamente collegato al calcolatore, in grado di codificare e trasmettere, oppure ricevere e decodificare i dati inviati dal calcolatore alla rete, e dalla rete al calcolatore.
**I mezzi di trasmissione** sono supporti fisici alla propagazione e trasmissione di segnali, quali cavi o fili elettrici, fibre ottiche, o semplicemente lo spazio tridimensionale nel quale si propagano le onde radio. Tali mezzi di trasmissione realizzano l’infrastruttura fisica della rete. Il costo di realizzazione dell’infrastruttura di rete rappresenta spesso un fattore rilevante e critico per la diffusione e l’implementazione di reti di calcolatori.
Il **connettore di rete** è semplicemente un’interfaccia standard presente sul dispositivo di rete, per il collegamento del dispositivo di rete al mezzo di trasmissione. Esistono vari connettori, diversi a seconda del tipo di tecnologia impiegata per la rete di comunicazione. I connettori possono avere varie forme, e tipicamente permettono il collegamento solo quando le tecnologie dei dispositivi di rete, dei protocolli di gestione, e dei mezzi di trasmissione sono tra loro compatibili.
I dispositivi di rete sono amministrati da componenti software del sistema operativo, e devono rispettare un insieme di regole standard per la gestione dei processi di comunicazione, definite dai protocolli di rete.
I **protocolli di rete** sono un insieme di regole, univocamente definite, per garantire la compatibilità e la corretta configurazione e gestione delle fasi della comunicazione tra i dispositivi di rete.

### 0.2.1 Mezzo fisico di trasmissione 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 8.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 8">

- Esempi mezzi di trasmissione

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 9.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 9">


**Il mezzo di trasmissione** è l’elemento fisico che supporta la propagazione dei segnali trasmessi tra i dispositivi della rete. Ne abbiamo parlato anche nella sezione dispositivi di rete
**Le connessioni di rete** possono essere realizzate mediante tre mezzi di trasmissione diversi:

1. cavi conduttori
2. fibre ottiche
3. connessioni senza fili.

**I cavi di materiale conduttore** (cavetti, doppino intrecciato o cavo coassiale), sono in grado di propagare segnali elettrici, cioè variazioni di tensione e corrente elettrica. Questi mezzi fisici sono i più utilizzati nelle reti locali, e nelle brevi distanze, per il loro buon rapporto tra costo e prestazioni. Oggi tale mezzo trasmissivo è in grado di supportare trasmissioni dati con una capacità
dell’ordine del miliardo di bit al secondo (1-2 Gbit/sec).

**La tecnologia a fibre ottiche** è tecnologicamente avanzata, e si basa sulla trasmissione di segnali ottici, cioè di luce, vincolata all’interno di una sottile fibra di vetro purissimo. La fibra è sottile come un capello, è elastica ed è protetta da una guaina esterna per facilitare il suo impiego. Il costo della fibra non è molto elevato, tuttavia la fibra è molto delicata per quanto riguarda la connessione degli estremi (giunzione) e questo influisce molto sui costi di distribuzione e di realizzazione dell’infrastruttura di rete. La capacità di una fibra ottica può arrivare oggi a qualche decina di migliaia di miliardi di bit al secondo (oltre 10000 Gbit/sec).

**Onde elettromagnetiche e dalla loro propagazione nello spazio**. Esempi in tal senso sono forniti dalle onde radio e dalla luce infrarossa. Tali tecnologie vengono dette senza fili (wireless). Le reti senza fili sono molto interessanti, e la loro diffusione è oggi esplosiva, in quanto permettono la mobilità dei dispositivi e degli utenti. La capacità dei collegamenti senza fili può arrivare oggi a qualche decina di milioni di bit al secondo (1- 54 Mbit/sec). Il limite della tecnologia senza fili è dato dalla vulnerabilità del segnale rispetto ad errori e interferenza dei segnali, e dai limiti fisici della propagazione dei segnali. Due dispositivi possono essere connessi senza fili solo se rimangono entro un limite di distanza $$d$$ che dipende dalla potenza del segnale radio emesso dal trasmettitore, e da eventuali ostacoli intermedi per il segnale.
Inoltre non è precisa, nel senso che non si riesce in modo effettivo ad isolare la direzione di arrivo (la destination e sorgente non sono isolate).

**Collisione** è un problema molto comune per

Ogni rete può essere realizzata attraverso un singolo mezzo fisico di trasmissione, oppure attraverso la composizione di mezzi fisici eterogenei.

**Canali,** vedi canali di comunicazione, dividono spesso il mezzo di comunicazione. (si potrebbe infatti dire che il singolo mezzo di comunicazione abbia un fascio di canali)

### 0.2.2 Dispositivo o scheda di rete 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 10.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 10">


Le **schede di rete** permettono la comunicazione in rete tra calcolatori diversi, attraverso i vari mezzi di trasmissione illustrati, avviene mediante dispositivi interni o periferiche esterne del calcolatore. Queste schede sono collegate al calcolatore attraverso un’interfaccia di collegamento del calcolatore: su tale interfaccia transitano i dati (bit di informazione) da trasmettere
in rete, oppure ricevuti dalla rete.

La scheda di rete si occupa inoltre di trasformare i bit di informazione in segnali trasmissibili sul mezzo di trasmissione della rete e viceversa: tali trasformazioni si chiamano codifica e decodifica dei dati. Un connettore di rete pone direttamente in contatto la scheda di rete con il mezzo di trasmissione per l’invio e ricezione dei segnali in rete.

> In sintesi, la funzione della scheda di rete è quella di memorizzare temporaneamente, codificare, decodificare, trasmettere e ricevere i dati da e verso il mezzo di trasmissione (cioè la rete) o il calcolatore.
>

**Identificazione della scheda di rete**
Il tipo della scheda di rete viene identificato a seconda del mezzo trasmissivo, e soprattutto a seconda dei protocolli di comunicazione utilizzati per la codifica, e per la trasmissione dei dati in rete.
Per le reti locali (LAN) basate su mezzo di trasmissione cablato, le tecnologie più diffuse sono chiamate con il nome del protocollo di comunicazione primario: ad esempio **Ethernet**, nelle varianti a 10, 100 Mbit/sec (Fast Ethernet) e 1000 Mbit/sec
(Gigabit Ethernet).

Per le reti LAN senza fili (WLAN), le schede di rete più diffuse sono denominate **Wi-Fi** (da 11 a 54 Mbit/sec), e **Bluetooth** (da 1 a 2 Mbit/sec).
Ogni scheda di rete, per permettere di essere identificata univocamente nel contesto di una rete locale, dispone dalla sua costruzione di un indirizzo univoco (unico) a livello mondiale, non modificabile, detto indirizzo **MAC** (Medium Access Control), spesso questa scheda di rete è specifica per il mezo trasmissivo!.
Tali indirizzi vengono assegnati dai costruttori delle schede, per evitare che si possano originare indirizzi MAC duplicati. (spesso hai moltissime informazioni riguardo al modello della scheda di rete e del produttore solo guardando questo).

Il **MAC** si occupa anche di evitare le collisioni (come non lo so).

### 0.2.3 Protocolli di rete 🟩

- Slide (la parte sull’architettura presente in slide è trattata in [Architettura e livelli 1, 2](/notes/architettura-e-livelli-1,-2)

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 11.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 11">


> Le regole che governano i processi di comunicazione in rete, tra dispositivi e sistemi eterogenei
>

*Perché è necessario:* La necessità di accordarsi su regole e servizi comuni per la comunicazione di rete ha lo scopo di permettere una completa compatibilità e supporto alla comunicazione su sistemi, tecnologie e dispositivi eterogenei.

Al fine di far ciò definiscono delle regole semantiche (processi) e sintattiche (struttura pacchetto) formali.

I protocolli definiscono aspetti e regole semantiche sulla sequenza dei messaggi, e regole sintattiche sul formato dei messaggi scambiati durante la comunicazione. La definizione dei protocolli di rete deve prevedere e supportare diverse finalità di comunicazione.

Non ha quindi senso definire un protocollo rigido, ma ha senso definire classi di protocolli, deputate a svolgere e gestire *determinate* funzioni della comunicazione. Tali classi di protocolli, opportunamente organizzate, permettono di semplificare la gestione della rete, ma è necessario definire in modo non ambiguo le relazioni tra le classi di protocolli (ovvero quale protocollo si occupa di gestire un certo problema? Come avviene il dialogo tra protocolli?)

## 0.3 Struttura della rete

### 0.3.1 Strutture della connessione di rete (4) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 12.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 12">


**Un collegamento o connessione fisica** di rete è fornita da un *mezzo di trasmissione* (ad esempio un cavo, una fibra ottica oppure lo spazio per la propagazione di onde radio) che sia condiviso tra due o più dispositivi ad esso collegati, e che permetta il trasferimento di segnali, e quindi informazione, tra i dispositivi stessi.

**Un’infrastruttura di rete** rappresenta l’insieme dei collegamenti o connessioni fisiche esistenti tra tutti i dispositivi di una rete.

**La comunicazione** tra una coppia qualsiasi di calcolatori in rete, detti **nodi (oppure host)** della rete, è possibile se esiste un collegamento diretto tra i nodi, oppure se esiste una sequenza di collegamenti, detta cammino, che permetta la comunicazione dei segnali passando per eventuali nodi e collegamenti intermedi.

**Classi di strutture di connessione della rete**. (4)

- *Le connessioni di rete punto a punto*, come nell’esempio (a), sono connessioni che possono essere instaurate tra una coppia di calcolatori, senza coinvolgerne altri. Esse rappresentano il caso più semplice di infrastruttura di rete, e sono semplici da gestire.
- *Reti completamente connesse:* Le connessioni di rete multiple permettono di connettere contemporaneamente un dispositivo a molti altri dispositivi.
Nell’esempio (b) viene mostrata una infrastruttura di rete nella quale ogni nodo è connesso attraverso un linea dedicata ad ogni altro nodo. Questa infrastruttura di rete viene detta completamente connessa, ed è molto ridondante: infatti esistono molti cammini, oltre al collegamento diretto, per connettere ogni coppia di nodi passando per nodi intermedi.
Una simile infrastruttura di rete si può ritenere a volte troppo complessa e costosa. Ad esempio, sarebbe impensabile disporre di una connessione dedicata (cioè un filo diretto) da ogni calcolatore ad ogni altro calcolatore sulle reti mondiali.
- *Reti parzialmente connesse:* Nell’esempio c, malgrado il ridotto numero di collegamenti rispetto al caso b, è comunque possibile per ogni dispositivo trasferire segnali, cioè comunicare, verso ogni altro dispositivo. In altre parole esiste un cammino, attraverso le connessioni disponibili, per trasferire informazione tra ogni coppia di dispositivi della rete.Nella rete (c) esiste però un fattore di rischio: in
seguito a un guasto di una connessione, potrebbe risultare un insieme di componenti separato da tutti gli altri, detto “**partizione**” della rete (esempio d).
- *Le partizioni della rete* limitano il grado di comunicazione possibile, e possono essere dovute a cause fisiche (guasti fisici della connessione) oppure a cause che dipendono da cattive applicazioni delle regole di utilizzo (ovvero dei protocolli, che vedremo in seguito).

### 0.3.2 Topologia di rete 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 13.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 13">


**Topologie di rete** sono i diversi schemi di connessione sono possibili per creare le infrastrutture di rete

Topologia per  PAN e locali LAN:
**Topologia ad anello** (esempio a) è basata sull’organizzazione delle connessioni tra i dispositivi, in
modo da creare un anello chiuso. Ogni componente può comunicare con ogni altro componente inviando i segnali attraverso la sequenza di connessioni in senso orario o antiorario.
**La topologia a stella** (esempio b) prevede un componente centrale direttamente connesso a tutti gli altri. Ogni componente periferico può comunicare con ogni altro componente periferico passando attraverso il componente centrale.
**La topologia a bus** (esempio c) prevede che ogni componente abbia una connessione verso un bus condiviso (cioè una connessione condivisa da tutti). Questo tipo di connessione permette di introdurre una delle problematiche fondamentali che saranno trattate in seguito: la gestione dell’accesso al bus, ovvero il decidere chi possa trasmettere tra tutti i possibili dispositivi, per evitare sovrapposizioni delle trasmissioni.
**La topologia ad albero** (esempio d) prevede un’organizzazione gerarchica delle connessioni.
Se pensiamo all’analogia con un albero genealogico, esiste un dispositivo (nonno) che connette direttamente due o più dispositivi (figli), ognuno dei quali a sua volta connette direttamente un numero variabile di dispositivi (nipoti), e così via.

Mano a mano che le reti più piccole vengono collegate tra loro e organizzate in strutture di rete più grandi, la topologia della rete globale può diventare incredibilmente complessa, e quindi uno schema topologico generalizzato non è quasi mai applicabile. In questo caso si parla di **rete con topologia a grafo complesso, oppure a maglia**. In tali topologie a grafo, possono essere presenti
cammini multipli che connettono coppie di nodi, dando luogo a possibili alternative per la connessione dei dispositivi.
Questo fatto può ridurre il rischio di incorrere in partizioni della rete, in quanto un certo grado di ridondanza dei cammini di connessione permette di aggirare i collegamenti soggetti a eventuali guasti.

### 0.3.3 I due generali 🟩

È possibile implementare una comunicazione sicura in un ambiente che possa fallire, anzi con un nemico che voglia far fallire questo?

Fai finta che A = 3, B = 3, e C = 5, ma A e B sono separati, è possibile avere una comunicazione per attaccare insieme? Se A o B attaccano da soli verrebbero ammazzati.

- Semplificazione del problema dei due generali

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 14.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 14">


Come si manda il messaggio in modo sicuro? Se si manda il singolo messaggio, senza aspettare nessuna risposta, allora è molto insicuro (per niente sicuro) che il messaggio sia arrivato.

Per questo motivo si aspetta un **acknowledgment**, e un altro acknowledgment dall’altra parte → SYN/ACK  protocol è simile.

Ma facendo in questo modo **non si è mai sicuri** che l’altro abbia ricevuto il messaggio. La rete a due è fallibile, e questo è dimostrato.

### 0.3.4 Reti commutazione a circuito 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 15.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 15">


Nelle reti a commutazione di circuito, i dati vengono trasmessi tra un mittente e un destinatario finale agli estremi di un cammino **end-to-end** (circuito) di canali di comunicazione punto a punto. Il circuito viene negoziato e prenotato, attraverso opportune procedure (come avviene quando si digita un numero per una chiamata telefonica). Una volta identificati e ottenuti i canali che collegano mittente e destinatario, la comunicazione dati può avvenire anche come un’unica sequenza di bit, senza interruzioni.

*Vantaggi*

- Non c’è bisogno di dichiarare periodicamente chi sia il mittente e il destinatario dei dati, in quanto entrambi sono fissati al momento della creazione del circuito riservato (riservato = prenotato da qualcuno).
- Ridotto ritardo di trasmissione per i dati, in quanto ogni nodo intermedio ha già disponibile il canale libero uscente sul quale inviare immediatamente i dati ricevuti sul canale entrante, dal mittente fino al destinatario finale.

*Svantaggi*

- Utilizzo basso dei canali del circuito
    - Quantità dei dati da trasmettere non è grande
    - I dati arrivano a gruppi, intervallati da tempi di vuoto.
- Inefficienza di utilizzo delle risorse del circuito nei casi sopraelencati (il canale resta tutto occupato).
- Pagato a tempo!
- Un pò di tempo in più per prenotare il percorso all’inizio.

### 0.3.5 Reti commutazione a pacchetto 🟩

- Slides

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 16.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 16">


La maggior parte delle reti per trasmissione dati digitali, inclusa la rete di reti globale Internet, sono di questo tipo.

**Come funziona**

I dati digitali vengono suddivisi in pacchetti separati, e vengono trasmessi su canali ad accesso multiplo (broadcast, non per forza deve essere punto a punto ).
Per consentire la corretta ricezione dei dati, è però necessario includere in ogni pacchetto l’informazione sull’identità del rispettivo mittente e soprattutto del destinatario.
Si attua in questo modo la condivisione di un canale unico per diversi flussi di pacchetti appartenenti a diversi mittenti e destinatari.
Componendo in serie una sequenza di canali broadcast a commutazione di pacchetto, i nodi ricevitori devono di volta in volta farsi carico di verificare se il pacchetto sia giunto a destinazione o, in caso contrario, possono provvedere all’inoltro del pacchetto ricevuto sul successivo canale broadcast.

*Svantaggi*

- Ritardo per la comunicazione dei dati tra mittente e destinatario (più lenti
    - dovuto all’esigenza di iterare più volte la ricezione e l’inoltro di pacchetti su canali broadcast in sequenza.
- Maggiore rischio di collisione dei pacchetti (*perdita di pacchetti*)
- A causa dei jitter, i pacchetti possono arrivare in ordine diverso(*perdita di ordine → riordinamento*)
- Se utilizzo il broadcast, serve il mittente e il destinatario

*Vantaggi*

- maggiore utilizzo dei canali ad accesso multiplo, e quindi alla possibilità di tariffare la comunicazione in base ai dati trasmessi, e non in base al tempo necessario.

### 0.3.6 Canali di comunicazione della rete 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 17.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 17">


Bisogna dire che è una virtualizzazione sul mezzo di comunicazione, ossia si utilizza il mezzo di comunicazione come se avesse alcuni canali diversi (che non interferiscono fra di loro) quindi possiamo riutilizzare la stessa risorsa fisica!

Da riallacciarsi con mezzi di comunicazione per capire come sono implementate fisicamente i canali di comunicazione.

**I canali punto a punto**  si basano sull’accordo tra un mittente e un destinatario riguardante la definizione del canale da usare (in figura equivale al colore). Solo due dispositivi possono usare il canale di tipo punto a punto a loro riservato. Possiamo creare un canale logico da un singolo mezzo trasmissivo (eg una frequenza diversa, che possono essere filtrate).
Il problema principale di questo è che è fisso, ossia posso comunicare solamente con un unico computer, senza poter cambiare il destinatario, direi che abbia più problemi nel momento di wiring.

**I canali ad accesso multiplo (broadcast)**  sono canali sui quali tutti possono trasmettere e dove tutti ricevono le trasmissioni di altri (chiaramente il problema di collissione è molto alto). Half duplex o uno trasmette o uno riceve mentre i Full-duplex possono trasmettere e ricevere contemporaneamente. Spesso per queste reti c'è un master e dei slave che gestiscono.

Ethernet risolve questo problema senza fare utilizzo di un master, utilizza un sistema di ___ (non mi ricordo, è comunque una race condition) lo risolve con un sistema di counter interno dopo il quale, se è ancora vuoto il canale di comunicazione broadcast, prova a fare la comunciazione.

### 0.3.7 Problema delle collisioni su canali multiple  🟨

Un problema per i canali ad accesso multiplo è legato alla possibile collisione di segnali appartenenti allo stesso canale di comunicazione. Se due trasmissioni di segnali si sovrappongono nel tempo sullo stesso canale di comunicazione, l’effetto sui segnali può essere distruttivo e l’esito della comunicazione può essere nullo. Intuitivamente, se due dispositivi trasmettono i loro segnali contemporaneamente, nessuno ricevitore sarà in grado di capire quali bit di informazione siano stati trasmessi.

Il problema delle collisioni è molto critico, e determina l’esigenza di arbitraggio nell’accesso al canale: chi trasmette e quando?
**Il problema dell’arbitraggio** può essere banale su canali punto a punto, dove mittente e destinatario possono definire semplici leggi (cioè protocolli di gestione della comunicazione) per evitare le collisioni: ad esempio, trasmetto io, poi trasmetti tu.
In canali condivisi ad accesso multiplo (broadcast) il problema risulta invece molto complesso, in quanto occorre definire leggi non ambigue, in grado di regolare gli accessi da parte di molti utenti, evitando le collisioni.

Il problema principale delle collisioni è che fanno perdere tempo o infomazioni (se il nostro protocollo non le gestisce).

**Utilizzo**

Di solito è uguale a $$capacità \cdot overhead$$, ad esempio se trasmetto 100 bit e solo 1 un bit è di informazione, questo è l'utilizzo del protocollo. Questo va a misurare efficienza di informazioni di questo protocollo.

### 0.3.8 Servizi orientati alla connessione  e non 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a reti/Untitled 18.png" alt="image/universita/ex-notion/Introduzione a reti/Untitled 18">


**I servizi orientati alla connessione (connection-oriented)** garantiscono che la spedizione di pacchetti di dati tra mittente e destinatario sia equivalente a una trasmissione affidabile e corretta. In altre parole, essi implementano una serie di operazioni attraverso le quali tutti i pacchetti perduti saranno ritrasmessi, e correttamente ordinati, fino a ricostruire esattamente tutta l’informazione trasmessa.
L’implementazione di tale tipo di servizi potrebbe essere basata sulla definizione di vari protocolli alternativi. Ad esempio, potrebbe essere definito un cammino riservato unico per i pacchetti. Intuitivamente, ciò equivarrebbe a un circuito virtuale per l’invio dei pacchetti. Un altro modo per ottenere tale servizio potrebbe essere basato sulla numerazione dei pacchetti inviati, sul
riordino dei pacchetti ricevuti e sulla richiesta di ri-trasmissione dei pacchetti perduti.

In breve questo risolve un problema di:

1. Riordinamento dei pacchetti
    - Soluzione riordinamento

        Basta numerare i pacchetti e poi far riordinare dal destinatario, questo è un problema molto facile da risolvere

2. Reinvio dei pacchetti perduti
    - Soluzione reinvio

        Bisogna che il destinatario mandi degli acknowledgements. Anche questi possono essere persi.

        1. Problema tempo da aspettare prima di reinviare il pacchetto
        2. Pacchetto duplicato quando si perde l'acknowledgement o ci mette troppo.

**I servizi non orientati alla connessione** (**connectionless**) non si preoccupano di garantire l’ordine corretto dei pacchetti inviati e nemmeno la ricezione di tutti i pacchetti. Tale servizio è simile all’invio dei pacchetti in modo analogo a una sequenza di lettere attraverso la posta ordinaria.

Non ci importa l'ordine di arrivo né per forza alcuni buchi.

Questo è come sono le reti normali, normalmente sono connectionless, con un protocollo in più sono connection-oriented.

In modo molto veloce si potrebbe dire che i servizi non orientati alla connessione non garantiscono nulla.