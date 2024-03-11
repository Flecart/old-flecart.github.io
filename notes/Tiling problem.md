---
layout: page
permalink: notes/tiling-problem
tags: italian
title: Tiling problem
---

### Formalizzazione del problema
#### Definizione formale del tiling

Consideriamo una tupla $$\langle \mathcal{T}, t_{0}, H, V \rangle$$
1. $$\mathcal{T}$$ è un insieme di piastrelle.
2. $$t_{0} \in \mathcal{T}$$ è la piastrella d'origine.
3. $$H \subseteq \mathcal{T} \times \mathcal{T}$$ le regole di adiacenza orizzontali.
4. $$V \subseteq \mathcal{T} \times \mathcal{T}$$ le regole di adiacenza verticali.

L'obiettivo è vedere se è possibile riempire tutto il piano con queste piastrelle, all'infinito. Sappiamo già che non è sempre possibile farlo. Ci chiediamo se è automatizzabile. Questo problema è stato risolto nel 1966, e sembra non essere riconoscibile nemmeno.

Ossia in matematichese definire la funzione
$$f : \mathbb{N} \times \mathbb{N} \to \mathcal{T}$$
Con 
1. $$f(1, 1) = t_{0}$$
2. $$\forall n,m \in \mathbb{N}, (f(n, m), f(n + 1, m)) \in V$$
3. $$\forall n,m \in \mathbb{N}, (f(n, m), f(n, m+1)) \in H$$

#### Strategia di dimostrazione
Vogliamo ridurlo da $$ETH^{-}$$ che abbiamo spiegato in [Halting Theorem and Reducibility](/notes/halting-theorem-and-reducibility).
Questo è un linguaggio non riconoscibile, perché il suo complemento è riconoscibile in modo banale.

Questa dimostrazione avrà un sacco di punti molto tecnici per dire che una macchina di turing deve essere tradotta in un problema di tiling...

### Dimostrazione inriconoscibilità del tiling
#### Codifica delle regole dei tiling
Posso codificare sia i tile disponibili, sia le regole di adiacenza in questo modo.

<img src="/images/notes/Tiling problem-20240307134015081.webp" alt="Tiling problem-20240307134015081">

Poi vogliamo codificare ogni casella verticale **un singolo step di computazione**.

#### Cella di identità
Questa cella non fa niente.
<img src="/images/notes/Tiling problem-20240307134139688.webp" alt="Tiling problem-20240307134139688">
#### Celle di transizione
Possiamo codificare le funzioni di transizione della macchina di Turing.
Poi ho ancora le cose che mantengono il simbolo nella cella di arrivo.

<img src="/images/notes/Tiling problem-20240307134228290.webp" alt="Tiling problem-20240307134228290">
#### Conclusione
sse non si ferma la macchina, allora esiste un tiling (che è una cosa banale perché significa che continua all'infinito, e quindi posso mappare tutto).

<img src="/images/notes/Tiling problem-20240307134959316.webp" alt="Tiling problem-20240307134959316">