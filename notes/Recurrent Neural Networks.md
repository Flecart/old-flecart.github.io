---
layout: page
permalink: notes/recurrent-neural-networks
tags: italian
title: Recurrent Neural Networks
---

Ultima modifica: February 16, 2023 1:26 PM
Primo Abbozzo: February 16, 2023 12:57 PM

## Introduzione ai RNN

Vorremmo costruire un modello che fosse in grado di predire delle cose che dipendono da vecchie sequenze (quindi un network che abbia in un qualche senso la memoria di un coso passato).

- Riassunto in slide
    <img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled">


## Formalizzazione del network

### Stato interno

La differenza principale col percettrone è la presenza di uno stato interno nascosto, che continua a trasformarsi a seconda degli input, lo chiamiamo interno perché non è dato in output, ma viene se

!<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 1.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 1">

Schema classico di update dello stato interno

In pratica è come se ad ogni step ci siano due output: 1. la nostra predizione, uno l’update del nostro stato interno.

### Funzionamento classico

!<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 2.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 2">

Solitamente lo codifichiamo in modo molto semplice così:


$$
h_{t} = g(Uh_{t-1} + Wx_{t})
$$


$$
y_{t} = f(Vh_{t})
$$

Dove $$U, V, W$$ sono matrici di pesi allenabili, e $$g, f$$ sono funzioni di attivazione (questo è leggermente diverso rispetto a quanto in figura qui)

- Codice classico per RNN
- **Cell state:** The cell state is a vector that is maintained by the LSTM cell and is used to store information over time.
- **Gates:** LSTMs use three gates to control the flow of information into and out of the cell state:
    - **Forget gate:** The forget gate determines which information from the previous cell state to discard.
    - **Input gate:** The input gate determines which new information to add to the cell state.
    - **Output gate:** The output gate determines which information from the cell state to output.
- **Backpropagation through time (BPTT):** LSTMs use a variant of BPTT called truncated BPTT to train the network. BPTT is a technique for training recurrent neural networks by unrolling the network through time and calculating the gradients of the loss function with respect to the parameters of the network. Truncated BPTT is a simplified version of BPTT that is more computationally efficient.

### Training a RNN

Questo è più o meno il pseudocodice per l’update della RNN

1. Far andare per t timestamps, e trovare un loss generale.
2. Utilizzare questo per fare backpropagation.
- Schematizzazione della backpropagation sul tempo

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 4.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 4">


TODO: problemi sui gradienti e Long-termi dependence.

### Vanishing gradient problem

Per exploding gradients la cosa bella è una soluzione veloce, come fare gradient clipping (che non so che cazzo sia)

Per vanishing gradient ho molte più soluzioni possibili

1. Activation function
2. Weight initialization
3. Custom gate cells

Una cosa buona (quindi tipida di questo RNN sono le gated cells, che riescono a controllare molto meglio il flow dell’informazione).

- Proprietà di LSTM

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 5.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 5">


### Word embeddings

**One-hot embedding**

Quando ho un array tipo di 10k, e il valore di una parola è [0, 0…., 1, 0,… 0] con 1 il suo index giusto.

**Learned embedding**

Quando lasciamo una NN a capire come fare un encoding delle parole, in modo che parole simili abbiano una distanza minore, anche se sarebbe molto meglio avere qualcosa di pratico per sta roba 😀

### Limitations of RNN

1. Encoding delle informazioni (che ci potrebbero far perdere certe informazioni molto carine a riguardo)
2. Lentissimo! Non riesco a parallelizzare questa computazione, dato che uno dipende dall’altro!
3. Alla fine non riesco proprio a fare **long term memory**.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |


Utili per modelizzare delle sequenze.

### Struttura

Lo stato interno che va passato avanti

### Caratteristiche principali

!<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled">

## Encoding

!<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 1.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 1">

Anche representation learning.

### Backpropagation through time

- Slide

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 2.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 2">


**Common problems**

- Vanishing gradiends ( con molti valori  < 1)
- Exploding gradiends

La ragione per cui succede è perché utilizzo $$W_{hh}$$ un sacco di volte su se stessa, quindi ci sono questi problemi i calcolo numerico.

## Long term dependecies

Perché ho problemi a mantenere informazioni molto distanti.

### Activation function

eg. Using ReLU function che manda funzione su

### Parameter initialization

??

### Gated Cells LSTM

slectively add or remove in each recurrent unit. → **LSTMs (Long Short Term Memroy**).
- LSTM What is does
    3 → more stable algo


## Application and limitation of RNN

### Examples

- Music generation

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 4.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 4">

- Classification with sequences

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 5.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 5">


### Limitations

1. : Encoding bottleneck (deve essere in una forma che possa gestire!!!)
2. 🕗 No parallelization (quindi difficoltà del calcolo!!)
3. Not long memory (max circa 100 con LSTM, ma non di più).

**Solution**

1. Continuous stream!
2. Faster, with parallelization (cant with recurrence)
3. Long memory!

We can **concatenate** the input in a feature vector! (solves recurrence + parallelization, but not scalable).

- Feed to dense network

    <img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 6.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 6">


## Transformers

Sono una cosa molto importante!! → **attention mechanism**. (features from regions with high attention, its a search problem) (**attention mask** over the keys).

<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 7.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 7">

High level of attention mechanism with transformers

- In brief → architecture of trasformer mechanism

    <img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 8.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 8">

- Some application of self-attention trasformers

    <img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 9.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 9">


- Summary of lecture

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 10.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 10">


# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
on trasformers

    <img src="/images/notes/Recurrent Neural Networks/Untitled 9.png" alt="Recurrent Neural Networks/Untitled 9">


- Summary of lecture

    !<img src="/images/notes/image/universita/ex-notion/Recurrent Neural Networks/Untitled 10.png" alt="image/universita/ex-notion/Recurrent Neural Networks/Untitled 10">


# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |