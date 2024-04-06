---
layout: page
permalink: notes/limiti
tags: en
title: Limiti
---

Ripasso Prox: 80
Ripasso: June 30, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: October 28, 2021 4:56 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# 4 Limiti

Riguardare [Successioni](/notes/successioni) per avere primo attacco sui limiti

## 4.1 Limiti finiti al finito

### 4.1.1 Intorno sferico

Dato l'insieme $$\R$$ si definisce l'intorno sferico aperto di $$x \in \R$$ di raggio $$r \in \R$$ l'insieme
 $$I_r(x) = (x -r, x + r)$$ questa nozione è molto importante per definire il limite. Lo useremo subito su un punto di accumulazione

### 4.1.2 Punto di accumulazione

Un punto di accumulazione $$x$$ di un insieme $$A \subseteq \R$$ è un punto tale per cui mi posso avvicinare in modo indefinito  in quel punto. Infatti deve $$\forall r > 0 \in R, \exists x_ 1 \in A : x_1 \in I_r(x) \wedge x_1 \not= x$$ ossia per cui $$A \cap I_r(x) \not= \empty$$.

Ecco che se mi avvicino in modo indefinito, possiamo definire per bene il limite tra poco.

### 4.1.3 Accumulazione per successioni

Un punto si può definire di accumulazione per una successione $$a_n$$ se si ha che

$$\lim_{n\to\infty} a_n = x$$ con x punto di accumulazione. e $$\forall n \in \N, a_n \not= x$$

### 4.1.4 Limite finito

Questo è il limite finito per una funzione


$$
\forall \epsilon > 0, \exists \delta \in\R: 0<|x-x_0| < \delta \implies |f(x) -y| < \epsilon
$$


