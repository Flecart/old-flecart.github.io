---
layout: page
permalink: notes/http-e-rest
tags: italian
title: HTTP e REST
---

Ripasso Prox: 40
Ripasso: May 25, 2023
Ultima modifica: April 15, 2023 10:21 PM
Primo Abbozzo: March 10, 2023 2:16 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# HTTP e REST

## HTTP

**HYPERTEXT-TRANSFER-PROTOCOL**

### Caratteristiche principali (3) 🟨

- Slide caratteristiche

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled.png" alt="image/universita/ex-notion/HTTP e REST/Untitled">

1. Comunicazioni fra client e server, e quanto sono comunicate le cose si chiude la connessione e ci sono politiche di caching molto bone (tipo con i proxy)
2. **Generico**: perché è un protocollo utilizzato per caricare moltissime tipologie di risorse!
3. **Stateless**, ossia non vengono mantenute informazioni su scambi vecchi, in un certo modo ne abbiamo parlato in [Sicurezza delle reti](/notes/sicurezza-delle-reti) quando abbiamo parlato di firewall stateless.

Solitamente possiamo intendere questo protocollo come utile per **scambiare risorse** di cui abbiamo parlato in [Uniform Resource Identifier](/notes/uniform-resource-identifier).

### La connessione 🟩-

È importante oggi rendere efficienti le connessioni, al tempo come descritto in [Livello applicazione e socket](/notes/livello-applicazione-e-socket) per HTTP, per richiedere ogni risorsa si apriva e si chiudeva una connessione (uno dopo l’altro, senza parallelizzazione).

con HTTP2 già questa cosa era cambiato, possiamo richiedere allo stesso tempo più connessioni, è la **pipeline**. Importante notare che la differenza col multiplexing è che nel pipelining ti risponde con l’ordine

**Multiplexing** invece utilizza la stessa connessione per chiedere e rispondere più volte (oggi anche più comune). La differenza principale è elaborare in ordine diverso rispetto a quanto abbia ricevuto.

- Slide connessioni

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 1.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 1">

- Slide esempio tipologie di richiesta

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 2.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 2">


Ci sono anche altri modi per rendere ancora più veloce il protocollo, un esempio è **l’operazione PUSH**, per esempio quando fai la pagina HTML, il server sai già che il client vai a richiedere altre risorse di quella pagina, quindi inizia subito a processare le richieste, prima che il client abbia effettivamente chiesto.

Un altro modo per rendere più veloce la trasmissione è la **compressione degli header** per tutte le richieste e fatte anche in parallelo.

### Richiesta HTTP (5) 🟩

Vogliamo ora andare a parlare della struttura di un pacchetto HTTP affinché si possa considerare valido. Ci sono 5 campi principali:

1. Versione del RFC per HTTP
2. Metodo, tipo PUT, GET etc, ne parliamo sotto.
3. URI, descritto in [Uniform Resource Identifier](/notes/uniform-resource-identifier).
4. Header, che si articolano in molti sotto headers (ci sono molti headers)
5. Body della richiesta
- Slide richiesta HTTP

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 3.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 3">


### Risposta HTTP (4) 🟩

La risposta del server va di 4 campi (cioè è quello che ti ritorna dopo aver elaborato la tua richiesta)

1. Status code
2. Version HTTP
3. Headers (nota headers sono credo praticamente le stesse della richiesta)
4. Body (in cui effettivamente ci sono le informazioni della risposta)
- Slide risposta HTTP

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 4.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 4">

- Esempio di risposta HTTP

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 5.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 5">


### Status codes (5) 🟩

Ci sono 5 campi principali che vanno a descrivere a grandi linee il significato della risposta (in un certo senso è come nella richiesta vado a specificare l’azione, gli status codes ti rispondono con informazioni precise riguardanti la tua richeista).

- Slides sugli status codes

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 6.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 6">

- Esempi di status codes

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 7.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 7">


È importante andare a utilizzare status codes corretti, per ragioni molto simili a un verbo HTTP corretto, perché questo aiuta tutti i servizi capire bene l’esito della nostra richiesta, aiuta i meccanismi di caching a capire se cachare o meno.

### Headers (4) 🟥++

Ci sono 4 tipologie principali di headers  HTTP, andremo a descriverli ora.

**HEADERS GENERALI**

- Slide generali

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 8.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 8">


Si mandano informazioni come cache, la codifica, la data, il tipo di connessione (se deve restare su o meno).

**HEADERS DI ENTITÀ**

- Slides entità

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 9.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 9">


Sono utili per andare ad interpretare le tipologie di content all’interno del body. In parte questa parte è condivisa anche negli headers per il MIME [Headers del MIME (2)🟨](/notes/headers-del-mime-(2)🟨).

