---
layout: page
permalink: notes/applicazioni-lineari
tags: italian
title: Applicazioni lineari
---

Ripasso Prox: 27
Ripasso: June 2, 2022
Ultima modifica: January 4, 2023 9:54 AM
Primo Abbozzo: March 22, 2022 9:19 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# 3 Applicazioni lineari

## 3.1 Introduzione e definizione

Si definisce applicazione lineare una funzione (omomorfica) che preserva la struttura dello spazio vettoriale, ossia vale che


$$
f:V \to W, tale che \\
f(u + v) = f(u) +f(v)\\
f(\lambda v) = \lambda f(v)
$$


### 3.1.1 Conservazione delle combinazioni lineari

In particolare le due proprietà delle applicazioni lineari mi preservano le applicazioni lineari, ovvero:

$$f(\lambda_1 a + \lambda_2 b) = \lambda_1 f(a) + \lambda_2f(b)$$ e questo lo puoi estendere a qualunque tipo di vettore

### 3.1.2 L'elemento neutro

L'elemento neutro è conservato nell'applicazione lineare (mappa sempre l'elemento neutro di uno all'elemento neutro dell'insieme di arrivo)

### 3.1.3 Esempi

Un esempio importante è la matrice che mappa da  $$\R^n\to \R^m$$

## 3.2 Esiste omomorfismo a insiemi qualunque (chiede) 5.1.7

<img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled">

- Dimostrazione

    Il passo più importante è **definire l'applicazione lineare**.

    Lo definiamo in questo modo:

    preso $$v\in V$$, allora in quanto ho una base di $$V$$, posso dire che

    $$v = \alpha_1v_1 +...+ \alpha_n v_n$$, allora definiamo la nostra funzione $$L:V\to W$$ tale che

    $$L(v) = \alpha_1w_1 +...+\alpha_nw_n$$, da notare che i coefficienti sono gli stessi, ma i vettori diversi e abbiamo anche cambiato possibilmente lo spazio

    **È una applicazione:**

    fai i calcoli e puoi notare che effettivamente è una applicazione lineare.

    - Calcoli

        <img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 1.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 1">


    **Unicità:**

    l'unicità di questa applicazione si può identificare con l'unicità delle coordinate rispetto alla base, c'è solo una tale funzione definita in questo modo per ogni vettore.

    Ma questa non è formale, quindi appiccico la dimostrazione formale: (si utilizza l'ipotesi dell'unicità delle coordinate inmodo implicito sctivendo v come combinazione lineare della base)

    <img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 2.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 2">


### 3.2.1 Coincidenza su basi

<img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 3.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 3">

La dimostrazione è abbastanza ovvia, sappiamo che esiste un unica applicazione lineare su una base e che arriva a W.

### 3.2.2 Osservazione sul teorema

Questo teorema ci permette di avere delle applicazioni lineari a caso, per qualunque spazio vettoriale, basta avere una base dello spazio iniziale.

### 3.2.3 modi di vedere l’applicazione lineare

Esistono tre modi per avere la definizione di applicazione lineare.

1. Classica definizione F(v) = espressione
2. Una matrice che mi rappresenta l'applicazione
3. F(base1) = qualcosa, ... F(basen) = qualcosaltro.

## 3.3 Teoremi su Ker e Im

### 3.3.1 Ker F e Im F sono sottospazi

Devo dimostrare che questi insiemi siano dei sottospazi.

1. Il vettore nullo appartiene a Ker F
2. Poi si dovrebbe dimostrare che siano chiusi per l'operazione di somma e prodotto scalare
In modo simile a quanto fatto in [Spazi vettoriali](/notes/spazi-vettoriali)

### 3.3.2 Suriettività e iniettività

**Enunciato:**

Data una applicazione lineare $$F: V\to W$$

Suriettivo sse $$Im(F) = W$$, questa è abbastanza ovvio.

Iniettiva sse $$Ker(F) = \{0\}$$

- Dimostrazione

    $$\implies$$Supponiamo che sia iniettiva, allora $$F(x) = F(y) \implies x = y$$,

    in quanto è una applicazione lineare so che $$F(0) = 0_w$$, quindi supponiamo che $$v \in V |F(v) = 0$$ per iniettività ho che $$v= 0$$, quindi l'unico elemento di $$Ker(F)$$  è 0.

    $$\impliedby$$Supponiamo che $$Ker(F) = \{0 \}$$ supponiamo che $$F(x) = F(y)$$ per certi $$x,y \in V$$,

    vogliamo dimostrare che $$x= y$$.

    Valutiamo $$F(x - y)  = F(x) - F(y) = 0_w$$, ma quindi $$x-y = 0_v$$ in quanto per ipotesi l'unico elemento in Ker(F) è 0v e abbiamo dimostrato che (x-y) appartiene a Ker(F), quindi $$x = y$$.


### 3.3.3 Calcolo del nucleo

Dato un omomorfismo, l'unica cosa che dobbiamo fare è risolvere la matrice omogenea associata.

In parole migliori

> Ker F  l'insieme delle soluzioni del sistema lineare omogeneo associato ad A, dato A matrice dell'applicazione lineare
>

### 3.3.4 Corrispondenza fra base V nell’immagine 5.4.4 (chiede)

<img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 4.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 4">

- Dimostrazione

    Vogliamo dimostrare una doppia inclusione, perché è questa la definizione dell'uguaglianza per un assioma di estensionalità in [Teoria assiomatica degli insiemi](/notes/teoria-assiomatica-degli-insiemi).

    Caso $$\implies$$, sia $$w \in Im(F)$$, allora $$\exists v\in V, F(v) = w$$, dato che abbiamo una base, si ha che $$v = \lambda_1v_1 +...+ \lambda_nv_n$$, allora

    $$F(\lambda_1v_1 +...+ \lambda_nv_n) = F(\lambda_1v_1) +...+ F(\lambda_nv_n) = \lambda_1F(v_1) +...+ \lambda_nF(v_n) \in \langle F(v_1),...., F(v_n)\rangle$$ e finisco questa freccia.

    Caso $$\impliedby$$Questa praticamente è uguale alla precedente, oppure, possiamo ricordare che per la 3.1.5 presente in [Spazi vettoriali](/notes/spazi-vettoriali) si ha che è il più piccolo sottospazio generato da quei elementi. Quindi questa inclusione è fatta in modo immediato. Ma anche ripercorrere la dimostrazione al contrario non è un problema.


**Note:**

Questo teorema ci è molto utile per calcolare lo spazio generato dell'immagine, perché ci permette di fare una sorta di cambio di base (che non è un cambio di base) stiamo solamente prendendo qualcosa di molto simile a una base, ma in un altro spazio vettoriale (non è detto che sia una base però! so solo che genera quello spazio vettoriale).

### 3.3.5 Calcolo dell'immagine

Avendo il teorema precedente, il calcolo del sottospazio dell'immagine è abbastanza veloce:

1. prendo l'insieme immagine della base
2. poi faccio gauss in modo diretto su questa.

SI può dimostrare che questo non è altro che gauss sulla TRASPOSTA.

## 3.4 Teorema della dimensione (!!!chiedissimo) 5.5.1

<img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 5.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 5">

Questo è uno dei teoremi più importanti per tutto il corso di geometria! Vale per qualunque applicazione lineare per spazi vettoriali!

- Idee per la dimostrazione

    A caratteri generali, i passi logici principali per la dimostrazione è questa:

    1. Prendiamo una base di V, e la base per Ker(F). Per il completamento posso completare la base del nucleo in una base di V.
    2. Prendo l'insieme dei vettori che ho aggiunto al nucleo, voglio dimostrare che la funzione applicata a questi vettori sia in grado di generare l'immagine, se questo succede, allora ho finito perché ho praticamente scomposto la base di V, in una per Ker(F), e una altra per Im L.
    3. Dimostro che effettivamente quanto preso è una base di Im F cercata, utilizzando la linearità dell'applicazione, e il fatto che l'insieme di vettori iniziale era base per V
- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 6.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 6">

    <img src="/images/notes/image/universita/ex-notion/Applicazioni lineari/Untitled 7.png" alt="image/universita/ex-notion/Applicazioni lineari/Untitled 7">


### 3.4.1 Verifica iniettività

Mi può dare in modo quasi immediato nozioni di iniettività e suriettività, se l'applicazione lineare ha la dimensione di kernel = 0 allora scopro subito che è iniettiva!

Siano dati due spazi vettoriali tali che $$\dim V > \dim W$$ allora non ho cose iniettive.

Perché supponiamo che ci sia tale applicazione lineare, ma al massimo l'immagine è di dimensione W, quindi la dimensione del Kernel non è nulla, per cui ho che non è iniettivo per il teorema in link

### 3.4.2 Verifica suriettività

Se la dimensione dell'immagine ha la stessa dimensione del codominio, allora ho trovato subito un una base per il codominio! Quindi so subito che è suriettiva.

In modo simile se ho due spazi vettoriali tali per cui $$\dim V < \dim W$$ allora  non ho funzioni suriettive perché la dimensione di arrivo è al massimo V.

## 3.5 Isomorfismi

### 3.5.1 Definizione

È una applicazione lineare bigettiva

SI può dimostrare che se V ha dimensione n, allora è isomorfo con $$\R^n$$

### 3.5.2 Equivalenza delle dimensioni per ISO (!! chiede)

Sse due spazi vettoriali sono isomorfi allora hanno la stessa dimensione.

- Dimostrazione

    $$\implies$$  In quanto è un isomorfismo si ha che è iniettiva e suriettiva, quindi

    dim V = 0 + dim W quindi hanno la stessa dimensione.

    $$\impliedby$$Suppongo che le dimensioni siano le stesse, vogliamo dimostrare che i due insiemi siano isomorfi.

    Date le rispettive basi di V e W, vogliamo costruirci un isomorfismo:

    1. Mi costruisco la funzione e dimostro che è suriettiva perché voglio mandare il vettore base 1 di V al vettore base 1 di W, così a corrispondere fino alla dimensione
    2. Poi uso il teorema delle dimensioni per concludere che la dimensione del nucleo è 0, per cui è iniettiva.

# 4 Registro ripassi

| 09/04 | Ti ricordi 0 riguardo alla dimostrazione del teorema della dimensione, ma per il resto è ok. |
| --- | --- |
| 19/04 | Tutto ok |
|  |  |
� iniettiva.

# 4 Registro ripassi

| 09/04 | Ti ricordi 0 riguardo alla dimostrazione del teorema della dimensione, ma per il resto è ok. |
| --- | --- |
| 19/04 | Tutto ok |
|  |  |

# References