---
layout: page
permalink: notes/algebra-logica
tags: italian
title: Algebra Logica
---

Ripasso Prox: 3
Ripasso: December 15, 2021
Ultima modifica: September 30, 2022 3:20 PM
Primo Abbozzo: December 15, 2021 9:18 AM
Stato: 🌕🌕🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

# 11 Strutture algebriche

## 11.1 Differenza matematica e informatica

Una osservazione per quanto riguarda la logica intuizionista è che sta a metà fra matematica e informatica perché la dimoostrazione intuizionista possiede in sé un algoritmo e una struttura di dati.

Infatti di solito l'informatico scrive senza fare la dimostrazione dell'algoritmo mentre il matematico scrive la dimostrazione senza fare l'algoritmo (inoltre può definire degli enti ed oggetti che non siano rappresentabili come dati in quanto possono essere infiniti.

Un opinione personale è che l'informatica è più pratica, e limitata in quanto non può estendersi al ragionamento infinito ma deve essere limitata al calcolo. Questo è si molto più utile ma molto meno creativo. Si può attaccare però il problema in questi modi!

### 11.1.1 Osservazioni generali

La matematica utilizza questi metodi da molto tempo prima dell'esistenza di una macchina di calcolo.

I concetti generali di matematica che si sono sviluppati nei secoli sono astrazioni e generalizzazioni. (non esiste ancora una base simile in informatica, e.g. le classi di java hanno proprio degli errori logici al suo interno, anche se non so esattamente quali, ma coen dice di sì)

## 11.2 Astrazione e generalizzazione

### Tesi di Church-Turing
Vedere [La macchina di Turing#Tesi di Church-Turing](/notes/la-macchina-di-turing#tesi-di-church-turing)
Guarda 
Questa tesi (non è un teorema) definisce il significato di **espressività di un linguaggio di programmazione**.

In altre parole deve avere:

1. Un modo di ciclare
2. branching (if condition)
3. E numeri
- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled.png" alt="image/universita/ex-notion/Algebra Logica/Untitled">


Ma quindi i linguaggi di programmazione non cambiano per capacità di calcolo, bensì nella **capacità di astrazione e generalizzazione.**

### 11.2.2 Astrazione

<img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 1.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 1">

Alcune caratteristiche le trascuro perché sono accessorie (dipendono dall'implementazione, dal caso specifico), questo mi permetti cambiare una implementazione trattenendo aspetti degli oggetti che mi interessino. esempio di astrazione è il **quozientamento** perché in questa operazione trattenevo solamente gli aspetti che mi interessavano buttando via tutto il resto. (il quozientamento non esiste in programmazione per la sua incapacità di gestire l'infinito)

- Esempio implementazione e astrazione di numeri naturali

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 2.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 2">

    L'implementazione posso farla in molti modi, qui ne sono rappresentati due.

    Mentre il concetto astratto sono le regole che mi definiscono l'ente (in questo caso gli **assiomi di peano,** il fatto che devo avere uno Zero una successione e l'insieme generali dei numeri natuali, un elemento appartiene a questo insieme solamente se è uguale allo zero oppure è un successore di un numero di questo insieme. S deve essere iniettiva. E nessun successore è uguale allo zero).

- Esempio implementazione e astazione liste di interi

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 3.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 3">


### 11.2.3 Generalizzazione

<img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 4.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 4">

Quindi vorrei che una caratteristica in un caso particolare sia vero anche in molti altri casi!

- Benefici di ciò (4)

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 5.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 5">


## 11.3 Struttura algebrica

### 11.3.1 L'elemento neutro (generalizzazione di essa)

<img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 6.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 6">

Si una generalizzazione esiste ed è questa:

<img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 7.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 7">

<img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 8.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 8">

Queste generalizzazioni sono utili nel caso mi creino una **teoria** utile da studiare dal punto di vista astratto (così posso scoprire altre proprietà).

<img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 9.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 9">

Se questa teoria è utile per comprendere concetti più bassi (dal punto di vista di livelli di astrazione) allora posso dire che queste sono teorie **informative**.

### 11.3.2 Definizione struttura algebrica

Il **magma** è il concetto fondamentale per una struttura algebrica come in definizione.

- Definizione

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 10.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 10">

    Chiamiamo magma perché non è ancora solidificato, qualcosa di abbastanza astratto.

    Dopo avere introdotto questi concetti astratti posso studiarle! Posso studiare una cosa che ho creato, mi piace sta scienza, perché chi ha creato qualcosa non sa a priori bene cosa ha creato.

- Prodotto cartesiano in left unital magma

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 11.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 11">

    Nell'esempio C è un prodotto cartesiano di R per questo motivo riesco a dirlo da questa generalizzazione!


### 11.3.3 In programmazione

## 11.4 Morfismi

Il morfismo mi permette di **preservare**  alcune proprietà che perdo in astrazione's trasformazione (un esempio è la perdita della struttura di numeri quando lo rappresento con un LUM (Left Unital Magma)

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 12.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 12">

    Questo concetto è importante anche in informatica perché vuol dire che posso prima applicare la funzione sulla somma di implementazioni oppure applicarli singolarmente.


### 11.4.1 Isomorfismo

L'isomorfismo è simile a un morfismo a due parti (in cui vale questa relazione in entrambe le parti) quindi **funzione bigettiva** in cui anche l'inverso sia un morfismo. Questa cosa mi dice che esiste una certa **corrispondenza fra strutture algebriche**.

- Enunciato ed esempio

    <img src="/images/notes/image/universita/ex-notion/Algebra Logica/Untitled 13.png" alt="image/universita/ex-notion/Algebra Logica/Untitled 13">


1. sintassi proposizione o primo ordine
2. ricorsione struturale
3. Domandina teorica
4. Dimostrazione per induzione strutturale (funzione o formule)
5. .
6. .
7. .
8. Logica proposizionale classica o intuizionista
9. Sostituzione o Albero ded.nautale al primo ordine
10. Un esercizio di astrazione o generalizzazione.
. .
6. .
7. .
8. Logica proposizionale classica o intuizionista
9. Sostituzione o Albero ded.nautale al primo ordine
10. Un esercizio di astrazione o generalizzazione.