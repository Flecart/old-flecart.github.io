---
layout: page
permalink: notes/bottom-up-parser-lr(1)
tags: en
title: Bottom-up Parser LR(1)
---

Ripasso Prox: 40
Ripasso: May 27, 2023
Ultima modifica: April 17, 2023 12:52 PM
Primo Abbozzo: November 22, 2022 1:22 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled">

# Bottom-up Parser -LR(1)

Si può osservare che per il parser costruito in [Bottom-up Parser LR(0)](/notes/bottom-up-parser-lr(0)), non riesce a riconoscere di linguaggi semplici come $$L = \{a, ab\}$$.
- Esempio di quanto detto
<img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 1.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 1">


## Parser SLR(1)

Questi parser qui utilizzano l’idea del look ahead ampiamente utilizzata in [Top-down Parser](/notes/top-down-parser), per escludere molte produzioni.

La s sta per **simple**, perché utilizza una idea semplice :D, credo ahah boh.

### Riduzione con follow 🟩

noi vogliamo **ridurre solamente se ho follow** corretto il terminale finale della stringa.

Quindi in pratica vado ad aggiungere questa nuova regola per togliere alcune riduzioni senza questo terminale nella tabella.

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 2.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 2">


alla fine non deve essere solamente per S, deve essere per il follow!, ma sotto nella tabella di parsing ne parliamo un pochino meglio.

### Osservazioni varie (4) 🟥+

- slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 3.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 3">

1. È molto raro che alcune produzioni che hanno la epsilon siano di LR(0), anche se è possibile!
2. Libero deterministico + prefix property → LR(0)
3. not LR(0) → libero deterministico + not prefix property or prefix property or not libero deterministico.
4. Finito e LR(0) → prefix property.
5. Se è infinito e LR(0) può non godere della prefix property.

### Tabella di parsing SLR(1) 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 4.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 4">


Praticamente il riempimento di questa tabella è identica a quella del LR(0), solo con il check in più sui follow di S.

L'unica cosa differente è che

$$A  \to \alpha. \in S, A \not\in S',$$  allora il reduce si può fare in $$M[s, x] \iff x \in Follow(A)$$, ossia solo se ho il follow, non devo andare a fare shift!

Mentre per LR(0) lo devo mettere per tutti gli entry!

## Parser LR(1)

### Item LR(1) 🟩-

In questa serie di Item dobbiamo ancora andare ad estendere il concetto di item esposto in [Bottom-up Parser LR(0)](Bottom-up Parser LR(0) 92be8778006943cf99add4d634a3fb1a.md).

Applicando anche una parte di lookahead, di non terminali

### Closure & goto 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 5.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 5">


La cosa nuova riguardante questo è che devo andare a considerare i first e simili!

Si l'unica cosa in più è che devo agigungere ogni cosa riguardante il first.

Il goto resta esattamente uguale!

### Tabella di parsing 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 6.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 6">


L'algoritmo di creazione della tabella di parsing mi sembra sia molto simile a quelle precedenti, però per capire se ho compreso questo concetto sarebbe utile fare qualche esercizio a riguardo! LR(0) ha detto che per forza ce lo mette in esame!

- Esempio di parsing LR(0)

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 7.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 8.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 8">


**Nucleo dello stato LR 1**

Se rimuovo il look ahead, allora ottengo lo stato dell'automa LR(0)! In questo senso potremmo osservare che le transizioni di LR 1 dipendono **solo** dal nucleo. Questo diventa un hint molto importante per andare a costruire poi un automa LALR.

## LALR (1)

> Questi automi sono **presenti all’orale** però allo scritto non ci sono proprio.
>

Questo è una forma di mezzo fra semplicità di SLR e la selettività di LR.

Si traduce come Look-Ahead Left-reading Right-most derivation 1 lookahead parser

### Osservazioni sulla tabella 🟨+

Questo ha una tabella con il **nucleo fuso** per quelli che hanno le cose uguali, in questo modo cerco di **limitare il numero di stati**.

Questa parte è molto simile a quanto fatto per la minimizzazione dei dfa in [Automi e Regexp](/notes/automi-e-regexp), perché stiamo andando ad **accorpare** stati che sono quasi equivalenti, questo col rischio di introdurre alcuni conflitti reduce-reduce che però non dovrebbero portare a troppi problemi, come andremo presto a vedere.

- Esempio slide entrambi errati

    lezione 16 slide 18

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 9.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 9">


### Possibilità di conflitti (no shift-reduce dimo) 🟨

- Slide

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 10.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 10">


Da questo esempio presente in slide vediamo che una grammatica può essere LR(1) e non LALR(1), quindi non sono esattamente equivalenti.

- Riassunto di questa lezione 16

    <img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 11.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 11">


### Esempio LR not LALR 🟨

Questo è un esempio importante solo perché è richiesto nelle domande, altrimenti l’avrei saltato. Comunque basta un pò ricordarsi cose riguardo simmetria della grammatica per costruire quasi ad Hoc un conflitto Reduce-Reduce nella grammatica LALR

- Esempio di conflitto
<img src="/images/notes/image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 12.png" alt="image/universita/ex-notion/Bottom-up Parser -LR(1)/Untitled 12">




# References