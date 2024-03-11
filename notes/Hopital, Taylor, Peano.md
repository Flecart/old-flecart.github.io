---
layout: page
permalink: notes/hopital,-taylor,-peano
tags: italian
title: Hopital, Taylor, Peano
---

Ripasso Prox: 40
Ripasso: May 17, 2022
Ultima modifica: March 7, 2023 1:41 PM
Primo Abbozzo: November 25, 2021 12:17 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# 7 Hopital , Taylor e Peano

## 7.1 De Hopital

### 7.1.1 Lemmi preliminari

Questo lemma preliminare era già presente per la prova del [teorema degli zeri](/notes/limiti#teorema-degli-zeri)


<img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled">


Questo lemma è molto interessante perché mette in relazione il finito (le successioni) con l'infinito (i reali)
In molte dimostrazioni si dà per scontato questo lemma, ma è una sottigliezza importante che giustifica l'utilizzo di successioni per limiti reali.
Ci permette di semplificare molto le dimostrazioni perché riusciamo a trattare le successioni molto meglio.

### 7.1.2 ipotesi

- Enunciato al finito, finito

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 1.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 1">

- Enunciato, limite al finito, asintoto

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 2.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 2">

- Enunciato, limite destro o sinistro

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 3.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 3">

- Enunciato limite all'infinito

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 4.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 4">


Il fatto che voglio che sia sigma sia la derivata di sigma siano diversi da zero, è perché la conclusione deve avere entrambi diversi da zero.

### 7.1.3 Dimostrazione

- Dimostrazione in slide

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 5.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 6.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 7.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 7">

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 8.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 8">

- Note sulla dimostrazione
    1. Utilizzo Cauchy per dire che esiste una successione che mi piace.
    2. Utilizzo il lemma delle successioni per dire che la successione trovata con cauchy è proprio quello che mi serve
    3. Faccio uguale questa cosa di cauchy con la divisione senza le derivate e concludo per una parte.

I passi principali sono:

Cercare di esprimere il limite della frazione come il limitie della frazione con input una successione.

1. Riscrivere la frazione come la frazione - il punto che vogliamo calcolare (per ipotesi sto sottraendo 0) perché così possiamo utilizzare dopo cauchy.
2. Utilizziamo cauchy ed esprimiamo la frazione al punto uno come una divisione fra derivate.
3. Dalla divisione fra derivate in successione utilizziamo il lemma e ci riconduciamo alla continuità.

## 7.2 Infiniti ed infinitesimi

Queste conclusioni si adagiano fortemente sulle conclusioni del teorema di de l'Hopital

### 7.2.1 Confronto fra infiniti

Il teorema di De l'Hopital è molto utile per descrivere una gerarchia degli infiniti. Possiamo confrontare quale funzione cresce più in fretta di un altro.

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 9.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 9">

    C'è anche il caso in L = $$\infty$$, in quel caso si dice che è di ordine inferiore.

- Conclusioni

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 10.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 10">


### 7.2.2 Confronto fra infinitesimi

Si potrebbe fare la stessa cosa per gli infinitesimi, si otterrebbero risultati opposti, ma il concetto è lo stesso si utilizza sempre il concetto di teorema di Hopital.

- Definizione infinitesimo

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 11.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 11">

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 12.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 12">


## 7.3 O-piccolo di funzione

Il concetto di O-piccolo riesce a catturare il concetto di errore di misura (più o-piccolo è grande, più precisa è la mia misura).

### 7.3.1 Definizione

**Intuizione**

In modo grossolano, se f è infinitesimo  di ordine maggiore rispetto al denominatore g, allora f è un opiccolo di g.

In pratica si dice che una funzione g è un o-piccolo di una funzione f se per il punto di cui stiamo calcolando il limite, g è un infinitesimo di ordine superiore rispetto a f. (ricolleghiamo con il confronto fra infinitesimi)

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 13.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 13">


### 7.3.2 Proprietà algebriche

O-piccolo possiede alcune proprietà algebriche di interesse, che sarebbe buona cosa studiare, quindi:

- Derivazione di altri O- e somma

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 14.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 14">

- Potenze

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 15.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 15">

- Composizione

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 16.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 16">

- Constante

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 17.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 17">


### 7.3.3 Funzioni di stesso ordine

- Enunciato e dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 18.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 18">


## 7.4 Serie di Taylor

L'idea principale per le serie di Taylor è trasformare le funzioni trascendentali con alcuni polinomi.

In modo che alla fine si abbia un limite di rapporto di polinomi che equivalga alla funzione trascendentale, vogliamo una approssimazione della funzione che sia abbastanza precisa.

sarà alla fine un polinomio infinito!

### 7.4.1 Intuizione

Vogliamo cercare quale polinomio approssima meglio una funzione per ogni grado. Scopriamo che per una funzione continua è la costante f(0) stessa per una funzione continua in questo punto.
Formalizzato leggermente meglio questo può diventare una dimostrazione.

e si ha che è O(1). Faccio lo stesso ragionamento per gradi superiori e mi trovo la serie di taylor, con qualunque approssimazione che mi serva.
Consideriamo il caso in cui siamo sul 0, per una funzione continua e derivabile reale.

 **Esempio con O(x)**
Allora sappiamo che

$$
\lim_{ x \to 0 } \frac{f(x) - f(0)}{x} = f'(0) \in \mathbb{R}
$$

Questo implica il fatto che 

$$
\lim_{ n \to 0 } \frac{f(x) - f(0)}{x} - f'(0) =  0
\implies \lim_{ n \to 0 } \frac{f(x) - f(0) - f'(0)x}{x}  =  0
$$

Dove abbiamo utilizzato la continuità del limite per somme e sottrazioni.
Questo ci dice che tutto quanto sopra è un $$o(x)$$
Ossia si può riscrivere quanto sopra come
$$f(x) = f(x) + f'(0)x + o(x)$$

Si può continuare su su questa scia e approssimare la funzione tramite $$o(x^{2})$$ e in teoria si può continuare così all'infinito.
Questo non è una dimostrazione formale, nemmeno matematica, ma dà la giusta intuizione sul perché la serie di Taylor funziona.

**Esempio con $$O(x^{2})$$**
Consideriamo per un instante questo limite

$$
\lim_{ x \to 0 }  \frac{f(x) - f(0) - f'(0) x - a_{1}x^{2}}{x^{2}}
$$

Notiamo che sia sopra che sotto è continuo, per questo motivo possiamo utilizzare il teorema [#7.1 De Hopital](#7.1-de-hopital) da cui ricaviamo 

$$
\lim_{ x \to 0 } \frac{f'(x) - f'(0) - 2a_{1}x}{2x}
$$

Si può notare che la prima parte è un altra derivata, mentre l'altra parte è un coefficiente, ossia abbiamo

$$
\lim_{ x \to 0 } \frac{f'(x) - f'(0)}{2x} - a_{1} = \frac{1}{2}f''(0) - a_{1}
$$

Questo significa che se settiamo il coefficiente in modo adatto possiamo avere un $$o(x^{2})$$ senza nessun problema!
Ossia se $$a_{1} = \frac{1}{2}f''(0)$$ vale che l'espressione di sopra è un $$o(x^{2})$$ di sopra, per cui possiamo scrivere che


$$
f(x) \approx f(0) + f'(0)x + a_{1}x^{2} + o(x^{2})
$$

Con $$a_{1}$$ il valore di sopra.
Applicando ancora Hopital sopra si può avere il termine con esponente ancora superiore così via!


### 7.4.2 Enunciato Taylor e Peano
Nota: si può analizzare Taylor in una altra forma, che è trattata in [Massimi minimi multi-variabile#Resto secondo Peano](/notes/massimi-minimi-multi-variabile#resto-secondo-peano)

#### Enunciato Taylor
Sia $$f: (a, b) \to \mathbb{R}$$ una funzione continua, e sia $$0 \in (a, b)$$
Poniamo $$f$$ derivabile **n-volte** in $$\bar{x} = 0$$

Allora andiamo a definire il **polinomio di taylor in** $$\bar{x} = 0$$ di grado $$\leq n$$ il polinomio

$$
T_{n}(x) = \sum_{j=0}^{n} \frac{f^{(j)}(0)}{j!}x^{j}
$$

Che è **l'unico** polinomio di grado $$\leq n$$ tale per cui valga

$$
f(x) = T_{n}(x) + o(x^{n})
$$

per $$x \to 0$$

#### Enunciato Peano
Questo è esattamente il precedente, ma stiamo shiftando il polinomio, permettendo di avere dei valori che non siano necessariamente su 0.
Sia $$f: (a, b) \to \mathbb{R}$$ una funzione continua, e sia $$\bar{x} \in (a, b)$$
Poniamo $$f$$ derivabile **n-volte** in $$\bar{x}$$

Allora andiamo a definire il **polinomio di taylor in** $$\bar{x}$$ di grado $$\leq n$$ il polinomio

$$
T_{n}(x) = \sum_{j=0}^{n} \frac{f^{(j)}(\bar{x})}{j!}(x - \bar{x})^{j}
$$

Che è **l'unico** polinomio di grado $$\leq n$$ tale per cui valga

$$
f(x) = T_{n}(x) + o((x - \bar{x})^{n})
$$

per $$x \to \bar{x}$$

## 7.5 Serie di Taylor note

### 7.5.1 Esponenziale e Logaritmo

- Dimostrazione espo

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 24.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 24">

#### Logaritmo

$$
\ln(1 + x) = \sum_{i = 1}^{n} \frac{(-1)^{i - 1}}{i} \cdot x^{i} + o(x^{n})
$$

con $$x \to 0$$.
### 7.5.2 Goniometriche

Una nota di valore è che l'espansione del seno ha solamente polinomi dispari, questo è in stretta relazione con la disparità del seno, mentre per il coseno, dato che è pari, si hanno solamente polinomi di gradi pari.

- Seno

    <img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 26.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 26">

- Coseno

    !<img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 27.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 27">


### Binomiale generalizzato

- Descrizione

    <img src="/images/notes/Hopital, Taylor, Peano/Untitled 28.png" alt="Hopital, Taylor, Peano/Untitled 28">
, Peano/Untitled 26.png]]

- Coseno

    !<img src="/images/notes/image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 27.png" alt="image/universita/ex-notion/Hopital, Taylor, Peano/Untitled 27">

# Elementi di ripasso

- Vecchi dubbi
    - Non ti ricordi esattamente le ipotesi (anche la tesi) di hopital (il fatto che deve esistere la frazione delle derivate, non l'avevo considerato in ipotesi e data per scontata, 2. il fatto di necessitare della continuità in tutto il dominio e della derivabilità tranne nel punto di valutazione.
    3. riguardo la tesi mi sono scordato la parte sull'esistenza del limite della frazione.
    - fai attenzione nella dimostrazione di Hopital a non farei calcoli dentro al limite che è un abuso di notazione.
    - Fai attenzione all'eliminazione dell'esiste nella dimostrazione di Hopital per caso finito.

Dopo più di un anno sembra che taylor sia la cosa più importante in questi appunti.

11/02/24 Sono ritornato a guardare questo appunto, di nuovo per Taylor lmao, ho riscritto bene l'intuizione di dimostrazione.