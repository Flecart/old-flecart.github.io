---
layout: page
permalink: notes/bottom-up-parser-lr(0)
tags: en
title: Bottom-up Parser LR(0)
---

Ripasso Prox: 70
Ripasso: June 25, 2023
Ultima modifica: June 9, 2023 2:56 PM
Primo Abbozzo: November 18, 2022 2:52 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled">


# Bottom up parser

Descrivo ora alcune domande utili per ripasso:

1. Quali sono schematicmente quali sono le operazioni migliori per un parser top-down?
2. Cosa è un prefisso viabile?
3. Quali sono i conflitti possibli, e come risolverli…
4. Non sai nemmeno definire inmodo formale cosa sia un item

## Bottom up

### Intro shift-reduce e LR 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 1.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 1">


In breve:

1. Shift = simbolo terminale messo nella stack
2. Riduzione utilizzando una produzione
3. LR = dettura da Sinistra, creazione della stringa da destra (derivazione rightmost)

### Algoritmo classico 🟨+

Quello che credo che intendevo per questo algoritmo classico è quello non deterministico, nel senso che prova a fare backtracking, finché non ha finito tutte le possibilità, oppure trova la derivazione giusta.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 2.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 2">


Questo è esattamente lo stesso presentato alla fine di [Linguaggi Deterministici e DPDA](/notes/linguaggi-deterministici-e-dpda)

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 3.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 3">


Il drawback classico di queste tipologie di parser è che c’è un enorme **non determinismo** causato dai conflitti shift-reduce e reduce-reduce, che non hanno una lettura immediata, andremo quindi in seguito a creare metodi che possano disambiguare ciò.

## Il parser LR

### Struttura di un parser LR 🟨++

- Slide schematizzazione

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 4.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 4">


In figura sono descritte tutte le componenti del parser in modo molto schematico.

Componenti importanti sono

1. DFA e stack degli stati del DFA
2. Pila dei simboli
3. Tabella di parsing

### Algoritmo alto livello di parsing 🟩

- Mosse di parser LR deterministico

    Ossia le operazioni che può fare il parser

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 5.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 5">

- Algoritmo in pseudocodice

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 6.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 6">

- Esempio di parsing LR

    Nota, spesso è molto comodo fare una grammatica aumentata in questo modo

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 7.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 8.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 8">


Il DFA degli stati pare quindi fondamentale per la costruzione della tabella di parsing, in seguito andremo a costruire dei metodi automatici utili a far questo.

Questo è un DFA con alcuni modi di tornare indietro.

È bene quindi andare prima a fondare una teoria solida per questa roba, la crazione dell’**automa canonico** per il parsing LR.

## Prefisso viabile

I prefissi viabili sono un modo per risolvere il non determinismo di un parser classico bottom up, ci permette di capire in modo univoco se andare a fare shift e reduce col sistema degli handle.

Per poter controllare bene i prefissi viabili utilizziamo una **tabella di parsing** per controllare lo stato dell’handle.

### Introduzione al perché (informale, non fare) 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 9.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 9">


L’idea è far in modo che in cima alla pila ci sia solamente qualcosa che possa essere un prefisso di una produzione se non lo può esere si può concludere chiaramente che non sia possibile!

Per controllare questi prefissi utilizzeremo di nuovo una tabella di parsing, ma con altra logica sotto.

### Definizione 🟨 —

<img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 10.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 10">

- Slide sui prefissi viabili.

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 11.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 11">


> **Informalmente**: una sequenza $$\in (T \cup NT)^*$$ che può apparire sulla pila del parser bottom up per una configurazione che accetta l’input.
>

Da notare differenza della definizione per stringa e per gramamtica.

1. Per stringa è qualunque stringa che può apparire sulla pila, al momento di una computazione che va a buon fine
2. Per grammatica, invece, andiamo a considerare le derivazioni destre. In questa parte si introducono anche concetti come **prefisso viabile completo e handle**. **(non credo sia importante questa definizione la salto).

