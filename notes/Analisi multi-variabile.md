---
layout: page
permalink: notes/analisi-multi-variabile
tags: italian
title: Analisi multi-variabile
---

Ripasso Prox: 20
Ripasso: June 4, 2022
Ultima modifica: 11 Marzo, 2024 12:08 PM
Primo Abbozzo: March 7, 2022 1:34 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Analisi multi-variabile

In questo capitolo cerchiamo di andare oltre alla singola dimensione per l'analisi.

Introduzione

### Lo spazio R^n

Possiamo definire uno spazio **Rn** come il prodotto cartesiano fra l'insieme R un numero di volte uguale a n $$\mathbb{R} \times \mathbb{R} \times ... \times\mathbb{R} = \mathbb{R}^n$$

Allora **un tipico elemento** in Rn è nella forma $$(x_1,...,x_n)$$, questo elemento si chiama punto, mentre gli elelmenti in R che costituiscono questo elemento si chiamano componenti.

**Osservazione**

La maggior parte dei risultati che dimostro nello **spazio ordinario (R3)** si può dimostrare per Rn, non andiamo più nel dettaglio perché i problemi che ho in spazi maggiori sono parte di materiale per analisi 2

### Operazioni definite

In modo simile a quanto definito negli [Spazi vettoriali](/notes/spazi-vettoriali) abbiamo principalmente due operazioni principali definite (in moto identico a quanto spiegato nell'altro documento) che sono:

1. l'addizione vettoriale
2. la moltiplicazione scalare.

In più aggiungiamo una operazione che non è presente nel documento degli spazi vettoriali ma che è importante in questo momento.

1. Prodotto scalare euclideo, definito qui sotto

### Il prodotto scalare euclideo

Dati due elementi in Rn, che chiamiamo x e y, rispettivamente di componenti $$x_1, ...,x_n$$ e $$y_1, ...,y_n$$


$$
\langle x,y\rangle =  x\cdot y\coloneqq\sum_{i=1}^nx_iy_i
$$


Possiamo individuare 3 proprietà principali per questo prodotto scalare (nota il significato x,y con parentesi cambia in algebra lineare rispetto a questo. (chiamo in questo caso x primo argomento e y secondo argomento).

1. **Simmetria**, se scambio x con y il risultato resta lo stesso $$x\cdot y = y \cdot x$$
2. **Distributività (linearità del primo argomento)  $$\forall x,y,z \in \mathbb{R}^n, \forall \lambda, \mu \in \mathbb{R}  (\lambda x + \mu y) \cdot z = \lambda(x\cdot z) + \mu(y \cdot z)$$**
Utilizzando la simmetria puoi dimostrare anche la linearità per il secondo argomento.
3. **Positività del riflessivo:** $$\forall x \in \mathbb{R}^n , x\cdot x \geq 0$$, e si può osservare che $$x\cdot x = 0 \iff x = 0_v$$

**Prodotto scalare nella forma col coseno**

Dato un elemento $$x \in \mathbb{R}^{2}$$, posso dire che $$x = \lvert x \rvert \dfrac{x}{\lvert x \rvert}$$ notiamo che il secondo fattore ha lunghezza 0, quindi possiamo scriverlo tramite una coordinata polare, qualcosa tipo $$\dfrac{x}{\lvert x \rvert} = (\cos \theta, \sin \theta)$$.
Quindi se prendo un $$x \neq 0$$ possiamo dire che $$x = (|x|\cos \theta, |x| \sin \theta), \theta \in \mathbb{R}$$

Allora se prendo due vettori scriviamo così!

$$
x \cdot y = \lvert x \rvert \lvert y \rvert  \cos \theta \cos \gamma + \lvert x \rvert \lvert y \rvert\sin \theta\sin \gamma = \lvert x \rvert \lvert y \rvert(\cos(\theta - \gamma))
$$


che è esattamente la formula che abbiamo visto alle superiori, il prodotto delle singole norme per il coseno dell'angolo fra i due.

### Ortogonalità

Si può definire l'ortogonalità di due vettori a seconda del risultato del loro prodotto scalare
$$x,y$$ perpendicolari $$\implies x \cdot y = 0$$
Da questo si può notare che  il vettore nullo è perpendicolare a ogni vettore.

### Norma di un vettore

Scopriremo in seguito che la norma è strettamente collegata con la lunghezza di un vettore, la definiamo in questo modo:

$$\lVert x\rVert = \sqrt{x\cdot x} = \sqrt{x_1^2 + ... + x_n ^2}$$

Puoi notare come questo sia esattamente la distanza.

**Proprietà**

1. $$|\lambda|\lVert x\rVert = \lVert\lambda x\rVert$$
2. $$\rVert x \lVert \geq 0$$ e anche l'altro con 0, esattamente come per la propreità 3 del prodotto scalare vettoriale
3. **Disuguaglianza triangolare $$\lVert x \cdot y \rVert  \leq |x| |y|$$**

**Normalizzazione**

Per la proprietà 1 possiamo sempre normalizzare un vettore, ovvero moltiplicarlo per un reale tale che la somma dei componenti è 1.
Per trovare questo valore basta trovare il valore nella norma attuale $$\lambda$$  e dividere ogni componente per questo valore. esempio
$$(3,4)$$ noto che la norma è 5, quindi questo punto normalizzato è $$(\dfrac{3}{5}, \dfrac{4}{5})$$

**Il quadrato della norma**
cerchiamo di calcolare questo valore $$||x + y|| ^2$$
Per definizione si ha


$$
\lvert x + y \rvert^ 2 = \left( \sqrt{ \sum_{i=1}^n (x_i + y_i) ^2} \right)^2 = \sum_{i=1}^n (x_i + y_i) ^2 = \sum_{i=1}^n (x_i^2 + 2x_iy_i + y_i^2) = \lvert x \rvert ^2 + 2x\cdot y + \lvert y \rvert ^2
$$


Si può anche dimostrare tramite le propreità 2 del prodotto scalare e l'additività, dimostrare in questo modo per esercizio (oppure chiedere a qualcuno che era in classe).

Osservazione:
Si può notare che se i due vettori sono perpendicolari si ritrova il teorema di Pitagora in quanto

$$x \cdot y = 0$$

### Disuguaglianza di Cauchy-Schwarz 

Siano x,y vettori in $$\mathbb{R}^n$$, allora vale che

$$\lvert x \cdot y\rvert \leq \lvert x \rvert \lvert y \rvert$$ dove uguale si ha sse x e y sono dipendenti.
Dimostriamolo nel caso in cui n = 2, per n superiori dovrebbe essere analogo,
prendiamo due valori come qui, allora ho che
$$\lvert x \cdot y\rvert = \lvert \lvert x \rvert \lvert y \rvert\cos(\theta - \gamma) \rvert \leq \lvert x \rvert \lvert y \rvert$$ osservando il coseno, questo è sempre compreso fra -1 e 1 quindi è ovvio che sia sempre minore. ed è ovvio che sono uguali nel momento in cui coseno è 0, quindi i due vettori sono dipendenti.

Questo poi si può espandere con spazi Hilbertiani e simili, ma non li conosco bene.

**Dimostrazione disuguaglianza triangolare da CS**

$$\lvert x + y \rvert \leq \lvert x \rvert  + \lvert y \rvert \iff \lvert x\cdot y\rvert \leq \lvert x \rvert\lvert y \rvert$$ fai il prodotto e guarda i calcoli

- Prodotto e calcoli
    $$\lvert x + y \rvert \leq \lvert x \rvert  + \lvert y \rvert \implies \lvert x + y \rvert^2 \leq (\lvert x \rvert  + \lvert y \rvert)^2 \implies  \lvert x \rvert^2 + 2x\cdot y + \lvert y \rvert ^2 \leq \lvert x \rvert^2  + 2\lvert x \rvert\lvert y \rvert + \lvert y \rvert^2$$ e cancellando opportunamente nell'ultimo passaggio, è banale la deduzione.


**Teorema di Pitagora**
Anche questa è una derivazione senza molti problemi in quanto basta la forma del quadrato della norma e il fatto che sono perpendicolari per dire che è uguale a 0.

### Distanza fra due punti

Possiamo definire la distanza fra due punti come la **norma del vettore differenza**:

$$Dist(x, y) = \lVert x - y \rVert$$ (il che ha senso, perché la differenza mi da un vettore differenza, mentre la norma mi da la lunghezza di questo vettore, ignorando il verso e la direzione, quindi riesco ad ottenere una distanza).

## Insiemi e intorni

### Intorno sferico

Andiamo a definire la nozione di **intorno sferico**

$$I_r(x)$$ è l'insieme di punti che distano al più r da x, ossia $$\{y \in \mathbb{R}^n ,t.c., \lvert x - y\rvert < r\}$$

Si può notare poi che questa forma dal punto di vista geometrico definisce una sfera in 3 dimensioni, un disco in 2, un intervallo in 1. Analogamente si possono definire i punti di un cerchio con più dimensioni in questo modo.

### Insieme limitato

Un insieme $$A$$ si dice limitato se $$\exists k > 0, k \in \mathbb{R},$$  $$A \subseteq I_k(0)$$. Quindi è contenuto all'interno di una area ben definita.

Una funzione che ha dominio fino ad infinito per esempio 1/x  non è limitato perché non riesco mai a rinchiuderlo, ma una macchia a caso invece si può racchiudere.

### Insieme aperto

Un insieme si dice aperto se per qualunque punto esiste un contorno abbastanza piccolo che è contenuto nell'insieme (cosa che non succede per un insieme chiuso, se prendo un punto nel bordo non trovo tale intorno).

## Successioni generali

### Definizione

$$(x_n)_{k \in \mathbb{N}}: x_k \in \mathbb{R}^n, \forall k \in \mathbb{N}$$ si potrebbe quindi sempre vedere come una funzione che va da $$\mathbb{N} \to \mathbb{R}^n$$

### Convergenza delle successioni (classica)

Una successione converge in un punto in Rn, se ogni suo componente tende alla componente corrispondente del punto di convergenza.

Es, suppongo che f tenda a un $$x_0, y_0$$ allora voglio dire che il limite per x tende a x0, anche limite per y tende a y0.

### Convergenza secondo distanza

Se si utilizza la convergenza secondo la nozione di stanza, allora questo assume una forma molto simile alla nozione di convergenza per i numeri reali.

$$x_k \to x \in \mathbb{R}^n \iff \lvert x_k - x\rvert < \epsilon, \forall \epsilon >0$$ ossia quella distanza tende a 0.

## Funzioni con più variabili

### Definizione

$$A\subseteq \mathbb{R}^n  , B \subseteq \mathbb{R}^n, f: A \to B, ,,Graf(f) = \{(x, f(x)) \in A \times B \}$$ quindi alla fine è sempre la classica definizione di insieme, ma con dominio e codominio diversi

$$Im(f) = (f(x) | x \in A)$$

### Categorie di funzioni

**Funzioni scalari**

$$\mathbb{R}^n \to \mathbb{R}$$

**Funzioni curve o cammini**

$$\mathbb{R} \to \mathbb{R} ^n$$

### Continuità

$$\forall (x_k)_{k \in \mathbb{N}} x_k \to x, \text { si ha che } f(x_k) \to f(x)$$ rispettivamente utilizzando i domini e codominio corretti (questa sarebbe anche una definizione utile per la continuità normale, ma stiamo utilizzando l'equivalenza che ci danno le successioni).

**tutte le funzioni elementari sono continue** (come le hai sempre viste)

Possiamo anche scrivere una funzione di continuità utilizzando gli intervalli (praticamente uguale a quella classica):

$$f: A \to B$$ è continua in $$\bar{x}$$ se ho che $$\iff \forall \epsilon > 0\exists \gamma >0 t.c. \lvert f(y) - f(\bar{x}) \rvert < \epsilon, \text { con } x\in A \lvert x - \bar{x} \rvert < \gamma$$

**OSSERVAZIONI**

si dimostra che tutti gli insiemi definiti con disuguaglianze strette sono aperti.

ovvero $$f_1,...f_n$$ una successione di funzioni $$\mathbb{R}^n \to \mathbb{R}$$, continue si ha che $$A = \{x \in \mathbb{R}^n \mid f_1(x) > c_1, ..., f_n(x) > c_n\}$$  si ha che A è aperto per questo teorema che non si dimostra nel nostro corso, però si ha che è vero.

### Funzione radiale

Una funzione si dice radiale se $$f: \mathbb{R}^2 \to \mathbb{R} t.c. \exists g: [0, +\infty[ \to \mathbb{R}$$ tale che $$f(x,y) = g(\lvert x,y\rvert)$$

**Intuizione**

Ovvero possiamo dire radiale se possiamo scriverlo solo in funzione dalla sua distanza dall'origine (spesso sono **superficie di rotazione**)

Di solito è comodo avere queste funzioni perché mi semplificano subito l'analisi.

Altro esempio: $$f(x,y) = e ^{-(x^2 + y^2)} \implies g(t) = e ^{ -t^2}$$ che basta disegnare g e poi ruotarlo sull'asse delle y.

### Insiemi di livello

Dato un insieme $$A \subseteq \mathbb{R}^2$$ e una funzione $$f: A \to \mathbb{R}$$ e dato un punto $$b \in \mathbb{R}$$ allora si dice insieme di livello $$b$$ di $$f$$ l'insieme $$L_b = \{ (x, y) \in A \mid f(x,y) = b\}$$ in pratica è la **pre-immagine**  della funzione (come se fosse $$f^{-1}$$).

Quindi la stessa cosa in una dimensione, ma col nome diverso, perché dal punto di vista livello, l'insieme di livello è come un taglio del dominio verso un certo punto.

Di solito si trova una **curva di livello,** una curva lineare che rappresenta questo insieme (percorrendo questo punto, il valore in output resta lo stesso, come se mi stessi muovendo parallelamente a una montagna senza salire e senza scendere.

### Piani

I piani sono nella forma $$f(x,y) = ax + by + c$$, è abbastanza ovvio, perché in R2 rappresenta una retta, se ho una retta ma posso variare z come mi pare, allora ovvio che si ha il piano...