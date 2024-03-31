---
layout: page
permalink: notes/base-e-dimensione
tags: italian
title: Base e dimensione
---

Ripasso Prox: 30
Ripasso: May 30, 2022
Ultima modifica: October 19, 2022 5:02 PM
Primo Abbozzo: March 12, 2022 11:51 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

1. Tutte le proprietà della basi, caratterizzazione delle dimensioni.

# 2 Basi e Dimensione

## 2.1 Basi

### 2.1.1 Definizione

Un insieme di vettori $$v_1,...,v_n$$ sono basi di uno spazio vettoriale $$V$$ se sono soddisfatte queste proprietà

1. $$V = \langle v_1,...,v_n\rangle$$
2. $$v_1,...,v_n$$ sono linearmente indipendenti

Dalla proprietà 2 potremmo anche dire che è il minimo insieme di vettori necessario per avere questa base.

**Finitamente generato**

Se l'insieme dei vettori nella base è finito allora posso dire che è finitamente generato

Ma possiamo trovare anche spazi che non sono finitamente generati come $$\R[x]$$ che non hanno un numero finito di basi (perché dipende dal grado dei polinomi che può essere infinito).

**Nota: base dello spazio vettoriale banale**

La base dello spazio banale è l'insieme vuoto!, se fosse il vettore 0, per definizione posso trovare un coefficiente diverso da 0 tale che sia zero. eg $$1\cdot 0_v = 0$$ quindi non è linearmente indipendente.

**Nota sulla seguente carrellata di proposizioni**

Le seguenti proposizioni parlando della possibilità di generare le basi partendo da vettori linearmente indipendenti e aggiungendo fino a generare, o partendo da vettori che generano e togliendo finché non hai una base.

Da questa idea generale si possono ricavare molte osservazioni, che sono elencate dalle proposizioni seguenti

### 2.1.2 Minimali e massimali

Si dice che una proprietà è minimale per un insieme, se ogni sottoinsieme proprio *possiede più la proprietà*

E si dice che è massimale se per ogni sovrainsieme proprio, questo insieme *perde la proprietà*

### 2.1.3 Prop 4.1.4 Teorema caratterizzazione delle basi

Questo teorema è equivalente alla definizione data di base, solo che esprime il concetto utilizzando i minimali e massimali.

**Enunciato**

Si dice che un insieme di vettori $$v_1, ..., v_n$$ è una base per uno spazio vettoriale sse:

1. L'insieme massimale di vettori linearmente indipendenti
2. Minimale di vettori generatori (cioè se ne tolgo uno non genera più, allora riesco a concludere che sono indipendenti) *già vista nella 4.2.1*

Si può notare come sia strettamente collegato alla 4.2.2

- Idee per la dimostrazione

    Caso 2$$\impliedby$$Se mi prendo un insieme minimale di generatori, mi basta dimostrare che siano indipendenti per sapere che sia una base.

    Supponiamo per assurdo che siano dipendenti. Allora esiste un vettore linearmente dipendente, e quindi esprimibile come combinazione lineare di altri vettori 3.2.4, ma se è una combinazione lineare allora non è più l'insieme minimale di generatori (cioè questo vettore non ha contributi sullo spazio) è il teorema 3.1.8 qed.

    Caso 1 $$\impliedby$$Se ho un insieme massimale di vettori linearmente indipendenti, voglio dimostrare che genera V.

    Allora per massimalità appena aggiungo un vettore, ho un insieme di vettori linearmente dipendenti, allora mi posso trovare una combinazione lineare con coefficienti non nulli tali che la combinazione sia 0.

    quindi $$\lambda_1v_1 + ...+ \lambda_nv_n + \beta w = 0$$, e per qualunque vettore $$\omega$$ so che $$\beta \neq 0$$ perché altrimenti si ha l'assurdo in quanto i vettori $$v_1, ..., v_n$$ sarebbero dipendenti. Se è diverso da 0 allora posso esprimerlo come combinazione lineare di altro, quindi riesco ad ottenere l'intero spazio.


### 2.1.4 Prop. creazione di base da vettori generatori

Questo teorema ci permette di ricavare una base partendo da un insieme di vettori che generino l'intero spazio vettoriale. L'idea principale è che possiamo trovare dei vettori che sono combinazioni lineari di altro e continuare a toglierli finché non trovo la base.

**Enunciato**

Sia $$v_1... v_n$$ un insieme che genera $$V$$, allora un sottoinsieme di questi vettori generatori sono una base per $$V$$.

**Dimostrazione**

Se i vettori sono linearmente indipendenti allora ho la base, se sono dipendenti allora sia $$\omega$$ il vettore dipendente, allora si può scrivere come combinazione lineare per la 3.2.4, e per la proposizione 3.1.8 lo spazio generato da tali vettori è esattamente lo stesso.

Posso continuare con questo argomento finché non ottengo la base o non ci sono più vettori. (nel caso in cui è lo spazio nullo).

**Nota**

Si può fare anche il contrario, da un insieme di vettori linearmente indipendenti posso aggiungere vettori fino a quanto non creo una base, l'algoritmo è molto simile, ma al contrario.

### 2.1.5 prop 4.2.1 Teorema del completamento

**Enunciato**

