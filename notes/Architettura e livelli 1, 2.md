---
layout: page
permalink: notes/architettura-e-livelli-1,-2
tags: en
title: Architettura e livelli 1, 2
---

Ripasso Prox: 140
Ripasso: June 1, 2023
Ultima modifica: March 15, 2023 3:01 PM
Primo Abbozzo: October 14, 2022 5:49 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# 1 Architettura e primi due livelli

## 0.4 Architettura di rete

### 0.4.1 Perché a stack 🟩-

Capire l’architettura significa capire la struttura (l’organizzazione) del nostro app e comprenderne i motivi (i sottoproblemi risolti) che ogni livello prova a risolvere

La soluzione che è stata individuata, e ha rappresentato uno dei principali cardini del successo delle reti e della nascita di Internet, è data dalla separazione delle classi di protocolli in livelli. La struttura dei livelli dei protocolli di rete prende il nome di architettura dei protocolli di rete.
Il concetto di architettura dei protocolli, suddivisa in livelli, è semplice ed è basato su alcune condizioni.

Ogni livello

- Svolge determinate funzioni di gestione dei processi di comunicazione, attraverso uno o più protocolli alternativi.
- Fornisce un livello di astrazione più elevato della rete di comunicazione sottostante, sfruttando i servizi implementati dai livelli sottostanti.
- Ha relazioni dirette solo con i livelli immediatamente superiore e inferiore, attraverso richieste e servizi concordati, detti interfaccia del livello

In altre parole, i livelli superiori non devono preoccuparsi di risolvere problemi che saranno gestiti e risolti dai livelli inferiori.

La cosa migliore per questa struttura è che se ho bisogni differenti posso individuare il livello che mi interessa e **re-mplementare solo quanto ho bisogno**, senza dover cambiare l'intera stack.

- Esempio architettura a livelli (fatta dal prof in persona e rubata da altri profzz, lel)

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled">

    Si ha un esempio di trasmissione e ricezione delle informazioni tramite questa metafora.

    Ogni livello risolvere un problema preciso nella fase di trasmissione dell’informazione…

    La cosa interessante è che dal livello di dichiarazione (o app) non si vede tutto il sotto, è come se magicamente fosse tradotto e presentato nella lingua corretta! Risolve un grande problema di complessità.


**Vantaggi**

1. Riutilizzabilità di molti layers, basta cambiare cose di un singolo layer se ho bisogno di fare cose mie.
2. Gli strati paritari si parlano astraendo tutto quanto avviene di sotto.

Si potrebbe andare a parlare di **encapsulation and data hiding** cioè tutti i dati di un singolo livello sono isolati a quello e i dati sono solamenti di questo livello. Esposte sono solamente le relazioni, come si parla sopra. (facilita anche il debuggin per singolo LIVELLO)

### 0.4.2 Architettura standard (OSI) !!! 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 1.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 1">


Lo Standard **ISO/OSI RM** (International Organization for Standardization (ISO)/Open System Interconnection Reference Model) definisce un insieme di livelli completo e rigoroso per l’architettura dei protocolli di rete, prevedendo un livello per la gestione di ogni problema di comunicazione in rete.

Ciò che si va a standarizzare è **l'interfaccia dei vari livelli*. (API)**. Mentre l'implementazione di queste funzioni è lasciato a piacere, basta che soddisfi quello che deve fare. (Questo è ciò che permette la *flessibilità* di questra struttura).
L’architettura dei protocolli di rete definita da ISO/OSI RM prevede sette livelli dei protocolli, numerati da 7 a 1 dall’alto al basso.