In pratica comunque prendo un valore vicino al valore y di limite, (quindi sto definendo la mia $$\epsilon$$ deve esistere sempre un $$\delta$$  tale che valga quella roba.

La soluzione tipica per la dimostrare di tale cosa è partire dalla tesi e scomporla, trovare che se x appartiene a un certo intervallo continuo allora possono sempre trovare un sottoinsieme di questo intervallo che sia  $$\delta$$.

## 4.2 Teoremi dei limiti

### 4.2.1 Permanenza del segno

Se il limite positivo allora esiste un x per cui f(x) è positivo, ma lo dovresti dimostrare (dovrebbe essere ovvio considerando l'intorno di $$\delta$$ per cui vale $$\varepsilon$$

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Limiti/Untitled.png" alt="image/universita/ex-notion/Limiti/Untitled">


### 4.2.2 Carabinieri

Quando una funzione si possa schiacciare all'interno di due altre funzioni ha lo stesso limite. Questo in modo intuitivo ma si potrebbe fare anche molto di più...

### 4.2.3 Alcuni limiti notevoli (!)

$$\lim_{x\to0}\sin(x) = 1$$ con i carabinieri per 0 e x

$$\lim_{x\to0} \cos(x) = 0$$ con duplicazione e altre osservazioni

$$\lim_{x\to0}\dfrac{sin(x)}{x} = 1$$

$$\lim_{x\to0} \dfrac{e^x - 1}{x} = 1$$

Queste sono i limiti notevoli di base per trigonometriche e esponenziali (o logaritmiche)

Esistono anche alcuni limiti notevoli riguardanti il confronto fra le funzioni polinomiali, esponenziali o fattoriali.

### 4.2.4 Dimostrazione perimetro e area cerchio (!)

Ti ricordi come si fa la dimostrare il valore dell'area e del perimetro del cerchio utilizzando il limit e noto?

## 4.3 Limiti finiti all'infinito

### 4.3.1 Definizione

Definiamo il limite di una funzione x tende a x_0 è uguale a più o meno infinito nel caso in cui:


$$
\lim_{x\to x_0} f(x) = +\infty \iff \forall M \in \R, \exists \delta : 0<|x-x_0| < \delta \implies f(x) >M
$$


In modo simile si può dire per il limite che tende a un valore infinito negativo

### 4.3.2 Limiti destri e sinistri

È molto simile alla definizione normale di limite, ma solo che invece di considerare un intorno completo di x debbo avere una parte, quindi invece di $$0 < \lvert x-x_0 \rvert< \delta$$  ho che deve essere che $$x_0 - \delta < x < x_0$$ per intorni sinistri e in modo simile per intorni destri ho che $$x_0 < x < x_0 + \delta$$

Il resto della definizione è tutto uguale.

### 4.3.3 Relazione limite e l destro e l sinistro

Si potrebbe dimostrare questa proprietà:


$$
 \lim_{x \rightarrow x_0} f(x)= L \iff
\begin{cases} \exists \displaystyle{\lim_{x \to x_0^-}f(x)}, \exists\displaystyle{\lim_{x \to x_0^+}f(x)}\\ \displaystyle{\lim_{x \rightarrow x_0^-}f(x)}=\displaystyle{\lim_{x \rightarrow x_0^+}f(x)}=L \end{cases}
$$


## 4.4 Limiti all'infinito

Si possono trovare 3 casi:

$$\forall \varepsilon, \exists \delta= \delta(\varepsilon) > 0 : \forall x \in A : x > \delta$$


$$
\lim_{x\to +\infty} f(x) = \begin{cases}
l \iff |f(x) - l| < \epsilon \\
+\infty \\
- \infty
\end{cases}
$$


### 4.4.1 Esercizi algebra dei limiti

<img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 1.png" alt="image/universita/ex-notion/Limiti/Untitled 1">

### 4.4.2 Limiti di polinomi

Si dimostra che per limite di x tendente a x0 con la funzione lineare che è uguale a x, poi si espande questo con i teoremi di algebra dei limiti e la moltiplicazione con le costanti in modo che il limite dei polinomi sia coincidente con il limite degli addendi moltiplicazioni e simili.

Con la definizione di limite fatta in seguito si ha che tutti i polinomi sono continui nel proprio dominio naturale.

## 4.5 Funzione continua

### 4.5.1 Definizione

$$\forall x_0 \in A, A \subseteq \R$$ allora deve essere che

$$x_0 \not\in D(A)$$ con $$D(A)$$ l'insieme dei punti di accumulazione di A.


$$
x_0 \in D(A) \implies \lim_{x \to x_0}f(x) = f(x_0)
$$


con il limite definito come prima.

E si scrive in questo modo $$f \in C(A)$$, data una funzione nello spazio di funzione $$A^\R$$

**Osservazioni**

La continuità di una funzione è interessante perché definisce una regolarità della funzione.

(anche se significa anche che possiamo tracciare la funzione senza lasciare la matita dal foglio).

### 4.5.2 Continuità destra e sinistra

Dalla definizione di funzione continua espansa si può dedurre che


$$
\lim_{x \to x_0}f(x) = f(x_0) \begin{cases}
\exists\lim_{x\to x_0} f(x) \\
\exists\lim_{x\to x_0^+} f(x),\exists\lim_{x\to x_0^-} f(x),\\
\lim_{x\to x_0^+} f(x) = \lim_{x\to x_0^-} f(x), = \lim_{x\to x_0} f(x)
\end{cases}
$$


### 4.5.3 Continuità per inverse

- Dimostrazione (non richiesta)

Non viene dimostrato ma, se è definita una funzione continua per una certa funzione, allora è continua anche la sua inversa. Per qualche motivo magico.

Questo teorema è importante per la dimostrazione della derivabilità dell'inversa (quindi per avere una base per dimostrare la derivabilità dell'inversa

## Teorema degli zeri

### Lemmi preliminari per THZero

**Primo (dim)**

- Enunciato
    <img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 2.png" alt="image/universita/ex-notion/Limiti/Untitled 2">


sia data una successione bn appartenente a $$\R$$ sempre positiva o sempre negativa tale che il limite di bn appartiene a $$\R$$ allora il limite ha lo stesso segno della successione o è nulla.

Si dimostra per assurdo ponendo il limite il contrario (si apre poi il limite e si sceglie un epsilon carino che mi porti a questa contraddizione).

**Secondo (no dim)**

<img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 3.png" alt="image/universita/ex-notion/Limiti/Untitled 3">


Data una funzione da A a $$\R$$, prendiamo x un punto di accumulazione di A tale che f sia continua in questo punto allora. Per ogni successione xn appartenente ad A che converga a x si ha che f(xn) tende a f(x)´´

### 4.6.2 THZero

data una funzione continua in [a,b] in R allora se $$f(a)f(b) < 0 \implies \exists c \in  ]a,b[ : f(c) = 0$$

Ossia, in modo intuitivo, dato un rettangolo tagliato da una linea, se prendo due punti nelle due parti, allora se provo a congiungere questi due punti si ha che deve tagliare la linea in almeno un punto.

**DIM**


$$
\lim a_n = \lim b_n = c\\
f(c) = 0
$$


Bisogna dimostrare queste due cose.

Si utilizza una divisione diadica in due parti, un algoritmo di costruzione costruttiva.(se l'algoritmo finisce è banale.

Voglio costruire due successioni, una sempre negativa una sempre positiva, entrambi devono tendere a 0, così lo trovo.

- Proprietà di queste successioni

    <img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 4.png" alt="image/universita/ex-notion/Limiti/Untitled 4">


Da queste proprietà ho ottenuto che entrambe le successioni sono limitate e sono crescenti o decrescenti, quindi per dimostrazione precedente esiste un limite che non conosciamo.

Una cosa molto interessare da considerare è la successione

$$a_n - b_n = \dfrac{a - b}{2^{n-1}}$$ che tende a 0. Poi insieme al teorema di convergenza dei limiti.

$$a_n$$ si può dire che è una approssimazione dal basso mentre $$b_n$$ è una approssimazione dall'alto

Poi utilizzando il lemma 1 e il lemma 2 si può concludere che, dato c questo limite che $$f(a_n) = f(c) \leq 0$$  e che $$f(b_n) = f(c) \geq 0$$ e quindi abbiamo dimostrato che esiste $$f(c) = 0$$

Costruttiva → Ho un metodo di approssimazione

### 4.6.3 THZero e polinomi

Nei polinomi di grado dispari si può notare che il limite del polinomio che tende a +infinito va a +infinito, uguale il contrario, grazie al thzero si può concludere che deve avere necessariamente uno zero (si può dimostrare anche la continuità di questo! È algebra dei limiti)

> Ogni polinomio di gradi dispari ha almeno una radice Reale.
>

## 4.7 Weierstrass e Valore intermedio

### 4.7.1 Weierstrass (Estremi finiti)

Studia il concetto di punto di massimo o minimo assoluto [qui](/notes/qui). In particolare dice che esistono quei due punti per funzioni:

1. Dominio limitato e chiuso
2. Funzione continua
- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 5.png" alt="image/universita/ex-notion/Limiti/Untitled 5">

- Dimostrazione (non richiesta)

### 4.7.2 Weierstrass riformulato

Quello che dice in più è che l'immagine della funzione coincide con il massimo e minimo assoluto.

Si dovrebbe dimostrare con weiestrass di prima e thzeri.

$$\forall y \in codominio, \text{considero } g(x) = f(x) - y$$ e poi utilizzo il teorema degli zeri per dire che esiste un x per cui $$g(x) = 0 \iff f(x) = y$$ e quindi ho trovato un x per cui vale.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 6.png" alt="image/universita/ex-notion/Limiti/Untitled 6">


### 4.7.3 Teorema del valore intermedio

- enunciato

    <img src="/images/notes/image/universita/ex-notion/Limiti/Untitled 7.png" alt="image/universita/ex-notion/Limiti/Untitled 7">


La dimostrazione è equivalente a Weierstrass riformulato.



# References