---
layout: page
permalink: notes/neural-networks
tags: italian
title: Neural Networks
---

Ripasso Prox: 10
Ultima modifica: May 6, 2023 5:55 PM
Primo Abbozzo: February 16, 2023 3:04 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

## Introduction: a neuron

Questi sono cosettini ispirati dalla struttura dei neuroni nel nostro cervello, ma mi sembra di aver sentito che alla fine non c’entrino proprio niente.

### Structure

1. Linear + activation

In pratica possiamo dire che un neurone in questa parte di AI è una funzione lineare (quindi che non fa altro che $$w^Tx + b$$ di solito indicata con $$z$$) ossia moltiplicazione lineare, e poi una funzione non lineare tra 0 e 1 che mi indica o meno se la cosa è attivata o meno.

### Model

Architecture and parameters (the weights), identify a model.

## Training network tricks

### Activation functions

Solitamente le funzioni classiche per i network neurali sono sigmoid, tanh, e ReLU. La cosa brutta delle prime due è **vanishing gradient**, perché se il valore è molto grosso o molto piccolo, la derivata è molto vicino allo 0, quindi è molto difficile aggiornare.

Invece ReLU si comporta meglio da questo punto di vista, perché la sua derivata è 0 se minore di 0 1 se maggiore.

### Input normalization

In un certo senso in questo modo abbiamo un pò di tati che sono Normali gaussiani. Non ho capito ancora perché normale gaussiana sia una tipologia di dati che ci piace così tanto. (il motivo che viene dato [in lezione]([https://www.youtube.com/watch?v=zUazLXZZA2U&list](https://www.youtube.com/watch?v=zUazLXZZA2U&list)=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU) è che Gradient Descent si comporta molto meglio per loss function che sono gaussiane, perché la direzione di discesa è sempre quella, e non deve zigzagare).

### Weight initialization

Ci sono moltissimi modi per inizializzare i Weights, in modo che si eviti il problema di vanishing or exploding gradients. L’idea è comunque tenere i valori vicini a 1 per evitare che esplodino, e inversamente proporzionali a n o funzioni di n, perché se n è molto grosso potrebbe esplodere lo stesso.

Alcune inizializzazioni famose sono

- Xavier
- He
- (qualcosa che funziona per Sigmoid, (alcune funzionano a seconda dell’activation function giusta)

C’è ne sono molte, non so se conviene lavorare sulla inizializzazione, non credo sia comunque buona spesa del tempo a capire queste.

### Optimization

Momentum, praticamente un gradient descent che tiene conto delle computazioni passate, e calcola la direzione anche secondo quelle (quindi se vado su e giù e a destra sempre nelle iterazioni passate, andrò a destra più spesso diciamo, questa è l’intuizione per questa idea).

Una cosa molto strana è che il training delle NN è molto stabile. Cioè vari un pò l’input e non varia molto l’ouput!

Possibili motivi:

1. Weights
2. Loss function
3. Internal redundancy? cioè ho troppi parametri e questo lo rende bello.(teoria del prof)

### Overfitting

- Slide ways to reduce overfitting 7

    <img src="/images/notes/image/universita/ex-notion/Neural Networks/Untitled.png" alt="image/universita/ex-notion/Neural Networks/Untitled">


Overfitting è il drago del training classico del machine learning, molto simile a dire che la macchina sta **allucinando alcuni pattern** causati probabilmente dalla varianza dei dati, o anche dal fatto che alcuni casi positivi sono pochi…

È comunque una cosa troppo specifica, perché significa che la macchina stia quasi imparando a memoria i casi,  dovrebbe provare a generalizzare, per farlo deve scordare dettagli non interessanti (che con overfitting può imparare) e imparare le cose importanti. Però i computer sono troppo bravi a memorizzare dettagli, a differenza di umani.

- Idea del dropout

    <img src="/images/notes/image/universita/ex-notion/Neural Networks/Untitled 1.png" alt="image/universita/ex-notion/Neural Networks/Untitled 1">


L’idea è il fatto che il network deve risolvere il problema, anche se è un pò rotto, questo cerca di renderlo più robusto, e sembra funzionare molto bene.

### Kullback-Leibler Divergence

We want to measure the **distance between two** distributions, usually from a real distribution and the one we are predicting.
Vedere Entropy#Relative Entropy or Kullback-Leibler
    


È una cosa che proviene dalla teoria dell’informazione.

Per capire questo, è molto importante andare a capire cosa sia la **cross-entropy** e questo è un modo abbastanza naturale per capire quanto vicino è una distribuzione, solitamente predetta, con quella del training data, si può comparare molto con **log-likelihood** loss function, si potrebbe dire che sia un caso particolare la log likelihood.

# Registro ripassi

| 01/04/23 | Non ci sto facendo troppa attenzione. |
| --- | --- |
|  |  |
|  |  |
tion, si potrebbe dire che sia un caso particolare la log likelihood.