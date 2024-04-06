---
layout: page
permalink: notes/cambio-di-base-e-autovalori
tags: italian
title: Cambio di Base e Autovalori
---

Ripasso Prox: 7
Ripasso: June 1, 2022
Ultima modifica: October 19, 2022 4:59 PM
Primo Abbozzo: April 5, 2022 10:40 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# 5 Cambio di base

## 5.1 Nozioni da avere prima di Cambio di Base

1. [Applicazioni lineari](/notes/applicazioni-lineari)
    1. La definizione di applicazione lineare
    2. La matrice associata
    3. L'esistenza e unicità di una applicazione lineare rispetto a una base
2. Le coordinate di un punto rispetto a una base.

## 5.2 Matrice del CdB e Identità

Se ho due spazi vettoriali

- Intuizione in R

    Le coordinate dei punti in R sono uguali a V per le basi canoniche, ma questo vale solamente per R, ora vogliamo andare a dire una cosa più forte, il cambio di base


Se ho una applicazione lineare $$F: V \to W$$ e un insieme di basi del dominio e del codominio, allora esiste una matrice $$A \in M_{m \times n} (\R)$$ tali che vale il cambio di base.

Questa matrice me la costruisco mettendo per ogni colonna le coordinate di $$F(v_1)$$ rispetto alla base del vettore di arrivo.

$$F(v)_{\beta '} = A v_{\beta}$$ cioè le coordinate di v rispetto alla base d arrivo è uguale a una matrice (costituita dalle coordinate **dell'immagine delle basi** ) per il vettore coordinate iniziali.

- Dal libro

    <img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled">

    <img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 1.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 1">


### 5.2.1 Matrici associate all’identità

Questa m̀atrice sono per applicazioni lineari del tipo $$f:V \to W$$, $$V = W$$ e ele due basi sono l'identità. Allora la matrice associata a queste due basi è $$I_{\beta \beta'}$$

Se le due basi sono esattamente le stesse, allora posso dire che è la matrice identità, la cosa un pò cambia quando le basi sono diverse.

Ovvero se mando la stessa base, le coordinate non cambiano, quindi riesco a costruirmi abbastanza in fretta la matrice identità.

Ossia $$I_{\beta\beta} = I$$, che è uguale rispetto a una base canonica qualunque.

Quindi la matrice associata a questa è

$$\begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}$$ e simili

### 5.2.2 L’inversa della composta dell’identità (8.2.2) (!!)

Si ha che  $$I_{eb} = I_{be}^{-1}$$, ovvero la matrice identità per certe basi è esattamente l'inversa.

Questo perché supponendo che le matrici associate si comportano bene per la moltiplicazione, ho che

$$I_{eb}I_{be} = I_{bb} = I$$ ovvero è l'applicazione identità.

E bisogna anche verificare l'inverso quindi $$I_{be}I_{eb} = I_{ee} = I$$

### 5.2.3 Coordinate di un vettore rispetto a una base non canonica

Sia v un vettore nel nostro spazio, e sia b una base di Rn allora si ha che

$$(v)_{\beta} = I_{\beta e}^{-1}v$$.

Prendiamo in considerazione la matrice $$I_{e\beta}$$, allora

$$id(v)_{\beta} = I_{e\beta}(v)_e$$ per come abbiamo definito la matrice, ossia riusciamo a calcolarci le coordinate di v nella nuova base, utilizzando il teorema di sopra /

### 5.2.4 Composizione fra matrici con basi qualsiasi

Posso dimostrare che un fatto dimostrato precedentemente si comporta bene anche con basi qualsiasi.

Ovvero vogliamo dimostrare che date le funzioni $$F: A \to B, G: B\to C$$ con ognuna una base, voglio una matrice associata per la composizione di funzioni si comporti bene. (comunque sì si può dimostrare)

## 5.3 Il cambio di base

L'idea principale di questo cambio di base per applicazioni lineari è **ricondurci a una base** voluta, più comoda per i nostri calcoli, quindi passare da qualcosa in mezzo

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 2.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 2">

Quindi avremo una applicazione lineare del tipo:

$$A_{\beta\beta'} = I_{e'\beta'} A_{ee'}I_{\beta e} = I_{\beta'e'}^{-1} A_{ee'}I_{\beta e}$$  ricordandosi che applico le funzioni a destra per prime.

(da notare che la la matrice $$I_{\beta e}$$  è molto semplice da calcolare, perché l'insieme di arrivo è canonico, e quindi è semplice.

# 6 Autovalori e Autovettori

Ha senso solamente parlare di autovettori quando si ha una **applicazione lineare con stesso dominio e stesso codominio.**

Vorremmo trovare una buona matrice che sia diagonale.

## 6.1 Diagonalizzabilità

### 6.1.1 Definizione per funzione e matrice

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 3.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 3">

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 4.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 4">

Questo perché vorrei una base in cui si abbia un matrice diagonale. (quindi probabilmente P è una matrice identità).

**Perché ci piacciono le matrici diagonali**

Se ho una matrice diagonale, si ha che l'applicazione lineare è un semplice scaling  dei vettori della base.

### 6.1.2 Matrici simili

> Date due matrici in uno spazio vetoriale con le matrici, allora se esiste un P nello stesso spazio tale che $$B = P^{-1}AP$$ si dicono **simili** (in pratica fare uno scambio di base).
>

**Osservazione 1**

Posso dimostrare che la matrice $$A_{ee'} \sim A_{bb'}$$ associata a una funzione, sono simili per il teorema del cambio di base di sopra

**Osservazione 2**

La simile, è una relazione di equivalenza (riflessività, simmetria e transitività)

### 6.1.3 Diagonalizabilità di una matrice quadrata

> Si può dire che una matrice quadrata A è diagonalizzabile se è simile a una matrice diagonale
>

(Anche la definizione di sopra è uguale (equivalente).

### 6.1.4 Equivalenza della diagonalizzabilità funzionale e matriciale (9.1.4)(!!!)

Si ha che una funzione F e la sua matrice associata.

Allora F diagonalizzabile SSE la sua matrice associata è diagonalizzabile.

- Dimostrazione

    $$\implies$$Supponiamo che la funzione sia diagonalizzabile, allora ho una base per cui si ha una matrice diagonale.

    A questo punto utilizzo il teorema del cambio di base per costruirmi la P voluta per la diagonalizzabilità (o avere una matrice simile) e ciò finisce.

    $$\impliedby$$ Supponiamo che si abbia una matrice diagonalizzabile, allora abbiamo una matrice P che mi dia una matrice diagonale.

    **Lemma:** le righe di P sono linearmente indipendenti. Si dimostra per il teoremone (l’esistenza dell’inversa, implica che è associata a una funzione bigettiva, che implica che le colonne sono indipendenti).

    Considero le colonne di P, queste sono N vettori indipendenti che fanno quindi span sullo spazio vettoriale Rn. Ma allora P è proprio $$I_{be}$$ con b la base definita dalle colonne!

    E quindi ho trovato la base per la funzione tale che sia diagonale, quindi la funzione è diagonalizzabile.


### 6.1.5 Condizione di diagonalizzabilità (!!!!) ⭐

> Si può dire che una funzione F sia diagonalizzabile sse esiste una base di Rn costituita da autovettori di F
>

La dimensione delle due frecce è identica (almeno le tecniche lo sono)

- Dimostrazione

    $$\impliedby$$Sia una base di Rn costituita da autovettori della F. Allora la matrice associata a questa funzione è una matrice diagonale per questa base (bisogna fare un pò di conti).

    $$\implies$$Sia b una base tale che la matrice associata alla funzione sia diagonalizzabile, allora ho una base per cui la funzione è diagonale. Elimino questo esiste con la base beta, voglio dimostrare che siano autovettori.


## 6.2 Calcolo degli autovettori e autovalori

### 6.2.1 Autovalore 0 e kernel (!)

> $$Ker F \neq 0_v \iff F$$ ha autovalore $$0$$
>
- Dimostrazione

    $$\implies$$ supponiamo che $$v \neq 0_v, v \in Ker F$$ allora $$F(v) = 0\cdot v = 0$$, ossia 0 è un autovalore.

    $$\impliedby$$Supponiamo che 0 sia un autovalore, allora esiste un autovettore (per definizione diverso da 0) allora esiste un elemento diverso da 0 nel kernel, e quindi non è iniettiva per una proposizione precedente


### 6.2.2 Polinomio caratteristico

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 5.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 5">

**Nota:** si ha che se ho una matrice n x n il polinomio caratteristico ha grado n.

### 6.2.3 Autospazio e Polinomio caratteristico (!!!)

L'autospazio per un certo autovalore è questo insieme

$$V_\lambda = \{v \in \R^n | F(v) = \lambda v\}$$, ossia è l'unione dei autovettori con lo zero.

**Proposizione:**

$$V_\lambda = Ker(A - \lambda I)$$, con il kernel della matrice definita come le soluzioni del sistema lineare omogoneo associato ala matrice (che poi è uguale al concetto della funzione).

- Dimostrazione

    $$\implies$$Sappiamo che $$V_y$$ è l'insieme degli $$x \in R^n| Ax = \lambda x$$ con A la matrice associata la nostra funzione. Vogliamo dimostrare che se $$x \in V_\lambda$$ allora appartiene al kernel, il che è abbastanza ovvio per la proprietà distributiva della moltiplicazione matriciale.

    $$\impliedby$$Se si ha un v appartenente al kernel, allora poi si ricava (aggiungendo e sottraendo una parte) che $$Ax = \lambda x$$ che è proprio la condizione sufficiente per appartenere all'autospazio


### 6.2.4 Polinomio car per Matrici simili (no chiede)

Matrici simili hanno lo stesso polinomio caratteristico, questo si dimostra con distributività e associatività della moltiplicazione matriciale.

- Dimo

    $$A - \lambda I = P^{-1}BP - \lambda I = P^{-1}BP - P^{-1}P\lambda I = P^{-1}(B - \lambda I) P$$


### 6.2.5 Condizione dell’autovalore (!!!)

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 6.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 6">

- Dimostrazione

    $$\iff$$Se $$\lambda$$ è un autovalore, allora ho un autovettore che appartiene all'autospazio relativo.

    Vogliamo che l'autospazio è diverso da 0, questo è vero sse il sistema lineare (A - lambdaI)x = 0 ha una soluzione non nulla, allora per il teoremone, questo è vero sse il determinante della matrice è uguale a 0.  quindi sse lambda è uno zero della nostra matrice.


## 6.3 Molteplicità e autov{ettori, alori}

### 6.3.1 Autovalori diverse fanno autovettori indipendenti (no chiede)

Si dimostra in modo induttivo, partendo da un unico vettore che è necessariamente indipendente, saltando per il passo induttivo e finire.

### 6.3.2 Molteplicità geometrica ed algebrica

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 7.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 7">

- DOmanda da fare alla marta

    Il fatto che la moltiplicità geometrica è minore o uguale alla molteplicità geometrica potrebbe essere insito nel polinomio caratteristico.

    Perché al massimo (è da dimostrare) che il grado del polinomio caratteristico è N, che è anche la dimensione della molteplicità geometrica???


### 6.3.3 Moltiplicità geometrica ≤ Molteplicità algebrica (no chiede)

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 8.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 8">

### 6.3.4 Diagonalizzabilità per somma di M-algebrica (no chiede)

<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 9.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 9">

Si può dimostrare che è un sse. e deve essere che le molteplicità algebriche e geometriche siano entrambi uguali.

- Dim-libro

    !<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 10.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 10">


# 7 Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
e molteplicità algebriche e geometriche siano entrambi uguali.

- Dim-libro

    !<img src="/images/notes/image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 10.png" alt="image/universita/ex-notion/Cambio di Base e Autovalori/Untitled 10">


# 7 Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |

# References