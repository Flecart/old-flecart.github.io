---
layout: page
permalink: notes/spazi-vettoriali-(vecchio)
tags: italian
title: Spazi vettoriali (vecchio)
---

Ultima modifica: October 19, 2022 5:05 PM
Primo Abbozzo: December 14, 2021 4:36 PM
Studi Personali: No

# Elementi di ripasso

# 0 pezzo di introduzione

## 0.1 Modi di vedere (3)

Ci sono principalmente 3 modi di vedere l'algebra lineare.

Visione Colonna, visione riga e visione matriciale

(La seguente è una visione riga)


$$
2x - y = 0 \\
-x + 2y = 3
$$


Questa cosa si può rappresentare in forma matriciale in questo modo:


$$
\begin{bmatrix}
2 & -1 \\
-1 & 2
\end{bmatrix}
\begin{bmatrix}
x \\
y
\end{bmatrix} =
\begin{bmatrix}

0 \\
3
\end{bmatrix}
$$


Si scrive in maniera carina $$Ax = b$$

### 0.1.1 Visione riga

Possiamo rappresentare le soluzioni di ogni riga attraverso un grafico n-dimensionale (quindi funziona finché non andiamo sopra il 3 grado!)

Vedere sopra

### 0.1.2 Visione colonna

Questa invece vuole chiedere una combinazione lineare ** che mi possa dare una soluzione.

es:

$$x\begin{bmatrix} 2 \\ -1\end{bmatrix} + y \begin{bmatrix} -1 \\ 2 \end{bmatrix} = \begin{bmatrix} 0 \\ 3 \end{bmatrix}$$

### 0.1.3 Obiettivo finale

Vogliamo avere delle soluzioni generali per tutte le matrici (si scoprirà che le matrici invertibili ci piacciono,, si scopriranno generatorie  simili...)

## 0.2 Eliminazione e Sostituzione

Questo è il metodo che viene utilizzato dalla maggior parte dei software per risoluzione di sistemi lineari.

### 0.2.1 Algoritmo di Gauss (eliminazione)

**idea principale:** Utilizzare dei pivot (la variabile che vogliamo eliminare nelle altre righe che non può essere nullo) e sottrarre in tutte le altre righe.

E poi richiamare in modo ricorsivo sulla sottomatrice n - 1, n - 1 perché tutto il resto era già apposto.

In questo modo abbiamo ottenuto nella diagonale principale tutti i pivot che ci interessano. **Chiamiamo questa nuova matrice equivalente U** al posto di A

**Caso di fallimento:** Fallisce quando esiste un pivot che sia 0 dopo che sia stato utilizzato l'algoritmo per bene (prima provo a scambiare righe). Quando sono tutti 0 per una intera sotto-colonna (sotto-colonna perché potrei anche trovarmi in un sottocaso, non necessariamente nella prima chiamata).

### 0.2.2 Sostituzione

Una volta che ho ottenuto la matrice U, posso sostituire fino sopra, perché nell'ultima riga ho una equazione a una unica variabile, poi trovata questa posso metterla sopra, sopra ancora finche'non finisce.

## 0.3 Tipologie di matrici

### 0.3.1 Matrici di eliminazione

Possiamo definire delle matrici per l'eliminazione di parti che ci interessano. e possiamo chiamarli matrici $$E_{ij}$$ con i righa e j colonna. Da questo potrei creare una unica matrice mi faccia tutta l'eliminazione in un passo solo.

Data che la moltiplicazione è associativa, posso prima fre le molitplicazioni fra le matrici di eliminazione prima.

### 0.3.2 Matrici di permutazione

Possiamo vedere che la moltiplicazione fra le matrici è fortemente non commutativo. Infatti diamo un occhiata alle matrici per invertire righe e colonne.

e.g.


$$
\begin{bmatrix}
0 & 1 \\ 1&0
\end{bmatrix}
\begin{bmatrix}
a & b \\ c & d \end {bmatrix}
= \begin{bmatrix} c & d \\ a & b \end{bmatrix}
$$


Però


$$

\begin{bmatrix}
a & b \\ c & d \end {bmatrix}\begin{bmatrix}
0 & 1 \\ 1&0
\end{bmatrix}
= \begin{bmatrix} b & a \\ d & c \end{bmatrix}
$$


Usando la stessa matrice di permutazione.

### 0.3.3 Matrici Inverse

La matrice inversa è trovare una matrice che moltiplicata alla nostra matrice di interesse ritorni una matrice identità.

## 0.4 Moltiplicazione delle matrici

### 0.4.1 Primo modo( Riga per colonna)

Questa è la definizione generale della moltiplicazione.

Vogliamo trovare il valore di $$C_{34}$$ creato da una moltiplicazione fra A e B ovvero Row 3 di A e Column 4 di B, prodotto scalare fra questi due.


$$
c_{mn} = \sum_{i=0}^k a_{mi} \cdot b_{in}
$$


Deve essere che il numero di colonne di A = numero di righe in B

Ma possiamo anche moltiplicare intere righe e intere colonne invece di guardare in modo singolo!

### 0.4.2 Matrice per colonna

Guardiamo le colonne della matrice risultato come **combinazioni** delle colonne del primo. (come combinarle me lo sta dicendo la colonna del secondo operatore.

### 0.4.3 Riga per matrice

In modo simile alla matrice per colonna, so che ogni riga della matrice di output è una combinazione lineare delle righe in B, che viene definito come fare in A.

### 0.4.4 Colonna per riga


$$
C = \sum_{i=0}^k A_i \cdot B_i
$$


Con $$A_i$$ la colonna i-esima e$$B_i$$ la riga i esima

### 0.4.5 A blocchi

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled.png)

## 0.5 Invertibilità delle matrici

Le matrici invertibili si chiamano **non-singolari**.

### 0.5.1 Non invertibilità delle matrici singolari

Per quelle singolari, sappiamo che lo spazio delle soluzioni è nello sottospazio vettoriale della loro combianzione, che semplicemente può non avere il punto dell'inverso.

Facciamo una dimostrazione per assurdo, assumiamo che esista un vettore che moltiplicato per questa matrice singolare dia un vettore nullo.
Allora sappiamo che $$Ax = 0$$, se esistesse l'inverso allora $$A^{-1}Ax = Ix = 0 \implies x = 0$$ assurdo.

### 0.5.2 Gauss-Jordan

Vogliamo trovare la matrice inversa.

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%201.png)

Esempio di applicazione

# 1 Spazi e sottospazi vettoriali

## 1.1 Introduzione

Possiamo identificare due operazioni principali per i vettori. Sommare e moltiplicarli. Vogliamo definire in modo formale il significato di queste due operazioni in un unico oggetto matematico che chiamiamo spazio vettoriale.

### 1.1.1 Intuizione di spazio vettoriale

**Spazio**, la parola spazio ha un significato preciso, è un insieme di vettori che abbiano una certa proprietà! Ma lo definiremo meglio fra poco.

Un sottospazio è un sottoinsieme dello spazio vettoriale che sia ancora chiuso nelle operazioni di addizione e moltiplicazione scalare.

Se ragioniamo in R2 notiamo che questi sono sottospazi:

1. R2 Stesso
2. Ogni linea che passa per 0,0
3. Il vettore nullo (sottospazio banale), o anche chiamato sottospazio Z.
4. Direi anche Q2, però è originato da un insieme ben diverso.

## 1.2 Spazi generati da una matrice

Questa parte sarà trattata forse in più dettaglio sotto.

Qui trattiamo la relazione fra matrice e questi spazi.

### 1.2.1 Spazio colonna

- Esempio di lezione

    [Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%202.png)


Vogliamo avere **tutte le combinazioni** lineari delle colonne! Perché altrimenti l'operazione di somma o moltiplicazione non sarebbe chiusa!

In questo caso viene generato un piano (che passa all'origine).

Questo spazio è molto importante perché una equazione del tipo

**RISOLVIBILITÀ**

$$Ax = b$$ è risolvibile **solamente nel caso in cui** $$b \in C(A)$$ perché può essere solamente una combinazione lineare di A.

Una altra condizione necessaria è che *se una combinazione sulle righe di A dà una riga zero, la stessa combinazione deve produrre un zero nella riga corrispondente in b,* altrimenti non è possibile risolvere l’equazione lineare.

### 1.2.2 Spazio riga (?)

In modo analogo rispetto allo spazio colonna posso avere uno spazio riga utilizzando le combinazioni lineari di righe.

### 1.2.3 Spazio nullo

Questo spazio contiene tutti i vettori x che risolvono l'equazione (questo è molto simile allo spazio riga

$$Ax = 0, x \in N(x)$$ (con 0 vettore di dimensioni volute).

Questo spazio può essere calcolato.

È uguale alle combinazioni lineari delle soluzioni delle colonne della matrice in forma echelon per irga (ovvero a scaletta, ridotta).

Ovvero per ogni colonna libera setto una variabile a 1 e tutte le altre a 0, e lo faccio per tutte le colonne libere. A questo punto ottengo delle soluzioni disgiunte. Per ottenere lo spazio nullo mi basta fare la combinazione lineare di queste.

**Forma echelon per riga ridotta**

Dopo aver ottenuto la forma di echelon, posso tornare sopra (in questo modo)

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%203.png)

## 1.3 Risolvibilità Ax=b

Come già accennato in [questa parte](Spazi%20vettoriali%20(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277.md), devono esserci certe condizioni soddisfate sulla matrice b affinche ci sia un sistema lineare soddisfacibile. Trovate due in quel momento.

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%204.png)

La soluzione particolare è la soluzione ponendo le variabili libere come 0

Questo è un pattern molto ricorrente in matematica, perché se ho una soluzione, allora posso aggiugnere tutti i vettori presenti nel N(A), tanto, sto aggiungendo uno zero. In questo modo ottengo tutte le soluzioni possibili. (non abbiamo dimostrato che siano tutte quelle!, ma probabilmente si può fare).

### 1.3.1 r = n < m

Quando il grado della matrice è uguale al numero delle colonne, allora ho solamente la soluzione particolare (che può anche non esistere). La forma ridotta a riga di echelon è solamente la matrice identità!

### 1.3.2 r = m < n

In questo caso ogni riga ha un pivot. la cosa bella di questo caso è che **ogni b è risolvibile** perché l’unica restrizione sarebbe stata avere una riga nulla!.

Il numero di variabili libere è uguale a n - r.

### 1.3.3 r = m = n

Questo è il caso più carino. La matrice è quadrata. Posso avere ogni b nel caso io abbia ogni pivot. Poi non ho nessuna colonna libera quindi ho una unica soluzione. Poi significa che è invertibile ⇒ avere ogni pivot.

### 1.3.4 r < m, r < n

è quando la reduced echelon form è una matrice lì in figura!

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%205.png)

## 1.4 Interdipendenza lineare e base (di vettori)

Una intuizione della indipendenza di vettori è quando uno non si può scrivere tramite combinazione lineare con altre.

Quindi

> Vettori $$x_0, x_1 ... x_n$$ se nessuna combinazione da un vettore zero eccetto la combinazione 0.
Ossia $$c_0x_0 +... +c_nx_n \not= 0$$
>

**n > m**

Nel caso in cui il numero di colonne è maggiore del numero di righe, sono sicuro che i vettori non siano indipendenti in quanto N(A) non è solo il vettore nullo.

quindi posso creare questo teorema (che non so come dimostrare lulz):


$$
\text{Dati vettori } v_1, v_2,...,v_n \text{colonne della matrice }A, \text{ allora sono indipendenti se }\\ N(A) = 0_v
$$


### 1.4.1 Base

> Una base per uno spazio è una seguenza di vettori $$v_1, v_2, v_3...,v_n$$ tali che
1. Sono indipendenti fra di loro
2. Riempiono uno spazio (contiene tutte le combinazioni lineari di quello)
Riprende l’idea che è il sottoinsieme più piccolo che sia ancora uno sottospazio vettoriale.
>

le basi degli spazi possono essere molti, ma **hanno tutti lo stesso numero di vettori!** Questo fatto non so come si dimostra. Però mi sta dando informazioni su quanto è grande questo spazio, infatti mi sta dando la **DIMENSIONE** dello spazio.

> La **dimensione** di uno spazio è il minimo numero di vettori che vanno a costituire una base per lo spazio in questione.
>

Questa dimensione è anche uguale al grado della matrice!

Grado di una matrice = dimensione di uno spazio, ecco che esiste questa strettissima correlazione fra spazio e matrice!

## 1.5 i 4 Sottospazi fondamentali

Siano le dimensioni della matrice $$A, m\times n$$

Queste sono gli spazi fondamentali della prima parte di algebra lineare.

Ci chiediamo in particolare quale siano le loro dimensioni, e quale sia la base.

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%206.png)

### 1.5.1 Spazio colonna

$$C(A)$$ sarà in $$R ^m$$

### 1.5.2 Spazio nullo

$$N(A)$$ sarà in $$R^n$$

### 1.5.3 Spazio riga

Questo spazio si ha tramite la transposizione della matrice, $$C(A^T)$$ sarà in $$R ^n$$

### 1.5.4 Spazio nullo della transposizione (o sinistro)

$$N(A^T)$$ sarà in $$R^m$$

## Ortogonalità

> Due spazi S e T sono ortogonali quando ogni vettore in S è ortogonale con ogni vettore in T. (una condizione necessaria è che l’unico vettore in comune sia 0v)
>

Due vettori o anche spazi, sono ortogonali quando il loro prodotto scalare è 0.

Questo è stato dimostrando facendo dei ragionamenti sul teorema di pitagora a lezione.

### Spazio riga e spazio nullo

Questi due spazi sono ortogonali fra di loro. Si può dimostrare ma non so esattamente come si fa....

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%207.png)

Come si vede in figura, x è ortogonale per ongi riga in quanto il prodo prodotto scalare è 0, e abbiamo dimostrato che se il prodotto scalare è 0 sono perpendicolari.

Si può definire il concetto di **complementi ortogonali** perché lo spazio nullo contiene tutti i vettori ortogonali allo spazio riga, non solo alcuni!

Nelle situazioni reali ci sono molti noise. ossia ho un sacco di misure per pochi parametri. Vorrei estrarre in qualche modo le informazioni utili, quindi avere una soluzione molto vicina, anche se non esatta.

Voglio dimostrare che $$N(A^TA) = N(A)$$, faremo dopo

### vettori ortonormali

Questi vettori saranno la base del nostro spazio (saranno fra le basi più carine!) (i calcoli diventano molto più carini, perché non vanno in underflow o overflow)

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%208.png)

Proprietà che deve andare a soddisfare.

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%209.png)

Come si può vedere il prodotto dà la matrice identità, come se Q fosse una matrice quadrata (dato che transpose per quadrata è uguale all’inverso, però qui Q non deve essere per forza un quadrato).

La proprietà che ho l’identità con quella moltiplicazione, mi semplifica molto la vita dei calcoli, in quanto l’equazione della proiezione diventa

$$x = Q^Tb$$, semplicemente, senza avere qualcosa in x.

### Gram-Schmidt

Questo calcolo (in qualche modo comune con l’eliminazione di Gauss) ci permette di avere dei vettori ortonormali partendo da due vettori a casso.

Gram ha contribuito con un ragionamento molto simile alla proiezione, se abbiamo due vettori, vogliamo trovare in qualche modo la proiezione, quella cosa perpendicolare! (dovrei fare un esempio o dimostrazione, ma sono pigro per scriverlo, spero che iol mio me futuro non mi uccida...)

Schmidt ha contruibuito alla normalizzazione delle matrici per averle ortonormali.

## Matrici Proiezioni

Posso creare delle matrici che mi calcolano delle proiezioni. Queste sono molto importanti perché l’equazione più vicina risolvibile sarà una sua proiezione su un piano multidimensionale.

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%2010.png)

La soluzione per trovare quel punto.

e si trova che


$$
x = \dfrac{a^Tb}{a^Ta}, p = ax, P = pb \implies  P = \dfrac{aa^T}{a^Ta} \\

\text{si nota in seguito anche che }\\ P = P^T \wedge P^2 = P
$$


e si trova che lo spazio colonna è proprio lo spazio che sto cercando... In poche parole viene qualcosa dimoslto carino...

### Formule importanti

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%2011.png)
o lo spazio che sto cercando... In poche parole viene qualcosa dimoslto carino...

### Formule importanti

[Spazi vettoriali (vecchio](/notes/spazi-vettoriali-(vecchio)%20c59484acce1c4c898b7c0d98e0e0f277/Untitled%2011.png)

# References