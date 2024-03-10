---
layout: page
permalink: notes/bias-variance-trade-off
tags: italian
title: Bias Variance Trade-off
---

## Introduction

È una cosa ormai risaputa che c'è una sorta di trade-off fra la varianza e il bias per una certo modello. Aumentare la varianza del modello certamente ci permetterà di avere un modello che abbia un errore di training molto basso, però appena vede dei dati nuovi non sarà in grado di generalizzare correttamente.
Dall'altra parte avere un bias alto significa avere un modello eccessivamente semplice, poco flessibile, che comunque allenato non riesce ad avere una grande accuratezza né in fase di allenamento, né di in fase di validazione o di test.

### Mathematical decomposition

Si può derivare una decomposizione di questo trade-off da un punto di vista matematico, quanto enunciato è dimostrato nel capitolo 8.1.1 delle [Note di andrew NG 229 stanford](https://cs229.stanford.edu/main_notes.pdf)
proviamo a descrivere in modo molto leggere questo presente in quelle note in questo luogo.
TODO: riscrivere la derivazione, una volta che l'hai compresa e capita

Dall'espressione matematica, deriviamo che anche nel caso in cui riusciamo ad eliminare del tutto la varianza e il bias, rimarrebbe l'errore irriducibile di cui abbiamo parlato in [Introduction to statistical learning](/notes/introduction-to-statistical-learning).

### Considerazioni generali
Questo trade-off è nato principalmente nell'analisi teorica dei modelli, però è bene tenere in mente la presenza di ciò anche per i modelli reali. Non possiamo calcolare esplicitamente il MSE, però ci dovrebbe essere. Questa è l'osservazione principale per asserire che non sempre il modelli più complicato è la migliore, abbiamo il no-free-lunch theorem!