Da una base $$v_1,..., v_n$$ e un insieme di vettori linearmente indipendenti $$\omega_1, ..., \omega_m$$ appartenenti allo stesso spazio allora so che $$m \leq n$$, inoltre è possibile aggiungere vettori a $$\omega$$ in modo che sia una base, questa base ha la stessa cardinalità della base si sopra

**Dimostrazione (non richiesta)**

Si utilizza la proposizione precedente al contrario probabilmente.

## 2.2 Dimensione

Il concetto di dimensione è strettamente correlato con il concetto di base. Possiamo intendere la dimensione come il minimo insieme di coordinate necessarie per creare l’intero spazio (questa è una definizione che c’è anche nel teorema di caratterizzazione delle basi).
Perché alla fine saranno le coordinate che ci interessano.

### 2.2.1 prop. 4.2.2 Basi hanno stessa dimensione DIMENSIONE (chiede)

C'è il teorema del completamento

**Enunciato**

Dato uno spazio vettoriale finitamente generato, allora tutte le sue basi hanno la stessa cardinalità, questo numero di chiama **dimensione dello spazio vettoriale**, ed è una proprietà caratterizzante di essa.

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Base e dimensione/Untitled.png" alt="image/universita/ex-notion/Base e dimensione/Untitled">

    Meglio una dimostrazione così: in quanto b1 è base e b2 è linearmente indipendente ho (per completamento) che $$n \geq m$$, in quanto b2  è base e b1 linearmente indipendente ho che $$n \leq m$$, quindi $$n = m$$


### 2.2.2 Basi canoniche

Ci sono certe basi che sono particolarmente interessanti, le chiamiamo basi canoniche, e sono definite come

$$e_i = \{0...0_{i-1},1,0_{i + 1},..., 0_n\}$$ ovvero ho un 1 alla n esima posizione

### 2.2.3 prop 4.2.4 relazioni fra dimensioni

Dato uno spazio vettoriale $$W$$e un suo sotto spazio $$V$$ si ha

1. $$dim(V) \leq dim(W)$$
2. $$dim(V) = dim(W) \iff V=W$$
- Dimostrazione

    Caso 1 Sia m la dimensione di $$V$$ allora la sua base ha m vettori che sono linearmente indipendenti. Questi vettori sono anche presenti in $$W$$, che poniamo abbia dimensione n, allora per il teorema del completamento ho che $$m \leq n$$

    Caso 2 $$\impliedby$$ questa freccia è ovvia, se sono la stessa cosa hanno la stessa dimensione

    Caso 2 $$\implies$$

    <img src="/images/notes/image/universita/ex-notion/Base e dimensione/Untitled 1.png" alt="image/universita/ex-notion/Base e dimensione/Untitled 1">

    scambiare W e V in questa dimostrazione


### 2.2.4 prop 4.2.6 Dimensione, base, lin ind, e generazione (3)!

**Enunciato**

<img src="/images/notes/image/universita/ex-notion/Base e dimensione/Untitled 2.png" alt="image/universita/ex-notion/Base e dimensione/Untitled 2">

- 3 to 1

    se ho un insieme di vettori che generano uno spazio allora posso togliere vettori fino a quando ho una base (ossia sono linearmente indipendenti). Ma per la dimensione ho che devo avere necessariamente n vettori, quindi un insieme di n vettori linearmente indipendenti è già una base.

- 2 to 1

    L'argomento presente qui è uguale alla superiore 4.2.4 (quindi dire per il completamento che posso espandere e ottenere una base) Anzi potresti direttamente utilizzare questa per dimostrare sto punto


### 2.2.5 Coordinate di un punto in uno spazio vettoriale

Sia data una base per uno spazio vettoriale $$v_1, ..., v_n$$, allora ho che posso scrivere qualunque vettore $$\omega$$ nello spazio in un unico modo, moltiplicando per corrispondenti fattori. Questi fattori sono **unici**.

- Dimostrazione unicità

    <img src="/images/notes/image/universita/ex-notion/Base e dimensione/Untitled 3.png" alt="image/universita/ex-notion/Base e dimensione/Untitled 3">


## 2.3 Algoritmo di gauss rivisitato

### 2.3.1 A.G non cambia sottospazio riga (non richiesta)

L'intuizione per questo è abbastanza ovvio, sto solamente applicando combinazioni lineari fra le righe, quindi sto sempre prendendo vettori che appartengono a questo spazio, non le sto modificando, questo giustificherebbe anche il motivo per cui l'algoritmo di gauss è utile.

- Dimostrazione

    la proposizione da utilizzare è lo span che non cambia se aggiungo e tolgo una combinazione lineare


### 2.3.2 Indipendenza delle righe non nulle

Dimostrazione non fatta.

# 3 Registro ripassi

| 12/03/ | Qualche difficoltà a dimostrare tutte le frecce per il teorema di caratterizzazione delle basi. |
| --- | --- |
| 20/03 | Tutto senza quasi nessuna difficoltà. |
| 30/04 | Tutto Ok |
lche difficoltà a dimostrare tutte le frecce per il teorema di caratterizzazione delle basi. |
| --- | --- |
| 20/03 | Tutto senza quasi nessuna difficoltà. |
| 30/04 | Tutto Ok |