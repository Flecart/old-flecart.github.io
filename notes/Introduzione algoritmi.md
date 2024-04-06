---
layout: page
permalink: notes/introduzione-algoritmi
tags: en
title: Introduzione algoritmi
---

Ripasso Prox: 50
Ripasso: May 27, 2022
Ultima modifica: April 25, 2022 9:17 PM
Primo Abbozzo: February 21, 2022 4:24 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# 0 Introduzione

## 0.1 L’algoritmo

Vogliamo cercare di creare algoritmi, ovvero soluzioni a problemi computazionali che **non dipendono dal linguaggio** di programmazione.

### 0.1.1 Definizione

> Procedura per risolvere un problema in un numero **finito** di passi (quindi un algoritmo deve finire)
>

### 0.1.2 Origine della parola

Il nome "algoritmo" deriva da un nome di un matematico persiano dell 800 d.c. *Muhammad ibn Musa al-Khwarizmi*, che latinizzato diventa *algorithmi*, quindi i latini hanno creato la parola!

Questo matematico aveva creato un trattato per studiare il sistema di numerazione arabico che sostituirà quello romano, si chiama *Algoritmi de numero Indorum*, un sistema più efficiente rispetto al romano.

### 0.1.3 Algoritmo vs programma

Un algoritmo è una cosa differente rispetto al programma, l'algoritmo è più concentrato sul design (la descrizione dei passi ad **alto livello**, di solito in pseudo codice che non è eseguibile) mentre il programma è l'implementazione dell'algoritmo, che dipende strettamente da un linguaggio di programmazione (che potrebbero esserci aspetti noiosi di implementazione) e dai limiti finiti della macchina, come memoria.

### 0.1.4 Esempio massimo comune divisore

<img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled">

## 0.2 Fibonacci

Possiamo trovare molteplici soluzioni per trovare il numero di fibonacci.

### 0.2.1 One-shot

Esiste la formula matematica per calcolare il numero di fibonacci. Questa la risolve subito, ma ha il problema di avere problemi di precisione in quanto le radici e simili non sono salvati correttamente in memoria.

### 0.2.2 Classico algoritmo ricorsivo

- Algoritmo

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 1.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 1">


Questo approccio funziona ma è dannatamente lento in quanto ha bisogno di tempo di tempo. (lineare di memoria)

La cosa brutta di questo algoritmo è che non utilizza il fatto di stare calcolando stesse istanze di quelle. Cioè non sta riutilizzando calcoli già fatti

**Giustificazione della linearità della memoria**

Possiamo osservare da questa rappresentazione dell'albero di chiamate che al massimo posso chiamare questa funzione un numero n di volte. (percorso più lungo radice foglia)

**Analisi temporale**

<img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 2.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 2">

Per una analisi temporale corretta si cerca di prendere in considerazione alcune operazioni primitive dei computer dato che non possiamo tenere in conto l'istruzione codice macchina (che dipende dal compilatore e non funziona nemmeno tenere conto dei secondi che ci mette perché dipende dalla macchina) Quindi consideriamo solamente operazioni primitive che hanno bisogno di un tempo costante  per esse eseguite.

- Dimostrazione della relazione temporale

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 3.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 3">

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 4.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 4">


### 0.2.3 Classico algoritmo iterativo

- Algoritmo

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 5.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 5">


**Analisi spaziale**

Stiamo allocando un array lungo n, per cui si ha n item di spazio

**Analisi temporale**

<img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 6.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 6">

Nel calcolo ha sbagliato a mettere un 3 davanti alla parentesi, dovrebbe essere 2 (ma resta lineare)

### 0.2.4 Iterativo ottimizzato in memoria

Una osservazione importante è che non ci serve tenere in memoria l'intero array perché gli unici elementi che ci interessano sono i vecchi due elementi, quindi possiamo creare una formula iterativa che tenga conto di questo fatto e migliorare l'uso della memoria da lineare a costante.

- Algoritmo

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 7.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 7">


### 0.2.5 Soluzione matriciale (mult non ottimizzato)

Notiamo che fibonacci può essere espresso come una potenza della matrice $$\begin{bmatrix}
1 & 1 \\
1 & 0
\end{bmatrix}$$.

Questo fatto si può dimostrare per induzione, una volta fatto possiamo andare ad implementare l'algoritmo nuovo. Questo algoritmo dopo una analisi ha stesse proprietà dell'algoritmo precedente, però può essere migliorato il passo di moltiplicazione matriciale

- Algoritmo e l'analisi di essa

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 8.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 8">


### 0.2.6 Matriciale ottimizzato

Utilizzando l'osservazione accennata sopra, che velocizza la moltiplicazione matriciale di molto, portandolo da n a log n.
in pratica l'idea è così: devo raggiungere n partendo da 1, nella precedente aggiungo 1 finché non arrivo a n, qui invece moltiplico per sé stessa finché non ci arrivo quindi faccio una cosa tipo: in pratica possiamo vederla così, guardiamo n in binario, se c'è un 1 moltiplico per matrice base, se 0 moltiplico per sé stessa. Farò sempre un numero logaritmico di operazioni.

- Algoritmo helper

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 9.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 9">

- Algoritmo finale

    <img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 10.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 10">


### 0.2.7 Algoritmi a confronto

In questa immagine sottostante riusciamo a osservare il grafico sull'efficienza dei vari algoritmi.

<img src="/images/notes/image/universita/ex-notion/Introduzione algoritmi/Untitled 11.png" alt="image/universita/ex-notion/Introduzione algoritmi/Untitled 11">

### 0.2.8 Valore in input vs dimensione di input

Alla fine sono la stessa cosa.

Si può anche analizzare un input in termini di bit necessari per la rappresentazione dell’oggetto. Dipende dall’algoritmo alla fine (per gli algoritmi di crittografia è molto più utile analizzare i bit dei numeri

- Cosa che non centrano

    $$
    f(n) \in O(g(n)) := \exists c \in \R|\lim_{n \to \infty} \dfrac{f(n)}{g(n)} \leq c \\

    f(n) \in \Omega(g(n)) := \exists c \in \R|\lim_{n \to \infty} \dfrac{f(n)}{g(n)} \geq c \\
    $$
$
    f(n) \in O(g(n)) := \exists c \in \R|\lim_{n \to \infty} \dfrac{f(n)}{g(n)} \leq c \\

    f(n) \in \Omega(g(n)) := \exists c \in \R|\lim_{n \to \infty} \dfrac{f(n)}{g(n)} \geq c \\
    $$

# References