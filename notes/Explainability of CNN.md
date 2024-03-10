---
layout: page
permalink: notes/explainability-of-cnn
tags: italian
title: Explainability of CNN
---

Ultima modifica: April 4, 2023 6:19 PM
Primo Abbozzo: April 1, 2023 11:11 AM
Studi Personali: No

# Elementi di ripasso

# Explainability of CNN

## Introduction

Capire in che modo una rete convoluzionale ci può dare insight migliori su come funzionano questi networks.

### Visualizzazione dei hidden layers

- Slide visualization

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled">


Potremmo fissare una immagine anche a caso, e modificare la x in modo che sia più simile a quanto vuole computare il neurone. In questo modo genero una immagine che generi una activation forte nel neuron trainato, e si potrebbe dire che sia il genere di immagine che viene generata da essa.

Forse questo è anche il metodo con cui vengono generate le immagini??

- Examples of extracted patterns

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 1.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 1">


Probabilmente tutte le CNN vanno quindi a tentare ad estrarre questo genere di patterns dall’immagine iniziale.

### Ricreazione di immagini

Vogliamo **computare la rappresentazione interna dell’immagine**, ossia l’attivazione prodotta da una certa immagine, e da questo possiamo sintetizzare una immagine e poi continuare a fare gradient descent su questa per massimizzare. Una volta al minimo dovremmo avere l’immagine migliore per questo layer.

- Slide di esempio

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 2.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 2">

    Per un certo layer non c’è differenza fra quei 6 immagini


Quindi prima partivamo da noise, da questo partiamo da una immagine già e guardiamo in che modo è rappresentato in questo layer.

- Slide sulla tecnica di solito utilizzata per queste

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 3.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 3">


Si puònotare che è **più difficile recovery dell’immagine nei layers lontani**, probabilmente perché sta creando una specie di astrazione dell’immagine iniziale, quindi l’immagine sarebbe l’immagine dell’astrazione. Riusciamo a visualizzare una astrazione, che sembra una contraddizione.

## Inceptionism

## Style transfer

Come facciamo a ricreare una immagine utilizzando lo stile di un certo autore?

- Esempi di risultati con style transfer

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 4.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 5.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 5">


Ma come facciamo a catturare un concetto astratto di stile di un certo autore?

### Concetto di stile di un autore

Non vogliamo solamente avere un contenuto simile (come abbiamo fatto prima, nei primi layers è una cosa abbastanza semplice) vorremmo proprio essere in grado di **catturare lo stile dell’artista**. Quindi da un punto di vista astratto

- Slides stile autore

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 6.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 6">


Ci interessa la **correlazione fra features maps** di un certo livello, e quando abbiamo una immagine vogliamo allenare per massimizzare la similitudine con la correlazione fra le feature maps.

## Data manifolds

### perché facile ingannare le reti

Si può vedere che con le tecniche dello stile si possono **ingannare molto facilmente le reti** di sopra. Questo è perché fanno delle classificazioni, fanno discriminazione anziché generazione. Ossia con generazione provo a stimare la probabilità iniziale che si sia creato la cosa che vogliamo classficiare e con questa probabilità poi andiamo a fare la predizione.

Invece nelle tecniche discriminazione vanno solamente a fare una discriminazione di dati, una cosa statistica. (la frontiera può essere molto diversa rispetto alla funzione che lo ha generata diciamo.

Seguendo comunque il ragionamento sui manifolds di data possiamo dire che **è molto improbabile ~0, che generando a caso, sia una immagine sensata**. Infatti lo spazio delle immagini è enorme, la maggior parte sono ranodm per umani, però stiamo provando a fare questo un modello di discriminazione (quindi è chiaro che molte zone che per noi non hanno senso, sono rappresentate nella rete neurale come categorizzate in un certo modo).

### Autoencoders

Vogliamo cercare di cambiare lo spazio in modo che la parte delle immagini sensate sia meglio descrivibile, vogliamo andare in pratica a creare una descrizione compatta di quello che vogliamo analizzare. Con gli autoencoder andremo proprio a **comprimere il data manifold** e poi lavorare su questa compressione.

- Slide intuizione autoencoder

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 7.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 7">

    Quello che vorremmo fare è una funzione identità per certe cose (dato che sono meno, non possiamo fare altro che perdere altre informazioni, ma vogliamo solamente perdere informazioni che non ci servano).


**Possiblità della compressione**

La compressione dovrebbe essere possibile perché **stiamo cercando regolarità nel data**, cosa che ci dovrebbe essere perché noi umani riusciamo a riconoscere questi pattern, non riusciamo ad insegnarlo ad una macchina. (quando è molto random però non si può comprimere, stranamente il random è la cosa con più informazione in termini di teoria dell’informazione, ma meno informazione per noi umani, che strana questa asimmetria).

**Caratteristiche della compressione**

- Slide caratteristiche

    <img src="/images/notes/image/universita/ex-notion/Explainability of CNN/Untitled 8.png" alt="image/universita/ex-notion/Explainability of CNN/Untitled 8">


La cosa di maggior rilievo è il fatto del **loss**, che non riusciamo a fare un reverse che diventi proprio uguale! E poi funziona solamente con data simili (con caratteristiche fortemente correlate fra di loro.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
 diventi proprio uguale! E poi funziona solamente con data simili (con caratteristiche fortemente correlate fra di loro.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |