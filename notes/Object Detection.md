---
layout: page
permalink: notes/object-detection
tags: en
title: Object Detection
---

Ultima modifica: April 16, 2023 4:23 PM
Primo Abbozzo: April 8, 2023 9:34 AM
Studi Personali: No

# Elementi di ripasso

# Object Detection

## Introduction

### Semantic segmentation

Vorremo trovare **regioni che corrispondano a categorie diverse**. E dividere in questo modo l’immagine secondo zone di informazione.

### Object detection

Vogliamo trovare **il più piccolo box** che vada a contenere l’oggetto. Questo è fatto con il **bounding box**.

In questo caso la funzione di loss è un pò più difficile da definire, si utilizza la funzione **intersection over union** con le aree, in pratica la percentuale di immagine comune diciamo.

### Deep object detection (2)

Region proposals

Questa è una versione che prova a catturare le regioni di interesse all’interno della nostra immagine. (più o meno non sa cosa sia l’oggetto, ma sa che c’è qualcosa in quella zona). Poi questa regione di interesse è passata in un secondo step che va a riconoscere cosa è presente in quella immagine. (la regione di interesse era presente anche prima di CNN).

SIngle shots

Questi sono più veloci dei precedenti, quindi sono buoni per applicazioni real time.

## YOLO

### You Only Look Once intro

[https://pjreddie.com/darknet/yolo/](https://pjreddie.com/darknet/yolo/)

[https://towardsdatascience.com/yolo-v4-or-yolo-v5-or-pp-yolo-dad8e40f7109](https://towardsdatascience.com/yolo-v4-or-yolo-v5-or-pp-yolo-dad8e40f7109)

Prova a trovare il bounding box con la predizione con una singola passata! CNN per individuare i boxes, poi algoritmicamente per cancellare i boxes.

### Main Idea

**FUNZIONAMENTO**

Fa delle predizioni, che sono dei bounding box con dei labels (espressi attraverso una probabilità).

Dopo avevi un certo numero di neuroni dopo aver fatto downsampling (queste hanno visisione solamente di una zona limitata dell’immagine).

L’idea principale è **allenare il singolo neurone** a riconoscere l’oggetto (wtf hoooow). E ignorare tutti i resti dei neuroni (si fa con una mask in qualche modo).

### Output format

- Slide formato dell’output

    <img src="/images/notes/image/universita/ex-notion/Object Detection/Untitled.png" alt="image/universita/ex-notion/Object Detection/Untitled">


Si deve tenere molte informazioni (i punti, lo score, e un valore di score per tutte le classi).

Solitamente si parte da un **anchor box** di dimensioni fisse (width e height). I valori di ritorno sono un displacement dal centro in entrambe le direzioni e un fattore di deformazione per ogni direzione.

### Loss function

- Localization loss function

    <img src="/images/notes/image/universita/ex-notion/Object Detection/Untitled 1.png" alt="image/universita/ex-notion/Object Detection/Untitled 1">


La loss di localizzazione non è altro che una differenza

Nota: c’è una binary map, che che è in una cella e 0 in tutto il resto (questo per dire che il neurone vuole predire solamente quello che gli sta intorno, il resto lo ignora tutto).

- Classification loss

    !<img src="/images/notes/image/universita/ex-notion/Object Detection/Untitled 2.png" alt="image/universita/ex-notion/Object Detection/Untitled 2">




# References