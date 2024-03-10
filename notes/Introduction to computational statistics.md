---
layout: page
permalink: notes/introduction-to-computational-statistics
tags: italian
title: Introduction to computational statistics
---

### What is it for
1. **Estimation**
2. **Sampling** generate numbers from *any* distribution! (distributions are important in statistics).
	1. Density
	2. Cumulative distribution (and others similar).
3. **Optimization** how to find computationally the min and max of functions.

Generating?
1. Random (difficile anche filosoficamente definire cosa significa questo).
	1. Molto importante perché si assume in Comp stats che abbiamo il random vero, e questa assunzione che non vale può rompere cose.
2. And independent

#### Sample proportion
Average of something (example of the lake cannonball).

Figa la possibilità di fare sampling secondo una distribuzione, partendo dalla $$U$$.

#### Lista delle nozioni
- Generalized inverse definition.
- Fai la **dimostrazione** della generalized inverse transform (non dovrebbe essere tanto difficile, una volta che enunci quanto importante dovrebbe andare liscio).
- Cosa dice la inverse transform? Perché possiamo partire dalla distribuzione uniforme?
- In che modo è relazionato la distribuzione $$\exp$$  con chi squared, gamma e beta distribution?
- Generalized transform **formula** (not in the exam, serve per avere le densità e non la CDF) 🟥, non ho proprio capito perché funziona, in questo corso si impara solo ad imparare a memoria ed applicare queste cose.

- Come fare sampling fra distribuzioni discrete (che è la soluzione idiota).
- Sampling discrete from long tail distributions.

- Explain and use the accept reject method.
- Probabilità di accettazione, sia normalizzato che non normalizzato.
- Fare gli esercizi a fine capitolo due per accept reject. (registrazione 7 primi 50 minuti parlano di questo).
- Guardare meglio l'esempio 3.4 per l'importance sampling (e la roba dei tail sampling).
- Minuto 52 Lecture 11, ci sono gli esercizi dispari del capitolo 3.
- Fino a Lecture 12 minuto 48 ci sono altri esercizi.

#### Cose pratiche
- Essere in grado di implementare grafico e calcolare i valori per la inverse (esattamente quelli).