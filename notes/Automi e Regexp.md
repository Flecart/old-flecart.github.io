---
layout: page
permalink: notes/automi-e-regexp
tags: en
title: Automi e Regexp
---

Ripasso Prox: 70
Ripasso: June 7, 2023
Ultima modifica: June 4, 2023 4:06 PM
Primo Abbozzo: October 14, 2022 2:19 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled">


# Automi e Regexp

Per l’analisi lessicale vogliamo cercare di ricordare le **parole legali** all'interno di questo linguaggio e questo è fatto con i linguaggi regolari.

## Introduzione a analizzatori lessicali

### Token 🟩

Struttura del token è fatto da due parti

- Identificatore della classe del token
- Identificatore del valore del token
- Pattern e lessema ci sono direi boh

### Pattern e Lessema 🟩

I pattern sono una descrizione generale della forma dei valori di una classe di token.

Lessema è una istanza di un particolare pattern

- Esempio di scan

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 1.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 1">


Di solito viene storato come puntatore alla tabella dei simboli

## Espressioni regolari

### Definizione 🟩

- Slide definizione espressioni regolari

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 2.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 2">

- Disambiguazione della grammatica

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 3.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 3">

- Esempio espressione regolare

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 4.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 4">


### Linguaggio generato da regexp 🟩

Per capire questa parte è importante avere in mente le operazioni sui linguaggio definiti in [Descrizione linguaggio](/notes/descrizione-linguaggio)

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 5.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 5">


### Linguaggio regolare 🟩

- Definizione linguaggio regolare

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 6.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 6">


