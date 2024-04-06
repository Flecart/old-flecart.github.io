---
layout: page
permalink: notes/metodi-di-discesa
tags: italian
title: Metodi di Discesa
---

Ripasso Prox: 13
Ripasso: December 23, 2022
Ultima modifica: January 3, 2023 11:12 AM
Primo Abbozzo: November 3, 2022 11:53 AM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

# Metodi di discesa

## Intro

### Generali sui metodi di discesa

Vogliamo creare algoritmi che riescano a trovare i punti di minimo delle funzioni non vincolate.

In generale **si trova un punto stazionario (condizioni necessarie)** ma non è garantito lo stato ottimo.

<img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled">

### Condizioni di arresto classiche (2) 🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 1.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 2.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 2">

    - Differenza fra due iterati è minore a una tolleranza, in modo simile a quanto fatto in [Equazioni non lineari](/notes/equazioni-non-lineari) sulla tolleranza per il metodo delle approssimazioni

I criteri di arresto sono i sempre classici

1. Numero di iterazioni superate
2. Tolleranza sull’obiettivo ossia **gradiente = 0** per il punto di stazionarietà.

### Idea principale dei metodi di discesa 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 3.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 3">

1. Trovare una direzione di discesa
2. Aggiornare x in modo da andare in quella direzione di un passo fissato. **direzione di ricerca e lunghezza del passo** sono due nuovi termini di interesse per questa roba

### Ottimizzazione non vincolata (non studiare)

In pratica questa parte è un ripasso molto veloce di 2 mesi di analisi 2… E poi ovviamente fatti molto male!

Guarda [Massimi minimi multi-variabile](/notes/massimi-minimi-multi-variabile). In pratica ottimizzazione è trovare il massimo o il minimo di una funzione…

## Discesa

### Condizione per direzione di discesa🟩-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 4.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 4">


Si può osservare che io stia proprio scendendo, in questo senso vado a cercare qualcosa che sia uguale a 0.

- Interpretazione geometrica della condizione di discesa

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 5.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 5">


Se forma angolo ottuso con il gradiente è OK!

E guardare le curve di livello è una cosa molto buona.

### Algoritmo generale di GD🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 6.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 6">


Si può notare che la **scelta del passo** è la parte critica di questo algoritmo. Scegliere un alpha fisso non garantisce la convergenza, devono essere soddisfatte certe proprietà.

## Ricerca dell’alpha

### Scelta della alpha (linea esatta)🟩-

- Definizione di funzione dipendente da alpha

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 7.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 7">


<img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 8.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 8">

Vado a scegliere l’alpha in modo tale che **assuma il valore più piccolo possibile,** significa minimizzare questa funzione di alpha.

Solitamente si utilizza quando f è in forma quadratica, per resto spesso non si utilizza (perché la f si calcola in modo molto veloce, di solito è molto lento. **dimostrato converge!** punto minimo o massimo boh.

### linea inesatta 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 9.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 9">


Quindi inesatta perché devo trovare l'insieme di alpha buoni, non quell preciso

### Condizioni di wolfe 🟨-

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 10.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 10">


Minore, inoltre minore di qualcosina..

### Armijo e backtracking🟨

- Intro a backtracking

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 11.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 11">

- backtracking

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 12.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 12">

- L’algoritmo

    **NOTA**: bisgona anche mettere una condizione di maxit, se si esce per quella allora è perché non si può trovare! (molto probabilmente)

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 13.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 13">


## Condizioni di ottimalità

### Definizione 🟩

Quando sono in un minimo locale o globale per la nostra funzione.

Andiamo a definire una condizione di ottimalità di primo secondo oordine perché andiamo a guardare le derivata

### Condizione necessaria e sufficiente al primo e secondo ordine 🟩

**Primo ordine**

Questo non è altro che il teorema di fermat del secondo ordine che puoi trovare qui [11.1.2 Condizione di stazionarietà (fermat) !!!](/notes/11.1.2-condizione-di-stazionarietà-(fermat)-!!!)

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 14.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 14">


Non esiste una condizione sufficiente al primo ordine

**Secondo ordine**

Questo è il modo con cui trovavamo i punti di minimo, è **anche una condizione sufficiente se è definita positiva**

### Ottimalità per funzioni convesse ! 🟩

<img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 15.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 15">

## Funzioni quadratiche

Questo tipo di funzioni ci piace molto perché sono convesse e le funzioni convesse sono facili da analizzare per sta robba.

### Quadratiche convesse 🟥

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 16.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 16">


Con $$Q$$ matrice simmetrica

Con $$q$$ convessa se la matrice è semidefinita positiva, e convessa stretta se è definita positiva.

Questa funzione ci può essere utile per la risoluzione dei  [Minimi quadrati](/notes/minimi-quadrati). Quando mi calcolavo la norma quadrata per quel problema, avevo una funzione quadratica convessa (quasi, credo che il termine noto non fa male)!

### Soluzioni eq. normali

- Slide

    <img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 17.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 17">


Con la roba di sopra dimostro anche che una soluzione ottima (ricorda che è ottima anche una soluzione locale) esiste sempre.

## Metodo di newton puro

L’unica cosa che cambia nello step di newton è che la **direzione di discesa è calcolata in modo differente**, in particolare possiamo vedere che lo step sia:

$$p_k = H(x_k) ^{-1} \nabla f(x_k)$$, le ragioni sono sconosciute, e non è conveniente in termini di tempo provare a capire questo. **lo step è sempre di 1**.

- La velocità di convegenza è **quadratica** come nel caso descritto per newton in [Equazioni non lineari](/notes/equazioni-non-lineari).

## Ripasso (roba di analisi)

### Derivata parziale

Guardare [Calcolo differenziale](/notes/calcolo-differenziale).

Ma è una roba troppo base sta roba 😑

### Hessiana

Questa matrice ci da informazioni sulle **derivate seconde**

1. Matrice simmetrica
2. derivata ij, prima derivo su i, poi su j

Ricordarsi il teorema di schwarz, che è sufficiente per dimostrare che la matrice è simmetrica

### Jacobiana

Questa ci da informazioni sulle **derivate prime** per tutti i modi possibili!

$$f: \R^n \to \R^m$$, $$J(f) : \R^n \to \R^{m\times n}$$

1. In particolare sulle righe ho tutte le derivate parziali possibili
2. Sulle colonne ho la derivata fatta su tutte le funzioni possibili

### Analogo minimimo massimo

Se ho il massimo e voglio il minimo, basta costruirsi la funzione swappata


$$
\argmax f(x) = \argmin - f(x)
$$


### Teorema sulle funzioni differenziabili

[Calcolo differenziale](/notes/calcolo-differenziale) Spiega bene questo teorema, con

> Se le derivate parziali esistono e sono continue, allora la funzione si dice differenziabile con continuità C.
>

### Punti di minimo locali e globali

**Globale**

Quando è minimo per tutto il dominio.

**Locale**

Se è un punto di minimo globale con dominio ridotto ad un intorno (basta che esista un interno).

### Funzioni convesse

Questa parte è trattata in analisi in [Convessità (cenni)](Convessita%CC%80%20(cenni)%20b097c1a254f84bd3926b796fb1179c89.md)

- Slides

    !<img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 18.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 18">

- Slide

    !<img src="/images/notes/image/universita/ex-notion/Metodi di Discesa/Untitled 19.png" alt="image/universita/ex-notion/Metodi di Discesa/Untitled 19">




# References