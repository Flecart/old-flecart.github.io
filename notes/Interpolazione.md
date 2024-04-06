---
layout: page
permalink: notes/interpolazione
tags: italian
title: Interpolazione
---

Ripasso Prox: 21
Ripasso: January 1, 2023
Ultima modifica: January 2, 2023 10:49 AM
Primo Abbozzo: October 26, 2022 4:45 PM
Stato: 🌕🌑🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

# Interpolazione

Vogliamo in questa sezione andare ad indagare la costruzione di funzioni che passano in tutti i punti che vogliamo, appunto interpolare. La funzione è molto simile alla regressione trattata in [Minimi quadrati](/notes/minimi-quadrati) (con il metodo della regressione, chiamato anche approssimazione ai minimi quadrati).

Quindi mentre la precedente voleva andare a minimizzare l'errore, questo attuale va a creare proprio da 0 la funzione che ci passa sempre.

## Introduzione

Andremo a creare una funzione f tale che per ogni x in input si abbia **esattamente** la y in output

### Metodi di interpolazione (3) 🟩

<img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled.png" alt="image/universita/ex-notion/Interpolazione/Untitled">

In questo corso utilizzeremo solmanete l'interpolatore polinomiale!

## Interpolazione polinomiale

### Enunciato e unicità 🟩
- Enunciato
    <img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 1.png" alt="image/universita/ex-notion/Interpolazione/Untitled 1">


Da notare che il grado della funzione è esattamente il numero delle y.

- Dimostrazione dell’unicità
    <img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 2.png" alt="image/universita/ex-notion/Interpolazione/Untitled 2">


### Polinomi di Lagrange e costruzione 🟩
- Costruzione del polinomio di interpolazione
    <img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 3.png" alt="image/universita/ex-notion/Interpolazione/Untitled 3">


In soldoni, mi sto costruendo molteplici funzioni che nel mio punto assumono il valore che voglio e in tutti gli altri punti sono nulli. Costruisco n funzioni per gli n input e li sommo assieme. Questa funzione qui mi basta per interpolare il tutto.

Importante in questa sezione capire cosa è la notazione.

$$\varphi_k(x_i)$$ è il **polinomio di lagrange** che per xi, con i = k è 1, altrimenti è 0.

In particolare è costruito in questo modo:


$$
\varphi_k(x) = \prod^n_{j =0, j\neq k} \frac{x - x_j}{x_k - x_j}, \forall k \in \{0, ..., n\}
$$


$$\Pi_n(x)$$ è la funzione di interpolazione costruita come


$$
\Pi_n(x) = \sum_{i = 1}^n y_i \varphi_i(x)
$$


### Teorema del resto d'interpolazione 🟥

- Slide della prof
<img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 4.png" alt="image/universita/ex-notion/Interpolazione/Untitled 4">


<img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 5.png" alt="image/universita/ex-notion/Interpolazione/Untitled 5">
<img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 6.png" alt="image/universita/ex-notion/Interpolazione/Untitled 6">


**Note e osservazioni**
Faccio finta di prendere i punti da una funzione già esistente e voglio in questo caso cercare di valutare quanto buona sia l’interpolazione.

la funzione più a destra mi dà una stima dell'errore della funzione di interpolazione.

**Esempio funzione di runge**
Questa funzione mostra come con l’aumentare del grado del polinomio, la precisione del polinomio di interpolazione non aumenta, anzi **diminuisce! L’errore cresce** con più punti.

<img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 7.png" alt="image/universita/ex-notion/Interpolazione/Untitled 7">


Ad intuito la funzione d’interpolazione oscilla, se ho un insieme di punti equidistanti non gli sto dando spazio per oscillare indietro.

- Esempio grafico runge
    <img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 8.png" alt="image/universita/ex-notion/Interpolazione/Untitled 8">


### Nodi di chebicheff 🟥

Questo è un modo intelligente per prendere i nodi, in modo che si risolva il problema dell’equidistanza e dando al poliminio spazio (non so poi perché dargli spazio risolva ciò).

Con n → inf, l’errore tende a zero! Quindi la **convergenza dell’interpolazione DIPENDE DAI PUNTI** scelti. (questo chiaramente non va sui dati random che troviamo in ambiente, quindi è molto inutile il metodo dell’interpolazione per altra roba, inoltre staremmo seguendo il rumore dei dati).

- Slide nodi di chebicheff-Gauss-Lobatto

    <img src="/images/notes/image/universita/ex-notion/Interpolazione/Untitled 9.png" alt="image/universita/ex-notion/Interpolazione/Untitled 9">


### Interpolazione a tratti 🟩

Dato che non ci conviene di interpolare troppi punti vogliamo spezzare l’interpolazione a tratti! E inoltre per avere una regolarità **impongo uguaglianza delle derivate 1 e 2** evitando spigoli nelel funzioni finali.

Ma questo è quanto ci vuole insegnare a riguardo la prof. quindi mi fermo in questo punto per questi appunti.



# References