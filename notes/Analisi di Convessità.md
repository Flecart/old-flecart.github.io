---
layout: page
permalink: notes/analisi-di-convessità
tags: italian
title: Analisi di Convessità
---

Ripasso Prox: 20
Ripasso: May 22, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: May 2, 2022 3:23 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# Argomento

Questo argomento è stato trattato durante dopo la discussione dei [Massimi minimi multi-variabile](/notes/massimi-minimi-multi-variabile), però è stato ripreso anche nella forma R to R, quindi credo necessiti di un foglio a parte.

## Convessità e Concavità

### Definizione di convessità

È convessa se la derivata seconda è diversa da 0, ma non è una buona definizione perché non è direttamente relazionata con la concavità.

Possiamo definire la funzione secondo le tangenti, potremmo dire che la retta tangente sia sempre minore del grafico, in altro modo è una forma di tailor!

$$f: A \to R$$ tale che f sia derivabile, allora se prendo un intervallo $$(a,b) \subseteq A$$ posso dire che la funzione è convessa in questo intervallo se $$\forall x,k \in (a,b)$$ ottengo che

 $$f(x) \geq f(k) + f'(k)(x -k) = T_1(x)$$

**Definizione vera**

Non vorremmo avere una definizione che dipenda dall'esistenza della derivata, quindi

sia f una funzione ben definita, allora è convessa sse $$\exists m$$  nel dominio per cui valga che

$$f(x) \geq f(y) + m(x - y)$$

Oppure:

- Definizione secondo libro (con i segmenti)

    Allora cerchiamo una definizione migliore:

    sia $$f : \mathbb{R}^n \to \mathbb{R}$$ allora questa funzione si dice convessa sse $$\forall t \in [0,1]$$ si ha che

    $$\forall a,b \in \R^n: f(tb + (1 - t)a) \leq t f(b) + (1-t) f(a)$$ se vale con $$<$$ posso dire che è *strettamente convessa.*

    **Intuizione:**

    Comunque prenda un punto all'interno di un intervallo ho che la funzione valutata in questo punto è minore della somma della congiungente di questi due punti.


### Teorema di caratterizzazione delle funzioni convesse(!!)

Questo è un risultato molto simile a quanto ottenuto con le funzioni crescenti e la loro derivata prima, che si può trovare in [Teoremi Base Analisi](/notes/teoremi-base-analisi).

**Enunciato**

Sia una funzione $$f: \mathbb{R} \to \mathbb{R}$$, allora $$f$$ è **convessa** sse la sua derivata prima è $$>0$$.

