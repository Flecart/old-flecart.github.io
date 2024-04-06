---
layout: page
permalink: notes/r-e-intervalli
tags: en
title: R e Intervalli
---

Ripasso Prox: 50.31
Ripasso: May 18, 2022
Ultima modifica: October 8, 2022 12:09 PM
Primo Abbozzo: October 11, 2021 6:08 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

- dimostrazione esistenza e unicità della radice, qui un pò di difficoltà (ti sei totalmente dimenticato del vincolo di voler avere cose maggiore di 0)
- Ho messo .31 ho fatto 50 l'ultima volta anche però l'esame è vicino e non avrebbe molto senso rifare dopo...

# 2 R e Intervalli

## 2.1 Necessità e caratteristiche di R

### 2.1.1 Radici di N non perfetti e Q

<img src="/images/notes/image/universita/ex-notion/R e Intervalli/Untitled.png" alt="image/universita/ex-notion/R e Intervalli/Untitled">

$$\sqrt{n} \in \mathbb{Q} \implies n \text{ è quadrato perfetto}$$

Fai lemma della divisibilità fra due numeri

**Lemma:**
Dati $$m,n,l$$ tali che $$MCD(m,l)=1$$ e $$l | m n$$ allora  allora $$l | n$$
Questo si risolve con ragionamenti sui fattori di m e n.
Per dimostrare che è razionale la radice di solamente una radice perfetta parto da un numero razionale, faccio certi ragionamenti e scoprirò alla fine che il numero deve essere una radice perfetta.

Questo teorema si può ancora estendere con questo:
- Esercizio (dimostrare)
    <img src="/images/notes/image/universita/ex-notion/R e Intervalli/Untitled 1.png" alt="image/universita/ex-notion/R e Intervalli/Untitled 1">


### 2.1.2 Necessità di R

Per dimostrazione del punto precedente, ci sono un sacco di lacune in quanto la maggior parte delle radici non appartiene a Q. C'è bisogno di un insieme che operi bene al limite, cosa che con Q non va bene.

**Intuizione di R**

Aggiungere a Q tutti i punti di cui mancano. Si dice che R è **Continuo**

- Esempio inefficacia di Q

    <img src="/images/notes/image/universita/ex-notion/R e Intervalli/Untitled 2.png" alt="image/universita/ex-notion/R e Intervalli/Untitled 2">

    In questo esempio l'esistenza di un $$sup$$ c'è solo in R perché in Q la radice di due non è presente e quindi non c'è...


**Caratteristican unica**

*Supremum property* esiste sempre il limite superiore o inferiore di un insieme ,questo non succede anche per Q.

### 2.1.3 Completezza di R


$$
\forall A:A\neq\empty \implies A\in \R
$$


Si ottiene completando Q con i pezzi mancanti, per farlo si deve introdurre il concetto di Continuità → Intervalli

Questa proprietà di R è molti importante perché **permette di avere sup e inf**  definiti in seguito [qui](/notes/qui)

### Innumerabilità di R

**Cardinalità**

Si può affermare che la cardinalità di R sia molto maggiore di N, infatti si può dimostrare che è innumerabile grazie

Cantor, si fa la costruzione a tabella e si dimostra che non è suriettiva, ovvero che nell'intervallo $$[0,1[$$ esiste un numero che non è mai raggiunto da un numero naturale, infatti riesco a costruire un numero che sia diverso in una cifra da tutti i numeri decimali in tabella.
Questa è la dimostrazione più semplice di Cantor.

Un altro argomento insiemistico lo puoi trovare qui [Relazioni fra insiemi#Diagonalizzazione di Cantor](/notes/relazioni-fra-insiemi#diagonalizzazione-di-cantor).
### 2.1.5 Esistenza unicità della radice

[File per pdf di lezione per questa](https://www.dropbox.com/s/uei17il1wnc43bh/11-10-2021-Analisi.pdf?dl=0)


$$
\forall a \in \R_+, \forall n \in \N - \{0\} ,\exists !b \in \R_+ : b^n = a
$$


Si indica con $$^n\sqrt{a} = b$$

Una serie di lemmi utili per la dimostrazione:

- Lemmi
    1. $$x^n \geq y^n \implies x \geq y$$
    2. $$x^n \leq y^n \implies x \leq y$$
    3. $$x ^n = y^n \implies x = y$$
    4. $$x^n < y \implies \exists \epsilon ,(x + \epsilon) ^n < y$$
    5. $$x ^n > y \implies \exists\epsilon (x - \epsilon)^n > y$$

NOTA: per dimostrare i lemmi potrebbe essere molto più semplice provare a dimostrare prima per $$n = 2$$ e poi estendere da questo e poi passando per n generalizzatot

Sapendo di tutti questi lemmi si può dimostrare esistenza ed unicità della radice n-esima.

Per l'unicità basta utilizzare il lemma numero 3 (che si dimostra utilizzando i lemmi 1 e 2)

Per dimostrare l'esistenza della radice bisogna dimostrare l'assurdo che la radice sia minore di quello e maggiore di quello (quello nel senso di 4 e 5)

Per farlo si parte dalla continuità di R creando prima un insieme in cui il sup è x, e da lì dimostrare che è assurdo che la radice sia diversa da quello

**Dimostrazione:**

Sia $$A := \{x \in \mathbb{R} \mid x^2 \leq b\}$$ devo dimostrare che esiste ed è unico la radice a: $$a ^2= b$$

Allora pongo per assurdo che non esiste tale radice, quindi devo dimostrare l'assurdo per $$a ^2 < b \wedge a ^2 > b$$.

Poniamo $$a$$ come il sup dell'insieme A, cosa che esiste dato che è superiormente limitato. (poi usiamo i lemmi 4 e 5)

Caso 1:

$$a^2 < b \implies (a + \epsilon) ^2 < b \implies a + \epsilon  \in A \implies a + \epsilon < a \implies absurd$$

Caso 2:

$$a^2 > b \implies (a - \epsilon)^2 > b \implies a - \epsilon \not\in A \implies a - \epsilon \geq a \implies absurd$$

Quindi esiste la radice.

Per dimostrare che sia unico mi basta usare il lemma 3

## 2.2 Intervalli, Maggioranti ed estremi

### 2.2.1 Intervalli

- Intervalli

    <img src="/images/notes/image/universita/ex-notion/R e Intervalli/Untitled 3.png" alt="image/universita/ex-notion/R e Intervalli/Untitled 3">


### 2.2.2 Maggioranti o minoranti

Un maggiorante (o minorante) è un elemento che è maggiore (o minore di tutti gli elementi) di un certo insieme.

### 2.2.3 Limitatezza

Un insieme è maggiormente o inferiormente limitato se esiste un maggiorante o un minorante di un insieme.

> Se un insieme è sia maggiormente sia inferiormente limitato si dice che è **limitato**
>

### 2.2.4 Estremi (superiori ed inferiori)

Un estremo è definito in questo modo, che funziona anche per i razionali.


$$
l = sup  X \iff
\begin{cases}
\forall x \in X , l \geq x \\
\forall\epsilon : \epsilon > 0,\exists x \in X, l-\epsilon \leq x    \\
\end{cases}
$$


1. l è un maggiorante
2. l è anche il più piccolo dei minoranti.

In modo simile si può definire la parte inferiore.

Detto in altre parole il sup è il minimo dell'intero insieme dei maggioranti, se esiste questo insieme

### 2.2.5 Massimi e minimi di insiemi

Dato un $$x \in X, x:= _{min} \forall y: y\in X \implies x \leq y$$

E in modo simile i massimi.

Si può mettere in relazione massimi e minimi fra di loro, quindi posso dire che:

**Se esiste il minimo, questo è il MASSIMO fra tutti i minoranti**.

### Punto di massimo e minimo

Questa parte sarà utile per weierstrass.

P**Massimo:**

$$f:X \to\R$$ si dice punto di massimo $$x$$ se:

$$\forall x_0 \in X, f(x) \geq f(x_0)$$

P**Minimo**

$$f:X \to\R$$ si dice punto di massimo $$x$$ se:

$$\forall x_0 \in X, f(x) \leq f(x_0)$$



<aside>
💡 Stai molto attento a non confondere il punto di massimo assoluto con il massimo assoluto! Uno sta sul dominio, l'altro sul codominio

</aside>

## 2.3 Valore assoluto

### Definizione del valore assoluto

$$\lvert a \rvert = max(a, -a)$$ e si può fare anche una funzione a tratti

### 2.3.1 7 Proprietà del valore assoluto

1. $$|a| \geq 0$$
2. $$|a| =|-a|$$
3. $$-|a| \leq a \leq |a|$$
4. $$|a + b| \leq | a| + | b|$$
5. $$||a|-|b|| \leq |a-b|$$
6. Espansione con disuguaglianze con altre cose senza valore assoluto

## Caratteristiche di R

### Campo ordinato

**Ordine totale e completo** (completo = con gli infiniti) **(in cui le relazioni di ordine valgono) vedi pp 76 di Foundations of real analisys.

**Proprietà archimedea** nessun numero in R è infinitamente grande
Nessun elemento in R è infinitamente piccolo (esiste sempre un elemento in Q più piccolo).
L'insieme R è **denso** e nessun numero in R è infinitamente grande
Nessun elemento in R è infinitamente piccolo (esiste sempre un elemento in Q più piccolo).

# References