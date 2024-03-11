---
layout: page
permalink: notes/semplificazione-grammatiche
tags: italian
title: Semplificazione grammatiche
---

Ripasso Prox: 65
Ripasso: June 21, 2023
Ultima modifica: June 9, 2023 12:53 PM
Primo Abbozzo: November 8, 2022 1:48 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled">


# Semplificazione grammatiche

## Gestione del non determinismo

Il modo più facile per gestire il non determinsmo è **semplificare le grammatiche** quindi andiamo a vedere metodi per fare ciò.

### Semplificazione grammatiche (5)

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 1.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 1">

1. No produzioni del tipo $$A \to \varepsilon$$ per bottom up (altrimenti va all’infinito!)
2. No produzioni unitarie, così evito cicli in cui da A derivo sé stesso.
3. No simboli inutili
4. No ricorsione sinistra (divergenza per top-down)
5. Fattorizzazione della grammatica

## Eliminazione delel produzioni nulle

Vogliamo creare un algoritmo utile ad eliminare le produzioni che non ci piacciono.

- Formalizzazione algo obiettivo

!<img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 2.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 2">


### **Insieme dei simboli annullabili** 🟩

Vogliamo con questa parte definire in modo formale l'insieme dei non terminali che portano a produzioni di quel genere

- Slide definizione simboli annullabili

!<img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 3.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 3">


Ossia una annullabilità in n passi, e andiamo ad indagare tutti i simboli che soddisfano queste cose.

**NOTA:** nello step induttivo, un simbolo è annulable solo se l’intera produzione è annullabile (quindi tutte le cose in output.

Una cosa del tipo $$A \to BC$$ è annullabile solo se lo sono **entrambi** (sia B che C).

### Derivazione grammatica annullabilità 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 4.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 4">

- Slide esempio

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 5.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 5">


**Intuizione**

In pratica vado ad eliminare i non terminali in tutti i modi possibili, e vado ad eliminare quelle che poi vanno ad eliminare. In pratica mi vado a tenere tutte le configurazioni che posso attenere, annullando quello che si può annullare.

Faccio questa cosa per tutti!

**Nota sul vuoto**

Se vogliamo che il nuovo linguaggio possa accettare il vuoto, allora basta aggiungere al non terminale iniziale la produzione dle tipo $$S \to \varepsilon$$, ma questo è presente solo al primo!.

## Produzioni unitarie

Vorremmo evitare le produzioni unitarie che portano a cicli perché altrimenti avrei dei cicli infiniti che non sono molto buoni per il parsing.

- Definizioni utili

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 6.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 6">


### Coppie unitarie 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 7.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 7">


In pratica è come se definissi una operazion per le coppie unitarie, e la chiudo per riflessività e transitività.

### Algoritmo di eliminazione 🟩

- Algoritmo per eliminare coppie unitarie

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 8.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 8">


Per la creazione della nuova grammatica, quello che faccio non è altro che filtrare quelle che mi portano a coppie unitarie.

Oltre a questo faccio una copia… Se guardi l’esempio comunque lo vedi un pò meglio

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 9.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 9">


## Rimozione di simboli inutili

### Def generatore e raggiungibilità (2) 🟩

In questa sezione andiamo a definire alcuni concetti utili a definire l'inutilità di alcuni simboli

- Slide

!<img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 10.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 10">


Così andiamo a definire come simbolo utile **simbolo generatore e raggiungibile**.

Così andiamo a racchiudere il concetto di simbolo che non genera nulla, come inutle

- Esempio in slide

!<img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 11.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 11">


### Calcolo dei simboli generatori 🟩-

- Slide

!<img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 12.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 12">


Ossia se da un simbolo ricavo qualcosa che è un generatore, allora questo è un generatore!

E posso creare un algoritmo ricorsivo che genera questi simboli, partendo dai terminali che sono sempre dei generatori

### Calcolo dei simboli raggiungibili 🟨++

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 13.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 13">


In pratica mi calcolo, ancora qui in modo ricorsivo, tutti i strumenti raggiungibili dal nodo di start, con qualcosa di simile a una dfs (aggiungo ai raggiungibili ogni non terminale figlio, e comincio ad esplorare questo non terminale).

### Wrap-up (chiede) 🟨+

- Enunciato e dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 14.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 14">


L’algoritmo è molto semplice, è costituito da due passi fondamentali:

1. Elimino tutti i simboli che non sono generatori
2. Rimuovo tutti i simboli non raggiungibili

**Nota sull’ordine**

È importante eseguire le operazioni in questo ordine, altrimenti capita come in slide

- Esempio importanza di ordine

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 15.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 15">

- Esempio più tosto di applicazione di questo

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 16.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 16">


## Eliminazione rico sinistre

### Rico sinistre immediate 🟨

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 17.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 17">


L'idea è spaccare la ricorsione sinistra in una altra produzione e un nuovo non terminale fittizzio che vado ad utilizzare come non terminale di supporto.

- Esempio di risoluzione

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 18.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 18">


Posso considerare queste immediate, quando non ho dei cicli chiari nelle ricorsioni sinistre, sotto proviamo a creare un algoritmo per risolvere ricorsioni sinistre con cicli.

### Rico sinistre non-immediate 🟥+

- Esempio di non-immediato

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 19.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 19">

- Algoritmo di risoluzione O(n2)

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 20.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 20">


In pratica provo a sostituire tutto quanto posso in modo greedy.

- Esempio di applicazione

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 21.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 21">

- Esempio applicazione con tutto finora

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 22.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 22">


### Fattorizzazione 🟩

- Slide problema generale

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 23.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 23">


L’intuizione per sta parte è **raccogliere** le cose in comune. L’algoritmo non va a far altro che guardare i prefissi, e prendere il più lungo per ogni non terminale.

- Algoritmo per fattorizzazione

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 24.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 24">

- esempio di applicazione

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 25.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 25">


## Forme normali

### Chomsky 🟩—

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 26.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 26">


Questa ci piace, perché le produzioni o sono di

1. SIngolo terminale
2. Doppio non terminale.

Si può notare che questa forma è **sia libera da epsilon** sia **sia libera da coppie unitarie**.

E si può sempre trovare una grammatica in questa forma, questa cosa ci piace.

### Greibach 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semplificazione grammatiche/Untitled 27.png" alt="image/universita/ex-notion/Semplificazione grammatiche/Untitled 27">


Anche questa si può sempre fare, ed è una forma che ci piace perché non abbiamo derivazione ricorsive sinistre brutte che ci distruggono tutto.