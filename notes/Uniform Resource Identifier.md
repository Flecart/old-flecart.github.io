---
layout: page
permalink: notes/uniform-resource-identifier
tags: italian
title: Uniform Resource Identifier
---

Ripasso: May 14, 2023
Ultima modifica: June 17, 2023 11:54 PM
Primo Abbozzo: February 24, 2023 1:33 PM
Studi Personali: No

# Elementi di ripasso

# URI

Sono stata LA vera invenzione di Berners Lee accennati in [Storia del web](/notes/storia-del-web). Il problema è avere un modo per identificare una risorsa in modo univoco sull’internet.

## Introduzione

### La risorsa 🟩

> Una risorsa è qualunque struttura che sia oggetto di scambio tra
applicazioni all’interno del World Wide Web.
>

Ora una risorsa può essere qualunque cosa, non solamente solo un file! Quindi è agnostico rispetto a contenuto oppure metodo di memorizzazione del dato, appare anche in questo ambiente importante vedere quanto siano importanti standard che permettano una comunicazione

Esempi di risorsa:

1. File di testo
2. Immagine
3. Chiave di Hash
4. Chiave per una query di database
5. Una funzione da chiamare da remoto

In pratica qualunque cosa che possa fare il web, e identificabile da un URI si potrebbe chiamare risorsa, è un termine molto generale, non definito in modo formale o tecnico.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled">


In breve è risorsa **qualunque cosa che possa essere oggetto di scambio** in una interazione web.

### URL and URN

> Gli URI (Uniform Resource Identifier) sono una **sintassi**
usata in WWW per definire i nomi e gli indirizzi di oggetti
(risorse) su Internet.
>

