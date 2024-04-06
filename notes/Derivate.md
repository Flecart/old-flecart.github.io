---
layout: page
permalink: notes/derivate
tags: en
title: Derivate
---

Ripasso Prox: 75
Ripasso: June 16, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: November 4, 2021 3:59 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - Invertibilità e derivata dell'inversa
    - Fare esercizi e provare derivate particolari.
    - Dimostrazione della formula di mul e div per derivate

# 5 Derivate

## 5.1 Geometria introduttiva

### 5.1.1 Tangente e pendenza

Si può trovare la relazione fra la pendenza della retta e la tangente.

Possiamo analizzare la retta dal punto di vista analitico, della formula e si può dimostrare che data una retta nella forma $$y = mx + q$$ $$m$$ è la pendenza della retta.

### 5.1.2 Formula generale delle rette

Dati qualunque due punti .$$(x_1, y_1), (x_2, y_2)$$ possiamo dire che la pendenza è esprimibile come

$$\dfrac{ (y_2 - y_1)}{(x_2 - x_1)}$$, possiamo anche creare un fascio di rette che passa per un punto come

$$y - y_0 = m(x - x_0) + q$$

### 5.1.3 Intuizione tangente

Per qualunque funzione, possiamo intuitivamente designare la derivata come se fosse il valore della retta tangente in quel punto al grafico.

## 5.2 Definizione

### 5.2.1 Rapporto incrementale

Data una funzione $$f(x)$$, si dice rapporto incrementale di $$f$$ in $$x_0$$ questo valore


$$
\dfrac{f(x) - f(x_0)}{x - x_0}
$$


### 5.2.2 Derivabilità

Allora cerchiamo di minimizzare la distanza fra i due punti che scelgo, allora ho la derivata in questo punto!


$$
\exists\lim_{x \to x_0} \dfrac{f(x) - f(x_0)}{x - x_0} \in \R = \dfrac{df(x)}{dx}
$$


E si può scrivere anche in una altra forma analoga: che è più comoda da gestire perché ho qualcosa che tende a 0


$$
\exists\lim_{h \to 0} \dfrac{f(x + h) - f(x)}{h} = \dfrac{df(x)}{dx}
$$


Se esiste questo limite, allora la funzione è derivabile in quel punto.

**Funzione**

Si dice che una funzione è derivabile se lo è nel suo dominio.

(Per gli estremi destri si considera solamente la derivabilità sinistra, in modo simile anche per gli estremi sinistri)

Se esiste la derivata in questo punto allora si può dire che in questo punto esista una tangente geometrica

### 5.2.3 Derivabilità destra e sinistra

Si dice che una funzione $$f$$ è derivabile a sinistra (in modo analogo a destra se


$$
\exists\lim_{x \to x_0^-} \dfrac{f(x) - f(x_0)}{x - x_0} = \dfrac{df(x)}{dx}
$$


### 5.2.4 Condizioni di derivabilità

Dato che la derivata è un limite, le condizioni di esistenza sono molto simili alle condizioni di esistenza di un limite. (no sono identtivi)

<img src="/images/notes/image/universita/ex-notion/Derivate/Untitled.png" alt="image/universita/ex-notion/Derivate/Untitled">

Si può analizzare la derivabilità delle funzioni utilizzando queste condizioni es:

$$f(x) = |x|$$ si scopre che non è derivabile perché a sinistra è  -1 mentre a destra è +1, si dice che è un punto angoloso (si scopre che per qualunque punto angoloso, questa non è più derivabile)

Bisogna fare però attenzione perché non è vero che ogni valore assoluto non è derivabile perché ad esempio $$x|x|$$  è derivabile.

## 5.3 Proprietà e osservazioni

### 5.3.1 Proposizione della retta tangente

Questa proprosizione collega il concetto di derivata e della tangente.

> Se $$f$$ è derivabile in $$x_0 \in I \implies \exists \text{retta tangente al grafico f in } x_0=x\\
\text{si può dire che abbia equazione} \\
y = f'(x_0)(x - x_0) + f(x_0)$$
>

### 5.3.2 Derivate conosciute

- Derivate

    <img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 1.png" alt="image/universita/ex-notion/Derivate/Untitled 1">


### 5.3.3 Algebra delle derivate

Si possono utilizzare in modo simile l'algebra delle derivate

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 2.png" alt="image/universita/ex-notion/Derivate/Untitled 2">


Derivazione [qui](https://it.wikiversity.org/wiki/Algebra_delle_derivate)

### 5.3.4 Composizione di funzioni

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 3.png" alt="image/universita/ex-notion/Derivate/Untitled 3">


Dimostrazione [qui]([https://www.math-linux.com/mathematics/derivative-of-a-function/article/chain-rule-proof-derivative-of-a-composite-function#:~:text=Derivative%20of%20composite%20function%20](https://www.math-linux.com/mathematics/derivative-of-a-function/article/chain-rule-proof-derivative-of-a-composite-function#:~:text=Derivative%20of%20composite%20function%20)(g,%C3%97%20v'(x)%20.)

### 5.3.5 Continuità e derivabilità

Si può dimostrare che se una funzione è derivabile in un punto allora è continua nel punto stesso.

x punto di accumulazione


$$
\lim_{h \to 0}\dfrac{f(x+h) - f(x)}{h} = l \iff \lim_{h \to 0}\dfrac{1}{h}\cdot(\lim_{h \to 0}f(x+h) - f(x)) = l\\
\iff \lim_{h \to 0}f(x+h) = f(x) + l\lim_{h \to 0}h = f(x)
$$


C'è anche una cosa dimostrazione molto simile.

- Dimostrazione del prof.

    <img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 4.png" alt="image/universita/ex-notion/Derivate/Untitled 4">


### 5.3.6 Derivate di inverse

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 5.png" alt="image/universita/ex-notion/Derivate/Untitled 5">


## 5.4 Derivate di ordine superiori

Una funzione potrebbe essere derivabile più di una volta, allora si dice che si può derivare più volte.

È interessante relazionare questo concetto di derivabilità con il concetto di continuità

### 5.4.1 Continuità classe C

È come classificare una funzione in base la sua regolarità, ossia rispetto a quante volte posso fare la derivata e la continutà di classe C è un buon modo di formalizzare questo dato.

- Continuità di classe C

    !<img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 6.png" alt="image/universita/ex-notion/Derivate/Untitled 6">


Si può notare che una funzione può essere continua in $$C^k$$ ma non in $$C^{k+1}$$.
zare questo dato.

- Continuità di classe C

    !<img src="/images/notes/image/universita/ex-notion/Derivate/Untitled 6.png" alt="image/universita/ex-notion/Derivate/Untitled 6">


Si può notare che una funzione può essere continua in $$C^k$$ ma non in $$C^{k+1}$$.

# References