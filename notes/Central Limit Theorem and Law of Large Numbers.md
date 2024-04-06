---
layout: page
permalink: notes/central-limit-theorem-and-law-of-large-numbers
tags: en
title: Central Limit Theorem and Law of Large Numbers
---

### Bounds

#### Markov Bound
Questo bound è abbastanza banale se fatto da un punto di vista grafico, comunque afferma che

$$
P(X \geq y) \leq \frac{E[X]}{y}
$$

Il motivo è che

$$
yP(X \geq y) = y\int _{x =y}^{+\infty} f(x) \, dx \leq \int _{x=y}^{+\infty} x f(x) \, d \leq \int _{-\infty}^{+\infty}xf(x) \, d = E[X]  
$$

Il che finisce la dimostrazione.

#### Chebychev Bound
Questa è una conseguenza abbastanza diretta sul bound precedente:
Afferma che

$$
P(\mid x - E[X] \mid \geq y) \leq \frac{\sigma^{2}}{y^{2}}
$$

E in pratica dice che all'infinito viene tutto compattata sul valore atteso
La dimostrazione è abbastanza semplice, si sostituisce $$(x - E[X])^{2}$$ su $$X$$ di Markov e $$\varepsilon^{2}$$ a $$y$$ e poi si dovrebbe già avere il risultato

#### Chernoff Bound
##### Moments of random variable
[https://en.wikipedia.org/wiki/Moment-generating_function](https://en.wikipedia.org/wiki/Moment-generating_function)
Per capire il significato di questo bound invece, è necessario prima capire cosa sia un **moment generating function**. È una funzione generale che crea i momenti di una variabile aleatoria.
Un momento per una variabile aleatoria è descrivibile come n-esimo momento: $$E[X^{n}]$$ 
La funzione generatrice dei momenti è describile come:

$$
M_{X}(\lambda) = E[\exp(\lambda X)]
$$

Il motivo per cui vale, è che con l'espansione di taylor, vedi [Hopital, Taylor, Peano](/notes/hopital,-taylor,-peano) 
Possiamo estrarre in modo abbastanza semplice i momenti:
Infatti:

$$
e^{tX} = 1 + tX + \frac{t^{2}X^{2}}{2!} + \frac{t^{3}X^{3}}{3!} + \dots
$$

Quindi per esempio se volessimo il primo momento, prendiamo la derivata rispetto a $$t$$e settiamo $$t=0$$, perché la cosa molto bella è che i coefficienti si cancellano tutti, e l'unico termine che rimane senza $$t$$ è il momento cercato, per questo motivo estraiamo easy i momenti.

##### Dimostrazione Chernoff's Bound
Anche questa è una conseguenza abbastanza immediata di Markov, viene affermato che

$$
P(Z \geq t) \leq \inf_{s > 0} e^{-st} M_{Z}(s) = \inf_{s > 0} e^{-st} E[e^{sZ}]
$$

Guardandolo dall'altro in basso non ho idea del perché valga.

La dimostrazione avviene così

$$
P(Z \geq t) = P(e^{sZ} \geq e^{st}) \leq \frac{E[e^{sZ}]}{e^{st}}
$$

Dove $$s$$ è qualunque $$s > 0$$ perché per quello la funzione resta crescente, e quindi la dimostrazione vale ancora.
La cosa interessante di questo bound è che la probabilità che succeda **scende in modo esponenziale**. 


#### Hoeffding's Inequality
L'enunciato è che se considero la somma delle classiche variabili aleatorie con stessa media varianza $$S_{n}$$ allora vale che, tale per cui con probabilità $$1$$ vale che $$a_{i} \leq X_{i} \leq b_{i}$$

$$
P(\lvert S_{n} - \mathbf{E}[S_{n}] \rvert  \geq t) \leq e^{-2t^{2}/\sum(b_{i} - a_{i})^{2} }
$$

Questo ci dice quanto velocemente la media converge nel valore atteso  che ci aspettiamo per la legge dei grandi numeri

La dimostrazione di questo mi sembra abbastanza tecnica, c'è bisogno di guardare 
[https://web.eecs.umich.edu/~cscott/past_courses/eecs598w14/notes/03_hoeffding.pdf](https://web.eecs.umich.edu/~cscott/past_courses/eecs598w14/notes/03_hoeffding.pdf)
Oppure [https://cs229.stanford.edu/extra-notes/hoeffding.pdf.](https://cs229.stanford.edu/extra-notes/hoeffding.pdf.)

Non ho bene capito l'utilità se non nel caso Bernoulliano in cui sembra si semplifichi abbastanza questo.

## Law of Large numbers

### Weak Law

La dimostrazione di questo è molto semplice, basta avere Chebicheff

Questa è l'intuizione di quanto presente nell WLLN
<img src="/images/notes/Central Limit Theorem and Law of Large Numbers-20240127132749421.webp" alt="Central Limit Theorem and Law of Large Numbers-20240127132749421">

Abbiamo **mean square convergence**.

Abbiamo che vale:


$$
\mathbb{P}\left( \left(  \frac{S_{n} - n\bar{X}}{n} \right)^{2} > y \right) \leq \frac{\sigma^{2}_{X}}{ny}
$$

E poi settando $$y = \varepsilon^{2}$$ si può avere il risultato. Nella forma corretta. Vedere capitolo 1.5 in [https://ocw.mit.edu/courses/6-262-discrete-stochastic-processes-spring-2011/resources/mit6_262s11_chap01/.](https://ocw.mit.edu/courses/6-262-discrete-stochastic-processes-spring-2011/resources/mit6_262s11_chap01/.)

Si può scrivere:

$$
\lim_{ n \to \infty } E \left[  \left( \frac{S_{n}}{n} - \bar{X} \right)^{2} \right] = 0 
$$

In questo senso possiamo dire che la successione $$S_{n}$$ arriverà sempre alla media. 

Ricordiamo che $$S_{n} = X_{1} + X_{2} + \dots + X_{n}$$.
Dove tutte le variabili $$X_{i}$$ sono IID con media $$\bar{X}$$ e varianza $$\sigma^{2}$$.

#### Weak law without finite variance
Potremo scrivere

$$
\lim_{ n \to \infty } \mathbb{P}\left( \mid \frac{S_{n}}{n} - E[X]\mid > \varepsilon \right) = 0
$$

Teorema 1.5.3 nelle note.

### Convergence types
Per qualche motivo che non ho ancora capito è importante andare a distinguere tipologie di convergenza diverse fra di loro.

#### Convergence in distribution
Una sequenza di variabili aleatorie $$Z_{1}, Z_{2}, \dots$$ converge in distribuzione se vale

$$
\lim_{ n \to \infty } F_{Z_{n}}(z) = F_{Z}(z)
$$

Per ogni $$z$$ in cui $$F_{Z}(z)$$ è continua. Una sequenza di distribuzioni che converge a una distribuzione.
Un esempio in cui questo vale è il central limit theorem in cui definiamo

$$
Z_{n} = \frac{S_{n} -n\bar{X}}{\sigma \sqrt{ n }}
$$

Converge alla normale, 0, 1 gaussiana.
Un altro esempio è la weak law of large numbers, in cui $$\frac{S_{n}}{n}$$ converge a $$\bar{X}$$.
#### Convergence in probability
Se prendiamo una sequenza $$Z_{1}, Z_{2}, \dots$$ a $$Z$$ se vale 

$$
\lim_{ n \to \infty } P(\mid Z_{n} - Z\mid > \varepsilon) = 0
$$


Vale anche qui l'esempio della WLLN.
#### Convergence in mean square
Una sequenza di $$Z_{1}, Z_{2}, \dots$$ converge in mean square a $$Z$$ se vale

$$
\lim_{ n \to \infty } E[(Z_{n} - Z)^{2}] = 0
$$

La nota è che Mean Square -> Convergence probability -> Convergence in distribution.

#### Convergence almost everywhere
(Il prof. lo chiama **with probability 1** e secondo lui serve sapere measure theory per poter comprendere la definizione originale).

Definiamo una sequenza $$Z_{1}, Z_{2}, \dots$$ e $$\Omega$$ il suo spazio campionatorio e sia $$Z$$ una altra variabile aleatoria, allora la sequenza **converge con probabilità 1 se vale**


$$
\mathbb{P}(\{\omega \in \Omega : \lim_{ n \to \infty }Z_{n}(\omega) = Z(\omega) \}) = 1
$$

Ossia, per definizione di variabile aleatoria $$Z_{n}(\omega)$$ è un valore reale, queste sequenze di numeri reali a volte convergono, se convergono vogliamo che il valore sia esattamente $$Z(\omega)$$.
Quello che vogliamo dire con questo è che la probabilità degli elementi dello spazio campionatorio che creano sequenze che convergono è uguale a 1.

### The strong Law



## Central Limit Theorem
 
### The Bernoulli Case

### The theorem

$$
\lim_{ n \to \infty } \left[ \mathbb{P}\left( \frac{S_{n} - n\bar{X}}{\sqrt{ n }\sigma} \leq y \right)\right] = \int_{-\infty}^{y} \frac{1}{\sqrt{ 2\pi }} \exp\left( -\frac{x^{2}}{2} \right) \, dx 
$$

Ossia che la sequenza di variabili aleatorie

$$
Z_{i} = \frac{S_{i} - n\bar{X}}{\sqrt{i} \sigma}
$$

Convergerà alla gaussiana normale. È un motivo per cui è una distribuzione molto importante.



# References