La dimostrazione è abbastanza diretta quindi la si omette. (però la dovresti fare lo stesso perché è importante).
- Hintini di dimostrazione
    $$\implies$$ Supponiamo che f sia convessa, allora vale quella formula in definizione, voglio  dimostrare che la derivata sia crescente. (scrivo quella definizione due volte e ottengo qualcosa del tipo $$0 \geq$$  intervallo * (intervallo funzione, e si può risolvere senza molti problemi ottenendo il voluto, bisogna fare soprattutto attenzione a come definisci questi indici se vuoi andare a farlo in modo formale.
    $$\impliedby$$ Supponiamo che la derivata sia crescente, allora poi vado ad utilizzare lagrange (due volte, prima con un intervallo x y tale che $$x < y$$ e poi il contrario) fatto questo utilizzo la crescenza della derivata per concludere


**Corollario**

Possiamo utilizzare il risultato sopra per concludere che una funzione è convessa sse la derivata seconda è maggiore uguale a 0 (si possono utilizzare i teoremi riguardante le relazioni fra derivate e crescenza per questa).

### Segmento in Rn e convessità di punti

Dati due punti in $$\R^n$$ si può individuare il segmento in due punti $$x, y$$ come l'insieme costituito da

$$\{x + t (y - x) | t \in [0,1]\} = [x, y]$$

SI può verificare che che è uguale alla linea che li collega, in particolare è una **retta parametrica**.

Avendo questa definizione di segmento, posso andare a definire l'insieme convesso per Rn!.

**Convessità di un insieme di punti**

Un insieme di punti si dice convesso se $$\forall a, b \in A \subseteq \R^n, [a,b] \subseteq A$$ (e la definizione di insieme concavo non esiste, potremmo dire non convesso, ma non che sia concavo).

Avendo questo si può dimostrare che l'intersezione di semipiani è convesso.



### Convessità (concavità) in Rn

Possiamo allargare la definizione di funzione convessa che abbiamo dato poco fa in modo che ora sia buona anche a funzioni di più variabili.

f una funzione ben definita, allora è convessa sse $$\forall a,b \in A$$ si ha che

$$f(a) \geq f(b) + \langle\nabla f(b), (a - b) \rangle$$ e per parlare di funzione concava basta rovesciare la disuguaglianza.

Questa formula da l'idea che la funzione deve essere sempre sopra al piano tangente per ogni punto!

### Caratterizzazione della convessità in più dimensioni (!!!)

- Enunciato

    sia $$A \subseteq \mathbb{R}^n$$ che sia aperto e convesso, sia $$f\in C^2(A) \to \mathbb{R}$$ allora

    $$f$$ è convessa su A $$\iff$$ $$Hf(x) \geq 0, \forall x \in A$$.


Non è definito ora il concetto di crescenza per un gradiente, o vettore, quindi vogliamo passare prima sul gradiente.

Una funzione è convessa sse la matrice hessiana è semi-definita positiva.

Sia la espansione di taylor come l'abbiamo definita prima (con resto secondo Lagrange).

Può essere utile dare un occhiata al teorema di Lagrange al secondo ordine a più dimensioni prima

$$f(w + vt) = f(w) + \langle \nabla f(w), v \rangle t + \dfrac{1}{2}\langle Hf(c)v,v\rangle t^2$$

- Dimostrazione
    $$\impliedby$$
    Dato che $$\dfrac{1}{2}\langle Hf(c)v,v\rangle t^2 \geq 0$$ posso conclude la convessità (ossia la disuguaglianza appare abbastanza in fretta)
    $$\implies$$ Assumiamo ora la convessità, vogliamo dimostrare che la hessiana sia semidefinita positiva. Per l'espansione di taylor ho che  $$f(a + h) = f(a) + \langle\nabla f(a), h\rangle + \dfrac{1}{2}\langle H(f(a + \theta h)) h, h\rangle$$ definendo a, h e theta correttamente.
    Per la convessità ho che $$f(a + h) \geq f(a) + \langle\nabla f(a), h \rangle$$ e questo vale $$\forall h : a + h \in A$$
    Ma allora so che $$\dfrac{1}{2}\langle H(f(a + \theta h)) h, h\rangle \geq 0$$ (perché altrimenti ci sarebbe un valore in input per cui nonvale la condizione di convessità.

    Devo dimostrare che $$v \in \R^n \neq 0 : a + v \in A$$, $$\langle H(f(a)) v, v\rangle \geq 0$$, scelgo una successione in questo modo:
    $$h_k = 1/k \cdot v$$ che tende a 0 per k che tende a infinito.
    Definito in questo modo ho che c'è un theta per cui valga   $$\dfrac{1}{2}\langle H(f(a + \theta v/k)) v/k, v/k\rangle \geq 0 \iff \dfrac{1}{2}\langle H(f(a + \theta v/k)) v, v\rangle \geq 0$$ arrivato a questo punto mando k all'infintio e utilizzo

    Per continuità ho che il limite $$\lim_{k \to \infty}$$ è uguale a  $$\langle H(f(a)) v, v\rangle$$  la permanenza del segno per concludere il voluto (se ogni elemento della successione è maggiore di 0 allora anche il limite a cui sta tendendo è maggiore di 0)

## Teoremi importanti
### Jensen
Questo è uno dei teoremi legati alla convessità (concavità più usati in assoluto). Una applicazione classica è per il il valore atteso, analizzato in [Variabili aleatorie](/notes/variabili-aleatorie) e simili.

Sia $$f$$ una funzione convessa in un intervallo $$[a, b] \subseteq \mathbb{R}$$, allora vale che

$$
f(\lambda a + (1 - \lambda)b) \leq \lambda f(a) + (1 - \lambda) f(b)
$$

Questa è la formulazione semplice, ma si può estendere per qualunque combinazione convessa dell'input (per combinazione convessa di $$a_{1}, a_{2}, \dots, a_{n}$$ intendo $$a_{1}\lambda_{1} + \dots + a_{n}\lambda_{n}$$ dei parametri $$\lambda_{1}, \lambda_{2}, \dots, \lambda_{n}$$ tale per cui $$\sum_{i=1}^{n}\lambda_{i} = 1$$).

Non so bene la dimostrazione, ma l'intuizione è abbastanza semplice in due variabili, se combini due punti su una retta sopra la funzione, questa sarà maggiore del valore che ricevi combinando gli input, dato che è convessa è una funzione ad $$U$$.


# Registro ripassi

| Giorno     | Commenti                                                                                 |
| ---------- | ---------------------------------------------------------------------------------------- |
| 03/03/2024 | Mi ricordo che ai tempi non l'ho fatta bene, perché  era una cosa per loro di poco conto |
|            |                                                                                          |
 (se ogni elemento della successione è maggiore di 0 allora anche il limite a cui sta tendendo è maggiore di 0)