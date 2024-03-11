---
layout: page
permalink: notes/rappresentazione-della-conoscenza
tags: italian
title: Rappresentazione della conoscenza
---

Ripasso Prox: 7
Ultima modifica: December 29, 2022 3:24 PM
Primo Abbozzo: August 13, 2022 5:03 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

August 25, 2022

# Rappresentazione della conoscenza

Questo è stato un capitolo molto vasto, che andava in certi punti a toccare la filosofia, la fisica. Un aspetto, quello di **codifica** delle informazioni reali in un ambiente logico (che per quanto i miei pregiudizi siano, ritengo una cosa molto impossibile, molto limitata e altrettanto impossibile). Si tratta dello **studio della logica per rappresentazione di conoscenza**.

Fatto sta che mi sembra assurdamente teorico tanto da non aver nessun utilizzo (probabilmente mi sbaglio di grosso), e che sia roba da filosofi.

Credo che questo capitolo sia **sopratuttto importante per i pattern di rappresentazione di certe cose**.

## Ontologia

Può fare comodo questa pagina di wikipedia,.

> Un ontologia **organizza tutto il mondo in una gerarchia di categorie**.
>

Il libro non fornisce mai una definizione dettagliata di ontologia, definisce solamente il suo scopo, che è quello di dare una struttura agli oggetti che possiamo trovare tutti i giorni (cani, gatti, frutta, pomodori) e li mette ognuna in qualche categoria precisa.

Credo (questa è una mia interpretazione che non esiste, o almeno non ho trovato nel libro), che **l’ontologia descriva la struttura tutto quanto può esistere** nel mondo creato. Quindi se ti dico Banana, tu puoi subito mettere nel cassetto giusto questo oggetto e averne molte proprietà, ma non sono sicuro che sia ciò che intenda il libro Norvig, però di sicuro propone alcuni modi per rappresentare oggetti come Eventi, tempo, credenze, oggetti fisici, credo siano questi 4 i fulcri del capitolo, come rappresentare queste cose astratte.

### Upper ontology

L’ontologia elevata è una **rappresentazione grafica**  di una possibile ontologia. (credo che una ontologia sia più o meno quello che descrive il mondo costruito in quel determinato istante).

**Caratteristiche di un ontologia generale**

1. Applicabilità**,** dovrebbe essere applicata a qualunque istanziazione concreta di oggetto.
2. Riutilizzabilità, dovrebbe avere in sé concetti abbastanza generati che possono essere utilizzati in più modi (esempio il concetto di tempo lo puoi usare come misurazione della durata, ma anche del costo dell’evento).

Ma sembra che sistemi simili non siano stati molto famosi (c’è un fattore umano che non permette la creazione di ontologie generali).

## Categorie

Le categorie sono come degli **insiemi grossi** che accomunano oggetti con certe proprietà. Però noi stiamo utilizzando la [Logica del Primo ordine](/notes/logica-del-primo-ordine) e quindi una categoria è un particolare **predicato**, che può essere **reificato** in un oggetto (ossia invece di tenerti il concetto astratto, definisci tutto quello che serve per poterlo rappresentare, proprio come se fosse una conversione).

La cosa bella è che esistono sottocategorie, che prendono in AUTOMATICO tutte le proprietà delle proprie super-categorie

### Decomposizione delle categorie

Possiamo andare a definire delle partizioni (molto simile a quelle in teoria degli insiemi, anzi direi che il concetto è praticamente lo stesso lol).

1. Disgiunzione (se non hanno nessun elemento in comune)
2. Decomposizione esaustiva (se la loro unione è l’elemento iniziale)
3. Partizione (se a due a due sono disgiunti e vale anche 2).

Se sai teoria degli insiemi credo che per questa parte non c’è nulla da dire

### Rappresentazione di oggetti fisici

Sono molto importanti le funzione **bunchOf, partOf** che definiscono un insieme di cose (che possono essere ad esempio 3 mele, o una parte di essa, come la gamba è una parte del corpo)

(poi su part of puoi fare la decomposizione come per le categorie, il concetto credo sia esattamente lo stesso).

### Misurazione

Di solito per la misurazione ti tieni una **funzione di unità** che restituisce il valore di unità astratto, questa poi la puoi andare ad eguagliare all’unità specifiche, come il metro, il pollice, la spanna etc.

quindi as esempio $$lunghezza(L) = metro(1) = pollici(39,3701)$$ etc. e questa cosa la fai per tutti. È una misurazione più astratta possibile.

Secondo il libro questo è un campo molto sviluppato in fisica quantitativa, anche se Milanese ha cringiato quando l’ho condiviso.

### Categorie naturali

Le categorie naturali sono molto difficili da definire con delle regole esatte come stiamo provando con la logica (l’essere umano è molto ambiguo a riguardo). Potremmo solo definire **qualcosa di tipico** e se soddisfa queste proprietà chiamarlo Banana e simili. Comunque questa parte sembra essere stato analizzato per benino da Wittgenstein 1953.

