---
layout: page
permalink: notes/spazi-vettoriali
tags: italian
title: Spazi vettoriali
---

Ripasso Prox: 30
Ripasso: June 7, 2022
Ultima modifica: October 19, 2022 5:03 PM
Primo Abbozzo: March 1, 2022 9:46 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

1. Esercizi, in particolare come trovare vettori in un sottospazio che soddisfino altre cose come l’interdipendenza lineare, e booh.
2. Dimostrazione delle conseguenze principali dello spazio vettoriale

6 Giugno 2016

# 1 Spazi vettoriali

## 1.1 Piano cartesiano

### 1.1.1 Definizione

Possiamo considerare il piano cartesiano come l'insieme $$\R^2$$ potremmo dire che esiste una corrispondenza fra una coordinata e un punto del piano, una volta che abbiamo definito un punto di origine. Si può vedere anche come corrispondenza biunivoca con vettori del piano per l'origine (parte dall'origine).

Questa cosa vale anche per uno spazio n-dimensionale, non soltanto due, ma per semplicità di introduzione di questo lo faccio con 2

### 1.1.2 Operazioni definite

Possiamo definire una somma fra questi punti in coordinata e un prodotto.

**Somma**

$$\forall a,b,c,d \in \R \,\,\langle a,b\rangle + \langle c,d \rangle = \langle a + c, b+d\rangle$$

(dovremmo definire invece queste cose nello spazio vettoriale, in quanto non necessariamente dobbiamo averle in R)

**Prodotto scalare**

$$\forall a,b \in V, \lambda \in \R, \lambda\langle a, b\rangle = \langle \lambda a, \lambda b \rangle$$

## 1.2 Introduzione agli spazi vettoriali

### 1.2.1 Assiomi di base

Definiamo qui le proprietà necessarie per essere uno spazio vettoriale.

1. Gruppo abeliano rispetto alla addizione (4) $$V \times V \to V$$
2. Moltiplicazione è scalare, definito su un *campo $$C \times V \to V$$*
    1. Associatività
    2. Neutro
3. Vale distributività destra e sinistra che collega addizione e prodotto

### 1.2.2 Conseguenze principali degli assiomi

<img src="/images/notes/image/universita/ex-notion/Spazi vettoriali/Untitled.png" alt="image/universita/ex-notion/Spazi vettoriali/Untitled">

### 1.2.3 Interpretazione geometrica (2)

Principalmente ci sono due interpretazioni possibili. Per punti o vettori.

1. **Punti** esiste una corrispondenza biunivoca fra uno spazio n-dimensionale e la coordinata
2. **Vettori** esiste una corrispondenza biunivoca fra vettori che iniziano dall'origine e in punti.

### 1.2.4 Polinomi a coefficienti in R (Esempio)

Questo è un **esempio di spazio vettoriale**. Si può fare una verifica per vedere che gli assiomi sono soddisfatti.

Altri spazi vettoriali sono l'insieme delle matrici con coefficienti reali, l'insieme delle funzioni continue in R.

### 1.2.5 Sottospazio vettoriale (def e banale)

Un sottospazio vettoriale è un sottoinsieme che è chiuso per l'addizione e moltiplicazione.

Sia U un sottospazio di V, allora per definizione vale:

1. U non è vuoto
2. chiuso rispetto somma
3. Chiuso rispetto moltiplicazione

Il sottospazio banale è un sottospazio che contiene solo l'elemento nullo per l'addizione

Si può anche trovare una serie di **assiomi equivalenti per il sottospazio**

1'. il vettore $$0_v$$appartiene al sottospazio U, e valgono 2 e 3

E si può scrivere una proprietà equivalente a 2 e 3, ossia chiuso rispetto a una combinazione lineare.

- Esercizio

    Dimostrare che le ipotesi 2 e 3 implicano che $$\lambda a + \lambda_2b \in V,$$  con i lambda valori del campo.


### 1.2.6 Minimi sottospazi (classificazione sottospazi di R2)

Se prendiamo un punto nel piano, ci basta una retta che passa per essa e per l'origine per avere il minimo sottospazio che lo contenga.

Il ragionamento per dire che è il minimo è più o meno su questa scia:

1. Se contiene quel punto diverso da 0, allora deve contenere tutti i punti sulla retta almeno (altrimenti non è chiuso per il prodotto scalare).
2. Se ne contiene di più non è più il minimo sottospazio, se ne contenesse di meno allora ci sarebbe un assurdo con il punto uno.

Si può dire la stessa cosa per 2 o più punti allineati. Se però non sono allineati, allora devo prendere il loro span. Ovvero se ho $$u, v$$ indipendenti fra di loro allora il minimo sottospazio è

$$\alpha v + \beta u$$ che è l'intero piano. (questo poi è anche la condizione 23 per dimostrare che è sottopiano).

Su questa analisi può dimostrare che gli **unici sottospazi di R2 sono 3**.

1. Banale
2. Retta
3. R2

Possiamo formalizzare il senso di *più piccolo sottospazio* che contiene un elemento come l'insieme sottospazio che è contenuto in ogni altro sottospazio (e si potrebbe dire quindi anche che non esiste un altro sottospazio più piccolo)

## 1.3 Combinazioni lineari

### 1.3.1 definizione

Si dice che $$v$$ è combinazione lineare di vettori $$v_1, ... v_n$$ se esistono $$\lambda_1,...,\lambda_n \in K$$ tali che

$$\lambda_1v_1 + ....+ \lambda_n v_n = v$$

Possiamo prendere **l'insieme delle combinazioni lineari** cihe scriviamo come

$$\langle v_1, ..., v_n \rangle = \{\lambda_1 v_1 +... + \lambda_n v_n | \lambda_1, ..., \lambda_n \in R\}$$

Se $$V = \langle v_1, ..., v_n \rangle$$ allora i vettori $$v_1, ..., v_n$$  **generano** lo spazio vettoriale $$V$$

### 1.3.2 Proposizione 3.1.5  minimo sottospazio (chiede in esame)

Enunciato:

Sia $$V$$ uno spazio vettoriale, allora $$v_1, ..., v_n \in V$$ allora $$\langle v_1,...v_n\rangle$$  è uno sottospazio vettoriale di  $$V$$ ed è **il minimo** sottospazio vettoriale contenenti questi punti.

Dimostrazione: esercizio (non troppo complessa).

- hint di dimostrazione

    Bisogna dimostrare due cose: 1 è uno sottospazio vettoriale (soddisfa quei tre requisiti) e 2 è il minimo sottospazio vettoriale, quindi qualunque latro sottospazio vettoriale che contiene quei punti contiene anche questo spazio vettoriale).


