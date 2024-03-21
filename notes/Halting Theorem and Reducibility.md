---
layout: page
permalink: notes/halting-theorem-and-reducibility
tags: italian
title: Halting Theorem and Reducibility
---

### Halting theorem
Questo è un problema fondamentale, che abbiamo trattato anche in [Fondamenti teorica#Halting problem](/notes/fondamenti-teorica#halting-problem), ma qui lo ritrattiamo, perché così lo rifacciamo per bene. In parte è stato trattato anche al corso di Logica.

#### Enunciato Halting theorem
Questo è molto simile a quanto presente sul @sipserIntroductionTheoryComputation2012.
Ossia consideriamo il linguaggio 

$$
HALT = \left\{ \langle x, y \rangle : y = code(M),M \text{ si ferma su } x\right\}
$$

#### Dimostrazione Halting theorem
La parte del sì è facile perché basta eseguirlo e vedere che si ferma (quindi abbiamo una [La macchina di Turing#La macchina di Turing universale](/notes/la-macchina-di-turing#la-macchina-di-turing-universale). Se si ferma appartiene al linguaggio, altrimenti è la parte in cui diverge.

**Dimostrazione non decidibilità**
Supponiamo sia decidibile e dimostriamo l'assurdo.
Se esiste una macchina $$f$$ tale per cui decida quel linguaggio, 

$$
\begin{cases}
f(g, y) = 1, g(y) \downarrow\\ \\
f(g, y) = 0, g(y) \uparrow
\end{cases}
$$

allora possiamo usare questa macchina per costruire un $$h$$ tale che per cui

$$
\begin{cases}
h(g) = 1, f(g, g) = 0 \\ \\
h(g) = \uparrow, f(g, g) = 1
\end{cases}
$$

Allora la computazione della funzione $$h(h)$$ genera un assurdo.

Il motivo è che $$h(h) = 1 \iff f(h, h) = 0 \iff h(h) = \uparrow$$
Questa cosa dovrebbe essere riscritta in modo $$code$$ per essere comprensibile da macchine di Turing.

#### Opposto di Halting theorem
Ossia vogliamo riconoscere il linguaggio 

$$
HALT^{-} = \left\{ \langle x, y \rangle : y \not= code(M) \cup y=code(M) \cap M \text{ non si ferma su } x\right\}
$$

Si può dimostrare che questo problema **non è nemmeno riconoscibile** da nessuno!
#### Dimostrazione complemento di halting theorem
Si ragiona anche qui per assurdo, se fosse riconoscibile, avremmo che Halting theorem principale sarebbe riconoscibile.

<img src="/images/notes/Halting Theorem and Reducibility-20240306120459845.webp" alt="Halting Theorem and Reducibility-20240306120459845">


### Mapping reducibility
#### Definizione mapping reducibility
Un linguaggio $$L'$$ è riducibile a un altro linguaggio $$L$$ se esiste una **funzione computabile totale** $$f : \Sigma^{*} \to \Sigma^{*}$$ tale che valga

$$
x \in L' \iff f(x) \in L
$$

E si scrive che $$L' \leq L$$
Ossia posso mappare qualunque parola in $$L'$$ in una stringa in $$L$$.
È molto importante che sia computabile, perché è un modo di dire che non stiamo barando nella dimostrazione, e mi appoggio soltanto all'espressività dei due linguaggi.

#### Proprietà di decidibilità basilari
- Se $$L$$ è decidibile, allora $$\forall L': L'\leq L$$ è decidibile.
- Se $$L'$$ è indecidibile allora lo è anche $$\forall L: L' \leq L$$ perché altrimenti si avrebbe un assurdo
- Se $$L$$ è decidibile e $$L'$$ no allora $$L' \not \leq L$$ altrimenti assurdo per il primo punto.

#### Ogni linguaggio decidibile è semplice
Ossia se $$L'$$ è decidibile allora per ogni $$L$$ tale che $$L \neq \emptyset$$ e $$L \neq \Sigma^{*}$$ Si ha che

$$
L' \leq L
$$


**Dimostrazione:**
Dato che $$L'$$ è decidibile, esiste $$g(x), \forall x \in \Sigma^{*}$$ tale che decide se $$x$$ appartiene o meno a quel linguaggio. Dato che $$L$$ è finito, esiste un $$\omega$$ che non appartiene e un altro $$v$$ che appartiene.
Allora costruisco la funzione $$f$$ così:
1. Runno $$g$$, se appartiene, mappo a $$v$$
2. Se non appartiene mappo a $$\omega$$.
Ez.

#### Indecidibilità su nastro vuoto
**NOTA:** in ogni caso devo vedere se il codice della macchina è valido.


Definendo il linguaggio

$$
ETH = \left\{ x \in \Sigma^{*}: x = code(\mathcal{M}) \text{ e } \mathcal{M} \text{ si ferma su } \varepsilon \right\} 
$$

Per dimostrare ciò basta dimostrare che $$HALT \leq ETH$$
Ossia dobbiamo costruire una funzione che mappa ogni stringa di $$HALT$$ in una di $$ETH$$.
Questo è molto semplice, solo definire qualche dettaglio (non banale) 
<img src="/images/notes/Halting Theorem and Reducibility-20240306125418004.webp" alt="Halting Theorem and Reducibility-20240306125418004">

#### Indicibilità ogni input
Definiamo il linguaggio

$$
FL = \left\{ x \in \Sigma^{*} : x = code(\mathcal{M}) \text{ e } \mathcal{M} \text{ ferma su ogni input} \right\} 
$$

Anche questo si può dimostrare in maniera simile al precedente, con una mapping reduction.
Questo è anche più semplice:
Per ogni input $$\langle \mathcal{M}, x \rangle$$ costruisco la seguente macchina
1. La macchina nuova prende un input $$y$$, la ignora per il momento, e simula $$\langle \mathcal{M}, x \rangle$$.
2. Se termina (e quindi appartiene a $$HALT$$) allora termino anche io ignorando l'input.
3. Altrimenti divergo, e quindi non appartengo.
Questa nuova macchina è bona. Quindi funziona l'indicibilità.

#### Equivalence problem decidability

$$
EQ = \left\{ \langle y, x \rangle \in \Sigma^{*} \times \Sigma^{*} : x = code(\mathcal{M}), y = code(\mathcal{M'}) \text{ e } \mathcal{M}, \mathcal{M'} \text{ hanno la stessa funzione parziale} \right\} 
$$

Anche in questo caso proviamo a ridurci al caso $$FL$$.
Sempre come prima, per input $$\langle \mathcal{M}\rangle$$ mi costruisco questa macchina
<img src="/images/notes/Halting Theorem and Reducibility-20240306132502507.webp" alt="Halting Theorem and Reducibility-20240306132502507">


#### Equivalence problem recognizability
Il linguaggio del problema di equivalenza non è nemmeno riconoscibile. Per fare ciò devo ridurre $$HALT^{-}$$ a questo EQ.
Dimostro la riduzione $$HALT \iff EQ^{-}$$ 

<img src="/images/notes/Halting Theorem and Reducibility-20240306133625876.webp" alt="Halting Theorem and Reducibility-20240306133625876">

#### Nota sulla gerarchia
Cosa curiosa è che $$HALT$$ è il suo opposto non sono comparabili. Mentre ci aspetteremmo che HALT sia più semplice.
Una altra cosa curiosa è che EQ non è riconoscibile, e nemmeno il suo opposto lo è.
z
### Turing riducibilità

#### Definizione di oracolo 🟩
Dato un linguaggio $$L$$ e una stringa $$x$$, l'oracolo mi dice in tempo finito se $$x \in L$$.

#### Definizione Turing-riducibilità 🟩
> Dato un  $$L'$$ , questo è Turing riducibile a $$L$$, quindi $$L' \leq_{TM} L$$, se dato un oracolo per $$L$$ possiamo decidere $$L'$$

#### Mapping reducibility => Turing-riducibilità 🟩-
Possiamo dimostrare in modo semplice che con Turing-riducibilità $$HALT$$ è riducibile a $$HALT^{-}$$. Senza problemi.
Mentre non posso farlo con Mapping reducibility.