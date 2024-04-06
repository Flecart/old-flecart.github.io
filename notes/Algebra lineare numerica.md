---
layout: page
permalink: notes/algebra-lineare-numerica
tags: italian
title: Algebra lineare numerica
---

Ripasso Prox: 24
Ripasso: December 23, 2022
Ultima modifica: January 2, 2023 9:50 AM
Primo Abbozzo: September 22, 2022 12:03 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No


# Algebra lineare numerica
#### Immagini
Lab 2 images

## Metodo di gauss

Vogliamo cercare un metodo per calcolare soluzioni a sistemi di equazione del genere:

$$Ax = b$$, classico. Supponiamo che questo sistema abbia una soluzione.

Il nostro obiettivo sarebbe scomporre la matrice $$A = LU$$
 come prodotto di due matrici Lower triangular e Upper triangular.

### Algoritmo per matrici Upper e lower triangular 🟩

Nel caso io abbia una matrice Lower o Upper triangular, i sistemi nella forma $$Lx=b$$ sono risolvibili con un algoritmo abbastanza banale che qui non riporto (sostituzioni via via…)

Il costo è di $$O(n^2)$$ e non ti scordare il /2 perché a lei piace

### Scomposizione A = LU 🟩

Questo è un algoritmo che necessita di una osservazione abbastanza difficile:

Noto che durante l'applicazione dell’algoritmo di gauss, per creare il pivot su una colonna, è esattamente come se moltiplicassi per una (matrice identità + fattori per la colonna di interesse).

Come in esempio

<img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled">

Si può notare inoltre che che l’inverso di L1 è in una forma molto bella, esattamente la stessa con numeri invertiti!, inoltre la moltiplicazione fra  Ln è anch’essa in una forma molto carina!!! Facilita molto il prodotto.
In questo modo mi creo una matrice L, in cui è molto facile invertire.

costo $$O(n^3/3)$$  per la fattorizzazione LU e  poi n2 due volte per risolvere L e U

### Scomposizione con permutazione 🟩

Ogni tanto potrebbe capitare che ci sia il bisogno di permutare, altrimenti non ho nessuna soluzione, da notare che questo è un passo all'interno dell’algoritmo di gauss.

Inoltre scegliere il maggiore dovrebbe aiutare ad eliminare mini-errorini dovuti all’imprecisione della somma floating point.

- Algoritmo

    <img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled 1.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled 1">


### Forma finale scomposizioni 🟩

Se utilizziamo una sorta di **pivoting parziale** ossia per ridurre gli errori scegliamo il massimo della colonna (come del resto fa l’algoritmo di sopra) allora non abbiamo bisogno di permutare colonne), se vogliamo invece un **pivoting totale** allora dobbiamo permutare le colonne e la matrice diventa qualcosa del tipo

