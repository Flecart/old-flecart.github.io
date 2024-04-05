---
layout: page
permalink: notes/optimization-methods
tags: en
title: Optimization methods
---

Metodi altri sono trovare una **approssimazione** facile da calcolare (simile all'approccio del modello surrogato credo).
Ma nel nostro caso proviamo a trovare metodi di esplorare lo **spazio dei parametri** in modo intelligente.

### Deterministic methods

Sono utilizzabili quando ci sono delle proprietà come convessità, limitatezza, continuità.

#### Newton Raphson method
Molte implementazioni in R usano questo metodo, è 
- Perfetto quando $$h$$ è quadratico, e in statistica molti problemi sono quadratici e funziona in modo perfetto
- Ma in cose non lineari si ha meno performance (perché l'hessiana è molto instabile per l'inversione, si dice che è mal condizionata, e si fa con attenzione.)

l'unica cosa da sapere secondo me è 


$$
f(x) = x - H^{-1}\nabla f(x)
$$


### Stochastic methods

#### Stochastic search
In pratica faccio uniform su tutto il dominio, e tengo il maggiore come la soluzione, solo che
1. Difficile da calcolare
2. Soffre di problemi di scaling
3. Ha bisogno che la funzione sia facile da valutare.

La caratteristica negativa è che spende tempo anche per zone di poco interesse, perché dà stessa importanza a tutto.
Sarebbe buono provare a fare sampling in modo proporzionale al valore di $$h(\theta)$$

Max of function = **mode** of the distribution, if that is a density! Quindi se faccio sampling usando quella funzione come densità riesco a trovare il massimo!

#### Stochastic gradient methods
È una categoria di algos.
#### Random walk
We use the gradients to guide the search.
Un esempio è solamente fare una cosa così 

$$
\theta_{j+1} = \theta_{j} + \varepsilon_{t}
$$

In cui $$\varepsilon$$ è una variabile aleatoria, questo è anche una catena di markov.
Questo è un **random walk** approach. (che è stupido perché comunque non sto utilizzando nessuna informazione sulla funzione!)

#### Gradient descent
Questo lo sai.
Solo che in questo caso viene fatta una sequenza di pesi (non è un learning rate)...
Solo che soffre molto facilmente sulla possibilità di stuck su minima o maxima.

C'è anche una versione **stocastica**, in cui si una una versione approssimata del gradiente (che strano, di solito questa informazione è disponibile). (si utilizza la definizione di gradiente in pratica, quindi si usa una variabile random sullo step...)


$$
\nabla h(\theta) \approx \frac{h(\theta_{j} + \beta_{j} \gamma) - h(\theta_{j} - \beta_{j} \gamma)}{2\beta_{j}}
$$

in cui ho di nuovo una sequenza di $$\beta$$ che mi definisco io, solo che $$\gamma$$ è sampling da sfera unitaria, è un tentativo di perturbare la discesa, in modo da non essere stuck in minimi o massimi locali.

Poi l'update diventa


$$
\theta = \theta - \frac{\alpha_{i}}{2\beta_{i}} \nabla h(\theta)\gamma
$$



### Simulated Annealing

**Boltzmann-Gibbs transform** quando proviamo in local search un sampling basato su local search minima.

We want to sample a sequence proportional to the time! $$\propto \frac{\exp(h(\theta))}{T}$$ 

Solitamente per fare questo si fa 

$$
\pi_{i}(\theta) \propto L(0)^{T} \pi_{0}(\theta)
$$

Dove $$\pi_{0}$$ è la distribuzione di densità iniziale, mentre l'altro è una costante. questo approccio si chiama **prior feedback approach**.

Il tempo possiamo sceglierlo di farlo scendere in molti modi
- Logaritmico
- Geometrico

#### Metropolis hastings
Vogliamo utilizzare la trasformata di boltzmann-gibbs per fare sampling del nuovo valore $$\theta$$ seguendo quello.

Algo:
1. Prendo $$y$$ da una distribuzione $$g$$, tale che sia **simmetrica** per questo motivo utilizzo una gaussiana. (anche questo deve essere scalato col tempo).
2. Poi faccio sampling condizionale: (con probabilità $$p$$ posso sommare, con probabilità $$1- p$$ rimane la stessa).
La cosa in più è che mi muovo con probabilità (la scelta stocastica) è la differenza con random walk...
In particolare $$p$$ non è costante ma cambia nel tempo, ed è calcolata come:

$$
p = min\left( \exp\left( \frac{\Delta h}{T} \right), 1 \right)
$$

Con $$h = h(\theta + y) - h(\theta)$$, una osservazione è che se è positiva, allora è sempre maggiore di 1, quindi mi muovo sempre (qui è equivalente a random walk).
Altrimenti vorrei essere più conservativo, e restare di più con la stessa posizione.
Ma allora continuo a **muovermi di meno** col tempo.


### EM Algorithms