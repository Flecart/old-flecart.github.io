---
layout: page
permalink: notes/reti-convoluzionali
tags: italian
title: Reti convoluzionali
---

Abbiamo trattato i modelli classici in [Convolutional NN](/notes/convolutional-nn). Con i vecchi files di notion
### Il Kernel
I punti interessanti delle immagini sono solamente i **punti di cambio** solo che attualmente siamo in stato discreto, quindi ci è difficile usare una derivata, si usano kernel del tipo:
$$\left[ 1, 0, -1 \right]$$, che sarà positivo se cresce verso sinistra, negativo se scende.
<img src="/images/notes/Reti convoluzionali-1700037160855.jpeg" alt="Reti convoluzionali-1700037160855">

#### feature map
Sono delle mappe che rappresentano alcune informazioni interessanti della nostra immagine.

## Principi di base
### Nota sulla depth
Come viene spiegato in @cohenExpressivePowerDeep2016 shallow e deep sono equivalenti, ma c'è una esplosione esponenziale sul numero di neuroni necessari

### Caratteristiche di convoluzionali
#### Località, Condivisione, Invarianza per traslazioni
Località perché ho una field of view, che è la grandezza del kernel precedente, condivisione perché i pesi del kernel sono sempre gli stessi.
Poi non ho capito perché il pooling fa invarianza per traslazioni.