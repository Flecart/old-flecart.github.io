---
layout: page
permalink: notes/minimi-quadrati
tags: italian
title: Minimi quadrati
---

Ripasso Prox: 20
Ripasso: February 9, 2023
Ultima modifica: January 2, 2023 10:14 AM
Primo Abbozzo: October 19, 2022 4:17 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

# Minimi Quadrati

## Note matematiche introduttive

### Vettori ortonormali 🟩

Due vettori si dicono ortonormali se $$vv^T = ||v|| = 1$$ e sono ortogonali, ossia $$v_i v^T_j = 0$$ con i e j diversi fra di loro

### Matrici ortogonale (4) 🟩-

> Matrici si dicono ortonomali se le sue colonne sono vettori sono ortonormali
>
1. Matrici ortonormali sono **isometrie**, cioè mantengono le distanze.
2. Queste matrici sono tutte non singolari e quadrate per definizione
3. La sua inversa è ortogonale
4. La sua inversa è uguale alla trasposta
- slide Proprietà matrice ortonormale

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled">


## Minimi quadrati lineari

### Introduzione al problema

Sappiamo che non esiste una soluzione esatta per sistemi di equazione lineare che più equazioni che soluzioni. Si può concludere che la soluzione a questo problema (in slide) esiste sempre ed è unica se $$k = n$$, se è minore ci sono infinite soluzioni.

- Slide introduzione

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 1.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 1">


Ossia mi interessa solamente **l’ascissa** del minimo, ossia

$$\argmin ||Ax - b||$$, cercando la x.

### Soluzione con equazione normale 🟨

Questo si può fare solamente se $$k = n$$

- Teorema, soddisfacimento delle equazioni normali è sufficiente per trovare una soluzione

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 2.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 2">


In questo caso **esiste una soluzione unica**.

- Soluzione equazione normale

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 3.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 3">

    nota ci sono errori sia sulla trasposta che sul gradiente in immagine

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 4.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 4">


- In breve

    Fare il gradiente della funzione ed eguagliarlo a 0, perché solo se ho 0 ho il punto di minimo di questa funzione convessa della norma


### Singular Value decomposition 🟩

Di solito è utilizzata per **ridurre lo spazio utilizzato** trattenendo la maggiore quantità di informazione possibile, utilizzata spesso in Principal Component Analys

- Enunciato SVD slide

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 5.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 5">

- Immagine esplicativa

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 6.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 6">


Questo è qualcosa che si può applicare a **qualunque matrice**. Sono di particolare interesse le matrici con numero di colonne maggiore del numero di righe.1

- Slide vecchia

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 7.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 7">


### Relazione valori singolari con AAt 🟩-

Con k ho il numero di numeri non zero che sono il **rango della matrice**. Questa matrice è particolare, la chiamiamo gramiano ed è sempre definita positiva.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 8.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 8">


Quindi i **valori singolari** che sono gli autovalori della matrice $$A^TA$$ sono

1. $$\geq 0$$
2. $$\in \R$$
3. se k è il rango di $$A$$, ho k elementi diversi da 0.

Il motivo per cui succede quanto sopra è perché è come se stessi facendo il cambio di base per trovare una matrice diagonale! [Cambio di Base e Autovalori](/notes/cambio-di-base-e-autovalori), e non c'è nessuna relazione altra fra la matrice di A e il valore singolare, deve essere con AAt!

- Relazione molto importante (!!!!!)

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 9.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 9">


### Vettori singolari sinistri e destri 🟩

Definiamo in questo modo i vettori associati a $$\sigma_i$$ che formano una base ortonormale rispettivamente di $$R^m, R^n$$. E in particolare sono le colonne delle matrici $$U, V$$

NOTA: è molto probabile che la relazione sotto che lega vettori singolari sinistri e destri sia errata
perché sulla pagina di wiki u e v sono invertite. È più importante il fatto che i vettori singolari sinistri e destri sono rispettivamente **autovettori di AAt e AtA**.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 10.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 10">


### Decomposizione diadica 🟥+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 11.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 11">


In pratica con la decomposizione a valori singolari, e utilizzando i vettori singolari si può dimostrare che


$$
A = U\Sigma V^T = \sum_{i=1}^k \sigma_iu_iv_i^T
$$


Espandere questi calcoli è abbastanza easy creddo, perché la matrice di mezzo è molto semplice da gestire. L’intuito per sta parte (che è l’unica cosa di cui si è preoccupata di spiegare) è che è utile qui il concetto di un **prodotto esterno** che po

### Risoluzione minimi quadrati con SVD 🟨+

- Enunciato teorema

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 12.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 12">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 13.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 13">

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 14.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 14">


### Regressione Polinomiale (!)

Abbiamo un insieme di dati, vogliamo creare un algoritmo che stimi la funzione migliore per approssimare i dati.

Siano dati un insieme di punti $$(x_i, y_i)$$, sia un polinomio p così definito

$$p(x) = \sum_{i =0} ^m c_ix^i$$, vogliamo andare a definire per bene i valori dei coefficienti in modo che **aderiscano** ai dati.

Per fare questo, in pratica è la risoluzione di certi errori.

In pratica mi costruisco la matrice di vandermonde per tutti gli input di dati, di n numero di colonne, con n l’esponente massimo del polinomio che voglio andare ad approssimare.

Poi faccio cose per minimizzare l’errori di questo e lo possono fare con SVD o minimi quadrati (nel cosi in cui il rango fosse giusto).

Importante per questa parte la **matrice di vandermonde**.

### Pseudo inversa (4) 🟥

- Slide

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 15.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 15">


Questa definizione ci permette di scrivere il problema dei minimi quadrati in modo più clean, infatti la soluzione della SVD diventa

$$x = V\Sigma^+U^Tb = A^+b$$, come se stessi prendendo l’inversa 😀, quindi ci permette di semplificare questa notazione.

Si può notare che **l’inversa** possiede tutte le proprietà della pseudoinversa.

In soldoni: inverto le matrici di vettori singolari e inverto tutti i valori singolari (prendo iil loro reciproco).

Importanti sono alcune loro proprietà (hermitiana per AA* e A*A, ossia simmetrica, inversa debole e l’altra boh).

Secondo la definizione di [moore-penrose]([https://en.wikipedia.org/wiki/Moore%E2%80](https://en.wikipedia.org/wiki/Moore%E2%80)%93Penrose_inverse) quelle 4 proprietà sono sufficienti per una pseudoinversa, in questo caso abbiamo la pseudoinversa della SVD, che è una cosa leggermente diversa (cioè istanziazione specifica della pseudoinversa).

### Condizionamento in LSQ (non fare)

> Questa sezione ha cose da ricordare a memoria (già leggermente presentate in precedenza) quindi non ha molto senso dare attenzione a sta roba brutta, imparare poi a memoria il costo dei vari argoritmi bruuh
>

Vogliamo in questa sezione andare ad indagare quanto influenza il numero di condizione tutte le tecniche che abbiamo introdotto in questo capitolo.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 16.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 16">

    <img src="/images/notes/image/universita/ex-notion/Minimi quadrati/Untitled 17.png" alt="image/universita/ex-notion/Minimi quadrati/Untitled 17">


Da ricordarsi di [Norme e Condizionamento](/notes/norme-e-condizionamento), che il condizionamento ci dice quanto cambia la soluzione quando cambio i dati (la b)



# References