---
layout: page
permalink: notes/cookie-e-autenticazione
tags: italian
title: Cookie e autenticazione
---

Ripasso: May 14, 2023
Ultima modifica: May 6, 2023 6:25 PM
Primo Abbozzo: March 30, 2023 4:20 PM
Studi Personali: No

# Cookies

Gli utilizzi più soliti sono per Autenticazione e per  Autorizzazione, perché sono delle informazioni che il server genera e mette al client, come se fossero dei segreti cifrati.

## Cookie

Questi sono una estensione di netscape, che si appoggiano al protocollo HTTP per implementare certe funzionalità (soprattutto il fatto di essere **stateless**, quindi è utile per avere informazioni sugli stati su qualcosa.)

- Slide cookie

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled">


Vengon utilizzati header specifici per settare il cookie.

### Architettura dei cookie

I cookie sono briciole di informazioni sul client generati dall'applicazione server, di seguito nelle slides vedi in che modo funzionano solitamente:

- Slide cookie

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 1.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 2.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 3.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 3">


### Tipologie di coockie

- **Permanenti** sono utili soprattutto per mantenere informazioni di **preferenza sugli utenti.
- **Di sessione** qui ti diverti a fare cose sulla sicurezza 😀.
- **Di terze parti** sono utilizzati per decidere che pubblicità mostrarti, per esempio basandosi sulla history di ricerche.

## Autenticazione

Non ci piacerebbe autenticarci ogni volta a ogni cambio di tab ossia **identificare chi stia facendo l'acceso alla risorsa** come se fosse un riconoscimento, i cookie sono buoni per storare queste informazioni.

### Schemi di autenticazione (3)

Se provi ad accedere a una risorsa, il server dovrebbe risponderti con 401 Not authenticated e darti un header `WWW-authenticate` dandoti informazioni su come autenticarti.

**BASIC**

- Slide basic auth

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 4.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 4">


Questo manda in pratica tutto in chiaro attraverso l'header del client, ovviamente non è che sia molto sicuro…

Quindi è in **disuso**.

**DIGEST**

- Slide digest auth

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 5.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 5">


In pratica è come il basic, ma invece di mandare la cosa in chiaro si manda **hash + nonce**, in modo da evitare replay attack come specificato in [Sicurezza delle reti](/notes/sicurezza-delle-reti).

Anche qui è difficile capire quando la sessione scade.

**BEARER**

In pratica il server produce qualcosa, un token e poi il client utilizza solo questo per autenticarsi nelle connessioni successive.

Può essere utilizzato sia in session sia in token auth

### Session-based authentication

- Slides session based authentication

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 6.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 7.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 7">


In pratica al primo collegamento ti metto dei cookie, che sono i **cookie di sessioen**, che scadono in un certo tempo. Poi per ogni collegamento ti mando anche i cookie di sessione, che danno informazioni di autenticazione.

Questo è uno schema classico, il server ha il controllo sul tempo e sulla revoca di questa sessione.

### Token-based authentication

- Slides token based auth

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 8.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 8">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 9.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 9">


Praticamente quando la prima volta fai auth io ti rispondo con un **token firmato** come potrebbe essere Il token JWT.

Questo poi viene utilizzato. la cosa bella è che utilizzo il server molto meno, nel senso che deve andare a memorizzare molto meno, basta verificare la firma ogni volta.

### Il token JWT

Questo l'abbiamo utilizzato molto spesso per la parte di cybersec!

- Slide JWT

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 10.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 10">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 11.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 11">

- Contenuto Header Payload e signature

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 12.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 13.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 13">


## Altre note: CORS e Caching

### Introduzione Cross site vulnerability

- Slide headers CORS

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 14.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 14">


Non vorremmo avere le javascript esterno non controllato, potrebbero avere codice maligno! Pensa se ti riuscissero a pishare il cookie di sessione.

Posso mettere nelle options di HTTP scripts permessi

### CORS headers

- Slide headers per cors

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 15.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 15">

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 16.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 16">


### HTTP Caching (2)

*Server specified expiration*

- Slide server specified expiration

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 17.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 17">


In pratica attraverso certe specificazioni dico quando il cache sarà expired.

*Heuristic expiration*

- Heuristic expiration

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 18.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 18">


Questo perché spesso

- Risposta dalla cache

    <img src="/images/notes/image/universita/ex-notion/Cookie e autenticazione/Untitled 19.png" alt="image/universita/ex-notion/Cookie e autenticazione/Untitled 19">


Se è non modificata ti mando un codice 304 Not modified altrimenti ti risponso, così non devo fare due richeiste, una head per veder elast modified e una altra per mandarti la get.