1. **il livello fisico** si occupa di definire le tecniche di codifica dei dati, la trasmissione e la ricezione dei dati sul mezzo fisico di trasmissione (→ *Fisica here*).
2. **livello LLC/MAC** si occupa di garantire l’affidabilità del mezzo di trasmissione e la gestione dell’accesso al mezzo trasmissivo ad accesso multiplo (evitando le collisioni).
A questo livello il pacchetto si chiama *FRAME.*
    1. *MAC* (Media Access Control) è sotto.
        1. Inserisce gli indirizzi di destinatario e mittente (MAC) (spesso questi indirizzi sono solamente locali, per sapere a chi dare come step intermedio), forniti dal costruttore
        2. Decisione di quando trasmette (ad esempio può chiedere al livello fisico se il canale è libero o meno, e gestisce questa cosa col suo protocollo, quindi dilazionare il tempo di trasmissione)
    2. *LLC* (Logical link control) è sopra
        1. Verifica che non ci siano stati errori di trasmissione delle informazioni ricevute.
        2. Dire di inviare l’acknowledgement, se è il momento giusto.
        3. Gestire pacchetti duplicati.
3. **Il livello rete** si occupa di frammentare i dati in pacchetti, scrivere gli indirizzi dei destinatari finali e instradare i pacchetti verso i destinatari intermedi del cammino.
In questa sezione andiamo oltre alla rete locale, è qui che nasce internet vero!
Il [router](/notes/control-plane) è un elemento principale di questo.
    1. Frammentazione dei pacchetti
    2. Indirizzamento *IP* che servono a dare un identificativo alla scheda di rete in ambito locale per capire in quale direzione trasferire.