### 1.3.3 Prop 3.1.8 dipendenza lineare + 1 (relativo a span)

sia $$\langle v_1, ..., v_n \rangle$$ uno spazio vettoriale generato da quei vettori, considero $$\langle v_1, ..., v_n, \omega \rangle$$ con $$\omega$$ una combinazione vettoriale dei vettori base, allora si ha che

$$\langle v_1, ..., v_n \rangle = \langle v_1, ..., v_n, \omega \rangle$$

- Hint di dimostrazione

    il primo è contenuto nel secondo (abbastanza ovvio, basta che tengo W 0), devo dimostrare che il secondo è contenuto nel primo.

    (in pratica riesco a dimostrare che qualunque combinazione lineare con $$\omega$$ è esprimibile come combinazione lineare dei vettori che generano lo spazio vettoriale iniziale

    Un altro modo per dimostrarlo è prendere Z generato dal primo insieme di vettori, so che tutti questi vettori sono contenuti in Z, così anche omega è contenuto, allora si ha per la 3.1.5 che questo spazio vettoriale è contenuto in Z.


Si può dimostrare una cosa anche contraria, ovvero

$$\langle v_1, ..., v_n \rangle = \langle v_1, ..., v_n, \omega \rangle \implies \omega$$ combinazione lineare di $$v_1,..., v_n$$

## 1.4 Indipendenza lineare

Questo concetto di indipendenza lineare ci permette di definire una base per uno spazio vettoriale (ossia il minimo insieme di vettori necessario per generare uno spazio)

### 1.4.1 Definizione

Un insieme di vettori $$v_1,..., v_n$$ sono linearmente indipendenti sse $$\alpha_1v_1 + ... + \alpha_nv_n = 0 \iff \alpha_1 = ... = \alpha_n = 0$$

Un insieme di vettori allora si dice *linearmente dipendente* se esiste un insieme di coefficienti tali che non tutti diversi da zero ottengo che $$\alpha_1v_1 + ... + \alpha_n = 0$$

**Osservazione**

Se un insieme di vettori contiene il vettore $$0_v$$ allora so per certo che sono linearmente dipendenti in quanto a questo vettore posso molitplicare qualunque cosa, fatto che va contro la definizione di indipendenza lineare

### 1.4.2 Prop 3.2.4 Corrispondenza combinazione e dipendenza lineare (chiede)

**Enunciato**

Se $$v_1,...,v_n$$ vettori dipendenti fra loro $$\iff$$  almeno uno di essi è combinazione lineare di dell'insieme dei vettori in questione.

**Dimostrazione**

- $$\implies$$

    Siano v1... vn vettori dipendenti fra loro, dobbiamo dimostrare che esiste uno che sia combinazione lineare di altri.

    Per ipotesi di dipendenza se $$\lambda_1v_1 +... + \lambda_nv_n =0, \exists k, 0 < k \leq n, \lambda_k \neq 0$$.

    Allora $$\lambda_kv_k = -(\lambda_1v_1 +...+ \lambda_{k-1}v_{k-1} +\lambda_{k+1}v_{k+1} +...+ \lambda_nv_n)$$ e da qui è abbastanza ovvio che posso scrivere $$v_k$$ come combinazione lineare di altri.

- $$\impliedby$$

    Sia $$v_k$$ una combinazione lineare dell'insieme di vettori $$v_1, ..., v_{k-1},v_{k+1},..., v_n$$

    Allora ho che $$v_k = \lambda_1v_1 +...+ \lambda_{k-1}v_{k-1} +\lambda_{k+1}v_{k+1} +...+ \lambda_nv_n$$ per certi valori di lambda.

    Allora se considero questa combinazione lineare

    $$-\lambda_1v_1 +... -\lambda_{k-1}v_{k-1} + 1\cdot v_k -\lambda_{k+1}v_{k+1} +...- \lambda_nv_n$$ ottengo che questo è uguale a 0 e in particolare ho che il coefficiente di $$v_k$$ è diverso da 0, quindi questi vettori sono dipendenti.


**Osservazione (sui multipli)**

Nel caso in cui ho due vettori, il fatto che uno è combinazione lineare dell'altro è equivalente a dire che uno è *multiplo* dell'altro.,

### 1.4.3 Geometria nella dipendenza lineare

**Due vettori**

Abbiamo detto che due vettori sono linearmente dipendenti quando uno sono multiplo dell'altro, possiamo intendere questo fatto algebrico come un *fatto geometrico* osservando che tali vettori devono giacere sulla **stessa retta**

**Tre vettori**

In modo analogo al precedente, possiamo concludere che tre vettori sono linearmente dipendenti sse **giacciono su uno stesso piano (COMPLANARI)**

**Più vettori**

Se ho n vettori, questi se fossero indipendenti giacerebbero su uno spazio n-dimensionale, appena è possibile esprimerli come appartenenti a  uno spazio di dimensione minore di n, allora posso dire che questi n vettori sono dipendenti, questa è l'astrazione necessaria per comprendere questo fatto.

| 12/03/22 |  Hai fatto tutte le dimostrazioni senza nessuna difficoltà. |
| --- | --- |
|  |  |
|  |  |
pendenti, questa è l'astrazione necessaria per comprendere questo fatto.

| 12/03/22 |  Hai fatto tutte le dimostrazioni senza nessuna difficoltà. |
| --- | --- |
|  |  |
|  |  |

# References