---
layout: page
permalink: notes/javascript
tags: italian
title: Javascript
---

Ripasso: May 14, 2023
Ultima modifica: May 6, 2023 6:25 PM
Primo Abbozzo: March 20, 2023 3:16 PM
Studi Personali: No

# Elementi di ripasso

# Javascript

Obiettivo principale è esegurie codice clientside

## Un pò di storia

nato all’inizio della prima guerra dei browser (da netscape, explorer è in visual basic comunque non compatibile con JS) come il fratellino di java nel senso che runnava ovunque, attualmente è ECMAScript, ed è la versione migliore. (era pensato per fare microscript!)

ECMAScript quando è nato è il nucleo a tutte le implementazioni JS eseistenti fino a quel momento (che è stato molto caotico!)

Anche **l’unico linguaggio che va sul browser**. Typescript sarebbe molto carino 😀.

## Esecuzione di JS

### Client side o Server-side

Possiamo eseguire server-side (node) per eseguire codice JS in server side, anche se non ho più questa integrazione con il client (come eventi, e simili).

Ossia l’evento triggera il codice JS corrispondente!

- Esecuzione sincrona o asincrona

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled.png" alt="image/universita/ex-notion/Javascript/Untitled">


Sincrona = caricamento dello script (quando carica, il browser non fa altro! È una cosa sincrona, quindi non carica altro HTML e simili).

Asincrono su eventi DOM o callback di eventi di rete. (esempio chiamata AJAX asincrona, mentre la chiama sincrona è molto brutto perché il server è bloccatooo)

Brevi e veloci per i sincroni! No n2.

### Posizionamento del codice (3)

1. Si può posizionare inline come il codice css
- Esempio 1.

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 1.png" alt="image/universita/ex-notion/Javascript/Untitled 1">

1. Sezione script all’inizio, come style di css
- Esempio 2.

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 2.png" alt="image/universita/ex-notion/Javascript/Untitled 2">

1. File separato
- Esempio 3.

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 3.png" alt="image/universita/ex-notion/Javascript/Untitled 3">


Questi sono i metodi principali, solitamente si preferisce il terzo metodo per migliore gestione degli script.

ma col terzo metodo si deve fare molta attenzione sul tempo di caricamento dlelo script (che è sincrona!)

### Cose del linguaggio

Cose come oggetti, arrays, somme, comparazioni, JSON, Dati, li hai fatti troppo dai.

Questo è tutto **ecmascript**, mentre se andiamo ad interagire con il browser abbiamo altri metodi!.

### Interpolazione (!!)

Se esiste una variabile visibile nello scope attuale, allora lo sostituisco nella stringa. Principalmente questo. Per la prima volta l'oggetto della computazione sono frammenti di HTML, questo permette di dividere html e JS (anche se non ho capito bene come).

### IIFE !

