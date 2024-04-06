---
layout: page
permalink: notes/the-rlhf-pipeline
tags: en
title: The RLHF pipeline
---

[https://huyenchip.com/2023/05/02/rlhf.html](https://huyenchip.com/2023/05/02/rlhf.html) è un blog post che lo descrive in modo abbastanza dettagliato e buono.

## Introduzione a RLHF

Questo è il processo che è quasi la migliore per la produzione di LLM moderni (maggior parte si basano su questo per dire).

### Struttura generale
Si può dire che RLHF si divida in 3 parti fondamentali

1. **Completion** il modello viene allenato a completare parole dal web,solitamente è molto inutile
2. **Fine tuning** per le singole task, per esempio riassumere, rispondere in certo modo etc.
3. **Reinforcement Learning** basato su un **reward model** scoperto.

Partiamo con l'approccio di reinforcement learning che è la parte un po' più interessante in questo momento

## Human Feedback

### Introduzione al metodo

Dato che utilizziamo gli LLM come aiutanti per noi umani, è importante che il loro output sia il più possibile allenato sulle preferenze di noi umani. Per questo motivo dobbiamo creare un metodo che permetta di allenare il modello basandoci su queste preferenze.

#### The reward model
Come descritto da [(Ziegler et al. 2020)](http://arxiv.org/abs/1909.08593), un approccio inizialmente utilizzato è provare a definire in modo esplicito un modello $$r(x, y)$$ in cui $$x$$ è il prompt iniziale e $$y$$ è la completion data dal modello.
Segue poi uno schema del genere:
$$y_{1}, y_{2}, y_{3}, y_{4}$$ generati dal modello, poi questi vengono rankati in ordine di preferenza (oppure anche solamente il migliore fra i quattro, poi si utilizzano 4 e non due in questo papero perché così una persona può scegliere, solo più veloce per dire).
E da questo si può allenare in un modo che non ho ancora capito una cosa di preferenza.





# References

[1] Ziegler et al. [“Fine-Tuning Language Models from Human Preferences”](http://arxiv.org/abs/1909.08593) arXiv preprint arXiv:1909.08593 2020