Gli handle sono di interesse perché appena li abbiamo siamo sicuri che vogliamo andare a fare una reduce, vorremmo trovare un modo per farceli comparire sti handle quando ne ho bisogno!

NOTA: la derivazione **deve essere rightmost** almeno nella definizione, anche se non ho ben capito per quale motivo deve essere cosi`.

### Th. prefissi variabili di G libera sono un linguaggio regolare 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 12.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 12">


Questo teorema ci è molto utile per continuare la nostra costruzione del parser, perché ora possiamo utilizzare questo DFA di supporto generato dal linguaggio regolare dei prefissi variabili per decidere cosa fare:

1. Se è completo faccio reduce
2. Se non lo è faccio shift
3. Se non è nemmeno un prefisso variabile sono in errore, perché mai ci potrò fare una reduce, questo per definizione di prefisso variabile.

Abbiamo così discusso su vantaggi che questo teorema ci può dare, ma non abbiamo ancora dato un modo per dimostrare questo teorema, lo dimostreremo in seguito, con la costruzione degli item e un DFA per esse. e poi sappiamo che i DFA sono anch’esse equivalenti a un linguaggio regolare.

### Shift e reduce sullo stato del DFA  🟩

In questa minisezione andiamo a trattare in che modo potremmo codificare il DFA in modo efficiente, in modo da non rifare ad ogni shift e reduce il ricalcolo dell’intera stringa!

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 13.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 13">


Quindi per lo shift molto easy, basta che ricomincio dallo stato vecchio.

Per il reduce invece mi serve poter tornare indietro! il modo più semplice per fare questo è tenersi uno **stack degli stati**, in modo che possa tornare indietro in modo lineare (poi quindi credo che l’algoritmo sarà lineare nei nodi dell’albero in questo modo).

## Automa canonico

L’automa canonico per il parser LR(0) è un DFA utilizzato per decidere se fare reduce oppure shift. (quindi vede se prefisso viabile è completo o meno).

### Item LR(0) 🟩

L’item è un costituente del DFA di supporto per il nostro DFA

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 14.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 14">


In pratica apro la produzione che ho, in un sacco di produzioni che contengono un punto, questo punto mi indica più o meno quanto è presente sulla stack.

### Intro Costruzione NFA dei prefissi 🟨—

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 15.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 15">


L’idea per questo algoritmo è utilizzata per gestire la grammatica aumentata degli item!.

1. Avanzamento dell’item, in questo caso avanzo semplicemente il punto (vado in stato corrispondente con punto in più!)
2. Letttura di un altro simbolo, collegamento epsilon a quest’altro punto.
- Esempio

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 16.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 16">


### Clos e Goto 🟩-

- Slide algo

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 17.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 17">


Questi due algoritmi codificano in pseudocodice i concetti precedenti.

1. Clos, è utilizzato per lettura di un altro collegamento epsilon, dato che va a checkare tutte le produzioni con quel coso in più, **simula tutto il raggiungibile senza leggere** in un certo senso.
2. Goto è per avanzare il punto, quindi mi crea tutte le produzioni con avanzamento del punto, e le chiude, specificatamente alle produzioni in una certa forma. **simula una lettura** in un certo senso.

Queste saranno delle funzioni di supporto per la costruzione dell'automa canonico di riferimento, così non dovremo passare all'algoritmo esponenziale per la costruzione del DFA, l’automa canonico.

### Costruzione dell’automa canonico 🟨

- Slide algo

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 18.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 18">


Questo algoritmo parte dal NFA dei prefissi viabili, e utilizza Goto e Clos per trovare il NFA in modo molto efficiente!

- Esempio 1

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 19.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 19">

- Esempio 2

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 20.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 20">


### Tabella di parsing LR 🟩

- Slide, descrizione generale, molto simile a LL

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 21.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 21">

- Costruzione tabella per LR(0)

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 22.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 22">


- Esempio tabella di parsing

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 23.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 23">

- Esempio 2

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 24.png" alt="image/universita/ex-notion/Bottom-up Parser LR(0)/Untitled 24">




# References