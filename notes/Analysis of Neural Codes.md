---
layout: page
permalink: notes/analysis-of-neural-codes
tags: italian
title: Analysis of Neural Codes
---

## Metodi di registrazione informazione
Ci stiamo chiedendo in che modo possiamo registrare attività del cervello e quindi cercare di fare decoding delle informazioni presenti
Prima parliamo di alcune tecniche non invasive che ci permettono di vedere alcune attività presenti nel cervello.
### Metodi macroscopici
#### Functional Magnetic Resonance Imaging
Un metodo è **fMRI**. (ci sono cose ) TODO capire come funziona

#### Electro-Encephalo-Gram
**EEG** che prende direttamente dai segnali 
Ma il drawback di entrambi è che **non registrano attività del singolo array**.

### Metodi a livello cellulare
#### Electrode arrays
Ci permette di registrare *voltaggi* di singoli neuroni (quindi capire se è in spike o meno). Solitamente si mette il tessuto cellulare direttamente su questo strato di elettrodi.

In modo simile si può anche misurare la differenza di potenziale studiata in [Campo elettrico](/notes/campo-elettrico), con una pipetta sonda, di solamente qualche micrometro di diametro, in modo da non danneggiare molto la membrana cellulare.

#### Calcium Imaging
Alcune cellule cambiano colore quando assorbono calcio, e si può utilizzare questo segnale visivo per capire se sta sparando o meno.


## Neural codes

Consideriamo una serie di neuroni su un array di elettrodi a cui è sottoposto a uno stimolo visivo. 
Utilizziamo un **raster plot** per capire il momento nel tempo in cui sparano, e otteniamo così un diagramma delle attivazioni di un neurone.

Vogliamo utilizzare un sistema probabilistico per gestire tutto sto rumore di così tanti neuroni. Una cosa tipo
1. Quant'è la probabilità che il neurone si attivi dopo questo stimolo? **encoding** (come viene memorizzato questo input).
2. Quant'è la probabilità che il neurone si attivi per questo stimolo? **decoding** (motivo per cui si è attivato diciamo).


Cosa interessante, se diamo rumore white a caso preso da una gaussiana, e poi prendiamo le risposte, queste risposte sono disposte in modo gaussiano.
Questo sistema con il gaussiano ci permette di trovare la **feature** ossia le attivazioni precedenti, il pattern diciamo, che contribuisce all'attivazione del neurone corrente.

## Note di ripasso

| Data | Commenti |
| ---- | -------- |
|      |          |