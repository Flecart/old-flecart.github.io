---
layout: page
permalink: notes/autovettori-e-determinanti
tags: italian
title: Autovettori e determinanti
---

Ultima modifica: January 4, 2023 9:56 AM
Primo Abbozzo: December 26, 2021 11:42 AM
Studi Personali: No

# Elementi di ripasso

# 2 Autovalori e Determinanti

## Determinanti

I determinanti sono un numero associato alle matrici quadrate. Più o meno ne sono il riassunto.

### Proprietà

Le prime 3 sono quelle fondamentali per calcolare il tutto, i numeri dopo il 3 sono alcune conseguenze.

1. det I = 1
2. Cambiare righe → cambiare il segno della determinante.
3. (Importante)
    1. Se moltiplico una riga per una costante, il determinante è moltiplicato per questa costante.
    2. Se sommo una costante a una riga, allora il determinante è una somma strana...
    - Immagine di esempio

        <img src="/images/notes/image/universita/ex-notion/Autovettori e determinanti/Untitled.png" alt="image/universita/ex-notion/Autovettori e determinanti/Untitled">

4. Se la matrice ha due righe uguali, il determinante è 0, questo è derivabile dalla proprietà 2.
5. Sottrarre un multiplo di una riga a una altra riga della matrice produce la stessa determinante.
(in pratica sto sottraendo una matrice che ha due righe uguali, la cui determinante è 0).
6. Una riga di 0 implica che il determinante dell’intera matrice sia 0, questo si può dimostrare con 3a.
7. Data una matrice uppertriangular, il determinante è la moltiplicazione degli elementi nella diagonale principale. (posso ottenere una matrice diagonale sottraendo all’insù, e poi posso tirare fuori multipli per riga).

L’ultima proprietà ci dice come si fa a calcolare il determinante, ossia ridurre in forma U e poi moltiplicare la diagonale. Ez. (da tenere in conto anche possibili cambi di riga).

1. det A = 0 quando A è singolare (possiede una riga di 0) e det A ≠ 0 quando non lo è
2. il determinante del prodotto di due matrici è il prodotto delle determinanti delle due matrici, è un isomorfismo!
Questa proprietà ci dà anche il determinante dell’inverso in modo immediato, questo ci dà anche un modo immediato per trovare l’inversa di una matrice diagonale (basta invertire tutti i numeri 🙂) e questo è anche un motivo per cui **se invertibile not 0, altrimenti divido per 0.**
3. determinante della transposizione di A è uguale al determinante di A, in quanto se ragioniamo nella forma diagonale la transposizione è esattamente uguale ad A.

### Calcolo

Possiamo splittare il calcolo della determinante in somme più semplici. Inoltre possiamo notare che un determinante è diverso da nullo, per la proprietà 8 se non è singolare, quindi vogliamo avere un elemento per ogni colonna e riga.

Continuando questo ragionamento possiamo cercare di riassumere tutto in una unica formula


$$
\det A = \sum_{\text{n! sums}} P(\alpha, \beta, ..., \omega) a_{1\alpha} a_{2\beta}...a_{n\omega}\\
\{\alpha,\beta, ..., \omega\} \in \text{ Perm of } \{1,2,3...,n\}, \text{ where } A \text{ is } n \times n \\
P(\alpha, \beta, ..., \omega) =\begin{cases}
1 \text{ if it's even permutation } \\
-1 \text{ if it's odd permutation }
\end{cases}
$$


### Determinante come volume

Per esempio se prendiamo una matrice 3x3, possiamo prendere ogni punto identificato da una riga come 3 punti. Questi tre punti riescono ad identificare una scatola. (ogni lato è un parallelogramma e il volume del cubo è uguale al determinante).

## Cofattori

I cofattori sono utili per semplificare il calcolo della determinante presentata in precedenza.

In altre parole si potrebbe dire che il determinante di una matrice quadrata grossa si potrebbe ridurre come una combinazione lineare di alcune sottomatrici.

<img src="/images/notes/image/universita/ex-notion/Autovettori e determinanti/Untitled 1.png" alt="image/universita/ex-notion/Autovettori e determinanti/Untitled 1">

### Determinante con cofattori

Quindi il calcolo del determinante si può riassumere come


$$
\det A = \sum_{i=1}^{n} a_{1i}C_{1i}
$$


### Inverse con cofattori

Si potrebbe notare che questo sia il metodo matematico per l’inverso, mentre le eliminazioni con il metodo di Gauss Jordan è il metodo più informatico.


$$
A^{-1} = \dfrac{1}{\det A} C^T
$$


Che è equivalente nel verificare che


$$
\det A  \cdot I = A C^T
$$


E questo ha senso, se moltiplico per righe corrispondenti ho la formula sopra per il determinante per riga.

Mentre se lo faccio per tutte le altre righe è come se stessi calcolando il determinante con una riga doppia, quindi il determinante è 0 per quelle righe.

Se utilizzo questo risulato, posso derivare la formula di cramer

### Regola di cramer


$$
Ax = b \\
x = A^{-1}b \\
x = \dfrac{1}{\det A} C^T b
$$


Questo è code rimpiazzare la prima colonna della matrice A con b

Questo algoritmo è lentissimo, costa molto calcolare un determinante.

## Autovettori

gli autovettori sono i vettori di Ax che sono nella stessa direzione di x.

Possiamo scriverlo come $$Ax = \lambda x$$ e ho che lambda è un autovalore

Sembra che

1. La somma degli autovalori è uguale alla somma delle diagonali
2. Una matrice di dimensioni n n ha n autovettori

### Autovettori e autovalori di proiezione

Nell’esempio di una proiezione, un autovettore sarebbe stato xa in quanto sarebbe già nello spazio colonna in arrivo, quindi non viene proprio modificato.

Ma non solo questi sono degli autovettori, ma anche i vettori che sono perpendicolari (hanno autovalore 0, perché vengono totalmente distrutti).

Così abbiamo trovato gli autovalori per una matrice di proiezione che sono **0 e 1**

### La ricerca di autovettori: equazione dell’autovalore

Possiamo riscrivere l’equazione in questo modo:


$$
(A - I\lambda)x = 0
$$


Quindi stiamo cercando soluzioni nello spazio nullo di una nuova matrice, che è interessante solamente se questa matrice è singolare, ossia che abbia una determinante uguale a 0

Cerchiamo le soluzioni di $$\det (A - I\lambda) = 0$$ per lambda
i una nuova matrice, che è interessante solamente se questa matrice è singolare, ossia che abbia una determinante uguale a 0

Cerchiamo le soluzioni di $$\det (A - I\lambda) = 0$$ per lambda