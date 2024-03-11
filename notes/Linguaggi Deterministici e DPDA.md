---
layout: page
permalink: notes/linguaggi-deterministici-e-dpda
tags: italian
title: Linguaggi Deterministici e DPDA
---

Ripasso Prox: 55
Ripasso: July 2, 2023
Ultima modifica: June 9, 2023 12:26 PM
Primo Abbozzo: November 5, 2022 10:55 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled">


# Linguaggi Deterministici e DPDA

## DPDA

### Definizione (2) 🟩

La definizione di DPDA è molto simile a quella trattata in [Linguaggi liberi e PDA](/notes/linguaggi-liberi-e-pda), con solo costraints sulla deterministicità, che si traducono in due condizioni:

1. Al massimo posso avere un risultato per ogni coppia di lettura e simbolo su stack
2. Se ho una transizione senza leggere, posso avere solo quella
- Slide

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 1.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 1">


### Linguaggio libero deterministico

> Un linguaggio è libero deterministico se esiste un PDA che lo riconosce per **stato finale**.
>

### Proprietà accettazione per DPDA 🟩

Per stato finale accettato resta sempre, cambia un pò l’accettazione per pila vuota, in cui si deve avere una **prefix property.**

Questa prefix property ha un certo interesse perché basta aggiungere un simbolo che non è presente nell’alfabeto, e ho la prefix property! (guarda esempi Lez12 prime slide).

### Prefix property 🟩

Due parole del linguaggio in cui il primo è interamente dentro il secondo.

- slide Prefix property

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 2.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 2">


Se aggiungo un simbolo **$$** riesco a far sempre che ci sia la prefix property.

La dimostrazione è più o meno su questa scia. affinché uno sia prefisso dell’altro, deve avere il dollaro nella stessa posizione, allora hanno la stessa lunghezza, ma se hanno la stessa lunghezza devono essere uguali, ecco la prefix property.

### Esiste DPDA che riconosce linguaggi regolari 🟩

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 3.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 3">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 4.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 4">


Praticamente la dimostrazione è la stessa per [Grammatiche Regolari](/notes/grammatiche-regolari), ma ho anche lo stack, basta che non lo uso e ho finito.

### Non ambiguità dei DPDA🟩

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 5.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 5">


Quindi se esiste un DPDA che riconosce il linguaggio, si può creare una grammatica non ambigua che riconosce lo stesso linguaggio.

Con la lezione del 29/11 abbiamo introdotto che un linguaggio è deterministico sse SLR(1) in [LR(k) e YACC](LR(k)%20e%20YACC%20af47672b50fb43258a6aecef0bacf891.md), quindi probabile che i DPDA posso essere ricondotti in una forma deterministica a singolo

### Proprietà dei linguaggi deterministici 🟩

1. Complemento sì
2. Unione o intersezione no.

Complemento probabilmente sì perché basta applicare lo stesso ragionamento fatto per le regex in [Automi e Regexp](/notes/automi-e-regexp), ossia basta invertire gli stati accettati.

Per dimostrare che non sono chiusi per intersezione o unione sarebbe buona cosa fornire un esempio.

<img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 6.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 6">

Esempio non intersezione ⇒ non unione.

## Analizzatori sintattici

In modo simile a quanto presentato in [Grammatiche Regolari](/notes/grammatiche-regolari) nell discussione dei Lex.

Questa parte utilizziamo abbiamo i strumenti automatici che prendono una grammatica libera e resituiscono un DPDA

### Tipologie di parser (2-2-2) 🟩

- Slide tipologie (det-nondet)

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 7.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 7">

- Slide tipologie (top-bottob)

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 8.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 8">


Oltre a ciò possiamo anche dividere i parse a seconda di

1. Lettura da destra o da sinistra
2. Creazione derivaizone rightmost o leftmost
3. Numero di look ahead.

Quindi per esempio se ho una grammatica che inizia a leggere da sinistra, crea derivazione leftmost e ha un lookahead di 1, lo rappresento come $$LL(1)$$

### Top down parsing con PDA singolo stato 🟩

Simile a quanto fatto in [Linguaggi liberi e PDA](/notes/linguaggi-liberi-e-pda) per il teorema di equivalenza di linguaggio libero e PDA, vado a crearmi un automa in un certo modo (in particolare con singolo stato **riconosce per pila vuota**).

- Slide enunciato

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 9.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 9">


Questa è una semplice **soluzione non deterministica**, possiamo togliere questo non determinismo con il Look Ahead come rpesentato sotto

### Look Ahead (+) 🟩

Posso andare a guardare la lettera avanti per capire in che modo comportarmi con la derivazione.

Utilizzo una **tabella di parsing** per capire in che modo devo espandere il non-terminale.

- Esempio di look ahead 1

    con $$S := aSb|\varepsilon$$

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 10.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 10">


**Note per risolvere i conflitti**

Posso

1. Fattorizzare (creare una nuov agrammatic aequivalente senza ricorsione sinistra che non riesco a gestirla, va a divergere, quindi non finisce mai
2. Fare un look ahead maggiore di 1

Queso è utile per togliere il non determinismo.

### Bottom up parsing (3)🟨-

- Slide rappresentazione classica

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 11.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 11">


Si tratta sempre della creazione di un PDA a singolo stato!, ma fatto in modo di verso, in modo tale che ci sia una uderivazione rightmost.

Importanti in questa parte sono 3 operazioni

1. Shift, in cui facci ocrescere verso destra la pila, come se stessi facendo lo shift
2. Reduce, quando creo il non terminale come se fosse una espansione di non terminale.
3. Accept

- Esempio di creazione di parser bottom up

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 12.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 13.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 13">

- Esempio di derivazione con il parser di sopra

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 14.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 14">

- Problema non determinismo per sopra

    <img src="/images/notes/image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 15.png" alt="image/universita/ex-notion/Linguaggi Deterministici e DPDA/Untitled 15">


Ma comunque andiamo a discutere meglio di questa parte in [Bottom-up Parser LR(0)](Bottom-up%20Parser%20LR(0)%2092be8778006943cf99add4d634a3fb1a.md).

### Tipologie di conflitti di bottom up

- Shift-reduce
- Reduce-Reduce

Oltre a questo c'è un grandissimo problema delle produzioni del tipo $$A \to \varepsilon$, perché queste **divergono sempre**, quindi è meglio non avere grammatiche con questa produzione se vogliamo utilizzare parsing bottom up.3