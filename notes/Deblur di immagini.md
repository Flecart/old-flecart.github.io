---
layout: page
permalink: notes/deblur-di-immagini
tags: italian
title: Deblur di immagini
---

Ripasso Prox: 4
Ripasso: December 23, 2022
Ultima modifica: January 3, 2023 11:54 AM
Primo Abbozzo: November 17, 2022 11:22 AM
Stato: 🌕🌑🌑🌑🌑
Studi Personali: No

# Elementi di ripasso

# Immagini

## Introduzioni

### Origini di sfocatura

- Slide

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled.png" alt="image/universita/ex-notion/Immagini/Untitled">

1. Rumore causata da problemi fisici che sono **errori di lettura** del segnale analogico Questo si indica anche come errore gaussiano bianco e si può considerare *additivo*.
2. Rumore causato dalla digitalizzazione, quindi dalla discretizzazione di essa.
- Slide formalizzazione errori per sfocatura

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 1.png" alt="image/universita/ex-notion/Immagini/Untitled 1">


### Point spread function

Un unico pixel bianco sembra influenzare il suo ambiente nero, come in immagine

<img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 2.png" alt="image/universita/ex-notion/Immagini/Untitled 2">

Vorremmo utilizzare delle funzioni ce siano in grado di approssimare questa funzione.

- Funzioni solitamente utilizzate per approssimare e risultati

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 3.png" alt="image/universita/ex-notion/Immagini/Untitled 3">


### Convoluzioni

Questa cosa lo avevo già studiato credo per CNN, in AI. La prof lo scrive in modo molto incomprensibile, ma è la stessa cosa… Che cosa triste..

- Slides

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 4.png" alt="image/universita/ex-notion/Immagini/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 5.png" alt="image/universita/ex-notion/Immagini/Untitled 5">


### Ricostruzione immagini

<img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 6.png" alt="image/universita/ex-notion/Immagini/Untitled 6">

Ossia cerco di **identificare** le cause del blur, e da quello provo a tornare indietro

- Resto della slide

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 7.png" alt="image/universita/ex-notion/Immagini/Untitled 7">


Da tenere in mente il fatto che A è mal condizionata!. Vogliamo quindi introdurre alcuni metodi di regolarizzazione in modo da far diventare più gestibile questo problema. (quindi vorremmo avere una matrice equivalente che sia più gestibile).

TODO: vedere perché minimi quadrati è mal condizionato.

## Regolarizzazione

Andiamo ad utilizzare un **funzionale di regolarizzazione** con un **parametro** che mi indica quanto è influenza la funzione finale.

### Regolarizzazione Tiknohov e Morozov

- Slide riassuntiva

    <img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 8.png" alt="image/universita/ex-notion/Immagini/Untitled 8">


Di solito come funzione phi di x metto l’identità e come lambda un valore che scelgo provando tante cose e prendendo alla fine il più grande che mi soddisfa

<img src="/images/notes/image/universita/ex-notion/Immagini/Untitled 9.png" alt="image/universita/ex-notion/Immagini/Untitled 9">

e è l’errore causato dal blur

Si può saltare la regolarizzazione con le altre norme 💀 perché alla prof non piace, saddo.

### Peak signal to Noise Ratio

Quanto più il valore è alto più l’immagine è buona, questo è un buon parametro per valutare che la funzione di approssimazione sia buona.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |