---
layout: page
permalink: notes/asymptotic-equipartition-property
tags: italian
title: Asymptotic Equipartition Property
---

Sembra essere molto simile a [Central Limit Theorem and Law of Large Numbers](/notes/central-limit-theorem-and-law-of-large-numbers) però per [Entropy](/notes/entropy).

### Enunciato
Data una serie di variabili aleatorie $$X_{1}, X_{2}, \dots$$ i.i.d. $$\sim p(x)$$ se vale che

$$
-\frac{1}{n} \log p(X_{1}, X_{2}, \dots, X_{n}) \to H(X)
$$

in probability (la definizione data in [Central Limit Theorem and Law of Large Numbers#Convergence in probability](/notes/central-limit-theorem-and-law-of-large-numbers#convergence-in-probability)).

#### Dimostrazione
Principalmente sorvolata, ma utilizza cose simili a [Central Limit Theorem and Law of Large Numbers](/notes/central-limit-theorem-and-law-of-large-numbers), e una idea simile a [Monte carlo integration](/notes/monte-carlo-integration) per le probabilità.

### Typical sets
Questo insieme è un oggetto matematico che ha delle proprietà interessanti, viene corretto analizzarlo dopo che si ha AEP, perché in breve la sua esistenza è giustificata da quello.
È l'insieme delle sequenze $$(x_{1}, x_{2}, \dots , x_{n})$$ prese da una distribuzione $$p(x)$$ sempre uguale tale per cui valga

$$
2^{-n(H(X) + \varepsilon)} \leq p(x_{1}, x_{2}, \dots, x_{n}) \leq 2^{-n(H(X) - \varepsilon)}
$$

Il motivo per cui abbiamo le cose strane all'esponente è proprio la definizione di convergenza in probabilità data. (basta che le espandi)
Ossia il fatto che

$$
P\left( \left\lvert  -\frac{1}{n} \log p(x_{1}, x_{2}, \dots, x_{n}) - H(X)  \right\rvert  > \varepsilon \right) = 0, n \to +\infty
$$

Se si espande quanto è presente dentro si ottiene quel bound di sopra.
#### Proprietà
Vedi 3.1.2 di @coverElementsInformationTheory2012.

Il risultato importante è che possiamo rappresentare sequenze di $$X^{n}$$ in media usando $$nH(X)$$ bits, senza perdita di informazione.