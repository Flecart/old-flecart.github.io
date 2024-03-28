---
layout: page
permalink: notes/analisi-di-convessità
tags: italian
title: Analisi di Convessità
---

Ripasso Prox: 20
Ripasso: May 22, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: May 2, 2022 3:23 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No


Questo argomento è stato trattato durante dopo la discussione dei [Massimi minimi multi-variabile](/notes/massimi-minimi-multi-variabile), però è stato ripreso anche nella forma R to R, quindi credo necessiti di un foglio a parte.

### Affine set

#### Lines
Let's take two points in $$\mathbb{R}$$ $$x_{1}, x_{2}$$, if we consider the parametrization

$$
x = \theta x_{1} + (1 - \theta)x_{2}
$$

This is a parametrization of the line

Example: 
<img src="/images/notes/Analisi di Convessità-20240327184319876.webp" alt="Analisi di Convessità-20240327184319876">

#### Def: affine set
A combination combinazione lineare where the coefficients **add up to** 1.
We can say that this set is unique given two points.

Example: solution of $$\left\{ x \mid Ax = b \right\}$$ is an affine set (easy to prove).
It can be proven that every affine set is a solution of such set of algorithms

### Convex sets
It's an affine set, where $$0 \leq \theta \leq 1$$. Sometimes it's written like $$\left[ x_{1}, x_{2} \right]$$. Sometimes this is called a **convex combination** of the two values.

- Every element of the set *sees* each other clearly, this is the intuitive notion of the convex sets
<img src="/images/notes/Analisi di Convessità-20240327184850815.webp" alt="Analisi di Convessità-20240327184850815">
#### Convex combination
Given $$x_{1}, x_{2}, \dots, x_{k}$$ then a convex combination is (sometimes called mixture, or weighted average, or expectation)


$$
x = \theta_{1}x_{1} + \dots + \theta_{n}x_{n}
$$

Where $$\theta_{1} + \dots + \theta_{n} = 1, \theta_{i} \geq 0$$

#### Convex Hull
It's the convex combination of all points in $$S$$. (so it's defined by the borders usually).
It can be viewed as the Smallest convex set that contains a set of points!
#### Convex Cone
Here we don ´t have the requirement that it all sums to one.
so $$x_{1}, x_{2}$$, the convex cone is the set of points such that exists $$\theta_{1}, \theta_{2}$$ that

$$
x = \theta_{1}x_{1} + \theta_{2}x_{2}
$$


1. Closed (contains borders)
2. Has an interior (some point in the middle of the borders).
3. Doesn't contain lines (pointed)

#### Norm Cone

$$
\left\{ (x, t) \mid \lVert x \rVert  \leq t \right\} 
$$

Also known as Lorentz cone (probably used for things related to relativity).
#### Positive Semidefinite Cone

Let $$S^{n}$$ be the set of symmetric matrices with $$n$$ elements, of dimension $$\frac{(n + 1)n}{2}$$. $$S^{n}_{++}$$ denotes the positive definite set, with one $$+$$ indicating semidefinite.
<img src="/images/notes/Norme e Condizionamento-20240327205850487.webp" alt="Norme e Condizionamento-20240327205850487">
#### Sublevel set
$$f: \mathbb{R}^{n} \to \mathbb{R}$$ such that:


$$
C_{\alpha} = \left\{ x \in dom f \mid f(x) \leq \alpha \right\} 
$$

It's a function that it's the best limited to a certain value $$\alpha \in \mathbb{R}$$

#### Epigraph of function


$$
epi f = \left\{ (x , t) \in \mathbb{R}^{n + 1} \mid x \in dom f, f(x) \leq t \right\} 
$$


it's the part of the function that is **bigger or equal to the function**.


#### Relation with convex functions
the function $$f$$ is convex iff $$epi f$$  is a convex set.
So if $$f$$ creates a convex set above it, we can say it's convex, this is a bridge between functions and geometry.


## Convessità e Concavità

### Definizione di convessità
Funzione $$f : \mathbb{R}^{n} \to \mathbb{R}$$ è convessa se vale, con $$0 \leq \theta \leq 1$$

$$
f(\theta x + (1 - \theta)y) \leq \theta f(x) + (1 - \theta) f(y)
$$

**Concavo** se $$-f$$ è convesso


L'approccio seguente è quella fatta in analisi, ma è abbastanza brutta.
È convessa se la derivata seconda è diversa da 0, ma non è una buona definizione perché non è direttamente relazionata con la concavità.

Possiamo definire la funzione secondo le tangenti, potremmo dire che la retta tangente sia sempre minore del grafico, in altro modo è una forma di tailor!

$$f: A \to R$$ tale che f sia derivabile, allora se prendo un intervallo $$(a,b) \subseteq A$$ posso dire che la funzione è convessa in questo intervallo se $$\forall x,k \in (a,b)$$ ottengo che

 $$f(x) \geq f(k) + f'(k)(x -k) = T_1(x)$$

**Definizione vera**
Non vorremmo avere una definizione che dipenda dall'esistenza della derivata, quindi
sia f una funzione ben definita, allora è convessa sse $$\exists m$$  nel dominio per cui valga che
$$f(x) \geq f(y) + m(x - y)$$

