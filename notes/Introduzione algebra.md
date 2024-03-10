---
layout: page
permalink: notes/introduzione-algebra
tags: italian
title: Introduzione algebra
---

Ripasso Prox: 36
Ripasso: June 1, 2022
Ultima modifica: October 19, 2022 5:05 PM
Primo Abbozzo: December 12, 2021 11:58 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- significato di compatibilità
- Il vettore dei termini noti, non ti ricordavi la parola termini noti 😀

# 0 Introduzione

Tutta sta parte si fa in modo formale in [Sistemi Lineari e determinanti](/notes/sistemi-lineari-e-determinanti), quindi potresti saltarla totalmente

## 0.1 Equazioni lineari

L'obiettivo dell'algebra lineare è risolvere n equazioni con n sconosciuti di primo grado.
Cosa che ci riesce con grandissimo successo! Andiamo ora a definire meglio cosa è una equazione lineare

### 0.1.1 Definizione

Una equazione lineare è una equazione a coefficienti appartenenti a un certo campo (che può essere R) e incognite il cui grado è 1 e che siano indipendenti:

es.


$$
a_1x_1 + a_2x_2 +...+a_nx_n=b
$$


lo puoi considerare come una equazione lineare, mentre cose come


$$
\begin{cases}
x^2 = 2 \\
xy = 2
\end{cases}
$$


Non lo sono.

### 0.1.2 Equivalenza e compatibilità

**Equivalenza:** due sistemi sono equivalenti quanto hanno le stesse soluzioni

**Compatibilità:** Un sistema si dice compatibile quando ammette soluzioni

### 0.1.3 Soluzione di una equazione lineare

Una soluzione di una equazione lineare a n variabili, è una n-tupla di valori ordinati che soddisfano l'equazione. La cosa che ci interesserà sarà la soluzione di un *sistema di equazioni lineari* ovvero tante equazioni lineari che vogliono essere tutte soddisfatte allo stesso momento.

### 0.1.4 Proprietà dell’uguaglianza

È molto importante per comprendere le equazioni comprendere le due proprietà dell'uguaglianza che si studiano di solito alle medie.

Sono due, una per la somma e una per la moltiplicazione scalare.

1. **Somma**:
Data una eguaglianza a = b, questa è uguale sse per ogni c, c + a = c + b.
2. **Moltiplicazione scalare:**
Data una eguaglianza a = b, questa è uguale sse per ogni c si ha ca = cb (la prof ha tolto il caso in c = 0)

## 0.2 Le matrici

### 0.2.1 Definizione

Potremmo definire la matrice solamente come una tabella che contiene dei numeri, a volte nemmeno si dà il nome di tabella, ma solamente come una *collezione indicizzata di coefficienti*.

potresti definire matrice così $$M = (a_{ij})_{nm}$$

In genere una matrice di dimensione nxm si scrive in notazione sul campo su cui è definito, per esempio

$$M_{n \times m}(\R)$$, se è quadrata di solito si sottindende l'altra dimensione e si scrive $$M_n(\R)$$.

### 0.2.2 Vettori riga e colonna

Si potrebbero definire dei vettori riga e colonna a seconda delle dimensioni della matrice:

di dimensione 1xn sono vettori riga

di dimensione nx1 sono vettori colonna

Questi vettori sono importanti poi per scomporre la matrice, quindi ora basta tenerli a mente

### 0.2.3 Costruzione della somma e prodotto scalare

Possiamo sempre fare la somma di due matrici con le stesse dimensioni definite sullo stesso campo.

**Somma**

Infatti se prendiamo A e B , la matrice somma C è la matrice costituita dalla somma elemento per elemento (somma per indici corrispondenti).

**Scalare**

Per il prodotto scalare moltiplichiamo ogni elemento della matrice per quel coefficiente.

### 0.2.4 Prodotto matriciale

Questo prodotto fra matrici è più complessa rispetto alla somma e il prodotto. (È utile perché le matrici rappresentano una trasformazione nello spazio, questo prodotto rappresenta la composizione fra le funzioni che rappresentano).

<img src="/images/notes/image/universita/ex-notion/Introduzione algebra/Untitled.png" alt="image/universita/ex-notion/Introduzione algebra/Untitled">

Tratto da wikipedia

Quindi vogliamo avere che il numero delle colonne del primo sia uguale al numero delle righe del secondo. Questo è soddisfatta questa condizione possiamo sempre fare la moltiplicazione.
Lo facciamo così, consideriamo il risultato fra il prodotto del vettore riga i con il vettore colonna j, questo è un prodotto scalare, che mi restituirà un unico numero, questo è il valore di $$c_{ij}$$

**Proprietà:**

Si può dimostrare che il prodotto fra matrici gode della proprietà

1. **Associativa**
2. **Distributiva**

Non è commutativa!

### 0.2.5 Transposizione

Si può definire una matrice trasposta, bisogna scambiare gli indici associati. Es:

$$(A^T)_{ij} = (A)_{ji}$$ con i, j gli indici della matrice

## 0.3 Matrici a scala

**Matrice a scala:** Si ha quando considerando il primo elemento non nullo partendo da sinistra, sotto di questo sta uno 0, e eementi a sinistra di questo sono nulli ( o niente), partendo a contare dall'alto.

### 0.3.1 Matrice associata a un sistema

Si può associare una matrice a ogni sistema lineare, come in figura.

- Dal libro

    <img src="/images/notes/image/universita/ex-notion/Introduzione algebra/Untitled 1.png" alt="image/universita/ex-notion/Introduzione algebra/Untitled 1">

    <img src="/images/notes/image/universita/ex-notion/Introduzione algebra/Untitled 2.png" alt="image/universita/ex-notion/Introduzione algebra/Untitled 2">


Notare il significato di matrice **completa** o **incompleta** presente nella slides

Costruendo la matrice associata completa, dobbiamo distinguere fra la matrice *delle incognite*, dei *coefficienti* e dei *termini noti*

### 0.3.2 Pivot e RR

**Pivot:** per ogni riga, il primo valore da sinistra per cui non è nullo, è il valore di pivot

**Rango righe:** il rango righe di una matrice a scala è il numero di pivot totale, si indica spesso con $$rr_a()$$ questo determina anche una dimensione dello spazio vettoriale o simili, li vedi in [Spazi vettoriali](/notes/spazi-vettoriali)

### 0.3.3 Risolvere una matrice a scala

Quando ho una matrice a scala diventa molto semplice risolvere il sistema per sostituzione.

Riesco subito a determinare se la matrice ha soluzione finita, infinita e simili. (è una cosa pratica quindi non ti metto appunti qui).

Per avere in generale un feeling generale su questo:

1. $$rr(A) = rr(A|b)$$ una sola soluzione
2. $$rr(A) < rr(A|b)$$ impossibile
3. $$rr(A) > rr(A|b)$$ infinite soluzioni con certe variabili libere

### 0.3.4 Operazioni elementari (3)

Possiamo agire sul sistema (e quindi anche sulla matrice associata al sistema) con certe operazioni che mi cambiano la matrice ma non cambiano la soluzione del sistema

1. Scambio posizione riga di due equazioni
2. Moltiplicazione per un numero reale diverso da 0 (deriva dalle proprietà dell'uguaglianza descritto in precedenza)
3. Sommare (o sottrarre) una riga all'altra. (quindi unendola alla 2 posso farlo con una riga scalata)

### 0.3.5 Trasformazione in matrice a scala

Data una matrice normale possiamo sempre trasformalo in matrice a scala

<img src="/images/notes/image/universita/ex-notion/Introduzione algebra/Untitled 3.png" alt="image/universita/ex-notion/Introduzione algebra/Untitled 3">

Una volta ottenuta questa matrice possiamo andare ad analizzarla con il rango righe come sopra

### 0.3.6 Sistema omogeneo

Un sistema di equazioni si dice omogeneo quando i termini noti sono tutti 0.

Questo sistema **ha sempre almeno una soluzione** la soluzione banale tutti 0.
### 0.3.6 Sistema omogeneo

Un sistema di equazioni si dice omogeneo quando i termini noti sono tutti 0.

Questo sistema **ha sempre almeno una soluzione** la soluzione banale tutti 0.