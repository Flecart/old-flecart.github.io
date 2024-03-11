---
layout: page
permalink: notes/poisson-processes
tags: italian
title: Poisson processes
---

### Introduzione ai processi di Poisson

#### Arrival processes

Sia una sequenza di variabili aleatorie $$0 < S_{1} < S_{2} < \dots$$ (il fatto che sia positivo  significa che per ogni elemento del dominio vale che quell'elemento è <, non so se mi sono spiegato.)
<img src="/images/notes/Poisson processes-20240128100752878.webp" width="443" alt="Poisson processes-20240128100752878">

Il fatto che siano crescenti ci permette di metterli in linea, perché siamo sicuri che $$S_{2}$$ produrrà un valore maggiore di $$S_{1}$$.

Incline a questo c'è anche il **arrival counting process** che semplicemente va a contare il numero di arrivi (indicati dagli $$S_{i}$$).
La relazione con l'originale è abbastanza semplice, e dato da questo evento:

$$
\{S_{n} \leq t\} = \{N(t) \geq n\}
$$


#### def: Renewal processes 

un arrival process in cui inter-arrival times $$x_{1}, x_{2}, \dots$$ sono IID.
#### def: Poisson processes

Sono renewal processes in cui gli $$X_{1}, X_{2}, \dots$$
$$F_{X}(x) = 1 - \exp(-\lambda x)$$, ossia seguono la cumulativa di Poisson.
### Proprietà
#### def: Memory-less
Variabile aleatoria è memory-less se vale.

$$
P(X > t + x)= P(X > t) P(X > x)
$$


Lo chiamiamo così perché assumiamo che non dipende dal tempo passato:

$$
P(X > t + x | X > t) = P(X > x)
$$

il prof. dice che non ha perso tempo né guadagnato niente. Perso tempo perché se vuoi la cosa prima o poi devi entrare in coda.

Si può dimostrare che se e solamente se la variabile aleatoria è esponenziale allora è memory-less.

#### Teorema indipendenza di arrival counting and arrival process

sketch:

Prendiamo un tempo $$t$$ 

#### Stationary increment property
Se prendiamo un **counting process**, questo si dice stazionario se la variabile $$N(t') - N(t)$$ con $$t' > t > 0$$  ha la stessa distribuzione di  $$N(t'- t)$$ ossia è lineare senza costanti.
Questo sembra chiaro perché ci sta dicendo che il numero di arrivi in un lasso di tempo resta sempre lo stesso.

Un esempio è che nel lavoro di Ermanno le sue cose non rispettano la stationary property.

#### Independent property

Vale se data una sequenza $$0, t_{1}, t_{2}, t_{3}, \dots$$ crescente vale che le distribuzioni

$$
N(t_{1}) - N(0), N(t_{2}) - N(t_{1}), \dots
$$

Sono indipendenti fra di loro

Per il teorema dimostrato sopra si può dire che la distribuzione di Poisson possieda queste proprietà.

### Equivalenze con i processi di Poisson

#### Arrival counting processes
Si può dire che un processo che soddisfa
(reference al libro) che sia independent increment e stationary increment sia un processo di poisson


### Conditional arrival densities

Se so che in un intervallo c'è un arrivo, allora è uniforme la probabilità di dove sia arrivato (solo che abbiamo una uniforme su un volume molto strano). Questo è una cosa che credo sia relazionata con la indipendenza di Poisson per questo genere di processi.

La cosa da notare è che questa densità è indipendente da $$s_{1}, s_{2}, .., s_{n}$$. 

si avrà che

$$
f(s_{1}s_{2}\dots s_{n}|n) = \frac{n!}{t^{n}}
$$


### Applicazioni
#### Neuronal firing
Da approfondire

#### Optical trasmission
Da approfondire