Oppure:

- Definizione secondo libro (con i segmenti)

    Allora cerchiamo una definizione migliore:

    sia $$f : \mathbb{R}^n \to \mathbb{R}$$ allora questa funzione si dice convessa sse $$\forall t \in [0,1]$$ si ha che

    $$\forall a,b \in \R^n: f(tb + (1 - t)a) \leq t f(b) + (1-t) f(a)$$ se vale con $$<$$ posso dire che è *strettamente convessa.*

    **Intuizione:**

    Comunque prenda un punto all'interno di un intervallo ho che la funzione valutata in questo punto è minore della somma della congiungente di questi due punti.

#### Examples of convex and concave functions

<img src="/images/notes/Analisi di Convessità-20240328135038638.webp" alt="Analisi di Convessità-20240328135038638">

### Convex function to a line

Consider $$g(t) = f(x + tv)$$ where the domain of $$g$$ are the $$t$$ such that $$x + vt$$ are in the domain of $$f$$.
Then $$f$$ is convex iff $$g$$ is.

### First-order condition in $$\mathbb{R}$$

Questo è un risultato molto simile a quanto ottenuto con le funzioni crescenti e la loro derivata prima, che si può trovare in [Teoremi Base Analisi](/notes/teoremi-base-analisi).

**Enunciato**
Sia una funzione $$f: \mathbb{R} \to \mathbb{R}$$, allora $$f$$ è **convessa** sse la sua derivata prima è $$>0$$.

La dimostrazione è abbastanza diretta quindi la si omette. (però la dovresti fare lo stesso perché è importante).
- Hintini di dimostrazione
    $$\implies$$ Supponiamo che f sia convessa, allora vale quella formula in definizione, voglio  dimostrare che la derivata sia crescente. (scrivo quella definizione due volte e ottengo qualcosa del tipo $$0 \geq$$  intervallo * (intervallo funzione, e si può risolvere senza molti problemi ottenendo il voluto, bisogna fare soprattutto attenzione a come definisci questi indici se vuoi andare a farlo in modo formale.
    $$\impliedby$$ Supponiamo che la derivata sia crescente, allora poi vado ad utilizzare lagrange (due volte, prima con un intervallo x y tale che $$x < y$$ e poi il contrario) fatto questo utilizzo la crescenza della derivata per concludere


**Corollario**
Possiamo utilizzare il risultato sopra per concludere che una funzione è convessa sse la derivata seconda è maggiore uguale a 0 (si possono utilizzare i teoremi riguardante le relazioni fra derivate e crescenza per questa).

### Segmento in Rn e convessità di punti

Dati due punti in $$\mathbb{R}^n$$ si può individuare il segmento in due punti $$x, y$$ come l'insieme costituito da

$$\{x + t (y - x) | t \in [0,1]\} = [x, y]$$

SI può verificare che che è uguale alla linea che li collega, in particolare è una **retta parametrica**.
Avendo questa definizione di segmento, posso andare a definire l'insieme convesso per Rn!.

**Convessità di un insieme di punti**

Un insieme di punti si dice convesso se $$\forall a, b \in A \subseteq \mathbb{R}^n, [a,b] \subseteq A$$ (e la definizione di insieme concavo non esiste, potremmo dire non convesso, ma non che sia concavo).

Avendo questo si può dimostrare che l'intersezione di semipiani è convesso.

### First-order condition in $$\mathbb{R}^{n}$$

Possiamo allargare la definizione di funzione convessa che abbiamo dato poco fa in modo che ora sia buona anche a funzioni di più variabili.

f una funzione ben definita, allora è convessa sse $$\forall a,b \in A$$ si ha che

$$f(a) \geq f(b) + \nabla f(b)^{T}(a - b)$$ e per parlare di funzione concava basta rovesciare la disuguaglianza.

Questa formula da l'idea che la funzione deve essere sempre sopra al piano tangente per ogni punto!
Si può vedere come *primo ordine Taylor approx* ad un certo punto.

### Second-order condition in $$\mathbb{R}^{n}$$

sia $$A \subseteq \mathbb{R}^n$$ che sia aperto e convesso, sia $$f\in C^2(A) \to \mathbb{R}$$ allora
$$f$$ è convessa su A $$\iff$$ $$Hf(x) \geq 0, \forall x \in A$$.

Non è definito ora il concetto di crescenza per un gradiente, o vettore, quindi vogliamo passare prima sul gradiente.
Una funzione è convessa sse la matrice hessiana è semi-definita positiva.
Sia la espansione di taylor come l'abbiamo definita prima (con resto secondo Lagrange).
Può essere utile dare un occhiata al teorema di Lagrange al secondo ordine a più dimensioni prima

$$f(w + vt) = f(w) + \langle \nabla f(w), v \rangle t + \dfrac{1}{2}\langle Hf(c)v,v\rangle t^2$$

- Dimostrazione
    $$\impliedby$$
    Dato che $$\dfrac{1}{2}\langle Hf(c)v,v\rangle t^2 \geq 0$$ posso conclude la convessità (ossia la disuguaglianza appare abbastanza in fretta)
    $$\implies$$ Assumiamo ora la convessità, vogliamo dimostrare che la hessiana sia semidefinita positiva. Per l'espansione di taylor ho che  $$f(a + h) = f(a) + \langle\nabla f(a), h\rangle + \dfrac{1}{2}\langle H(f(a + \theta h)) h, h\rangle$$ definendo a, h e theta correttamente.
    Per la convessità ho che $$f(a + h) \geq f(a) + \langle\nabla f(a), h \rangle$$ e questo vale $$\forall h : a + h \in A$$
    Ma allora so che $$\dfrac{1}{2}\langle H(f(a + \theta h)) h, h\rangle \geq 0$$ (perché altrimenti ci sarebbe un valore in input per cui nonvale la condizione di convessità.

    Devo dimostrare che $$v \in \mathbb{R}^n \neq 0 : a + v \in A$$, $$\langle H(f(a)) v, v\rangle \geq 0$$, scelgo una successione in questo modo:
    $$h_k = 1/k \cdot v$$ che tende a 0 per k che tende a infinito.
    Definito in questo modo ho che c'è un theta per cui valga   $$\dfrac{1}{2}\langle H(f(a + \theta v/k)) v/k, v/k\rangle \geq 0 \iff \dfrac{1}{2}\langle H(f(a + \theta v/k)) v, v\rangle \geq 0$$ arrivato a questo punto mando k all'infintio e utilizzo

    Per continuità ho che il limite $$\lim_{k \to \infty}$$ è uguale a  $$\langle H(f(a)) v, v\rangle$$  la permanenza del segno per concludere il voluto (se ogni elemento della successione è maggiore di 0 allora anche il limite a cui sta tendendo è maggiore di 0)

## How to know if a set is convex

### Definition application

Try to prove the [#Convex combination](#convex-combination) theorem.
Aka, $$\forall x_{1}, x_{2} \in C, 0 \leq \theta \leq 1 \implies \theta x_{1} + (1 - \theta)x_{2} \in C$$
But this is the last resort, not advised by prof. Stephen Boyd

### Composition of convex-preserving operations

If we can create the $$C$$ by using this composition we can still have a convex  set!

#### Intersection is convex
> The intersection of convex sets is convex

This is easily provable. 

Example of interesting case:
Consider $$p(t) = x_{1}\cos t + \dots + x_{n}\cos nt$$
The set $$\left\{  x \in \mathbb{R}^{n} \mid \lvert p(t) \rvert \leq 1 : t \in \left[ 0, \frac{\pi}{3} \right] \right\}$$ is convex. (It's easy to show that this is an intersection of slabs (see lecture 2, the idea is beautiful, although not formally defined or proved, but it seems intuitive!))

#### Affine functions are convex preserving
> Affine functions preserve convex sets

If we apply an affine function (that is just linear function + $$b$$) aka : $$f(x) = Ax + b$$.
Because the inverse of affine is affine (if it exist), also the inverse of affine functions are inverse.
This is easy to prove too.

#### Perspective functions are convex preserving
$$P : \mathbb{R}^{n + 1} \to \mathbb{R}^{n}$$ is a perspective function (lower dimensional!)

For example a function is $$P(x, t) = \frac{x}{t}$$

> Images and inverse images of convex sets under perspective are convex

Not sure why is it true.

#### Affine-fractional functions are convex preserving

$$
f(x) = \frac{Ax + b}{c^{T}x + d}
$$

Example of these functions are mapping from 3D in computer geometry to flat camera views.
<img src="/images/notes/Analisi di Convessità-20240327214317752.webp" alt="Analisi di Convessità-20240327214317752">
## Teoremi importanti
### Jensen
Questo è uno dei teoremi legati alla convessità (concavità più usati in assoluto). Una applicazione classica è per il il valore atteso, analizzato in [Variabili aleatorie](/notes/variabili-aleatorie) e simili. La cosa carina è che lui non l'ha inventato, ma ha detto che tipo 14 tizi stavano usando sta cosa, senza chiamarla per nessun nome, quindi l'ha popolarizzato.


Sia $$f$$ una funzione convessa in un intervallo $$[a, b] \subseteq \mathbb{R}$$, allora vale che

$$
f(\lambda a + (1 - \lambda)b) \leq \lambda f(a) + (1 - \lambda) f(b)
$$

Questa è la formulazione semplice, ma si può estendere per qualunque combinazione convessa dell'input (per combinazione convessa di $$a_{1}, a_{2}, \dots, a_{n}$$ intendo $$a_{1}\lambda_{1} + \dots + a_{n}\lambda_{n}$$ dei parametri $$\lambda_{1}, \lambda_{2}, \dots, \lambda_{n}$$ tale per cui $$\sum_{i=1}^{n}\lambda_{i} = 1$$).

Non so bene la dimostrazione, ma l'intuizione è abbastanza semplice in due variabili, se combini due punti su una retta sopra la funzione, questa sarà maggiore del valore che ricevi combinando gli input, dato che è convessa è una funzione ad $$U$$.