---
layout: page
permalink: notes/integrali
tags: italian
title: Integrali
---

Ripasso Prox: 40
Ripasso: June 21, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: February 21, 2022 1:20 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- dimostrazione continuità implica integrabilità (e osservazioni)
-

# 8 Integrali

## 8.1 Introduzione

### 8.1.1 Il problema che risolve

Vogliamo cercare di creare un metodo matematico che sia utile per calcolare area di qualunque curva.

L'idea principale per risolvere questo problema è approssimare l'area, lo facciamo utilizzando rettangoli, la formalizzazione sarà molto aiutata dal limite.

### 8.1.2 Sottografico di funzione


$$
A = \{ (x,y) \in \R^2 | x \in D(f(x)), 0\leq y \leq f(x)\}
$$


Praticamente sto prendendo tutti in punti positivi sotto al grafico.

## 8.2 Somma di Riemann

La somma di riemann sta alla base della definizione di integrale.

### 8.2.1 Intuizione a rettangoli

Vorremmo cercare di approssimare l'area del grafico utilizzando un sacco di rettangoli di stessa ampiezza

### 8.2.2 Definizione (formula)

Diviso l'intervallo di interesse, che chiamiamo $$[a,b]$$ con n intervalli di stessa lunghezza, e presa in questi $$\xi_k$$ n punti a caso per ogni intervallo, allora consideriamo la somma di Riemann:


$$
h = \dfrac{b- a}{n},\\
S = \sum_{i=1}^nf(\xi_i) \cdot h
$$


## 8.3 Integrale di Riemann

### 8.3.1 Criterio di integrabilità secondo Riemann

> Se una funzione è continua su un certo intervallo, allora è integrabile secondo Riemann qui
>
- Dimostrazione (Non richiesta)

    Servono teoremi che non hai mai fatto tipo heine borel etc.


### 8.3.2 Osservazioni su questo integrale

1. $$\int_a^af(x) = 0$$ perché si può notare che l'ampiezza del rettangolo è 0, quindi sto sommando uno 0.
2. Nel caso di funzione costante.... bah non lo scrivo nemmeno perché se ragioni sulla somma di Riemann è abbastanza banale.

### 8.3.3 Proprietà dell’integrale

1. **Linearità** (se ho f, g continue sullo stesso intervallo, allora l'integrale della funzione somma è uguale alla somma degli integrali singoli). (posso anche moltiplicare per un fattore e considerare la funzione fattore * f, o fattore * g).
2. **Additività**, posso dividere l'intervallo su cui sto integrando come la somma di due intervalli che coprono tutto l'intervallo iniziale
    1. Convenzione: se b<a e ho un integrale tipo così $$\int^b_a = -\int^a_b$$, ovvero cambio il segno.

    Questa convenzione mi permette di scriverlo per ogni punto (basta che sia continuo).

3. **Monotonia**, (se ho due funzioni definite in un intervallo in cui entrambe sono continue tali che f < g, allora anche l'integrale possiede questa disuguaglianza).

### 8.3.4 Teorema della media integrale

In modo simile alla media finita, in cui andiamo a dividere il numero di addendi per il valore della somma totale, possiamo andare a definire una media anche per gli integrali.

Partiamo dalla somma di Riemann, per poi andare dalla media integrale:


$$
\text{INTUIZIONE: }S_n = \sum^n_{k=1} f(\xi_k)\dfrac{b-a}{n} \implies \dfrac{S_n}{b-a} = \dfrac{\sum^n_{k=1}f(\xi_k)}{n}
$$



$$
f:[a,b] \to \R \text{  continua}\\
\exists c \in [a,b] \, t.c. \,\\
\dfrac{1}{b-a} \int_a^bf(x)dx = f(c)
$$


- Dimostrazione:

    Si utilizza il teorema del valore intermedio: qui in passato

    $$\exists x_0, x_1 \in [a,b]$$, questi sono scelti in modo tale per cui $$f(x_0) = min, f(x_1) = max$$

    che è effettivamente ciò che dice weierstrass per l'estremo valore, poi utilizziamo la definizione di funzione per diree che esitono anche tali x0 e x1, per ricordarci delle loro proprietà li chiamiamo m e M sotto.

    $$
    \exists m, M \in [a,b]\text{ che diano massimo e minimo per weierstrass, ovvero che:} \\
    f(m) \leq f(x) \leq f(M) \, \forall x \in [a,b] \text{  utilizziamo la monotonia dlel'integrale} \\
    \int_a^b f(m)dx \leq \int_a^b f(x)dx \leq \int_a^b f(M)dx ,\\\text{ noto che alcuni sono costanti, allora} \\
    f(m)(b-a) \leq \int_a^b f(x)dx \leq f(M)(b-a) \implies
    f(m) \leq \dfrac{1}{b-a} \int_a^b f(x)dx \leq f(M)
    $$

    Arrivati all'ultimo passo allora possiamo dire che esiste un tale c, grazie al teorema del valore intermedio.

- Mini riassunto del valore intermedio (che serve qui)

    Una funzione continua su un intervallo per Weierstrass possiede un minimo e un massimo, grazie al teorema degli zeri possiamo costruirci una funzione tale per cui si annulli per qualunque punto all'interno di questo intervallo. Cioè possiamo concludere che

    $$\forall y \in [m,M], \exists c \in [a,b] | f(c) = y$$


## 8.4 Primitiva e f integrale

### 8.4.1 La primitiva

Una primitiva F di una funzione f è una funzione definita nello stesso intervallo tale per cui per tutti i valori si ha che F'(x) = f(x).

### 8.4.2 Unicità della primitiva

La funzione primitiva è unica a meno di una costante, in un intervallo ben definito. Possiamo osservare che esistono **infinite primitive aggiungendo costanti**.

Ma si può dire che questa funzione è unica in quanto:

- Dimostrazione

    Siano f e g primitive di una funzione a. Allora consideriamo la funzione h definita come f - g. è chiaro che la sua derivata è a - a, quindi 0, quindi la sua derivata è sempre 0.

    Per una conseguenza del teorema di lagrange ho che h deve essere una constante. Per cui si ha la relazione f = g + C. e abbiamo trovato che le funzioni primitive sono tutte a meno di costante


---

I capitoli sotto sono probabilmente utili per altre cose dopo

### 8.4.3 La funzione integrale

Sia f una funzione continua definita su un certo intervallo. sia c un punto in questo intervallo, allora posso avere una funzione I tale che


$$
I_c(x) = \int^x_cf(t)dt
$$


Ovvero sto prendendo tutta l'area da un punto a un punto di input di variabile per una certa funzione. chiamo c *punto base*.

### 8.4.4 Osservazione sulla funzione integrale (fondamentale 1)

Sia $$f$$  continua su $$(a_0, b_0)$$ sia $$c \in (a_0, b_0)$$ allora $$\forall x \in (a_0, b_0)$$ ho che $$I_c'(x) = f(x)$$

- Accenno di dimostrazione mia

    vogliamo f(x) continua e definita in un intervallo.

    La funzione integrale sarà fondamentale poi per il calcolo integrale. Possiamo relazionarla strettamente con la funzione primitiva, in quanto se fosse una primitiva, sarebbe uguale a un integrale che ci piace. Proviamo a giustificare questa cosa, proviamo a prenderne la sua derivata:

    $$
    \dfrac{I_c(x) - I_c(x_0)}{x - x_0} = \dfrac{\int^x_cf(x)dx - \int^{x_0}_c f(x)dx}{x - x_0} = \dfrac{\int_{x_0}^xf(x)dx}{x - x_0}
    $$

    E questa ultima cosa esiste, ed è compresa fra il massimo e il minimo della funzione f(x) per il teorema della media integrale.

    Non siamo stati abbastanza formali per la dimostrazione di esistenza della derivata. Vogliamo dire che

    $$
    \lim_{x \to x_0}\dfrac{\int_{x_0}^xf(x)dx}{x - x_0} = f(x)
    $$

    Andiamo a dividere la dimostrazione di questo limite in limite destro e limite sinistro.

    Vogliamo creare una successione (perché l'equivalente è una cosa reale, si può dimostrare).

    Per media integrale diciamo che $$\exists c, x_0 \leq c \leq x : f(c) = \dfrac{\int_{x_0}^xf(x)dx}{x - x_0}$$ , riusciamo quindi per ogni succesione xn che tende a x0 trovare una successione cn che tenda a x0 per carabinieri, quindi esiste questo limite ed è uguale a f(x), si fa la stessa cosa con l'altro.

- Dimostrazione nelle note del prof

    <img src="/images/notes/image/universita/ex-notion/Integrali/Untitled.png" alt="image/universita/ex-notion/Integrali/Untitled">


### 8.4.5 Tutte le funzioni integrali di f differiscono per una costante

Una cosa molto simile alle funzioni primitive! basta svolgere i calcoli in modo simile alla funzione integrale con c diversi 🙂 e ottengo che la loro differenza è sempre una costante! Questo mi fa pensare che potrebbe essere una primitiva! E infatti per 8.4.4 lo è

### 8.4.6 Teorema di Torricelli (fondamentale del calcolo integrale)

- Enunciato

    Data una funzione f definita in un intervallo aperto in R continua, e una altra funzione primitiva della prima F, allora si ha

    $$\int^b_af(x)dx = F(b) - F(a)$$

- Dimostrazione mia

    Sia c un numero reale a Caso, sia $$I_c(x)$$ la funzione integrale relativa a $$f$$, per dimostrazione precedente ho che $$I_c(x)$$  è una primitiva di $$f$$, allora per l'unicità della primitiva a meno di costante ho che $$I_c(b) - I_c(a) = F(b) - F(a)$$ (tolto costanti e simili)


### 8.4.7 Fondamentale del calcolo generalizzato

- Enunciato

    Sia  $$f: I\to\R \text{ continua}\\
    h: \R \to I \text{ derivabile}$$, vogliamo calcolare l'integrale di sopra. e sia $$A_c(x)$$ la funzione integrale

    Allora vale che $$D(A(h(x)) = D(\int_c^{h(x)}f(t)dt) = f(h(x))h'(x)$$


Vorrei dimostrare in questo teorema la possibilità di valutare l'integrale con una altra variabile.

ad esempio come calcolare


$$
\int_c^{g(x)}f(x)dx
$$


E vogliamo ricondurci a funzioni integrali normali.

Innanzitutto proviamo a ricordare alcuni risultati passati (derivata di funzione composta e il fondamentale).

- Risultati passati utili ora

    Sia I un intervallo di R, sia $$I_c(x) = \int _c^xf(t)dt$$ per il teorema fondamentale ho che $$I_c'(x) = f(x)$$ in ogni punto.

    Considero ora $$H_c(x) = \int_x^cf(x)dt$$, questo, grazie alla convenzione sugli integrali è uguale a $$-I_c(x)$$

- Dimostrazione

    Prendiamo l'integrale

    $$
    \forall z \in I, I_c(z) = \int_c^zf(t)dt
    $$

    Allora se semplicemente sostituisco h(x) a z, allora sto facendo questo

    $$I_c(h(x)) = \int _c^{h(x)}f(t)dt$$, che non è altro che una funzione composta.

    Proviamo allora a prenderne la derivata, che per il teorema fondamentale del calcolo integrale è f(x). Quindi

    $$
    f(x)  = I_c'(x) \text{ dal teorema fondamentale} \\
     D(I_c(h(x)) = h'(x)I_c'(h(x)) \text{ dalla derivata di f composta} \\
    h'(x)I_c'(h(x)) = h'(x)f(h(x)) \text{ sostituendo}
    $$


### 8.4.8 Integrale generalizzato (Integrale funzioni con discontinuità) !!

Possiamo andare a definire un intervallo di integrazione infinito, come $$0, +\infty$$, basta definirlo con un limite.

 se esiste il limite (altrimenti non è definito) e si definisce in modo analogo per il infinito negativo.


$$
\lim_{z\to+\infty} \int^z_af(x)dx = \int^{+\infty}_a f(x)dx
$$


## 8.5 Calcolo di integrali

### 8.5.1 Tabella degli integrali

Sono pigro per scrivere tutti

### 8.5.2 Funzioni composte

siano due funzioni componibili (quindi dominio codominio compatibili).

La primitiva di una funzione


$$
g \cdot f = \int g'(f(x))f'(x)
$$


### 8.5.3 Integrazione per parti

notiamo che

$$D(F(x)g(x)) = f(x)g(x) + F(x)g'(x)$$

Se prendiamo ora l'integrale da entrambe le parti e giriamo un pò di cose riusciamo a trovare l'integrale che cerchiamo, in questo senso


$$
\int f(x)g(x) = F(x)g(x) - \int F(x)g'(x)
$$


Questo è dimostrabile grazie al teorema fondamentale, che dice qualcosa a riguardo la derivata di una primitiva è la funzione integranda di un integrale.

**Alcune funzioni classiche che si fanno per parti**

$$f(x) = xe^x$$

$$f(x) = ln(x)$$

$$x^n \arctan(x)$$

### 8.5.4 Sostituzione (cambio di variabile)

Un pò di teoria:

sia h una funzione doppiamente derivabile da I in J, e f una funzione continua da J a R, allora, dati alpha e beta in I, si ha questa relazione:


$$
\int_{h(\alpha)}^{h(\beta)}f(x)dx = \int_\alpha^\beta f(h(t))h'(t)dt
$$


La dimostrazione si ha con il teorema fondamentale dell'integrale generalizzato, più precisamenta guardare il toggle sotto.

- dimostrazione

    Vogliamo dimostrare che una funzione integranda in

    Siano F, G due funzioni da I a R, voglio dimostrare che

    $$F(z)  = \int_{h(\alpha)}^{h(z)} f(x)dx, G(z) = \int_\alpha^z f(h(x))h'(x)dx$$ queste due siano uguali

    Cerco di dimostrare che abbiano la stessa derivata (per cui le funzioni originali distano al massimo di una costante) e che siano uguali in un punto (per cui sono uguali ovunque).

    L'ultima tesi si fa in modo immediato perché sto provando ad integrale in un unico punti, quindi sono entrambe 0.

    $$G'(z) = f(h(z))h'(z)$$ per la prima versione del teorema fondamentale del calcolo

    $$F'(z) = f(h(z))h'(z)$$ per la dimostrazione precedente in questo passo, quindi sono la stessa funzione.

    Questo termina la dimostrazione


esempio (sostituendo con t^2)


$$
\int e^{\sqrt{x}}dx = 2e^{\sqrt{x}}(\sqrt{x} - 1) + c
$$


# Registro ripassi

| 21/02/22 | Primo ripasso assoluto, i due teoremi principali sono l’unicità per la primitiva a meno di costante, il teorema del valor intermedio e la caratteristica sulla funzione integrale, li sai abbastanza bene, è il primo ripasso. 4.5/5 |
| --- | --- |
| 09/03/22 | Ho notato che ci sono un sacco di cose che do, per scontato, se vorrei ripassare bene dovrei rifarmi le dimostrazioni (oggi unicità delle primitive e fondamentale 1) in particolare il passaggio con le successioni in fondametntale uno è da rifare. |
| 20/03/22 |  Il passaggio con le successioni va bene, l’unica cosa a cui dovrei dare più attenzione è la dimostrazione di integrazione per parti. Per il resto lo sai abbastanza bene. |
| 19/05/22 |  Più o meno ci sei,  volte sei insicuro su come sono esattamente definite le funzioni per i vari teoremi, ma per la maggior parte ci sei. Bisognerebbe fare un ripasso finale e direi che sie pronto per sta parte |
ono esattamente definite le funzioni per i vari teoremi, ma per la maggior parte ci sei. Bisognerebbe fare un ripasso finale e direi che sie pronto per sta parte |