## Oggetti

I concetti di maggiore importanza da capire degli oggetti è che certi oggetti, anche se divisi, mantengono ancora la propria sostanza, un esempio di questo è un butto, mentre invece esseri umani non lo sono (una mano o gamba non sono un essere umano, mentre un pezzo di burro è ancora burro).

Quindi differenza fra **stuff and things**.

Oltre a ciò l’esistenza di proprietà *intrinseche ed estrinseche*, ossia cose che sopravivivono o meno alla suddivisione

### Eventi

Le relazioni di maggiore imoprtanza per rappresentare gli eventi sono questi

<img src="/images/notes/image/universita/ex-notion/Rappresentazione della conoscenza/Untitled.png" alt="image/universita/ex-notion/Rappresentazione della conoscenza/Untitled">

Se hai queste proprietà definite, puoi proprio avere un sistema di **calcolo degli eventi** per descrivere quanto accade durante qualcosa, mentre in passato col fluente potevi solamente descrivere cosa c’era prima o dopo

### Tempo

<img src="/images/notes/image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 1.png" alt="image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 1">

No comment, questi sono quelle cose di cui hai bisogno per descrivere il tempo (si noti che si utilizza una **funzione di misura** descritta in precedenza).

**Nota dei fluenti con oggetti**

È difficile che l’oggett *Presidente* identifichi una certa persona, perché questa persona cambia nel tempo, quindi teniamo questo come se fosse una classe astratta. E una funzione che prende come input il tempo d’inizio e di fine e una persone e ti dice se è vero o falso se questa persona era presidente in questo periodo di tempo.

### Logica modale

La logica modale permette la rappresentazione metaconoscitiva ossia la conoscenza del conoscere.

Introduce il concetto di **operatore modale** (che in pratica è come se fosse un punto di vista, un frame of reference), che è come se restringesse il campo di conoscenza al singolo operatore.

**Semantica**

La semantica di questa logica cambia totalmente, ora si può dire che un modello è vero, se è vero in tutti i mondi accessibili, non tutti i mondi possibili. Un mondo è accessibile quando non sa nulla su di essa.

esempio se so A, allora questo è accessibile nel mondo A and not B, ma anche al mondo A and B, e sarebbe vera in entrambi i mondi quindi OK.

**Onniscienza**

Il problema di questa logica è che l’agente conosce tutto quello che può sapere, automaticamente si ricava tutte le inferenze possibili da suo campo di sapere, questo è alquanto irrealistico (altrimenti l’essere umano, lol, potrebbe conoscere tutte le conseguenze della matematica per esempio, perché tanto sono tutte inferenze da basi conosciute, ma è chiaro che sia qualcosa di altamente irrealistico.

## Sistemi di ragionamento su categorie

### Network semantici

All’inizio della loro creazione, i network semantici erano in forte discussione con la logica, ma si è poi notato a posteriore che non sono altro che la stessa cosa, ma formulati in modo molto differente.

I network semantici permettono una bella e semplice visualizzazione dei concetti

- Esempio di un network semantico

    <img src="/images/notes/image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 2.png" alt="image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 3.png" alt="image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 3">


Questi si comportano bene per l’ereditarietà (che puoi andare a sovrascrivere come se stessi lavorando su un OOP). però ha problemi con la eridarietà molteplice, perché ci sarebbe ambiguità se entrambi i genitori condividono una informazione, ma sono contrarie uno dall’altra.

### Logica descrittiva

Non è altro che una logica di primo ordine semplificata nella verbosità, soprattuto per i concetti di almeno n elementi e simili.

<img src="/images/notes/image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 4.png" alt="image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 4">

## Informazioni di default

Spesso torna molto comodo nella semantica del database (in cui è a mondo chiuso, tutto quello che non conosci espressamente è negato) avere delle informazioni di default in esse, e questo si può raggiungere principalemtne in due modi ora presentati molto velocemente

### Circoscrizione

mah, non l’ho proprio capita

### Logica di default

Ovvero se vengono soddisfatte delle premesse, e la conseguenza non è assurda, allora conoscerò questa conseguenza.

- Esempietto

    <img src="/images/notes/image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 5.png" alt="image/universita/ex-notion/Rappresentazione della conoscenza/Untitled 5">


### Truth maintenance systems

I sistemi come  **JTMS (Justification-based truth maintenance system)** che tengono per tutte le inferenze che hanno una spiegazione ossia le regole usate per inferire questa cosa, quando si aggiorna tale sistema bisogna andare a togliere tutte le regole che hanno questa altra nella spiegazione .

Un suo amico stretto è **ATMS(assumption-based truth maintenance system)** in cui per colmare l’inesistenza di qualcosa si ha qualche regola di default (credo di stare sbagliando in questo passo) ma comunque non è molto importante ed è molto probabile che stia semplificando troppo in questa parte