Queste sono funzioni dichiarate e subito eseguite, sono utili per avere delle **variabili private**. (con solamente gli oggetti infatti non è possibile definire tali variabili.

## Client defined classes

Un sacco di robe, non ha senso scriverle, quindi le enumero in modo molto breve qui

### Window
In pratica è il **tab** della pagina di questo istante (sia in lettura sia in scrittura), contiene in sé il documento.

### Document
Sono la rappresentazione in memoria del documento che è mostrato (quindi ci sono tutti i nodi che ci importano!

## Ajax

**PROBLEMA:**
Ogni volta in cui devo cambiare elemento dell'interfaccia, non posso fare altro che **duplicare la pagina**, ossia fare una piena richiesta HTTP con le modifiche, infatti è grande cambio di informazioni, nel senso che non mi servirebbe.

### Introduzione Ajax
- Slide introduzione
    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 4.png" alt="image/universita/ex-notion/Javascript/Untitled 4">


La cosa carina che significa anche AIACE 😀, ma non c’entra niente.

L’obiettivo è caricamenti **asincroni per frammenti XML** con questo aggiorno la pagina HTML, invece di cambiare da un altro URL.

Oggi XML è considerato troppo verboso, in verità andiamo a scambiare frammenti JSON di cui abbiamo parlato in [Alcuni linguaggi di Markup (non impo) 🟥+](/notes/alcuni-linguaggi-di-markup-(non-impo)-🟥+), e sempre in [Javascript](/notes/javascript).

Ora il formato è tipo:

- carico HTML molto vuoto
- carico applicazione JS anche complessa
- L’applicazione fa richieste e popola la pagina in modo attivo
- Utente fa altra attività, triggera altre richieste, la pagina cambia.

Ecco l’interattività!

- Slide AJAX

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 5.png" alt="image/universita/ex-notion/Javascript/Untitled 5">

- Confronto architettura scambi HTML e AJAX

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 6.png" alt="image/universita/ex-notion/Javascript/Untitled 6">

    Quando faccio la richiesta, il browser è bloccato, poi quando il server finisce il browser riceve tutto, butta via vecchio e comincia a fare le cose nuove. (continuo stop and go)

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 7.png" alt="image/universita/ex-notion/Javascript/Untitled 7">

    Nota: **browser non si blocca per l'utente** (script sono molto veloci che non sembra bloccarsi!)


Un esempio di applicazione AJAX è maps.google.com, perché inizia a caricare secondo attività dell’utente, le piastrelle a un certo livello i zoom 🙂

### Struttura processo ajax (4)

- Slide processo applicazione Ajax

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 8.png" alt="image/universita/ex-notion/Javascript/Untitled 8">


- Creazione della richiesta

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 9.png" alt="image/universita/ex-notion/Javascript/Untitled 9">

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 10.png" alt="image/universita/ex-notion/Javascript/Untitled 10">

    On Ready state change chiama la funzione ogni volta che cambia lo stato (che abbiamo detto possono essere 5 valori.

    se è 4 la richiesta è tornata ed è stata elaborata →**completata:D**

- Invio della richiesta (DIFFERENZA POST E GET!!!!)

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 11.png" alt="image/universita/ex-notion/Javascript/Untitled 11">

- Gestione della risposta

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 12.png" alt="image/universita/ex-notion/Javascript/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 13.png" alt="image/universita/ex-notion/Javascript/Untitled 13">


### Vantaggi svantaggi AJAX

Importantissimo per AJAX e js!

- Navigazione della pagina non è sincronizzato con lo scambio di dati! mentre prima sì
- Slide vantaggi AJAX

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 14.png" alt="image/universita/ex-notion/Javascript/Untitled 14">

1. Usabile, interattiva, senza tempi morti
2. Molto più veloce, per minore numero di pacchetti mandati
3. Chiunque lo implementa :D

- Slide svantaggi AJAX

    <img src="/images/notes/image/universita/ex-notion/Javascript/Untitled 15.png" alt="image/universita/ex-notion/Javascript/Untitled 15">

1. Devo aggiungere step di navigazione di history fittizi per poter andare avanti indietro nella storia! (non lo fa il browser ma lo fa la mia applicazione) si chiama **routing**
2. Ajax è inerentemente **non lineare** perché posso cambiare contenuto ovunque, anche mentre il mio sintetizzatore sta leggendo la pagina (per accessibilità invece serve la linearità).
3. L’implementazione può cambiare da browser a browser, qualcosa potrebbe essere rotto qui e non in un altro browser.

### Framework Ajax

*XMLHTTPRequest*

È la libreria per Ajax, ma è molto molto macchinosa! Per questo motivo utiliziamo altro, come JQuery che vedremo dopo.

**jQuery**

È un framework che è nato per semplificare tutta la parte macchinosa dell’applicazione AJAX, oggi **non è più utilizzato** perché le funzionalità sono già direttamente presenti sul browser.
È più per mantenere codice vecchio.
Ce ne sarebbero altre ma non le ha descritte