**URL** indicano la locazione della risorsa (che il browser riesce ad andare a questa locazione, ma può essere cambiato dal gestore della risorsa, e quindi può essere spostato e mai più trovato!), a volte non piace molto questa cosa, e quindi si cerca di creare un URL permanente. Che di solito o è fatto per redirezione quando si sposta o Ho un sistema di virtualizzazione di uri fisici (in qui veramente c’è la risorsa e virtuali (quelli in interfaccia su cui faccio la richiesta).

**URN** è una etichettazione permanente di una risorsa, è PERMANENTE ma ha bisogno di una *risoluzione* per la sua locazione, per risolvere il problema della locazione nel caso venisse spostata.

Gli URI potremmo definirli come l'intersezione fra le due, sia un modo per identificare la locazione (quindi andare ad accederci) sia un modo per etichettarli in modo definitivo (in questo modo sono degli URN).

### Caratteristiche 🟨

URI sono un sistema sintattico (focus sul fatto che siano puramente sintattici!!!, non descrivono la semantica (cosa fare per accedere, ma comunicano il protocollo usato per accedere)che possiamo vederlo anche come sistema di 7 livello OSI utilizzato per identificare la risorsa è importante quindi che

1. **Trascrivibili**, ossia hanno caratteri limitati, e tutti leggibili da umani.
2. **Identificazione, non interazione**, avendo solo l’URI non posso fare operazioni sulla risorsa.
3. **Gerarchizzazione dei nomi** url ha una certa struttura (come i caratteri speciali nell’URL), in questo senso esiste una certa gerarchizzazione dei nomi! (simile a quanto faccia il filesystem).

### Struttura dell’URI 5

> URI = schema : [// authority] path [? query] [# fragment]
>
- Slide

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 1.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 2.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 2">


Per favorire la trascrivibilità ci sono certi caratteri scpeciali tenuti apparte (e se servono sono encodati). **curi** si parla di caratteri per URI.

```jsx
curi = unreserved | reserved | escaped
```

- Slide sui caratteri encodati

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 3.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 3">


Per sapere i caratteri encodati, sarebbe bene tenersi a mente le slides, o comunque la grammatica diciamo!

### URI resolution and dereference (!)

Un uri può essere assoluto oppure una **URI reference**. Se è assoluto allora deve soddisfare tutta la struttura di cui sopra, oppure semplicemente dire il nome del file a seconda di una certa base.

In questo caso si parla di **URI Reference** perché è relativo a un certo dato.

**resolution:** Quando do in input un URI reference e in output mi aspetto una URI completa

**Dereferencing:** quando do in input un URI completo e mi aspetto indietro una risorsa.

- Alcune regole di URI resolution

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 4.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 5.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 6.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 6">


## Routing

### Tipologie di routing (2)

**Managed Route**

Questo è la forma di gestione degli URI più nuova, in pratica il mapping di gestione delle risorse è fatto a livello **server**. (quindi e.g. in Express posso dire a un certo URL quale risorsa interna corrisponde).

**File-system route**

Questo è il modo più facile diciamo, praticamente c’è corrispondenza fra un percorso all’interno del file system all’indirizzo URI.

Questo ha problemi di security perché

1. Do informazioni sulla struttura interna del nostro sito
2. Non ho controllo sull’accesso dall’esterno
3. Non è molto malleabile se voglio cambiare la struttura

### **URI Rewriting**

È un modo di virtualizzare la URI, una risorsa interna (con uri fisico vero, cioè dove sta fisicamente) con un uri virtuale all’esterno, questo è quello che farebbe ad esempio **mod_rewrite** di apache.

È particolarmente comodo perché mi permette di essere più sicuro di informazioni nascoste e di gestire meglio il nome delle risorse esposte a seconda di cosa io abbia internamente, praticamente è un **sistema managed route**.

La differenza con URI alias è che l’URI vero qui è nascosto, e non è esposto

### CURIE

Compact URI, un nome carino per riferirsi a modi compatti di scrivere gli uri sono nella forma [prefix:curie].

- Slides

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 7.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 8.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 8">


## Alcuni protocolli (schema URI)

Di questi non ci importa sapere esattamente i dettagli della loro sintassi, ma che esistono e sono degli URI per qualche tipologia di risorsa!

### HTTP e HTTPS

HTTP è uno dei protocolli più comuni per il WWW. HTTPS è la sua forma sicura.

<img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 9.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 9">

Per maggiori dettagli riguardo funzionamento del protocollo guardare [HTTP e REST](/notes/http-e-rest)

### File Schema

Equivalente ad aprire un file dal browser.

Importante osservare che **non esiste un server che gira** con questo schema

- Slide

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 10.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 10">


### Data

Di solito questo è presente nel payload come messaggio di risposta a qualcosa.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 11.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 11">


### FTP

- Slide

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 12.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 12">


## Tentativi di internazionalizzazione

### CDN

> una rete fortemente distribuita di server commerciali
che collaborano tra loro per distribuire in maniera omogenea
contenuti di grande successo senza inutili duplicazioni di
occupazione e trasmissione di file.
>

in pratica questi sono dei server che fanno **caching** con praticamente la stessa idea che avresti avuto in [Memoria](/notes/memoria)! Una zona di computer che praticamente contiene tutte le librerie più utilizzate, che siano di facile accesso, e che quindi velocizzano il tempo per prendere una risorsa di molto!

### X-WWW-URLENCODED

Una estensione al formato URI per HTTP, questo credo sia un modo per evitare di madnare dei form-multipart data che si leggono male, ma con questo si dovrebbe leggere meglio. Altri motivi non mi vengono in mente del perché sono proprio necessari.

### IRI e IDN

IRI è un International resource identifier che permette di risolvere risorse identificate da nomi non solo in ASCII 7, senza dover utilizzare url-encoding. Esteso a UTF-32!!!

Il problema principale è che da problemi di aliasing (a cirillica molto simile di a latina, quindi uno potrebbe fare pishing basandosi su questa cosa), questo è stato permesso da **IDN (Internationalized DomainName**) che permette di avere nomi di nominio anche non di soli caratteri latini, utilizza UNICODE ???. Questi sono **attacchi via omografi**.

### La visione dei software

Le cose online dovrebbero essere accessibili anche ai software, non solo agli umani. Questo e importante per i crawling bots credo, così riescono a farsi una idea del sito o allo stesso modo queste cose strane…

Per berners Lee, che introdusse il **Linked Data** questo era importante perché così un dato poteva essere accessibile anche da applicazioni. affermazioni atomiche minimali

- Nome, proprietà, Valore (sono in sta forma, come URI però).

Questo è quello che fa WIkiDATA!!!

- Slides

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 13.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Uniform Resource Identifier/Untitled 14.png" alt="image/universita/ex-notion/Uniform Resource Identifier/Untitled 14">


Questo si collega senza nessun problema all'ultima parte trattata nel corso riguardante il [Metadati web e web semantico](/notes/metadati-web-e-web-semantico).

In cui si vanno a parlare di **RDF** e simili. (immagine di un web accessibile tanto ai bot quanto agli umani, perché i dati sono tutti tanto strutturati).

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
**RDF** e simili. (immagine di un web accessibile tanto ai bot quanto agli umani, perché i dati sono tutti tanto strutturati).

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |