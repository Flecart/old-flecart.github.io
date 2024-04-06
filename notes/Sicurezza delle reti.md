---
layout: page
permalink: notes/sicurezza-delle-reti
tags: en
title: Sicurezza delle reti
---

Ripasso Prox: 23
Ripasso: May 17, 2023
Ultima modifica: May 1, 2023 10:58 AM
Primo Abbozzo: March 1, 2023 1:10 PM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Elementi di ripasso

# Sicurezza delle reti

## Introduzione

### Obiettivi della sicurezza (!!!) 🟩

Vogliamo creare delle reti che abbiamo certe garanzie di sicurezza, soprattutto:

1. **Confidenzialità**, non vorremmo che il nostro messaggio sia intercettabile e leggibili da persone intermedie
2. **Integrità**: non vogliamo che messaggi possano essere cambiati senza intervento del sender
3. **Autenticazione**: vorremmo sapere con chi stiamo parlando, e vorremmo essere sicuri che non stiano mentendo sull’identità.
4. **Sicurezza operativa**: vorremmo essere in grado di poter continuare a fornire il servizio (quindi non sia possibile dossare, o installare malware che modifichino il comportamento del servizio).

Questi principi possono essere messe in pratica con specifiche politiche nella fase di invio dei messaggi, implementate nei vari livelli o firewall per poter identificare tentativi di intrusione.

**Come vengono raggiunti questi obiettivi**

Vedremo in seguito che il primo obiettivo viene raggiunto senza molti problemi utilizzando la crittografia, mentre le altre due con le funzioni di hashing. Il quarto con la creazione di protocolli solidi.

### Un principio di sicurezza 🟩

La sicurezza del messaggio non dovrebbe essere basato sull’algoritmo utilizzato per codificare, ma solamente sull’utilizzo della chiave.

