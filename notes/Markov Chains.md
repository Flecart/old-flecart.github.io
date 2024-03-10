---
layout: page
permalink: notes/markov-chains
tags: italian
title: Markov Chains
---

### Introduzione alle catene di Markov
#### La proprietà di Markov
Una sequenza di variabili aleatorie $$X_{1}, X_{2}, X_{3}, \dots$$ gode della proprietà di Markov se vale:


$$
P(X_{n}| X_{n - 1}, X_{n - 2}, \dots, X_{1}) = P(X_{n}|X_{n-1})
$$

Ossia posso scordarmi tutta la **storia precedente**, mi interessa solamente lo stato precedente per sapere la probabilità attuale.

Da un punto di vista filosofico/fisico, ha senso perché mi sta dicendo che posso predire lo stato successivo se ho una conoscenza (completa, (lo dico io completo, originariamente non esiste)) del presente.

#### La catena di Markov
È una successione di variabili aleatorie che possiede la proprietà di Markov. 
Solitamente lo rappresentiamo a grafi oppure tramite la matrice di transizione. A me piace più la versione a grafi
#### Catena di 3 variabili
Siano $$X, Y, Z$$ è chiaro che se viene formata la Catena di Markov $$X \to Y \to Z$$ allora deve valere

$$
p(x, y, z) = p(x)p(y|x)p(z|y)
$$

Altra cosa è che deve vare se e solo se $$X, Z$$ sono indipendenti, dato $$Y$$ ossia se vale

$$
P(x, z|y) = P(x|y)P(z|y)
$$

Che dovrebbe essere una conseguenza diretta della parte di sopra.
Una altra osservazione è che se vale quella catena, vale anche l'inversa, ossia $$Z \to Y \to X$$.
#### Data processing inequality
Se abbiamo una catena di Markov $$X \to Y \to Z$$ allora vale che 

$$
I(X ; Y) \geq I(X; Z)
$$

Perché una parte di computazione è possibile modellarlo con la catena di Markov. E mi sta dicendo che l'informazione comune all'input $$X$$ con  l'output $$Y$$ o output $$Z$$ dopo seguente computazione viene sempre meno con più computazione, e anche che non aggiungo informazione con più computazione.

**Dimostrazione**

### Definizioni Comuni

#### Raggiungibilità
Il nodo $$j$$ è raggiungibile da un nodo $$i$$ se esiste un numero di passi $$m$$, tale per cui

$$
P_{ij}^{m} > 0
$$

Molto più facile vedere sta cosa se lo rappresentiamo come un comunissimo Grafi|grafo|Grafi|grafo.

#### Classe di stati
Sono un insieme di stati tutti raggiungibili fra di loro (comunque presi due stati all'interno della classe, esiste un percorso che parte da uno e finisce sull'altro per dire).

#### Recurrent vs Transient
È *recurrent* se per ogni nodo, tutti i nodi raggiungibili da un nodo $$i$$ raggiungono anche il nodo $$i$$ stesso.
*Transient* se non è *recurrent*
Alcuni chiamano la *recurrent* come *irreducible* come in @coverElementsInformationTheory2012.

#### Periodic vs Aperiodic
Sia $$d$$ il massimo comune divisore per tutti gli $$m$$ tali per cui vale $$P_{ii}^{m} > 0$$ (ossia può raggiungere sé stesso con probabilità non nulla), allora è periodico se $$m \neq 0$$ altrimenti è aperiodico.

#### Ergodic Markov Chain

Una catena di markov si dice Ergodico se è *recurrent* e *aperiodico*.

Possiamo avere un teoremino carino su queste tipologie di catene, ed è più o meno il motivo per cui si chiamano ergodiche, ossia che una particella che segue questa legge prima o poi va a visitare tutti gli stati una volta. 
Abbiamo come teorema:

$$
P^{(M - 1)^{2} + 1}_{ij} > 0
$$

Con $$M$$ il numero totale di stati, e $$ij$$ qualunque stato iniziale o finale. Dimostrazione è un esercizio

#### Unichain
Una catena che continiene una **singola** classe *recurrent* più alcuni stati transienti

#### Chapman-Kolmogorov Equation
Alla fine è una relazione molto semplice, che deriva in modo facile dalle matrici di transizione, dice che
Sia $$P$$ una matrice di transizione per un processo di Markov, allora

$$
P^{n + m}_{ij} = \sum_{k = 0}^{N} P_{ik}^{n} P_{kj}^{m}
$$

Ossia posso moltiplicare matrici di transizione assieme per avere la probabilità di muovermi da uno stato $$i$$ a uno stato $$j$$ in $$n + m$$ passi.

### Convergenza

Ha senso pensare che una catena di Markov converga nel proseguire delle transazioni.

#### Teorema di convergenza per catene ergodiche
Questo è un teorema importante.


#### Convergenza per unichains ergodiche.

### Con rewards

Vogliamo associare a ogni stato $$i$$ un reward $$r_{i}$$
Si può creare allora una altra variabile aleatoria che prende la variabile aleatoria di Markov $$X_{i}$$ e lo mappa a un reward.
Quello che ci interessano di più sono le **expectation dei rewards**.

Noi vogliamo il valore


$$
E[R(X_{n})| X_{0} = i] = \sum_{j}r_{j}P_{ij}^{n}
$$

E per la proprietà di Markov credo sia la stessa cosa quando non parto da step 0.

#### Aggregate reward function
Questo è definito anche come **value function**in [Reinforcement Learning, a introduction](/notes/reinforcement-learning,-a-introduction).

$$v_{i}(n) = E[R(X_{m}) + \dots + R(X_{m + n - 1}) | X_{m} = i]$$

Se la catena è convergente, abbiamo che anche il value function è convergente a un valore preciso, ed è:


$$
g = \sum \pi_{j}r_{j} = \vec{\pi} \cdot \vec{r}
$$

Indipendentemente allo stato iniziale (che stupisce molto).

## Note di ripasso

| Data       | Commenti                                                                |
| ---------- | ----------------------------------------------------------------------- |
| 04/03/2024 | Non mi ricordavo cosa significasse periodico o aperiodico, o recurrent. |