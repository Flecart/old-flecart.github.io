---
layout: page
permalink: notes/livello-isa
tags: italian
title: Livello ISA
---

Ripasso Prox: 37
Ripasso: December 31, 2021
Ultima modifica: October 20, 2022 5:12 PM
Primo Abbozzo: October 29, 2021 1:21 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Activation record
- Busy waiting e polling, priorita' interrupt

# 8 ISA livello

il livello isa è il livallo delle istruzioni

## 8.1 Struttura

Solitamente le istruzioni sono divise in due parti:

### 8.1.1 Opcode e indirizzamento

**Opcode**

Questo opcode indica la tipologia di istruzione.

Per esempio per l'architettura HACK è il primo bit, che indica se è una istruzione C oppure una istruzione A.

Questo insieme poi alle altre istruzioni che definiscono cosa deve fare costituiscono OPcode.

**Indirizzamento**

Poi c'è una sezione che indirizza, cioè dice all'istruzione cosa deve prendere e dove deve salvare.

## 8.2 Indirizzamento

### 8.2.1 Diretto

chiamato un indirizzamento diretto quando l'istruzione deve contenere l'informazione della memoria su come operare:

un esempio è $$inc[5]$$ per dire di incrementare il valore all'indirizzo 5

### 8.2.2 Immediato

Ha già l'operando da usare. Quindi nel caso dell'architettura HACK, per l'istruzione A ho già quello che devo fare

### 8.2.3 Registro diretto

Questo è l'indizzamento solito, si utilizza il nome simbolico per dire su quale registro operare.

Ad esempio:

```haskell
inc dx
```

in cui sto direttamente incrementando il registro

### 8.2.4 Registro indiretto

un esempio di indirizzamento indiretto è

```haskell
inc [dx]
```

in cui sto andando a operare sulla locazione di memoria contenuta in dx.

Quindi prende la locazione di dx, che può essere 5 10 o quel che i vuole e poi opera su questo.

È molto simile al diretto, ma utilizza i registri

### 8.2.5 Indicizzato

Per esempio :

```haskell
inc [dx + 5]
```

Prendo l'indirizzo di dx e ci prendo un offset

Di solito può essere utile per activation record, che non so cosa sia, o accedere a certo tipo di strutture.

### 8.2.6 con Stack

Questa è una indicizzazione molto utilizzata, tanto che ci sono dei registri apposta.

Alcune operazioni solite sono pop e push, e la presenza di un registro sp che mantiene la locazione attuale dello stack (un pointer!)

Anche questo per activation record

## 8.3 Tipologie di istruzioni

### 8.3.1 Dati

da memoria a registro.

Registro a registro e simili

### 8.3.2 Aritmetico-logiche binarie

Quindi somme, divisioni moltiplicazioni sottrazioni.

### 8.3.3 Unarie

Per esempio shift. (moltiplicazione o div per due)

Di solito risparmiamo molte istruzioni a livello assembli utilizzando le operazioni unarie.

### 8.3.4 Salti

Quindi spostamento del PC che contiene l'istruction register

### 8.3.5 Invocazione procedure

In hack queste non esistono, ma esistono per la maggior parte delle altre architetture.

Questo salta alla procedura poi fa un return sulla procedure vecchia (si dice chiamata di stack)

Quindi sono due comandi in più che non esistono per il nostro calcolatore

## 8.4 Procedure

### 8.4.1 Activation record

Quando viene chiamata una procedura, si crea un nuovo frame, salvando

1. Variabili locali delle nuova chiamata
2. Un puntatore alla vecchia istruzione

Quando si ritorna alla istruzione precedente tutta questa roba, questo nuovo frame, viene eliminato.

<img src="/images/notes/image/universita/ex-notion/Livello ISA/Untitled.png" alt="image/universita/ex-notion/Livello ISA/Untitled">

- Esempio di chiamata di procedure

    <img src="/images/notes/image/universita/ex-notion/Livello ISA/Untitled 1.png" alt="image/universita/ex-notion/Livello ISA/Untitled 1">


## 8.5 Trap & interrupt

Questi due gestiscono errori del programma. NO

### 8.5.1 Caratteristiche del trap

Questo errore viene chiamato nel caso in cui ci siano accessi non consentiti come

1. Opcode non definito (strano, succede solo se codice corrotto o sistema sballato)
2. Un accesso a memoria non consentita

Questo è gestito dal sistema operativo con un **gestore di trap**. Quindi togliere il controllo (e ucciderlo) al programma con la forza grazie al sistema operativo.

### 8.5.2 Differenze con Interrupt

La differenza principale è che interrupt è chiamato dall'esterno e interpretato grazie al sistema opertivo: per esempio il ctrl-c per ucciderei l programma. Questo è gestito da **interrupt Service Routine - ISR**. Si può dire che sono asincroni mentre le trap sono sincrone.

Es. quando la lezione è interrota da una domanda a cui si vuole rispondere.

### 8.5.3 Priorità dell'interrupt

La CPU può scegliere di non seguire gli interrupt, si parla di **interrupt mascherati** nel caso in cui ci sia un lavoro molto importante (per esempio passare da un thread all'altro, qualcosa di strano che non dovrebbe essere interrotto mentre sta operando).

Oppure anche per scegliere delle priorità se tastiera o disco e simili..

<img src="/images/notes/image/universita/ex-notion/Livello ISA/Untitled 2.png" alt="image/universita/ex-notion/Livello ISA/Untitled 2">

Tipo se il prof non risponde subito alla domanda e dice che lo farà dopo.

### 8.5.4 Busy waiting

È una altra soluzione all'interrupt, cioè ogni 100 millisecondi il sistema operativo va a guardare se esiste un input umano. Ovviamente è molto inefficiente. (in pratica sta aspettando se il disco ha finito per ricominciare a fare le cose normali).

### 8.5.5 Polling

È molto simile al busi waiting, però invece di non fare nulla e aspettare soltanto quando non va a guardare, fa qualche operazione.

Tipo il prof che chiede se ci sono delle domande.
e al busi waiting, però invece di non fare nulla e aspettare soltanto quando non va a guardare, fa qualche operazione.

Tipo il prof che chiede se ci sono delle domande.

# References