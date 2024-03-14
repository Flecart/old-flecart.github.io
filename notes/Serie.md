---
layout: page
permalink: notes/serie
tags: italian
title: Serie
---

Questo è un tentativo di aggiungere un argomento che non era presente quando abbiamo fatto il corso due anni fa. Inizio la scrittura il 2024-03-03. Questo non è stato trattano nel corso, ma è importante per molte cose. Quindi introduco questo appunto.

### Introduzione alle serie

Le serie infinite sono dei mostri strani perché non si comportano spesso come dovrebbero.

#### Limit Comparison Test
Siano date due [Successioni](/notes/successioni) $$a_{n}$$ e $$b_{n}$$ sempre positive. Allora se esiste ed è finito il limite

$$
\lim_{ n \to \infty } \frac{a_{n}}{b_{n}} = c
$$

Si hanno due casi possibili per il valore di $$\sum_{i=1}^{+\infty}a_{n}$$ e di $$\sum_{i=1}^{+\infty}b_{n}$$
1. Entrambi convergono a un valore $$c$$
2. Entrambi divergono

Questo è abbastanza intuitivo se pensiamo che l'ipotesi ci sta dicendo che al limite le due successioni distano al massimo di un fattore reale.
Se divergono, e distano di un fattore reale, anche l'altro dovrà divergere, se invece converge, anche l'altro dovrà convergere. 

La dimostrazione credo passa dalla definizione di limite per successioni presente in [Successioni#3.2 Limiti di successioni](/notes/successioni#3.2-limiti-di-successioni).