---
layout: page
permalink: notes/teorema-di-rice
tags: italian
title: Teorema di Rice
---

### Introduction to the Rice Theorem
Ci sono molti teoremi che non possono essere decisi, vedere [Halting Theorem and Reducibility](/notes/halting-theorem-and-reducibility).
Qui andiamo a chiederci quale sia l'insieme dei problemi decidibili.

#### Proprietà dei linguaggi TM
Data una macchina $$\mathcal{M}$$ definiamo il suo linguaggio come

$$
L_{\mathcal{M}} = \left\{ x \in \Sigma^{*}: \mathcal{M} \text{ accetta } x \right\} 
$$

Allora con questa definizione di linguaggio possiamo dire che una **proprietà**, ossia una funzione da tutti i $$TM$$ possibili a  $$\left\{ 0, 1 \right\}$$ tale per cui se il linguaggio riconosciuto è lo stesso, ossia 

$$
L_{\mathcal{M}} = L_{\mathcal{M}'} \implies P(\mathcal{M}) = P(\mathcal{M}')
$$

Definiamo questa **non triviale** se esiste una macchina per cui è 0, e una per cui è 1 (ossia non è costante).

#### Enunciato di Rice
Se $$P$$ è una proprietà dei linguaggi TM, allora è indecidibile questo problema $$\mathcal{M}$$ ha la proprietà $$P$$.

### L'insieme delle funzioni non decidibili