**Ogni linguaggio finito è un linguaggio regolare** questo è una proposizione che lega fortemente i linguaggi (utilizzati poi veramente per l'implementazione) (basta fare l’unione!)

- Esempio linguaggio finito generato da linguaggio regolare

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 7.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 7">

- Esempi di espressioni regolari infiniti

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 8.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 8">


Oltre ai classici operatori definiti in precedena per questa sezione aggiungiamo

*Ripetizione-positiva*, *Possibilità*, *Elenco*

### Definizioni regolari 🟩-

Le definizioni regolari ci aiutano a creare una struttura del token di cui dobbiamo fare lo scanning.

In pratica andiamo a creare delle definizioni che rendono più facile la descrizione di un pattern con regexp.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 9.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 9">

- Esempi

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 10.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 10">


### Equivalenza regexp 🟩

<img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 11.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 11">

- Esempi di equivalenze

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 12.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 12">


Queste equivalenze non sono sempre facili da dimostrare

## Automi

In questa parte si fa una descrizione molto generale di cosa siano gli automi.

### Caratteristiche (3) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 13.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 13">

1. *Memoria* finita (dato da un numero di stati)
2. *Input* una stringa da riconoscere
3. *Output* è solamente un singolo bit (si oppure no)

### Descrizione e funzionamento 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 14.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 14">


**Descrizione**

- Testina sul primo carattere in input.
- Su stato q0

**Funzionamento**

Il funzionamento dell'automa è molto semplice, esegue un semplice algoritmo:

1. Leggi il carattere attuale, se esiste una transizione etichettata con quanto letto spostati secondo la regola di quel carattere.
2. Dopo aver finito di leggere la stringa, se è in uno stato buono restituisci 1, altrimenti 0
3. Se è bloccato in uno stato ritorna 0

### Diagrammi di transizione 🟩

I diagrammi di transizione sono utili per definire in modo grafico cosa fa l'espressione regolare

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 15.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 15">


## Automi finiti non deterministici (NFA)

### Definizione (5) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 16.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 16">


Possiamo definire gli automi non deterministici come una quintupla di


$$
(\Sigma, Q, q_0 \in Q, F \subseteq Q, \delta) \\
\delta : Q \times (\Sigma \cup \varepsilon) \to P(Q)
$$


1. Albeto dei simboli di input
2. Stati possibili
3. Stato iniziale
4. Stati finali (accettati)
5. Funzioni di transizione, che ha come codominio l'insieme delle parti di Q

Alla fine, per scopi didattici si utilizza sempre il diagramma di transizione. La differenza principale con gli automi a stati finiti è che posso avere lo stesso label di transizione per singolo stato

### Caratteristiche (2) 🟩

1. Facili da realizzare (esiste quasi una bigezione credo fra NDA ed espressione regolare)
2. Inefficienti (backtracking, e fallibile), principalmente causato dal suo non determinismo

### Stato finale accettato 🟩 —

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 17.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 17">


Questo è una slide molto importante per definire il concetto di **stringa accettata/riconosciuta**. Praticamente posso affermare che una stringa è riconosciuto da questo automa finito non-deterinistico se anche un solo cammino da q0 a un qualunque stato accettato.

Oltre questo voglio andare a definire in modo formale il concetto di mossa, o cammino in un diagramma di rappresentazione per un automa finito.

- Descrizione istantanea, mossa, cammino, stringa accettata

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 18.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 18">


Indico che uno stato $$q$$ è raggiungibile da uno stato $$s$$, con il simbolo $$\vdash$$, ossia $$s \vdash v$$, questo è possibile solo se sto leggendo una stringa che ha come relazione una stringa buona, ma questo pezzo è più chiaro negli appunti quindi ti invito di leggere dalì con la rappresentazione logica classica.

La chiusura riflessiva e transitiva di questo concetto di mossa è indicata con $$\vdash ^*_N$$, N è il nome di questo automa, dovrebbe essere ancora sopra.

TODO: da definire bene cosa sia la mossa e il cammino!

### Linguaggio riconosciuto da NDA e equivalenza 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 19.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 19">



$$
L[N] = \{ w \in \Sigma^* |  \exists q \in F, (q_0, w) \vdash ^*_N (q , \varepsilon)\}
$$


La parte di sopra è la definizione di un **linguaggio riconosciuto da un automa**, è un modo molto compatto per esprire l'esistenza di un cammino come sopra.

Inoltre possiamo definire il concetto di **equivalenza fra NDA** che è quando il linguaggio riconosciuto è esattamente lo stesso.

### Definizione di linguaggio riconosciuto con e-closure 🟨+

- Linguaggio riconosciuto, scritto in modo più elegante, con epsilon closure

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 20.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 20">


Con la definizione di delta cappuccio possiamo definire che un linguaggio in questo modo:


$$
w \in L[N] \iff \exists p \in F : p \in \hat{\delta}(q_0, w)
$$


### NFA da espressioni regolari (!!!) (duplicato) 🟩

Questo è un teorema molto importante per rappresentare una sorta di equivalenza fra linguaggi regolari e NFA.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 21.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 21">

- Hint dimostrazione

    Induzione strutturale sulla sintassi BNF delle espressioni regolari, andremo a dimostrare che posso comporre NFA che alla fine riescono a riconoscere il linguaggio regolare

- Consigli di studio

    Impararsi i metodi di conversione di ogni parte della sintassi in NFA, poi li componi come dei lego e sei apposto

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 22.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 22">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 23.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 24.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 24">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 25.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 25">


## Automi finiti deterministici (DFA)

### Definizione 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 26.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 26">

- Differenze rispetto NDA

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 27.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 27">


Principalmente la definizione è uguale agli automi non deterministici l’unica cosa che cambia è il delta che ora è definito come


$$
\delta: Q \times \Sigma \to Q
$$


Non c’è più l’insieme delle parti, magari dopo vediamo come questi automi sono equivalenti, ma c’è una esplosione esponenziale al momento di conversione da deterministico a non deterministico.

### Algoritmo creazione DFA da NFA 🟩

<img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 28.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 28">

- L’algoritmo di creazione

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 29.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 29">

- Esempio di utilizzo dell'algoritmo (lezione 6)

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 30.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 30">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 31.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 31">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 32.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 32">


con $$F$$ l’insieme degli stati finali della NFA.

### DFA equivalente a NFA (non chiede) 🟨

- Dimostrazione both, e osservazioni in modo informale
    - Slide →

        <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 33.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 33">


    Questa proposizione si può vedere dalla definizione

    - Slide ←

        <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 34.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 34">


C'è veramente in questo passo una **esplosione esponenziale** perché il numero degli stati diventa esponenzialmente tanto.

<img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 35.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 35">

- Dimostrazione, induzione, molto formale.

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 36.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 36">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 37.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 37">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 38.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 38">

- Esempio di conversione

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 39.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 39">

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 40.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 40">


### epsilon-closure 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 41.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 41">

- Algoritmo per epsilon-closure

    <img src="/images/notes/image/universita/ex-notion/Automi e Regexp/Untitled 42.png" alt="image/universita/ex-notion/Automi e Regexp/Untitled 42">


Questo concetto di chiusura Epsilon ci racchiude il concetto degli stati raggiungibili in un NFA senza leggere nessun input.



# References