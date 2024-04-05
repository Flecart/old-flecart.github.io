---
layout: page
permalink: notes/linguaggi-liberi-e-pda
tags: en
title: Linguaggi liberi e PDA
---

Ripasso Prox: 69
Ripasso: May 29, 2023
Ultima modifica: April 25, 2023 9:50 AM
Primo Abbozzo: October 28, 2022 12:52 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled">


# Linguaggi liberi e PDA

## Introduzione

In questa parte del nostro percorso nei linguaggi di programmazione proviamo ad espandere NFA e DFA in modo che possano riconoscere linguaggi come $$ww^r | w \in \{a, b\}^*$$ , con r maggiore o uguale a zero (r per dire che è il contrario di w) (questo linguaggio per il pumping lemma).

## Push-down automata

### Introduzione automi a pila (7) 🟩 --

L’idea principale per espandere gli NFA è il concetto di **stato** o memoria, avere quindi una stack o pila può rendere molto più espressivo queste entità.

Il prof. definisce **automa a pila non deterministico** (PDA) questa settupla $$(\Sigma, Q, \Gamma, \delta, q_{0}, \bot, F)$$
- $$\Sigma$$ l'alfabeto finito dei simboli in input
- $$\Gamma$$ l'alfabeto dei simboli sulla pila
- $$Q$$ l'insieme degli stati
- $$\delta$$ transizione, nella forma $$\delta: Q\times (\Sigma \cup \left\{ \varepsilon \right\}) \times \Gamma \to \mathbb{P}(Q \times \Gamma^{*})$$
- $$q_{0}$$ lo stato iniziale
- $$\bot \in \Gamma$$ il simbolo iniziale sulla pila 
- $$F \in Q$$ l'insieme degli stati finali.
Una differenza che fa questo prof. contro [La macchina di Turing](/notes/la-macchina-di-turing) è che lui fa distinzione dei simboli sulla pila, mentre l'altro no, una altra differenza è che gli stati finali sono esterni nell'altro. Ma credo alla fine sia equivalente.

Attenzione: l’automa può leggere qualcosa solo se la sua stack non è vuota!

La parte intressante dei PDA rispetto agli automi studiati in [Automi e Regexp](/notes/automi-e-regexp) è la funzione di transizione, che è ora nella forma


$$
\delta: Q \times (\Sigma \cup\{\varepsilon\}) \times \Gamma \to P(Q \times \Gamma ^*)
$$


- Esempio hard di PDA
<img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 2.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 2">


### Computazione automi a pila 🟩 --

- Slide

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 3.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 3">


- Esempio 1

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 4.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 5.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 5">

- Esempio 2

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 6.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 7.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 7">


### Accettazione della stringa 🟩

La cosa particolare degli automi a pila è che accettano la stringa anche quando la pila diventa vuota, non solo quando finisco di leggere e ho uno stato che è bello. Ossia detto meglio, posso costruirmi un automa a Pila che accetta la stessa stringa quando la pila diventa vuota, c’è una sorta di equivalenza fra stato e cose sulla pila.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 8.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 8">


La cosa importante da capire per questa parte è che si differenziano **due metodi di accettazione** per la stringa:

1. Pila vuota
2. Stato finale.

In entrambi i casi devo **leggere tutto l’input**, e poi vado a vadere dove sto. Nel primo caso se ho letto tutto l’input e la pila è vuota allora accetto, nel secondo caso se ho letto tutta la stringa e sono in uno stato finale allora vado ad accettare.

### Teorema equivalenza accettazione Vuoto-Stato 🟩

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 9.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 9">

- Dimostrazione in slide

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 10.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 10">


L'idea dietro questo teorema è molto simile a quanto presente nella conversione fra espressione regolare e NFA, perché sto andando in modo ricorsivo, supponendo che ho già un vecchio automa che funzioni, e basta che ci costruisca cose intorno ad essa. (in questo caso simbolo iniziale nuovo e stato finale che più o meno racchiude tutti gli stati finali!

Z è un simbolo stack nel nostro nuovo automa, solo utilizzato per gestire meglio alcune cose con la stack.

### Ogni linguaggio è libero sse riconosciuto da PDA (chiede)🟩

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 11.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 11">


- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 12.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 13.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 14.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 14">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 15.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 15">

- Diagramma PDA per →

    Nota questo non è il PDA di cui parlava il prof nelle slides, bisognerebbe condensarlo in un unico stato. Questo qui risolve per stato finale, quello del prof per stack vuota

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 16.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 16">


**Note sulla dimo**

Vogliamo dimostrare un sse, in una proviamo a costruire un automa partendo dalle regole della grammatica, (non dimostriamo che l’automa riconosce effettivamente, la costruiamo ebbasta.

Per l’altra freccia bisogna avere dimostrato prima alcuni lemmi che noi saltiamo per ora.

## Proprietà dei linguaggi liberi

### Unione, Conc, e Kleene 🟩

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 17.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 17">


In pratica i non terminali e terminali sono uniti assieme, e con qualche produzione in più sullo stato iniziale per gestire le cose.

### Intersezione con linguaggio regolare (chiede per alto voto) 🟩

Questa è qualcosa di leggermente più tosta, però in soldoni sto facendo un bruteforce, e prendendo tutte le combinazioni possibili per cui si possa riconoscere

- Th e dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 18.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 18">


Con questo teorema è spesso utile per dimostrare che un linguaggio non è libero.

Invece **non sono chiusi per intersezione** i linguaggi liberi

- Esempio di non chiusura

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 19.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 19">


Da questo dato si può concludere che **non sono chiusi per complemento** altrimenti lo sarebbero anche per l'intersezione.

### Pumping theorem, tosta (!) 🟨++

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 20.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 20">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 21.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 21">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 22.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 22">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 23.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 24.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 24">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 25.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 25">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 26.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 26">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 27.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 27">

- Dimostrazione libro sispser (più chiaro)

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 28.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 28">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 29.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 29">


L’idea è sempre avere così tanti stati che avrò per forza dei **non terminali duplicati**. uno sotto l’altro, in una forma ricorsiva, allora prendo il minore e vado a fare ragionamenti lì.

## Classificazione dei linguaggi

### Chomsky (5) 🟥+

Chomsky, linguista, ha descritto una gerarchia di linguaggi
- Caratterizzazione dei linguaggi

    <img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 30.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 30">


Sulla decidibilità guardare [Fondamenti teorica](/notes/fondamenti-teorica) e [La macchina di Turing](/notes/la-macchina-di-turing)

In questo caso i nuovi sono

- Grammatiche dipendenti dal contesto, in cui una singola produzione può avere **più non-terminali**.
- Grammatiche motonone, le cui produzioni basta che crescano
- Grammatiche generali, in cui non c’è nessun vincolo di produzioni

### Schema generale delle grammatiche 🟩
Per turing, vedere [La macchina di Turing](/notes/la-macchina-di-turing).

<img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 31.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 31">

### Gerarchia automi 🟨+

In generale si può estendere dicendo

- Automi Limitati riconoscono grammatiche dipendenti dal contesto
- Automi di Turing riconoscono i linguaggi ricorsivi, e sono in grado di enumerare ricorsivamente quelle generali. (anche se è semidecidibile, quindi forse non riesce a ricononscerli tutte??)

<img src="/images/notes/image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 32.png" alt="image/universita/ex-notion/Linguaggi liberi e PDA/Untitled 32">