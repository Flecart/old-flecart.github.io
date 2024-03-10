---
layout: page
permalink: notes/circuiti-sequenziali
tags: italian
title: Circuiti Sequenziali
---

Ripasso Prox: 45
Ripasso: December 22, 2021
Ultima modifica: October 27, 2022 12:17 PM
Primo Abbozzo: October 15, 2021 12:53 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- la caratteristica che contraddistingue DFF e Latch D
- Se hai voglia approfondisci la costruzione di una memoria (reale)
- December 14, 2021 3:43 PM

# 7 Circuiti sequenziali

## 7.1 Introduzione

### 7.1.1 Perché usarli

Sono utili per mantenere delle informazioni nel tempo

### 7.1.2 Caratteristiche

**Hanno feedback** cioè ci sono degli output che tornano dentro al circuito, quindi è molto difficile senza sapere niente cosa succede dentro

Questo circuito non è combinatorio, che è formalizzabile in modo deterministico con l'lgebra booleana.

### 7.1.3 Il Bit di memoria

Questo bit ha due input, un load e un input, se il load è attivo comincia a storare, altrimenti l'output è sempre il bit che ha memoriazzato.

## 7.2 Latch

### 7.2.1 Latch SR

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled">

Con 0 0, qualunque bit ci sia, rimane sto bit che gira.

1 1 = reset, 0 0 , NON FARLO

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 1.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 1">

Questo è uno dei più semplici circuiti non sequenziali. Se l'input sono diversi fra di loro, allora sappiamo cosa esce,

Ma nel caso in cui l'input è 0  0 oppure 1 1 allroa non va bene.

### 7.2.2 Latch SR temporizzato e clock

Il clock serve per stabilizzare la ram, il clock (voglio prendere solamente dei valori che siano stabili)

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 2.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 2">

### 7.2.3 Latch D

Questo latch possiede un unico input per impedire che sia possibile che si verifichi

il caso 1, 1, che non ci piace.

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 3.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 3">

### 7.2.4 D-Flip Flop

È uguale al Latch D ma solo con qualcosa in più, dovrebbe sempre tornare in Zero il clock, però il Not ha un pò di delay, che permette un velocissimo segnale a passare

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 4.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 4">

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 5.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 5">

Quindi questo circuito carica solamente quando c'è il clock che gli va, e permette il loading di qualcosa, quindi **effettivamente riesce a mantenere il bit in memoria**.

QUesto è migliore perché con il flipflop ho più tempo per far stabilizzare i dati, invece di poter caricare per l'intero tempo in cui clock è su, posso farlo in un solo piccolo frangente (ma sufficiente)

Ho un intero ciclo di clock per farlo stabilizzare, invece per il latch solo metà (in quanto l'altra metà è di caricamento)

## 7.3 Registri e RAM

### 7.3.1 Registro

Questi il DFF è il componente principale per il registro, che messo insieme ad altro è in grado di creare la memoria RAM necessaria per far funzionare.

in

X

0

0

1

1

load

X

0

1

0

1

clock

Null

Salita

Salita

Salita

Salita

out[N]

Mem

out[N-1]

0

out[N-1]

1

Da notare che l'out vale il valore di in solo nel caso in cui il load è 1 e il clock sta permettendo di salvare il dato.

Per il resto è sempre memoria.

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 6.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 6">

### 7.3.2 Program counter

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 7.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 7">

### 7.3.3 chip RAM

Il ram è costruito da una serie di registri. In Input può avere il valore in in, l'indirizzo in cui si vuole scrivere e un booleano che dice se vogliamo scrivere o no.

Ci saranno demultiplexer che indirizzeranno l'in al registro giusto. In out ho solamente l'out di questo registro, quindi devo anche filtrare fra l'output di tutti gli altri registri in quanto voglio solamente uno.

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 8.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 8">

## 7.4 Il microprocessore HACK

<img src="/images/notes/image/universita/ex-notion/Circuiti Sequenziali/Untitled 9.png" alt="image/universita/ex-notion/Circuiti Sequenziali/Untitled 9">

In questo schema si possono vedere tutti gli elementi principali per il processore HACK, come ALU, program counter, il decoder e simil.

Una caratteristica principale è la ROM di HACK (noi oggi abbiamo solamente una ROM per boostrap, ma invece in HACK deve avere solo ROM per le istruzioni).

outM è il mit della memoria che viene fuori

### 7.4.1 Accesso ai dati in memoria S, D, RAM

Questa parte si può considerare un approfondimento di una zona in [Memoria](/notes/memoria).

Parliamo d SRAM e DRAM.

**SRAM** si parla di Cache, sono più costose rispetto alle memorie ram dinamiche

**DRAM** è la memoria principale, fatte con transistor e un condensatore. (contiene una carica per un pò di tempo)

Ecco che allora DRAM ha bisogno di Refresh! In modo che il condensatore venga ricaricato.Questo rallenta anche la velocità del ram, ma si guadagna in economia

## 7.5 Altro

Abbiamo fatto anche altro riguardo a questa lezione.

Da notare principalmente è il funzionamento della cache [qui](/notes/qui) di cui abbiamo anche fatto degli esercizi.

Poi la predizione di pipelining distrutta dai salti nelle istruzioni presentata [qui](/notes/qui)
almente è il funzionamento della cache [qui](/notes/qui) di cui abbiamo anche fatto degli esercizi.

Poi la predizione di pipelining distrutta dai salti nelle istruzioni presentata [qui](/notes/qui)