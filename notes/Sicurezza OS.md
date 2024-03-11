---
layout: page
permalink: notes/sicurezza-os
tags: italian
title: Sicurezza OS
---

Ripasso Prox: 12
Ripasso: May 27, 2023
Ultima modifica: May 16, 2023 1:10 PM
Primo Abbozzo: April 19, 2023 9:19 AM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Elementi di ripasso

# Sicurezza OS

## Introduzione

### Note generali sulla sicurezza

Su tre fronti

- Hardware
- Software
- humanware (lol).

Una altra tendenza generale è che **più è complessa più è insicura**. e questo senso di insicurezza cresce in modo maggiore rispetto al lineare.

### Tre capisaldi (!!!) 🟩

Ne abbiamo parlato in modo leggermente inverso in [Sicurezza delle reti](/notes/sicurezza-delle-reti).

In questo caso sono

1. Availability
2. Integrity
3. Confidentiality

È cambiata solamente l’availability, ossia la disponibilità in confronto alla sicurezza delel reti, in cui c’era l’autenticazione.

Availability significa la disponibilità del servizio agli utenti, fare un DDoS per esempio è una violazione di questo genere.

La cosa difficile è **garantire tutti e 3**.

**VIOLAZIONE NOME**

- Disclosure
- Alteration
- Denial of service

Nel caso dell’autenticazione sarebbe il phishing, furto didentità diciamo.

### Sistema politica e meccanismi 🟩

già descritta in [Architettura software dell’OS](/notes/architettura-software-dell’os). l’idea è la stessa, separazione meccanismi e segurie questi meccanismi, solo che siamo in ambito sicurezza ora e non implementazione del kernel.

### Crittografia 🟩

Anche questo è stato descritto in [Sicurezza delle reti](/notes/sicurezza-delle-reti), pubbliche private, simmetriche asimmetriche, DES AES RSA e ora curve elittiche etc.

**One-way functions**. difficili da invertire.

Simmetrica, in cui sapere la chiave sai tutto.

### Tipologie di attacchi 🟨

- Slides attacchi tipologie

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled">


Divisione per attività dell’attaccante

Per veicolo dell'attacco (se da dentro o da fuori)

Obiettivi dell’attacco (quindi gravità della compromissione della macchina diciamo.

- Slides veicoli di attacco (3)

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 1.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 1">


## Attacchi soliti

### Buffer overflow 🟩

- Slides contromisure

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 2.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 2">


### Time of Check Time of use 🟩

Tipo access ha detto, quando non è atomico il check e l’utilizzo, nel mezzo il file potrebbe essere cambiato

### Trojan horse 🟩

- Slides trojan horse

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 3.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 3">

- Esempi di trojan horses

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 4.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 4">


### Virus e batteri 🟨

- Slides virus e batteri

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 5.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 5">


Solitamente questi virus hanno comportamenti classici, e si può estrarre una firma, questo è quello con cui utilizzano antivirus per checkare.

## Autenticazione

### Memorizzazione password 🟩

**SALT**

Parlare di etc passwd ed `/etc/shadow`

### Login spoofing 🟩

### Sniffers 🟨+

### Challenge based 🟩

### Smart card and physical objects 🟩-

### PAM🟨

- Slide PAM

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 6.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 6">


I campi sono 2/3, si indica per chi si utilizza la policy, poi politiche della policy (se passa o meno o simili) e poi qualcosa di pam da utilizzare

## Autorizzazione

Vogliamo dare i permessi alle persone (chi può fare cosa).

### Principi d’autorizzazione (4) 🟨-

<img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 7.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 7">

<img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 8.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 8">

### Domini di accesso e ACL 🟩—

Definiamo una riga per utente e in questa riga mettiamo tutti i permessi per questo utente.

<img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 9.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 9">

Slide Access control list

### Extended ACL

Quando nelle acl

Praticamente ogni posso associare dei permessi aggiuntivi che vanno ad ogni user del singolo gruppo. Poi queste sono passate da delle mask. In pratica mi permette di avere più controllo sui permessi.

In linux se viene utilizzato questo c’è un + alla fine della lista permessi.

si utilizzano comandi come `getfactl` per gestire queste credo.

### Capability 🟩—

C’è il concetto di **capability** ossia ogni risorsa deve essere associata una serie di diritti d’accesso.

- Slides capability

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 10.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 10">


Quando viene mantenuto in lato utente, in pratica viene cifrata con la chiave privata del root, e questo viene sempre verificato. (solitamente nei sistemi distribuiti viene utilizzato questo metodo (posso eliminare la capability)

Ma come eseguire la revoca della capability di questi servizi?

### REVOCA DELLE CAPABILITIES(4)

- Slides rimozione della capability (4)

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 11.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 11">


### Effective user nad real 🟩—

- Slide effective and real

    <img src="/images/notes/image/universita/ex-notion/Sicurezza OS/Untitled 12.png" alt="image/universita/ex-notion/Sicurezza OS/Untitled 12">


Si possono fare attacchi Toc Tou anche su questi checks (real son oquelli effettivi, dell’utente, mentre effettive sono i permessi utilizzati durante il momento di check).

### MAC and DAC

Mac BLP (bell lapadula)