$$A = QLUP$$ con Q le permutazioni su riga, e P quelle su colonna (quelle su colonna non è che ci importa molto, perché basta moltiplicare per $$P^T$$, ossia la sua inversa per x e si risolvono problemi di questo genere… dato che alla fine $$PP^T = I$$

### Metodo di Cholesky 🟩

Se prendo una matrice A **simmetrica definita positiva** (ricorda analisi per questo), allora con questo metodo riesco a riscriverla nella forma $$A = LL^T$$, e so che la matrice L triangolare inferiore non è singolare perché ho tutti gli autovalori positivi.

Questo metodo costa $$O(n^3/6)$$ leggermente più veloce della fattorizzazione di Gauss.

Una volta fatto la scomposizione poi va subito

$$Ly = b, L^Tx = y$$ e si risolve, sul come funziona l'algoritmo, per ora ci importa solamente che è più veloce.

Se non è simmetrico o non è definita positiva il programma crasha (lel che non sa come funzioni la prof. è un sapere, non un conoscere, come diceva Bononi)

### Matrici simmetriche semidefinite o definite positive 🟩

Se prendo un qualunque vettore e vale


$$
x^TAx \geq 0
$$


Oppure avendo autovalori sempre positivi sono maggiore di 0, si può vedere che è equivalente.

Guarda [Massimi minimi multi-variabile](/notes/massimi-minimi-multi-variabile) nella sezione forme quadratiche per questo.

## Metodi iterativi

Sono buoni perché l'errore di questi è molto più alto, ma spesso molto più veloce, mentre per i metodi diretti è esattamente il contrario (errore basso, alta complessità).

In modo molto generale, possiamo definire un metodo iterativo come una funzione $$G$$ applicata all'input stesso: $$x_n = G(x_{n - 1})$$

### Note introduttive convergenza e iterazione

Questa sotto è la definizione di **convergenza ad $$\alpha$$ con ordine $$p \geq 1$$**

<img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled 2.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled 2">

Spesso la convergenza è fissata da una condizione di arresto (che può essere dipendente anche dal numero di iterazioni. Possiamo definire **C = fattore di convergenza** quando $$p = 1$$, perché più è piccolo più converge in fretta. C'è anche una relazione simile fra i p, più è grande, in questo caso, più velocemente converge.

## Metodi iterativi stazionari

### Idee Generali 🟩

Questi sono nella forma  $$x _{k +1} = Hx_k + d_k$$ Poi scriverlo come una differenza di matrici in particolare vorre $$A = M - N$$ , dove $$M$$  sia non singolare (e possibilmente facilmente invertibile). Se ciò è possibile allora

$$Ax = b \implies Mx - Nx = b \implies x = M^{-1}Nx + M^{-1}b \implies x = Tx + c$$

Una volta avuto questa matrice $$T$$ possiamo riutilizzarla per ogni iterazione di successione!

Avremo che $$x_k = Tx_{k - 1} + c$$, e si ha che $$x* = \lim x_k$$ deve essere che


$$
x* = Tx* + c
$$


E vorremmo che questo metodo **converga per ogni input** quindi potrei mettere un x_0 a casissimo

Una cosa non espressa durante la lezione è che $$N = M - A$$ quindi


$$
M^{-1}N = M^{-1}(M - A) = I - M^{-1}A
$$


Che ci permette di scrivere la stessa cosa sente fare utilizzo della matrice $$N$$ e secondo me è più clean. Questa cosa è presente nel libro.

### Condizione necessaria e sufficiente di convergenza 🟩

**Teorema sulla condizione di convergenza:**

<img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled 3.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled 3">

Questo risultato si può connettere col raggio spettrale e si può concludere che converge sse


$$
\rho(T) < 1
$$


<img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled 4.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled 4">

### Metodo di Jacobi 🟩

Sia $$D$$ la parte diagonale di $$A$$, allora l’iterazione in questa forma converge e si chiama metodo di jacobi


$$
x_{k + 1} = (I -D^{-1}A)x_k + D^{-1}b
$$


Nota: attento che la prof non ha insegnato in questo modo! Quindi probabilmente se te la chiede diglielo nella forma che le piace,

$$M = D, N = E + F$$

### Metodo Gauss-Seidel 🟩

Si ricorda che $$A = D - E - F$$ in modo molto strano di scriverlo…

Si fa uso della matrice Lower con anche la diagonale, per il resto è esattamente uguale a tutto il resto per i metodi iterativi., quindi


$$
M = D - E, N = F
$$


### Condizioni di convergenza per Jacobi e Gauss-Seidel 🟥

Per comprendere questa parte è importante il concetto di matrice con diagonale dominante. In parole umane deve essere che ogni elemento sulla matrice deve essere maggiore della somma di tutto quanto non stia sulla diagonale maggiore.

- Slide condizioni

    <img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled 5.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled 5">


Nota questi sono in pratica da imparare a memoria, ma non me ne ricordo!

### Gradiente coniugato

Questo è un metodo di arresto molto misterioso, direi di cacharla 🤑.

<img src="/images/notes/image/universita/ex-notion/Algebra lineare numerica/Untitled 6.png" alt="image/universita/ex-notion/Algebra lineare numerica/Untitled 6">

## Metodi di cui non ha parlato

### Metodo SOR

### Metodi di Rilassamento

### Metodi di Krylov



# References