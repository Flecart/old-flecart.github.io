---
layout: page
permalink: notes/teoremi-base-analisi
tags: en
title: Teoremi Base Analisi
---

Ripasso Prox: 75
Ripasso: June 22, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: November 11, 2021 5:41 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Fare attenzione alla dimostrazione di monotonia (stretta o lasca) nei casi in cui si può usare lagrange o meno (RIPETO IL FARE ATTENZIONE A STA COSA)
- Fare attenzione all'enunciato di fermat, lo ho invertito
- Vecchi dubbi
    - Teorema di permanenza del segno (enunciato)
    - DImostrazione del corollario di Lagrange
    - Ripetere le ipotesi del teorema di Fermat
    - Vedere se si ricorda come dimostrare tutti i teoremi
    - Monotonia funzioni!!!

# 6 Teoremi di analisi

## 6.1 Definizioni

### 6.1.1 Massimo minimo relativo (locale)

<img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled">

### 6.1.2 Massimo minimo assoluto

<img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 1.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 1">

## 6.2 Fermat

### 6.2.1 Ipotesi

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 2.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 2">


### 6.2.2 Note

Un pò intuitivamente, questo teorema ci sta dicendo che il valore della derivata in un punto di massimo oppure di minimo deve essere uguale a 0.

Bisogno fare attenzione che **il punto non deve essere sugli estremi** perché la derivata lì non è definita in modo sufficiente per soddisfare questo teorema.

- Dimostrazione

    Sono due casi diversi, ma con la stessa logica

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 3.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 3">

    La permanenza del segno è una dimostrazione per assurdo implicita, perché se si pone che il limite è minore di 0 allora per la permanenza del segno per gli X presenti in quell'intorno vale che è minore o uguale a 0!

    Stessa cosa per quell'intorno.


## 6.3 Rolle

### 6.3.1 Ipotesi

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 4.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 4">


### 6.3.2 Note

Ricorda l'esempio della montagnola per dare l'intuizione di questo teorema

**Dimostrazione**

Uso  weierstrass e posso dire che la funzione deve avere tutti i valori nel massimo e nel minimo.

Ci sono due casi, entrambi minimo e massimo sono estremi o uno dei due oppure uno dei due sono dentro l'intervallo, se sono dentro posso utilizzare fermat, invece la funzione è constante nel primo caso.

## 6.4 Lagrange

### 6.4.1 Ipotesi

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 5.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 5">


### 6.4.2 Osservazioni

Sembra che sia una generalizzazione di Rolle, in verità è come Rolle ma con il piano cartesiano girato, in questo senso possiamo intuire che siano **equivalenti**, poi si può anche provare a dimostrare (da Rolle si deriva lagrange e da lagrange si può derivare rolle).

**Dimostrazione**

Per la dimostrazione di questo teorema si vuole in qualche modo utilizzare il teorema di Rolle, quindi sarebbe buona cosa costruirsi una **funzione ausiliaria** in cui si possa utilizzare il teorema di Rolle.

### 6.4.3 Corollario costante

<img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 6.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 6">

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 7.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 7">


## 6.5 Cauchy

### 6.5.1 Ipotesi

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 8.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 8">

- Osservazione sull'ipotesi 3

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 9.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 9">


### 6.5.2 Osservazioni

La dimostrazione è molto simile a Lagrange, in quanto voglio costruirmi una funzione ausiliaria che soddisfi Rolle.

### 6.5.3 Legame con le altre funzioni

Si può notare che nel caso in cui la seconda funzione sia uguale alla funzione identità si può trovare la funzione di Cauchy senza nessun problema, si può dire che siano equivalenti

<img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 10.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 10">

Si può quindi dire che i due teoremi sono **equivalenti a livello logico** in quanto sostanzialmente mi dicono la stessa cosa, in forme diverse (seque dalla coimplicazione delle funzioni).

## 6.6 Monotonia funzioni

Ora si tende a correlare la crescita di una funzione al segno di una funzione.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 11.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 11">


### 6.6.1 Nota

Bisogna fare attenzione alla dimostrazione inversa.

Perché non si può utilizzare il teorema di Lagrange nello stesso modo con cui si va l'implica nella prima direzione. Per la seconda direzione bisogna utilizzare un assurdo con il teorema di permanenza del segno

### 6.6.2 Dimostrazioni

- Freccia in giù

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 12.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 12">

- Freccia in su

    <img src="/images/notes/image/universita/ex-notion/Teoremi Base Analisi/Untitled 13.png" alt="image/universita/ex-notion/Teoremi Base Analisi/Untitled 13">


## 6.7 Lo studio di funzione

### 6.7.1 I passi per l'analisi:

1. Studio del dominio
2. (Facoltativo) Studio di simmetrie
3. Studio dei limiti sulle frontiere del dominio
4. Studio della monotonia

# References