---
layout: page
permalink: notes/monte-carlo-integration
tags: en
title: Monte carlo integration
---

DI Law of Large Numbers e Central limit theorem ne parliamo in [Central Limit Theorem and Law of Large Numbers](/notes/central-limit-theorem-and-law-of-large-numbers).

### Law of large numbers
Data una sequenza di variabili aleatorie, $$X_{1}, X_{2}, \dots, X_{n}\dots$$, tali che siano i.i.d tali per cui $$E(X_{1}) = E(X_{2}) = \dots = E(X_{n}) =\dots = \mu$$ tale che sia **finito**.
Consideriamo 

$$
S_{n} = \sum^n_{i=1} x_{i} ,:, \bar{x}_{n} = \frac{S_{n}}{n}
$$

Allora questo teorema afferma che:

$$
\bar{x}_{n} \to \mu
$$

Ossia il limite converge sul valore atteso di tutte le variabili aleatorie.

Inoltre se abbiamo che la varianza di tutte le variabili aleatorie, abbiamo che

$$
var(\hat{x}_{n}) = \frac{\sigma^{2}}{n} \to 0
$$


#### Strong Law of large numebrs

$$
\mathbb{P}(\lim_{ n \to \infty } \bar{x}_{n} =\mu) = 1
$$

Ci permette di prendere la **sample average** per quei valori di mezzo.
E posso fare la stima della nostra funzione di interesse $$h$$ tenendo conto:

$$
\bar{h}_{n} = \sum_{i=1}^{n} \frac{h(x_{i})}{n}
$$

E questo converge $$O(\sqrt{ n })$$ per la legge dopo.

#### Central limit theorem
Data una sequenza di variabili aleatorie, $$X_{1}, X_{2}, \dots, X_{n}\dots$$, tali che siano i.i.d tali per cui $$E(X_{1}) = E(X_{2}) = \dots = E(X_{n}) =\dots = \mu$$ tale che sia **finito**, e con varianza tutti uguali $$= \sigma^{2}$$ **finito**.

Abbiamo come risultato che

$$
\sqrt{ n } (\hat{x}_{n} - \mu) \to N(0, \sigma^{2})
$$

La prima parte è una **variabile aleatoria** e converge a quel valore. (questo permette di utilizzare la gaussiana quando $$n$$ è grande abbastanza).


### Monte carlo integration

Abbiamo che:

$$
\int_{X} h(x) \cdot f(x) dx = E_{f}[h(x)] = \mu
$$

Questo è tutto il significato dell'integrazione di monte carlo (molte variabili aleatorie per stimare il valore di qualcosa). 
E questo vale sempre, anche se $$f$$ non è una funzione di densità, basta che sia positiva (basta riscalare).

Il motivo per cui funziona è per LLN, perché abbiamo che convergerà su $$\mu$$ in lungo termine, basta considerare molte variabili aleatorie consecutive.

Cose interessanti:
1. Posso stimare il valore atteso grazie a LLN
2. Posso stimare la varianza grazie ad essa
3. Posso stimare variabili condizionali.

#### Importance sampling
1. Deve soddisfare la cosa del supporto (contiene supporto sia di h che di f)
2. Deve avere **varianza finita** per i pesi che sono trovati. (ci sono metodi per stimare poi il $$g$$).
	1. la frazione $$\frac{f}{g)}$$ deve essere limitata e la varianza di $$h$$ rispetto alla densità $$f$$ deve essere finita.

# References