4. **Il livello trasporto** si occupa di garantire i servizi di trasmissione dei pacchetti (orientati alla connessione e non) e del controllo della congestione della rete.
Un esempio di protocollo a questo livello è il *TCP(Trasmission Control Protocol*). Che fa i controlli sull’acknowledgement e simili
    1. Potrebbe essere ch ealcuni router siano congestionati, quindi che droppino alcuni pacchetti
    2. Non è una soluzione dire agli altri router di inviare in modo più lento. (Dovrebbe essere il mittente che dovrebbe rallentare nell'invio di pacchetti, in modo che non si congestionano nessun nodo).
5.  **Il livello sessione** mantiene e gestisce lo stato attuale del collegamento tra due applicazioni remote. (quindi poter riprendere da un certo stato quando per un certo momento ti sconnetti).
Di solito questo è gestito dall’applicazione, e non viene implementato.
6. **Il livello presentazione** risolve eventuali eterogeneità del formato dei dati tra i nodi della rete.
Perché i formati sono già leggibili, senza dover interpretare i bit per capire cosa rappresentano.
7. **Il livello applicazione** fornisce alle applicazioni in esecuzione sul calcolatore i servizi e le primitive di trasmissione e ricezione dei dati. *primitive* che servono al processo di esecuzione per funzionare. es. funzione per mandare i dati e simli. Qui le funzioni possono essere moooltee

### 0.4.3 Architettura dei protocolli di internet 🟩

In questa sezione si tratta di come effettivamente quanto dell'architettura OSI è implementata

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 2.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 2">


L’architettura dei protocolli di Internet, nel senso più comunemente adottato, prevede di fatto l’implementazione di solo cinque livelli dei sette livelli dello Standard ISO/OSI RM. Rimangono spesso esclusi i livelli 5 (sessione) e 6 (presentazione), gli altri livelli sono uguali. Il motivo per cui succede è che principalmente questi livelli sono implementati a livello applicazione.

Un aspetto che si pone in evidenza, è il concetto di **incapsulamento dei dati** tra i livelli implementati. In fase di trasmissione, ogni livello riceve dati dall’alto (dati spediti dall’applicazione) e li inserisce in “buste virtuali” (**incapsulamento**) ponendo in testa e in coda alcuni dati aggiuntivi, necessari per fornire al livello della controparte ricevente le informazioni utili all’implementazione del protocollo dello stesso livello. In fase di ricezione, ogni livello X riceve dal livello più basso i dati imbustati dallo stesso livello X sul trasmettitore, quindi verifica i dati della busta, agisce in conseguenza alle specifiche fornite nei dati della busta, e passa solo il contenuto della busta ai livelli superiori (**decapsulamento**).
Il livello trasporto spezza i dati dell’applicazione in frammenti e li imbusta, aggiungendo informazioni utili all’ordinamento e al riassemblaggio dei dati ricevuti, oltre che al controllo della congestione della rete.

Il livello rete frammenta ulteriormente i dati in pacchetti (se sono troppo lunghi), scrive l’indirizzo del destinatario sulla busta, e decide il cammino sul quale inviare il pacchetto a seconda dell’indirizzo di rete del destinatario.

Il livello MAC/LLC esegue la consegna finale dei dati a dispositivi di una rete locale.

## 0.5 Livelli ISO/OSI

**Livello fisico**

Sono a livelli fisico perché devono avere lo stesso mezzo fisico (eg ethernet solo ethernet!, wifi solo wifi!)

### Segmento di rete 🟩 -

- Segmento di rete

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 3.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 3">


> un mezzo di trasmissione *condiviso* con canale ad accesso multiplo, in cui **tutte** le schede collegate al segmento ricevono quanto trasmesso
>

Gli indirizzi MAC sono consapevoli dell'esistenza di questo mezzo di broadcast, con prima il destinatario, così lo legge subito.

Collegarli tutti in un canale broadcast non è che sia molto buono

1. Rischio di collisioni molto alto
2. Perdita di intensità dei segnali elettrici
3. Principalmente spreco di tempo ed energie.

Quindi abbiamo bisogno di modi per creare segmenti per risolvere questi problemi., che facciano cose intelligenti.

Il segmento di rete è importante! Mini rete locale, è anche il modo in cui mando il pacchetto al router con source e destination.

### Composizione di segmenti di rete (4) 🟩

- Appunti prof  di dispositivi per livello 1 e 2

    A questo punto esistono i presupposti per introdurre alcuni dispositivi che possono essere usati per comporre ed estendere una rete locale di calcolatori, unendo segmenti di rete altrimenti separati.
    Il primo dispositivo è il ripetitore (**repeater**). Siccome i segnali emessi su qualsiasi mezzo fisico si degradano al crescere della distanza percorsa, esiste un limite massimo per la lunghezza di un segmento di rete. Ad esempio, un segmento Ethernet, può variare dai 100 ai 200 metri. Un repeater è un dispositivo che agendo solo a livello fisico, amplifica e rigenera il segnale ricevuto
    verso un prolungamento del segmento di rete. Mediante un repeater è possibile collegare due segmenti di rete aventi la stessa tecnologia a livello MAC, ed estendere la lunghezza dei segmenti di rete locale.
    Un **Hub** (che significa perno di una ruota a raggi) è un altro dispositivo che agisce solo a livello fisico. Esso realizza il punto centrale di connessione, detto concentratore, dei segmenti di una rete locale con topologia a stella. In pratica si tratta di un ripetitore (repeater) con tante connessioni entranti e uscenti.
    Un **Bridge** (ponte) è invece un dispositivo che agisce anche da traduttore a livello due (MAC/LLC). Un bridge permette di connettere segmenti di una stessa rete locale ma con tecnologie e MAC diversi tra loro (ad esempio un segmento Ethernet con uno Token Ring). I bridge fanno quindi da traduttori dei frame nei formati richiesti dal livello MAC di ogni segmento connesso al bridge, e provvedono alla trasmissione su segmenti diversi adottando il protocollo MAC opportuno.
    I Bridge sono dotati della capacità di filtrare e instradare opportunamente i frame di dati sul segmento opportuno, osservando sui frame le informazioni di indirizzo MAC del dispositivo destinatario.
    Uno **Switch** (commutatore) è un dispositivo di livello due (MAC/LLC) analogo al bridge. Al contrario del bridge, esso permette di connettere un numero maggiore di segmenti diversi (fino a 10 o 12).


**Repeater**

Ripetitori. I segnali trasmessi sul mezzo fisico degradano con la distanza, nella fattispecie l’ethernet degrada dopo circa 200 metri, quindi ogni 200 (o, meglio, 100) metri si aggiunge un ripetitore. Il ripetitore **amplifica** e **rigenera** il segnale ricevuto. Il repeater collega due segmenti di rete che hanno la *stessa* tecnologia MAC; non legge i dati, vede semplicemente che sta arrivando un segnale e lo amplifica e passa oltre. Con l’allungarsi delle distanze chiaramente le trasmissioni impiegano un po’ di tempo in più per viaggiare da mittente e destinatario, quindi nel caso di reti LAN più grandi diventa necessario allungare i tempi di timeout.

**Hub**

È un repeater multiporta. È il nodo centrale di una rete a stella. Quando riceve un segnale da una porta lo copia e lo manda a tutti gli altri elementi della rete. È usato pochissimo in quanto costa poco meno dello switch, che però offre più funzionalità e porte.

**Bridge**

*hub* ripete tutto quanto ha avuto a tutti quanti sono collegati, ma ha il problema grosso delle collisioni

**Switch**

Connette tecnologie omogenee.

riesce a filtrare e inviare i frame al segmento giusto. Quindi si comporta come un hub quando non sa dove andare, ma riesce ad **ascoltare** gli segmenti e vedere se è libero, se è libero manda, e se torna l’ACK allora aggiorna la propria **tabella dei segmenti** che mappa il MAC con il segmento corretto.

- Appunti di bianchi

    Lavora a livello 2. A differenza del bridge permette di connettere molti più
    segmenti (oggi gli switch hanno anche 96 porte). Interconnette tecnologie
    omogenee, non diverse, e filtra i pacchetti da inoltrare a seconda della
    loro destinazione. Manda i dati in broadcast solo se non sa dov’è il destinatario. - Buffered switch: ha un buffer di memoria che ha la funzione
    di memorizzare tutti i frame che arrivano. Questo siccome la trasmissione
    deve essere smistata e non è automatica, ma segue le regole del protocollo MAC, può essere necessario che una trasmissione debba attendere il
    completamento di un’altra precedente.


**Bridge**

Funziona come uno switch (quindi lavora a livello 2) ma connette tecnologie a livello locale con MAC protocol **diversi** (ad es. Ethernet e Wifi). Se riceve trasmissioni da un protocollo (ad es. Ethernet) e deve mandarle ad un altro protocollo (ad es. Wifi) prende il pacchetto, lo smembra e lo ricostruisce in un frame compatibile con l’altro protocollo (i dati cambiano la “busta gialla”).

## Note sui primi 2 livelli

### 0.5.1 Livello fisico 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 4.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 4">


È il livello della scheda di rete, dei mezzi di trasmissione fisici, codifica e decodifica dei segnali in analogici e digitali.

Importante in questa parte è il concetto di **velocità del mezzo trasmissivo e velocità di trasmissione**.

La velocità di trasmissione dipenda dalla durata del vagone, o della rappresentazione dei dati nel mezzo trasmissivo.

- Appunti prof Livello fisico

    I valori possibili per i dati digitali (bit) del calcolatore sono solo due: i valori 0 e 1.
    Tali valori devono essere trasmessi o ricevuti sui mezzi di trasmissione delle reti, sotto forma di variazioni di segnali analogici (elettrici, ottici o radio), uno di seguito all’altro.
    Per questo scopo, i dati digitali devono essere opportunamente codificati o decodificati, in sequenza, da parte della scheda di rete.
    L’attività di codifica, effettuata in fase di trasmissione, equivale a tradurre i valori dei bit in segnali analogici. L’attività di decodifica, effettuata in fase di ricezione, equivale a tradurre i segnali analogici ricevuti nei valori dei bit.
    Le tecniche di codifica digitali permettono di ridurre, ma non di escludere completamente, la possibilità di errori di trasmissione sulla rete.
    Una nota importante riguarda l’ambiguità di fondo sul concetto di velocità della trasmissione dei segnali in rete. Dal punto di vista fisico, tutti i segnali analogici, elettrici, ottici o radio, si propagano praticamente alla stessa velocità, cioè alla velocità della luce, pari a circa 300.000 Km/sec. Non ha quindi senso parlare di bit, oppure di segnali, più veloci di altri. Tuttavia, nell’esempio in figura, un canale A di comunicazione sul quale siano codificati dieci bit al secondo ha una **densità di trasmissione** dei bit (detta anche capacità del canale) pari alla metà della capacità ottenuta da un canale B, sul quale possano essere codificati venti bit al secondo. I canali a capacità più elevata, ovvero in grado di trasmettere più bit al secondo, devono tali prestazioni al fatto di usare meno tempo per codificare, ovvero rappresentare il valore del bit sul mezzo trasmissivo, rispetto
    a canali più “lenti”.
    Le migliori tecnologie di rete sono quelle che permettono di codificare i bit nel minor tempo possibile, ottenendo quindi alte capacità dei canali (ad esempio, miliardi di bit trasmessi al secondo).


### Livello di collegamento 🟩

**MAC**

- Canale Mac di broadcast
- Struttura e utilizzo dell'indirizzo MAC
- Policies generali per l’arbitraggio del canale per risolvere le collisioni.
- Appunti prof Livello Mac

    Analizziamo ora l’esempio più semplice per la definizione di una rete di calcolatori a commutazione di pacchetto: un **segmento di rete locale**. Un segmento di rete locale è definito come un mezzo di trasmissione condiviso sul quale sia definito un canale ad accesso multiplo.

    Ogni calcolatore si assume dotato della scheda di rete opportuna per il mezzo trasmissivo e i protocolli di codifica utilizzati al livello uno (fisico). Ogni scheda di rete è dotata di un identificativo (indirizzo) di livello MAC unico al mondo (assegnato dal costruttore). Ogni trasmissione di un pacchetto di dati (detto frame a questo livello) sul canale ad accesso multiplo è ricevuta da tutti i calcolatori la cui scheda di rete sia connessa al canale stesso.
    Immaginiamo che il dispositivo con indirizzo MAC1 voglia spedire un frame di dati al dispositivo con indirizzo MAC5, e allo stesso tempo il dispositivo di indirizzo MAC4 voglia spedire un frame di dati al dispositivo di indirizzo MAC2.

    Nel contesto del canale condiviso, la conoscenza degli indirizzi MAC dei dispositivi mittente e destinatario basta ad effettuare la trasmissione, sul canale comune. Semplificando molto il problema, per ragioni di presentazione, è sufficiente aggiungere le informazioni sull’indirizzo MAC del destinatario e del mittente sulla busta di ogni frame, prima di trasmetterlo.

    Ogni frame trasmesso sul canale da parte di ogni dispositivo risulta quindi rilevato da tutti gli altri dispositivi, ma viene ricevuto (cioè copiato e passato ai livelli superiori) solo se l’indirizzo MAC del destinatario specificato nel frame coincide con l’indirizzo MAC del dispositivo ricevente.
    Il compito principale dei protocolli di livello 2 (MAC/LLC), oltre all’indirizzamento dei frame trasmessi sul canale condiviso del segmento di rete locale, è dato dall’arbitraggio degli accessi al canale. Ossia

    1. Determinare i nodi che possono trasmettre
    2. Quando possono trasmettere
    3. L’ordine di trasmissione per evitare collisioni

**LLC**

- Slide prof

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 5.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 5">

- Controllare se i dati sono corretti, o ricevuti doppi (se doppio o errato faccio finta di non averlo ricevuto).
- Mandare acknowledgment (che non succede col broadcast).
- Appunti prof  affidabilità di questo livello (ACKs)

    Scopo dei protocolli del livello 2 (MAC/LLC) è *nascondere* ai livelli superiori i dettagli del mezzo fisico, e mostrare il canale condiviso sul segmento di rete locale come se si trattasse di un canale affidabile, **senza alcun errore di trasmissione**. A tal fine il frame di dati viene delimitato mediante particolari etichette di bit, poste all’inizio e alla fine del frame, e viene arricchito con altri campi di dati utili al protocollo.
    La trasmissione di un frame procede per tentativi, fino alla **ricezione di una conferma** (un frame di conferma) da parte del destinatario. Quello qui illustrato è solo un meccanismo semplice per realizzare trasmissione affidabile, tra quelli possibili.
    La figura mostra la sequenza temporale di eventi gestiti dal livello 2 (MAC/LLC) per la trasmissione affidabile di un frame di dati tra due dispositivi sulla stessa rete locale. Il frame di dati viene spedito dal dispositivo con indirizzo MAC1 al dispositivo con indirizzo MAC2 sul mezzo trasmissivo. Il mittente fa partire un timer dopo la trasmissione. Il ricevente MAC2 si accorge che il frame è destinato a lui, ma rileva errori sui bit ricevuti, per cui non fa nulla (non passa il frame ai livelli superiori) e non invia la conferma a MAC1. Allo scadere del timer, MAC1 verifica che non ha ricevuto conferma, per cui ripete da capo la trasmissione, e fa ripartire il timer. Questa volta MAC2 riceve correttamente il frame e spedisce a MAC1 un frame di conferma. MAC1 riceve il frame di conferma e solo ora considera terminata con successo la trasmissione del frame.
    Ai livelli dei protocolli superiori al livello due tutto ciò viene nascosto, e appare solamente la trasmissione corretta del frame sul segmento di rete.


### Collaborazione livelli per affidabilità (!!)🟩

- Acknowledgement livello 4

    <img src="/images/notes/image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 6.png" alt="image/universita/ex-notion/Architettura e livelli 1, 2/Untitled 6">


Non è sufficiente verificare che funzioni a livello 2, bisogna anche avere un ACK a livello 4 che sia end-to-end, così so sicuro che tutto il processo passo passo a livello MAC funziona, ossia sono riuscito effettivamente a raggiungere il destinatario.

Quindi serve questo ack a livelli diversi e tempi diversi (uno fa end-to-end ack, l’altro fa ack ogni step). Ma l’ACK a livello 4 è necessario, perché il mittende deve sapere se sia ricevuto, mentre il livello 2 non sarebbe strettamente necessario, ma è molto probabile che vada male qualcosa a livello intermedio, e questo ACK riesce a risolvere problemi a questo livello ritrasmettendo.

- Livello 2 Evitare che un fallimento di singolo frame fallisca l’intera trasmissione a livello più alto (e quindi riuscire a recuperare molto più in fretta se viene perso a questo livello).
- Livello 4 Informare il mittente che l’informazione è stato ricevuto correttamente (quindi end-to-end).

**Caso di segmento faulty !**

Nel caso in cui il livello MAC non riesce proprio a ricevere l’ACK, questo lo comunica al livello di Rete che ha una immagine della sua topologia di rete, e prova a creare un nuovo percorso per arrivare a destinazione. Si vede qua come avere più strare possibili per arrivare alla destinazione sia necessario.

### Alcune tecnologie di rete 🟩

**Ethernet**

Il più famoso è il protocollo **Ethernet** che da il nome a una vasta serie di schede di rete che implementano la sua definizione, per l’utilizzo in reti locali basate su mezzo fisico cablato.
L’idea di base di Ethernet, per ridurre le collisioni dei segnali, è di adottare il **principio dell’ascolto** del canale, prima di ogni trasmissione (se vede che è occupato, viene rigenerato un tempo di attesa casuale). Se nessuno sta già trasmettendo, allora la trasmissione può essere iniziata senza collisione con le trasmissioni in atto. Siccome può accadere che due schede di rete possano iniziare allo stesso istante le rispettive trasmissioni, occorre trovare una soluzione all’insorgere di possibili collisioni. La scheda di rete trasmittente è in grado di rilevare le collisioni in atto *durante* la trasmissione, e in tal caso interrompe immediatamente il tentativo di trasmissione.
Il tentativo verrà tentato da capo, dopo un attesa di tempo casuale, variabile da scheda a scheda.

**Wifi**

Una tecnica simile a Ethernet viene adottata nelle reti senza fili (wireless), ad esempio in reti **Wi-Fi conformi allo Standard IEEE 802.11**. Il problema principale in reti senza fili è dato dall’impossibilità pratica di realizzare la rilevazione di collisioni in atto durante la fase di trasmissione. La tecnica si basa sulla prevenzione delle collisioni, dilazionando nel tempo i tentativi di accesso.

**Token Ring**

Il protocollo **Token Ring** è un protocollo MAC concepito per reti locali con *topologia ad anello*.
L’accesso è regolato per mezzo di un frame speciale, detto Token, che viene passato (trasmesso), come se fosse un “*testimone*”, ciclicamente tra tutti i dispositivi in rete. Solo chi detiene il token ha diritto di trasmettere sul canale, evitando il rischio di collisione, dopodiché deve trasmettere il token alla stazione successiva nell’anello.

La cosa bella di questo è che la trasmissione è necessariamente senza collisioni dato che parla solo uno alla volta, questo è una cosa molto bella.

Un altra cosa è acknowledgement implicito perché se il messaggio ritorna al mittente uguale, allora è OK. Potrei anche costruire comunicazioni a pochi bit, veloci (simili a voice over IP).

**Svantaggio**

Non ho modo di recuperare se

1. Perdo il token (questo è una cosa molto grave!).
2. Un host va giù, e viene rotto il link. (unique point of failure!)

**Note generali**

Queste reti si identificano tutte come best effort perché possono sempre non funzionare, causa collisioni o interferenze di rete

### Esempio di rete locale

- Appunti prof di boh

    La figura mostra un esempio di rete locale composta da diversi segmenti: un segmento con topologia ad anello e protocollo MAC di tipo token ring colorato in rosso e da vari segmenti ethernet, con topologia a stella e a bus, colorati in blu. A sinistra, un calcolatore dotato di dispositivo di rete token ring con indirizzo MAC A è connesso a un anello di rete token ring insieme ad altri 3 calcolatori e insieme a un bridge (oppure uno switch) identificato dal colore giallo (per indicare che agisce a livello MAC/LLC) e dalla lettera B sullo schermo. Il bridge B agisce da collegamento e traduttore dei frame tra il segmento token ring (rosso) ed il successivo segmento ethernet (blu). Il bridge B ha quindi due connettori di rete: uno token ring e uno ethernet. Il segmento ethernet del bridge B è connesso a un Hub (H) dal quale partono sei segmenti ethernet, di tipo punto a punto, verso altrettanti calcolatori. Uno di questi calcolatori, identificato dalla lettera R è un repeater, che propaga e amplifica i segnali verso un
    successivo segmento ethernet con topologia a bus, sul quale esistono quattro calcolatori. Al termine del bus esiste un nuovo repeater R, che propaga e amplifica i segnali verso un ultimo segmento ethernet con topologia a bus, al quale è collegato un calcolatore dotato di scheda ethernet con indirizzo MAC B. Al di sopra dei dispositivi citati viene rappresentato il cammino logico di un frame trasmesso dal calcolatore con MAC A al calcolatore con MAC B, passando per i segmenti, i connettori di rete, e i livelli dei protocolli opportuni. In particolare, il bridge B
    è l’unico elemento nel quale il frame trasmesso sul segmento token ring sale fino al livello 2, per essere tradotto e ritrasmesso sul segmento uscente adottando il nuovo protocollo MAC ethernet. Nei rimanenti dispositivi hub e repeater, i frame sono semplicemente ricevuti e ri-trasmessi sui segmenti uscenti. Se il bridge avesse dovuto connettere più di due segmenti diversi, allora si sarebbe utilizzato uno switch, che svolge l’attività del bridge gestendo più interfacce di rete e protocolli. Dovrebbe essere chiaro a questo punto come sia possibile connettere diversi segmenti di rete locale, e gestire la trasmissione di frame di dati tra due dispositivi qualsiasi di una rete locale, semplicemente identificando i dispositivi attraverso il loro indirizzo
    MAC.




# References