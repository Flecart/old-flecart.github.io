---
layout: page
permalink: notes/successioni
tags: italian
title: Successioni
---

Ripasso Prox: 55.81
Ripasso: May 20, 2022
Ultima modifica: October 8, 2022 12:09 PM
Primo Abbozzo: October 11, 2021 6:14 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Interrogare sé stessi se abbiamo capito con esattezza il significato di limite, vedere se lo abbiamo imparato a memoria oppure meno, chiedersi del perché lo si abbia definito in questo modo.

# 3 Successioni e Limiti

## 3.1 Successioni


$$
\begin{cases}
f: \mathbb{N} \to \mathbb{R} \\
n \to f(n) \\
\{a\}_{n \in \mathbb{N}} \vee a_n
\end{cases}
$$

È una funzione che mappa dai naturali ai Reali indicata spesso solamente come

$$
\left\{ a \right\} _{n \in \mathbb{N}}
$$


### 3.1.1 Immagine e successione

> L'immagine di una successione (l'insieme dei suoi elementi) **non è una successione!** la successione è anche ordinata.
>

### 3.1.2 Limitazioni della successione

Come per gli insiemi si può definire se **l'insieme è limitato superiormente, inferiormente o entrambi**, a seconda di come lo definiamo in questo modo possiamo poi farci altri ragionamenti

Per decidere se esiste questo limite, continui a fare gli stessi ragionamento sul maggiorante e minorante come per gli insiemi.

Se uniamo l'essere superiormente o inferiormente limitato con la monotonia allora possiamo unire questa con il concetto di **convergenza a un limite finito**.

### 3.1.3 Monotonia delle successioni

Le successioni possono essere **crescenti, descrescenti.**

La definizione di queste successioni è lasciata al lettore.

## 3.2 Limiti di successioni

### 3.2.1 Intuizione

Mi **posso arrivare a un certo valore di quanto mi pare**, del singolo valore che mi pare so che esiste sempre un valore che mi posso avvicinare.

### 3.2.2 Limite Convergente

Si definisce un limite per x che tende all'infinito di una successione $$a_ n$$ in questo modo:


$$
L=\lim_{x\to\infty} a_{n}:=\forall \epsilon\in \R^+, \exists n_0\in \N^*,\forall n \in \N:n \geq n_0 \implies |a_n - L| < \epsilon
$$


### 3.2.3 Limiti divergenti

Ossia per qualunque  k, posso andare a cercare un $$n_0$$ da qui in poi la successione è sempre maggiore, posso scegliere come mi pare


$$
\infty = \lim_{ x\to +\infty} a_ n:= \forall k\in \R^+, \exists n_0\in \N^*,\forall n \in \N:n \geq n_0 \implies a_n \geq k
$$



$$
-\infty = \lim_{ x\to +\infty} a_ n:= \forall k\in \R^+, \exists n_0\in \N^*,\forall n \in \N:n \geq n_0 \implies a_n \leq k
$$


- Nota di italiano

    SI può dire solamente se una **successione tende** ma non puoi mai dire che il limite tende a qualcosa, perché il limite è definito come un certo valore.


### 3.2.4 Limiti finiti