Il primo è molto facile da recuperare, o farci reverse engineering, ne abbiamo parlato qui in breve On security of cipher 🟩.
[Classical Cyphers#On security of cipher](/notes/classical-cyphers#on-security-of-cipher)
### Tipologie di attacchi (!!) 🟨

Se è possibile l’attaccante può avere moltissimi vettori di attacchi che possono incrinare i principi di sicurezza che abbiamo enunciato sopra

1. **eavesdrop:** spiare la conversazione (eventualmente rubando password e dati)
2. **Impersonation:** impersonare un altro soggetto (o la macchina di un soggetto).
3. **Hijacking** dirottare una sessione in corso, quindi controllare le richieste che fai, magari ti mando su una copia di paypal falsa, o
4. **Denial of service:** negare il servizio agli utenti legittimi, questo sulla sicurezza operativa.

## Crittografia

La crittografia diventa una delle tecnologie chiave per poter garantire i principi di sicurezza.

### Alcune tipologie di cifrari simmetrici 🟩

Approfonditi in [Block Ciphers](/notes/block-ciphers) che solitamente sono utiizzati negli scambi di messaggi simemtrici.
Elenco qui alcuni cifrari classici:

1. Cifrario monoalfabetico (sostituzione) (come codice cesare, in cui c´è una mappatura per ogni singola lettera ad altra lettera).
2. Cifrario polialfabetico (in cui la cifrazione dipende anche dalla posizione).
3. Cifrario a blocchi, come DES, AES etc.

Importante diventa anche l’hashing, che serve un sacco per poter mantenere l’integrità del messaggio.

Il problema principale di questo metodo è lo scambio delle chiavi, che dovrebbe essere sicura anche questa parte. Ma solitamente cifrari asimmetrici come RSA risolvono questa parte.

La soluzione ottima per questo metodo è utilizzare un sistema a chiave pubblica PKI per scambiarsi la chiave privata con cui continuare le transazioni da lì in poi.

### Tipologie di attacco 🟩

i principali metodi di attacco sono

Ciphertext only attack:

1. Forza bruta, in cui cerco la chiave
2. Statistical analysis attack (per cercare alcuni pattern che possono esistere per rompere il cifrario).

Oltre a questi ho anche classici attacchi col plain text: chosen-plaintext attack, known plaintext attack, questi mi permettono un pò più informazioni.

### Chiavi di sessione e RSA 🟩

Si è parlato di questo ambito per abbastanza, ma non la ritengo molto interessante quindi non la metto, è però molto importante, ma credo tu sappia come funzioni quindi non la scrivo.

Semmai due note sulle chiavi di sessione, è molto semplice, in pratica dato che RSA è molto più lento e costoso (in termini di energia) dei cifrari a chiave simmetrica utilizzo RSA per scambiarmi la chiave con cui faccio la crittazione simmetrica, questa è la **chiave di sessione.**

da notare che la combinazione di Cifrari simmetrici e asimmetrici riescono a dare forti garanzie (non assolute, perché i cifrari possono essere comunque rotti) di confidenzialità fra le persone.

## Autenticazione

### Protocollo di autenticazione 🟩

Il libro prova a costruire passo passo un protocollo di autenticazione (cioè una serie di passaggi che finiscono per riuscire ad asserire l'identità con cui si stia comunicando).

- Protocolli di autenticazione passo passo

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 1.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 2.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 3.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 4.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 4">


Dato che lo scambio di password è sempre vulnerabile a **playback attack**. Ci costruiamo un segreto temporaneo, la **nonce**, che è una mini specie di challenge utilizzata per convincere dell'identità. Se provo a rimandare la nonce criptata con una chiave privata, allora potrei dire che sono ALICE.

E dato che la nonce è unica, non è vulnerabile a playback attack.

- Ultimo protocollo con NONCE e PKI

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 5.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 5">

    R è la nonce


Nel nuovo sistema con la nonce e il sistema chiave pubblica e chiave privata è **ancora vulnerabile a MITM**. Dato che Eve può sempre mettersi in mezzo, e praticamente avere in chiaro tutti i collegamenti, dovremmo cercare di identificare in qualche modo la chiave pubblica della identità giusta. (devo prendere la chiave pubblica da un servizio fidato, queste sono le **certification autorities, CA**).

### Certificate authorities 🟩

Sono dei servizi utili ad identificare l'identità di una persona, e sono in grado di giustificare la corrispondenza della chiave pubblica con una certa identità. Generano per te la chiave pubblica E privata.

Ovviamente la sicurezza dipende dai processi di autenticazione di questa CA (potrebbe chiederti la carta d'identità, o latre informazioni simili), che potrebbe essere vulnerabile anch’essa. (nella storia sono anche stati hackerati, quindi hanno molte coppie di chiavi messe a gente falsa).

- Slide CA

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 6.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 6">


### Integrità del messaggio 🟩

Potremmo utilizzare il PKI, per **firmare** con la nostra chiave privata (e poi CA per trovare la chiave pubblica per poter verificare il messaggio) in questo modo il nostro interlocutore è sicuro dell’**integrità** del nostro messaggio e dell’autenticità di chi me lo sta mandando (con le CA).

Se poi si fa la stessa cosa mandando un messaggio già cifrato, allora ho anche segretezza, senza nessun problema!

Ma poi, dato che è molto costoso firmare un messaggio tanto lungo, solitamente si firma solamente **l'hash** del messaggi originale, quindi rende molto più efficiente il protocollo. ma anche il fatto che in questo modo posso firmare messaggi molto corti! Ho sempre un codice della stessa linguaggio.

- Slide integrità e autenticità

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 7.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 8.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 8">


### **Funzione di hashing** 🟩

Ci sono un sacco di caratteristiche che dovrebbero tutte le funzioni di hashing soddisfare

- Un digest fisso, di una certa lunghezza.
- **Pre-image collision**, dovrebbe essere difficile trovare un altro messaggio con lo stesso hash.
    - Una proprietà che dovrei soddisfare è il fatto che se **cambio un bit di input** cambi di molto l'output, ossia ci sia pochissima correlazione fra input e output! (certamente cose lineari non ci piacciono)

**Esempio di hash brutto** Internet checksum

Un esempio di hash brutto è l'internet checksum perché è molto facile poter creare una collisione!

È in grado di rilevare solamente errori idioti (quelli fatti senza l'intelligenza di un EvE che prova a cambiarti i bit, ma sono abbastanza random!)

### Protocollo Mail sicura 🟩

- Slide protocollo MAIL

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 9.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 9">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 10.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 10">


Praticamente generiamo una chiave simmetrica, poi se vogliamo firmarla e metterci un coso di integrità MAC possiamo farlo, cifriamo con chiave pubblica di bob presa da CA la nostra chiave e mandiamo il pacco con Messaggio privato, magari firmato, e chiave criptata.

Bob riceve e riesce a ricavare tutto quanto possibile per verificare l’integrità del messaggio e comprendere il messaggio!

## Protocollo SSL

Se rendiamo il socket sicuro, rendiamo sicuro tutto quello che c'è sotto, quindi dal livello 4 in giù, vedi [Architettura e livelli 1, 2](/notes/architettura-e-livelli-1,-2) per dettagli sulla stack. In questo modo le applicazioni possono decidere se utilizzare o meno questo protocollo, dato che è sotto di essa.

- Slide presentazione ssl

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 11.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 11">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 12.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 12">


### Implementazione Toy-SSL 🟨+

Utilizzando il sistema presentato sopra riescono a cambiare un segreto (come una chiave condivisa per comunicare, ma sarà un robo per **creare un set di chiavi**, o il vettore di inizializzazione)

Il set di chiavi sono utilizzati per invio direzionale e verifica di integrità direzionale (quindi sono 4 chiavi). Che sono generate dalla Master Key scambiata dalla prima fase.

- Slide SSL

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 13.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 14.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 14">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 15.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 15">


**CARATTERISTICHE PACCHETTI SSL** 🟥

Durante il trasferimento dei dati vogliamo avere anche altre caratteristiche che aiutino a mantenere la sicurezza di questo protocollo:

1. **Numerazione** per evitare che eve duplichi pacchetti o simili.
2. **Verifica di integrità** ha un proprio hash MAC (hashato è anche la numerazione a livello SSL).
- Slide record and sequence numbers

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 16.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 16">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 17.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 17">


**COMMON ATTACKS**

**Reorder attack**, utilizzo le sequence numbers per numerare i records, così sono sicuro che non può riordinare dato che non possiede le chiavi

**Replay attack** riutilizzo anche in questo momento le nonce

**Truncation attack** vogliamo anche avere un modo per terminare in modo sicuro la comunicazione, cioè non dovremmo permettere a Eve di terminare la comunicazione per noi. Per fare questo mettiamo anche una parte tipologia di messaggio in ogni MAC. (importante il fatto che è su due versi la chisura!)

### Implementazione SSL (skip)

Questo è uguale al toy SSL alla fine… Solo con qualche accorgimento in più, non è importante sta parte

- handshake è leggermente più complicato, c’è anche una fase di autenticazione dell'utente e **scelta dell’algoritmo crittografico asimmetrico**.
- Alla fine mando anche MAC di tutti i messaggi di handshake per **prevenire tampering,** come l’eliminazione degli algoritmi più forti per poter provare a bruteforcare meglio.

**RECORD FORMAT**

in questo modo si chiamano i pacchetti di SSL, contengono cose simili a quanto abbiamo descritto per il toy SSL

- Slides format record:

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 18.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 18">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 19.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 19">


La cosa particolare è che i dati e il mac sono entrambi criptati con la chiave simmetrica che abbiamo derivato prima, in modo simile a quanto fatto dal toy-SSL.

## IPsec

Questo è un protocollo di sicurezza a livello Rete e non più a livello socket!

Perché vorremmo avere sicurezza a questo livello? È una cosa troppo comune da dover mettere a livello superiore (ma solitamente viene messa a questo livello per la sicurezza, quindi non è implementata ovunque per dire).

È una cosa molto utile per implementare cose come i **VPN** di aziende. Solitamente solo per questo, in altro non è implementato perché è troppo complesso, per poco di guadagno.


**Esempio:**
<img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 20.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 20">

Nota l'imbustamento e imbustamento è fatto nei router nell'esempio qui, ma può essre fatto anche di computer.

In qualche modo, che non ho capito, lo puoi vedere come se fosse la stessa rete, perché l’IP locale è messo nell'IP sec credo, anche se non sono molto sicuro


### Garanzie IPsec

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 21.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 21">

- Integrità
- Confidenzialità
- Autenticazione dell’origine (credo perché conoscono solamente la chiave della VPN)
- Replay attack non funziona

Con Jocelyn vengono aggiunti anche altre due
- Access control
- Integrity

La cosa bella di applicare la sicurezza a questo livello è che diventa **trasparente** rispetto agli utilizzi da utenti non bene addestrati o applicazioni che la ignorano. In ogni caso ho le garanzie di sopra.

### **Tunnelling mode (2)** 🟩
<img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 22.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 22">

#### Tunneling mode
- **Routers IPsec aware**, quando sono i routers che mettono su il protocollo
Questo metodo solitamente viene utilizzato per reti VPN, perché è il router che si occupa di decriptare ed inoltrare a livello rete locale.

#### Transport mode
- **Host IPsec-aware**, in modo che siano solamente gli host che siano aware, mentre i routers non sanno niente, e si comportano in modo normale in questo modo, secondo una connessione IP.

In questo caso viene cryptato solo il payload, viene utilizzato in host-host




### Security Headers - Service Models

Sembra end-to-end, che dovrebbe essere una garanzia a livello trasporto, dato che alla fine solamente gli utenti finali dovrebbero ricevere il messaggio. Possono essere **Authentication header** oppure **Encapsulation Security Protocol**, la prima non fornisce la confidenzialità, mentre la seconda anche la confidenzialità. Questa è praticamente la differenza principale.

Il primo ha il vantaggio che utilizzi meno energie perché non devi metterti a cifrare (l’altro è sicuro con chi sta parlando, per esempio uno streaming può far uso di AH, dato che non ho bisogno di cifrare il tutto).
<img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 23.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 23">

È la versione più comune Tunnel mode con confidenzialità per gli usi in VPN.
In entrambi i metodi esiste un **sequence number** che viene utilizzato per evitare replay attacks.
In entrambi c'è un **hash** per l'integrità.

### Security Association (4)🟨+

Prima di mettermi a scambiare messaggi, devo essere sicuro con chi sto parlando, quindi vogliamo andare a creare una **security association**, scambio di chiavi e algoritmi di criptazione comune, solo da una direzione verso l'altra.

<img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 24.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 24">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 25.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 25">

#### Security association parameters

Uses usually three parameters
- Security Parameter Index  (32 bit) è un **identificatore** della SA.
- IP destination e sorgente
- Identifier of the security protocol (ESP or AH).
- Altre chiavi di codifica e decodifica.

#### Security Association Database
Posso anche creare un **database di SA** questo si chiama SAD

C’è una security associazione fra tunnel e ogni host

- Slides su SAD

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 26.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 26">


Cose che vengon ostorate qui sono:

1. Identificatore di SA, SPI
2. Chiavi di cifratura e algo di cifratura
3. Interfaccia di inizio e arrivo della SA
4. MAC e chiave di MAC

### IPsec Datagram 🟨

Si noti che anche il pacchetto di livello trasporto è cifrato, quindi anche l'indirizzo di porta e l'indirizzo IP finale dovrà essere cifrato

<img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 27.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 27">


Il modo con cui queste vengono programmate è attraverso alcune regole del router (che controllano se il datagramma va verso certi host, oppure parte da certi host e simili).


### Key Determination Protocol
Quello che viene usato in questo caso è chiamato IKEv2.
Che è una versione di Diffie-Hellman in [Key Exchange protocols](/notes/key-exchange-protocols).
Ma risolve i problemi di Man in the middle, autenticando le due parti. E risolve anche problemi di denial of service dovuti al costo di computazione di diffie-hellman.
Per il problema di flooding usano delle specie di cookie autenticati, che sono creati da chi vuole comunicare (firmati da questi diciamo). Poi usano un cifrario a chiave asymmetric come curve ellittiche o RSA

## Firewalls

Vogliamo cercare di **filtrare quello che entra dall'esterno**. mentre in generale ci fidiamo di quello che è presente all’interno del firewall (quindi se riesco a controllare una macchina che sia dentro avrei pieno accesso).

### Obiettivi dei Firewalls 🟨-

L’obiettimo principale dei Firewalls è proteggere da attacchi esterni, esempi di attacchi potrebbero essere

- Vorrei evitare DoS, ossia permettere senza problemi di aprire delle porte TCP senza andare a chiuderne una.
- Non devo permettere la modifica arbitraria dei dati (che hanno conseguenze penali credo)
- Permettere l’accesso solamente a **utenti autenticati**

Per fare ciò possono avere a disposizione tre tipologie di firewalls, quelly che iltrato senza avere uno stato quelli con uno stato, ma anche le application gateways (che controllano il contenuto di quello che esce e quello che entra).

- Slide obiettivi

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 28.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 28">


### Access control List 🟨+
    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 29.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 29">

In sede diversa, questa strategia è stata analizzata anche in analisi delle autorizzazioni nei sistemi operativi. Vedi [Sicurezza OS](/notes/sicurezza-os).
Vogliamo permettere certe cose, e negarne altre. La ACL è solamente una lista di regole di permessi e negazioni, con specificazione di source, address, protocollo, porta di arrivo e di partenza e flag…

Con queste regole posso implementare senza problemi il Stateless filtering

### Stateless/Stateful Packet filtering 🟩

- Alcuni pacchetti vengono droppati quando ci sono certe informazioni all'interno del pacchetto.
- Informazione come Source e destination IP
- Port numbers for TCP or UDP
- ICMP messages
- Syn and Ack bits, and maybe more
- Slides Stateless packet filtering

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 30.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 30">

    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 31.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 31">

- More examples of these
    <img src="/images/notes/image/universita/ex-notion/Sicurezza delle reti/Untitled 32.png" alt="image/universita/ex-notion/Sicurezza delle reti/Untitled 32">


Quando una cosa non ha molto senso da sola, e ha bisogno di tenere conto dello stato della connessione allora abbiamo bisogno di utilizzare uno **stateful packet filtering** in cui si monitora la storia della connessione TCP una volta che la connessione è stata aperta.

### Application gateway and IDS 🟩

Fanno a vedere il contenuto, e gli header dei pacchetti che provengono dall'interno. TODO meglio, il prof ha saltato.

**Intrusion detection systems /turn**

Vogliamo cercare di capire se siamo sotto attacco, quindi se qualcuno fa port scanning, oppure packet filtering pesante da certe cose, oppure provare a vedere se il contenuto del pacchetto potrebbe essere dannoso.

### Demilitarized 🟩

[https://doubleoctopus.com/security-wiki/network-architecture/demilitarized-zone/](https://doubleoctopus.com/security-wiki/network-architecture/demilitarized-zone/)

in pratica è possiamo considerarla come una rete di appoggio per accedere a una rete untrusted esterna, come Internet.

Solitamente in questa DMZ ci mettiamo cose come Email, web servers e cose simili. È una zona quarantinata, cioè per interagire col network interno si passa di nuovo d aun firewall, questo per garantire maggiore protezione della roba interna, solitamente molto più importante.



# References