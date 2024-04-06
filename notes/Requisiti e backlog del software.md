---
layout: page
permalink: notes/requisiti-e-backlog-del-software
tags: italian
title: Requisiti e backlog del software
---

## Introduzione sui requisiti del software

### Note introduttive

#### In linguaggio naturale (dizionario) 🟥+

> Sono tutte le **qualità necessarie** per *uno scopo ben determinato*.

Secondo il prof. I requisiti sono dei **desideri** ossia ciò che idealmente vorresti riguardo qualcosa (nel nostro caso il software). Ma credo sia anche una tendenza italiana di fare le cose meglio possibile senza mai soddisfare tutto

#### Functional requirements 🟩
Sono **ciò che permetterà di fare il sistema**

*Esempio*:
> Il sistema permetterà di prenotare un taxi e di avere una stima del tempo di attesa

Nel nostro caso possiamo anche definire **scenario** ossia un caso di utilizzo concreto del sistema e [user story](/notes/modelli-agile#user-stories) come ciò che **il cliente** vuole che il sistema debba fare.

#### Legge di Humphrey 🟨-
> I requisiti di un nuovo prodotto software non saranno chiari finché gli utenti non iniziano a usarlo

Ossia finché non ho una prima soluzione, non so bene cosa voglio -> "I'll know it when I'll see it".
In un certo senso questo giustifica anche la scelta di iniziare a costruire subito, perché prima non puoi sapere, quindi non puoi farne un design.
Quando hai una prima versione, poi puoi iterarci.


#### Processo di analisi del requisito (3) 🟨++
È una **analisi preliminare**, ossia prima ancora di iniziare lo sviluppo e serve per:

1. Capire ciò che vuole il cliente (quindi le funzionalità che deve avere il sistema finale).
	1. Questo è stabilito **senza sapere** come *effettivamente* viene implementato il sistema.
2. Cosa deve soddisfare il sistema, quindi una **proprietà**
	1. Test per verifica dei requisiti, quindi capire esattamente cosa testare, perché la proprietà possa essere verificabile
3. **Vincoli** per esempio di sistema operativo, o risorse (quindi giochi per esempio), oppure di tempo, per esempio in cose real time. (o ciò che deve essere costruito, cose funzionali)

#### Requisiti in livelli diversi 🟨-
Certe formulazioni di requisiti sono più utili a certe parti d'azienda, dipende dal *livello di astrazione* che deve avere il requisito. vedere il triangolino in immagine:
<img src="/images/notes/Requisiti del software-1698072930836.jpeg" alt="Requisiti del software-1698072930836">

#### User Personae 🟩

Sono degli **utenti ideali**, che dovrebbero essere i nostri utenti.
Esempio:
<img src="/images/notes/Requisiti del software-1698075419027.jpeg" alt="Requisiti del software-1698075419027">
Ci chiediamo cosa fa questo utente ideale? Quali sono i suoi obiettivi? Cosa fa di solito di abitudine?

## Backlog management

### Digital product management

#### Passi per la creazione del prodotto digitale (3) 🟨--
1. **Ricerca di mercato**: ci chiediamo quali sono i prodotti utili?
2. **Ideazione del prodotto:** quali sono i target principali? Cosa deve essere il prodotto? Per chi è buono il prodotto?
3. **Requisiti del prodotto** piano dettagliato di tutti i requisiti




# References