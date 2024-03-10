---
layout: page
permalink: notes/analisi-multi-variabile
tags: italian
title: Analisi multi-variabile
---

Ripasso Prox: 20
Ripasso: June 4, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: March 7, 2022 1:34 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

# 9 Analisi multi-variabile

In questo capitolo cerchiamo di andare oltre alla singola dimensione per l'analisi.

## 9.1 Introduzione

### 9.1.1 Lo spazio R^n

Possiamo definire uno spazio **Rn** come il prodotto cartesiano fra l'insieme R un numero di volte uguale a n $$\R \times \R \times ... \times\R = \R^n$$

Allora **un tipico elemento** in Rn è nella forma $$(x_1,...,x_n)$$, questo elemento si chiama punto, mentre gli elelmenti in R che costituiscono questo elemento si chiamano componenti.

**Osservazione**

La maggior parte dei risultati che dimostro nello **spazio ordinario (R3)** si può dimostrare per Rn, non andiamo più nel dettaglio perché i problemi che ho in spazi maggiori sono parte di materiale per analisi 2

### 9.1.2 Operazioni definite

In modo simile a quanto definito negli [Spazi vettoriali](/notes/spazi-vettoriali) abbiamo principalmente due operazioni principali definite (in moto identico a quanto spiegato nell'altro documento) che sono:

1. l'addizione vettoriale
2. la moltiplicazione scalare.

In più aggiungiamo una operazione che non è presente nel documento degli spazi vettoriali ma che è importante in questo momento.

1. Prodotto scalare euclideo, definito qui sotto

### 9.1.3 Il prodotto scalare euclideo (3 + 1)

Dati due elementi in Rn, che chiamiamo x e y, rispettivamente di componenti $$x_1, ...,x_n$$ e $$y_1, ...,y_n$$


$$
\langle x,y\rangle =  x\cdot y\coloneqq\sum_{i=1}^nx_iy_i
$$


Possiamo individuare 3 proprietà principali per questo prodotto scalare (nota il significato x,y con parentesi cambia in algebra lineare rispetto a questo. (chiamo in questo caso x primo argomento e y secondo argomento).

1. **Simmetria**, se scambio x con y il risultato resta lo stesso $$x\cdot y = y \cdot x$$
2. **Distributività (linearità del primo argomento)  $$\forall x,y,z \in \R^n, \forall \lambda, \mu \in \R  (\lambda x + \mu y) \cdot z = \lambda(x\cdot z) + \mu(y \cdot z)$$**
Utilizzando la simmetria puoi dimostrare anche la linearità per il secondo argomento.
3. **Positività del riflessivo:** $$\forall x \in \R^n , x\cdot x \geq 0$$, e si può osservare che $$x\cdot x = 0 \iff x = 0_v$$

**Prodotto scalare nella forma col coseno**

Dato un elemento x in R2, posso dire che $$x = |x| \dfrac{x}{|x|}$$ notiamo che il secondo fattore ha lunghezza 0, quindi possiamo scriverlo tramite una coordinata polare, qualcosa tipo $$\dfrac{x}{|x|} = (\cos \theta, \sin \theta)$$.

Quindi se prendo un $$x \neq 0$$ possiamo dire che $$x = (|x|\cos \theta, |x| \sin \theta), \theta \in \R$$

Allora se prendo due vettori scriviamo così!

$$x \cdot y = |x||y| \cos \theta \cos \gamma + |x||y|\sin \theta\sin \gamma = |x||y|(\cos(\theta - \gamma))$$ che è esattamente la formula che abbiamo visto alle superiori, il prodotto delle singole norme per il coseno dell'angolo fra i due.

### 9.1.4 Ortogonalità

Si può definire l'ortogonalità di due vettori a seconda del risultato del loro prodotto scalare

$$x,y$$ perpendicolari $$\implies x \cdot y = 0$$

Da questo si può notare che  il vettore nullo è perpendicolare a ogni vettore.

### 9.1.5 Norma di un vettore (3 + 2)

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
||x + y||^ 2 = \left( \sqrt{ \sum_{i=1}^n (x_i + y_i) ^2} \right)^2 = \sum_{i=1}^n (x_i + y_i) ^2 = \sum_{i=1}^n (x_i^2 + 2x_iy_i + y_i^2) = ||x||^2 + 2x\cdot y + ||y||^2
$$


Si può anche dimostrare tramite le propreità 2 del prodotto scalare e l'additività, dimostrare in questo modo per esercizio (oppure chiedere a qualcuno che era in classe).

Osservazione:

Si può notare che se i due vettori sono perpendicolari si ritrova il teorema di pitagora in quanto

$$x \cdot y = 0$$

### 9.1.6 Disuguaglianza di Cauchy-Schwarz (+2)

Siano x,y vettori in $$\R^n$$, allora vale che

$$|x \cdot y| \leq |x| |y|$$ dove uguale si ha sse x e y sono dipendenti.

Dimostriamolo nel caso in cui n = 2, per n superiori dovrebbe essere analogo,

prendiamo due valori come [qui](/notes/qui), allora ho che

$$|x \cdot y| = ||x||y|\cos(\theta - \gamma)| \leq |x||y|$$ osservando il coseno, questo è sempre compreso fra -1 e 1 quindi è ovvio che sia sempre minore. ed è ovvio che sono uguali nel momento in cui coseno è 0, quindi i due vettori sono dipendenti.

**Dimostrazione disuguaglianza triangolare da CS**

$$|x + y| \leq |x|  + |y| \iff |x\cdot y| \leq |x| |y|$$ fai il prodotto e guarda i calcoli

- Prodotto e calcoli

    $$| x + y| \leq |x|  + |y| \implies |x + y|^2 \leq (|x|  + |y|)^2 \implies  |x|^2 + 2x\cdot y + |y| ^2 \leq |x|^2  + 2|x||y| + |y|^2$$ e cancellando opportunamente nell’ultimo passaggio, è banale la deduzione.


**Teorema di pitagora**

Anche questa è una derivazione senza molti problemi in quanto basta la forma del quadrato della norma e il fatto che sono perpendicolari per dire che è uguale a 0.

### 9.1.7 Distanza fra due punti

Possiamo definire la distanza fra due punti come la **norma del vettore differenza**:

$$Dist(x, y) = \lVert x - y \rVert$$ (il che ha senso, perché la differenza mi da un vettore differenza, mentre la norma mi da la lunghezza di questo vettore, ignorando il verso e la direzione, quindi riesco ad ottenere una distana).

## 9.2 Insiemi e intorni

### 9.2.1 Intorno sferico

Andiamo a definire la nozione di **intorno sferico**

$$I_r(x)$$ è l'insieme di punti che distano al più r da x, ossia $$\{y \in \R^n ,t.c., |x - y| < r\}$$

Si può notare poi che questa forma dal punto di vista geometrico definisce una sfera in 3 dimensioni, un disco in 2, un intervallo in 1. Analogamente si possono definire i punti di un cerchio con più dimensioni in questo modo.

### 9.2.2 Insieme limitato

Un insieme $$A$$ si dice limitato se $$\exists k > 0, k \in \R,$$  $$A \subseteq I_k(0)$$. Quindi è contenuto all'interno di una area ben definita.

Una funzione che ha dominio fino ad infinito per esempio 1/x  non è limitato perché non riesco mai a rinchiuderlo, ma una macchia a caso invece si può racchiudere.

### 9.2.3 Insieme aperto

Un insieme si dice aperto se per qualunque punto esiste un contorno abbastanza piccolo che è contenuto nell'insieme (cosa che non succede per un insieme chiuso, se prendo un punto nel bordo non trovo tale intorno).

## 9.3 Successioni generali

### 9.3.1 Definizione

$$(x_n)_{k \in \N}: x_k \in \R^n, \forall k \in \N$$ si potrebbe quindi sempre vedere come una funzione che va da $$\N \to \R^n$$



### 9.3.2 Convergenza delle successioni (classica)

Una successione converge in un punto in Rn, se ogni suo componente tende alla componente corrispondente del punto di convergenza.

Es, suppongo che f tenda a un $$x_0, y_0$$ allora voglio dire che il limite per x tende a x0, anche limite per y tende a y0.

### 9.3.3 Convergenza secondo distanza

Se si utilizza la convergenza secondo la nozione di stanza, allora questo assume una forma molto simile alla nozione di convergenza per i numeri reali.

$$x_k \to x \in \R^n \iff |x_k - x| < \epsilon, \forall \epsilon >0$$ ossia quella distanza tende a 0.

## 9.4 Funzioni con più variabili

### 9.4.1 Definizione

$$A\subseteq \R^n  , B \subseteq \R^n, f: A \to B, ,,Graf(f) = \{(x, f(x)) \in A \times B \}$$ quindi alla fine è sempre la classica definizione di insieme, ma con dominio e codominio diversi

$$Im(f) = (f(x) | x \in A)$$

### 9.4.2 Categorie di funzioni

**Funzioni scalari**

$$\R^n \to \R$$

**Funzioni curve o cammini**

$$\R \to \R ^n$$

### 9.4.3 Continuità (+ 1)

$$\forall (x_k)_{k \in \N} x_k \to x, \text { si ha che } f(x_k) \to f(x)$$ rispettivamente utilizzando i domini e codominio corretti (questa sarebbe anche una definizione utile per la continuità normale, ma stiamo utilizzando l'equivalenza che ci danno le successioni).

**tutte le funzioni elementari sono continue** (come le hai sempre viste)

Possiamo anche scrivere una funzione di continuità utilizzando gli intervalli (praticamente uguale a quella classica):

$$f: A \to B$$ è continua in $$\bar{x}$$ se ho che $$\iff \forall \epsilon > 0\exists \gamma >0 t.c.|f(y) - f(\bar{x})| < \epsilon, \text { con } x\in A |x - \bar{x}| < \gamma$$

**OSSERVAZIONI**

si dimostra che tutti gli insiemi definiti con disuguaglianze strette sono aperti.

ovvero $$f_1,...f_n$$ una successione di funzioni $$\R^n \to \R$$, continue si ha che $$A = \{x \in \R^n | f_1(x) > c_1, ..., f_n(x) > c_n\}$$  si ha che A è aperto per questo teorema che non si dimostra nel nostro corso, però si ha che è vero.

### Funzione radiale

Una funzione si dice radiale se $$f: \R^2 \to \R t.c. \exists g: [0, +\infty[ \to \R$$ tale che $$f(x,y) = g(|x,y|)$$

**Intuizione**

Ovvero possiamo dire radiale se possiamo scriverlo solo in funzione dalla sua distanza dall'origine (spesso sono **superficie di rotazione**)

Di solito è comodo avere queste funzioni perché mi semplificano subito l'analisi.

Altro esempio: $$f(x,y) = e ^{-(x^2 + y^2)} \implies g(t) = e ^{ -t^2}$$ che basta disegnare g e poi ruotarlo sull'asse delle y.

### Insiemi di livello

Dato un insieme $$A \subseteq \R^2$$ e una funzione $$f: A \to \R$$ e dato un punto $$b \in \R$$ allora si dice insieme di livello $$b$$ di $$f$$ l'insieme $$L_b = \{ (x, y) \in A | f(x,y) = b\}$$ in pratica è la **pre-immagine**  della funzione (come se fosse $$f^{-1}$$).

Quindi la stessa cosa in una dimensione, ma col nome diverso, perché dal punto di vista livello, l'insieme di livello è come un taglio del dominio verso un certo punto.

Di solito si trova una **curva di livello,** una curva lineare che rappresenta questo insieme (percorrendo questo punto, il valore in output resta lo stesso, come se mi stessi muovendo parallelamente a una montagna senza salire e senza scendere.

### Piani

I piani sono nella forma $$f(x,y) = ax + by + c$$, è abbastanza ovvio, perché in R2 rappresenta una retta, se ho una retta ma posso variare z come mi pare, allora ovvio che si ha il piano...

| 19/03 | Tutto apposto per questo capitolo direi, basta avere definizioni messe bene. |
| --- | --- |
| 19/04 | Ripassato insieme a Simo, per la maggior parte degli argomenti è chiaro anche se uno studio individuale (simo non è buon compagno di studi bruh) farebbe meglio |
|  |  |
|  |  |
passato insieme a Simo, per la maggior parte degli argomenti è chiaro anche se uno studio individuale (simo non è buon compagno di studi bruh) farebbe meglio |
|  |  |
|  |  |