Questa definizione di limite di rifà al concetto di intorno, ed è un limite valutato su un unico punto
![https://wikimedia.org/api/rest_v1/media/math/render/svg/057d94a7aef9a27c4ba3aa20605828d98b93b809](https://wikimedia.org/api/rest_v1/media/math/render/svg/057d94a7aef9a27c4ba3aa20605828d98b93b809)

### 3.2.5 Limiti su successioni monotone !!!

Sia data una successione crescente $$a_n$$, allora $$\lim_{x \to \infty} = \sup \{a_n | n \in \N\}$$

Simile per successioni decrescenti

**Dimostrazione**

Dimostriamo ora per il caso decrescente.

Allora il limite $$L$$ è o finito, o è $$-\infty$$.

Caso 1 $$L = -\infty$$:

La successione non ha un limite inferiore, quindi **non esistono dei minoranti** per questo insieme, allora $$\forall k >0 \implies \exists n_0 : a_{n_0} < k$$ allora essendo la successione decrescente abbiamo che $$\forall n : n\in\N, n < n_o \implies a_n < a_{n_0}$$ quindi $$a_n < k$$ per ogni n minore di $$n_0$$ ciò è sufficiente per dimostrare la tesi dell'esistenza del limite divergente

Caso 2 $$L$$ finito:

dobbiamo dimostrare che $$-\epsilon \leq |a_n - L| \leq \epsilon \iff L - \epsilon \leq a_n \leq L + \epsilon$$ ma sappiamo in quanto $$L$$ è un minorante che vale $$L - \epsilon \leq a_n$$, consideriamo ora, $$L + \epsilon$$, non essendo un minorante, deve esistere un $$a_{n_0} < L + \epsilon$$ allora essendo la successione decrescente abbiamo che $$\forall n : n\in\N, n < n_o \implies a_n < a_{n_0}$$ , quindi esiste un $$n_0$$ tale per per ogni $$n$$ minore di quello vale la sufficienza per il limite.

## 3.3 Algebra dei limiti

- Ipotesi e tesi di ciò

    <img src="/images/notes/image/universita/ex-notion/Successioni/Untitled.png" alt="image/universita/ex-notion/Successioni/Untitled">


### 3.3.1 Somma limiti finiti

Siano $$a_n , b_n$$ successioni con limite finito $$l_1,l_2$$, allora il limite di $$a_n + b_n$$ è $$l _1 + l_2$$.

 $$-\epsilon_a \leq a_n - l_1 \leq \epsilon_a$$

allora $$-\epsilon_b \leq b_n - l_1 \leq \epsilon_b$$

allora $$-\epsilon_a -\epsilon_b \leq a_n - l_1  + b_n - l_1\leq \epsilon_a +\epsilon_b$$ e ciò finisce la dimostrazione.

### 3.3.2 Somma limiti

Se usiamo un limite tale che una dei due è infinito e hanno lo stesso segno allora abbiamo quello che abbiamo.... Guarda le slides!

### 3.3.3 Prodotto dei limiti finiti

### 3.3.4 Prodotto di limiti infiniti

### 3.3.5 Forme indeterminate somma e prodotto e divisione

Somma di $$+\infty-\infty$$ oppure il contrario.

$$0 \cdot \pm\infty$$

Qualunque divisione fra infiniti .

## 3.4 Numero di Nepero

### 3.4.1 Necessità per dimostazioni

Per dimostrare l'esistenza del numero di Nepero come


$$
\lim_{n \to \infty} (1 + \dfrac{1}{n})^n = e
$$


Devo dimostrare in particolare due cose:

1. Crescenza della funzione
2. Limitatezza della funzione (ricorda che per questa proprietà ho che una successione crescente o è limitata e ha limite finito o è divergente)

### 3.4.2 La disuguaglianza di Bernoulli

- La tesi e ipotesi della disuguaglianza di Bernoulli

    <img src="/images/notes/image/universita/ex-notion/Successioni/Untitled 1.png" alt="image/universita/ex-notion/Successioni/Untitled 1">


**Dimostrazione:**

Si ha una dimostrazione per induzione

**PB:**

$$n = 0 \implies 1 \geq 1$$ Verificato

Supponiamo che valga per n, dobbiamo dimostrare che

$$(1 + x) ^{n + 1} \geq 1 + x + nx$$

$$(1 + x) ^{n + 1} \geq (1 + x)(1 + nx) = 1 + nx + x + nx^2$$ ovvio che sia maggiore della parte di destra, per cui è dimostrato.

### 3.4.3 Crescenza della successione

La successione è strettamente crescente, con 2 pagine e mezzo di calcoli.

Prima dimostri che la divisione fra due numeri successivi della sequenza sia $$> 1$$, poi fai i calcoli, in modo strano, facendo delle mosse anche intelligenti per quanto riguarda togliere e aggiungere degli uno e finisci a dire che vale.

### 3.4.4 Limitatezza della successione

Questa dimostrazione si dimostra espandendo la definizione con il binomio di Newton, in seguito si devono avere queste seguenti osservazioni interessanti:

1. Semplificare  $$\dfrac{n(n-1)...(n-k+1)}{n^k}$$ dicendo che è minore di 1, in quanto tutti i $$k$$ fattori al numeratore sono minori del denominatore.
2. Semplificare il restante $$\dfrac{1}{k!}$$ con le somme telescopiche (usando la disuguaglianza 1/k! ≤ della somma telescopica) e dimostrare che è finito.

Si dimostra quindi che l'upper bound è 3.