Infatti in risposta con una risorsa le content-type e lenght son oobbligatori per specificare informazioni sulla risorsa ritornata.

**HEADERS DI RICHIESTA**

- Slides richiesta

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 10.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 10">


Sono utili per dare informazioni sul client al server.

Esempi sono l’host, l’user-agent che sta facendo la richiesta. Per esempio a seconda dello user agent ho dei CSS leggermente differenti!

**HEADERS DI RISPOSTA**

- Slides risposta

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 11.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 11">


### Metodi HTTP (!)

I metodi HTTP sono presenti all’interno del campo metodo di un pacchetto HTTP, sono anche chiamati **verbi HTTP** perché vanno a descrivere cosa bisogna andare a fare sulla risorsa identificata dall’URI.

- Slide esempio di get e POST

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 12.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 12">


In teoria tutto può essere fatto con GEt, ma se utilizzo bene le API avere status codes corretti rende molto più chiaro ed uniforme l’interazione con essa, quindi molto più **interoperabile**.

**CARATTERISTICHE METHODI HTTP (!!!)**

Sono **sicurezza e idempotenza**. Vorremmo che HTTP sia stateless, quindi vorremmo che non generi cambiamenti dello stato oltre che avere dei logs.

idempotente quando richieste identitiche hanno stesso risultato.

**GET**

- Slide GET 3

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 13.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 13">


**HEAD**

- Slide HEAD 3

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 14.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 14">


**POST**

- Slide POST 0

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 15.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 15">


**PUT**

- Slide PUT 2

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 16.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 16">


**DELETE**

- Slide DELETE 2

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 17.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 17">


**PATCH**

- Slide PATCH 0

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 18.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 18">


la differenza principale con PUT è che patch è per cambiare parzialmente una risorsa e non sostituirla completamente.

**OPTIONS**

- Slide OPTIONS 3

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 19.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 19">

- Slide riassunto caratteristiche

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 20.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 20">


E poi ce ne sarebbero altre, ma solitamente si utilizzano Get post put e delete perché sono quelle più consone per il modello CRUD per rest.

## REST

REpresentational State Transfer è una metodologia di costruzione di API, avevamo già fatto qualcosa cone tipo protobuf. È un **modello architetturale**, ossia modo per creare applicazioni che sfruttano HTTP che possano essere utilizzati da altre applicazioni il modo più chiaro possibile.

1. Connesse sull’ambiente di utilizzo (quindi cose come collezioni, singolo elemento della collezione e simili).

### Modello CRUD (!) (4) 🟩

Quando ho una collezione di dati vogliamo descrivere le operazioni principali che posso fare su essa:

1. Creazione di elemento singolo o di un gruppo
2. Lettura di un individuo o di un gruppo
3. Aggiornamento di dati già esistenti
4. Eliminazione di dati

- Slide su CRUD

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 21.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 21">


Importante notare che questo pattern è indipendente da REst, di solito utilizzato per Database, ma possiamo utilizzare lo stesso mecanismo con Rest e le operazioni di HTTP

Ossia URI come identificatore e Richieste HTTP per andare a modificarle.

- Utilizzo CRUD per Metodi HTTP

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 22.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 22">

- Esempio Verbi HTTP con rest

    <img src="/images/notes/image/universita/ex-notion/HTTP e REST/Untitled 23.png" alt="image/universita/ex-notion/HTTP e REST/Untitled 23">


> In breve REST utilizza URI per identificare la risorsa, e semantica HTTP per andare a richiederla e stabilire la connessione di trasferimento.
>

### Metodologie URI REST 🟨+

Ci sono delle specifiche metodologie per dare senso a un uri che possa essere rest, l'idea principale è la distinzione fra **collezione vs individuo**, che implica anche un utilizzo di metodo HTTP diverso. Per distinguere collezioni da individui dobbiamo mettere il plurale e terminare con lo slash (che direi anche sia una cosa molto strana!)

Queste entità così definite possono essere anche gerarchiche, quindi uno impilato sull'altro, ma sembra tenere a mente la semplicità dell'interfaccia e della navigazione.

### Open API

> Questa parte è molto pìu pratica, andiamo direttamente ad impararla da lì!
>

Open api è una sintassi di solito scritta in YAML presentato molto velocemente in [HTML e Markup](/notes/html-e-markup) nella sezione di markup, permette di specificare in modo molto chiarlo l'interfaccia di un API, e la creazione della documentazione associata.

Di solito questo è il modello preferito (industry standard) per creare queste cose, rende molto chiara la comunicazione delle api diciamo, per il progetto potrebbe essere un buon metodo per interagire col database? Oppure meglio farci richiesta diretta con un ORM. Credo sia molto simile.