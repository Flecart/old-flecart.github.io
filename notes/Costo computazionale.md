---
layout: page
permalink: notes/costo-computazionale
tags: italian
title: Costo computazionale
---

Ultima modifica: November 3, 2021 11:27 AM
Primo Abbozzo: November 3, 2021 11:24 AM
Studi Personali: No

# Elementi di ripasso

# Costo computazionale

In modo intuitivo il costo in tempo è il numero di cicli di clock che il computer deve avere per forza per finire l'esecuzione di un codice.

Si cerca di avere **un costo massimo** quindi possiamo fare per casi:

### Costo condizionale

Costo guardia più max guardia

costo_della_guardia + max(costo_ramo_then, costo_ramo_else)

### Costo iterativo

numero_iterazioni*(costo_della_guardia+costo_del_corpo) + costo della guardia
dia più max guardia

costo_della_guardia + max(costo_ramo_then, costo_ramo_else)

### Costo iterativo

numero_iterazioni*(costo_della_guardia+costo_del_corpo) + costo della guardia