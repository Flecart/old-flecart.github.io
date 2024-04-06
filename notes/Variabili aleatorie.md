---
layout: page
permalink: notes/variabili-aleatorie
tags: en
title: Variabili aleatorie
---

Ripasso Prox: 5
Ultima modifica: May 6, 2023 5:51 PM
Primo Abbozzo: March 14, 2023 10:50 AM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Variabili aleatorie discrete

Con le variabili aleatorie cominciamo ad entrare nel noccio della questione, finalmente possiamo in un certo senso legare l’outcome di un evento, alla probabilità dell’evento.

## Introduzione

### Definizione VA 🟩

> Si definisce variabile aleatoria $$X$$ una funzione da $$\Omega \to E$$, con Omega il nostro spazio campionario, e $$E$$ qualunque insieme (quando $$E = \mathbb{R}$$ si parla di **variabile aleatoria reale**
>

Quindi un esempio classico per il dado, potremmo definire una variabile aleatoria dallo spazio campionario $$\Omega = [1, 2, 3, 4, 5, 6]$$ ai reali, tali che $$X(1) = 1, X(2) = 2$$ etc, in questo senso stiamo facendo una funzione fra abitanti di insiemi diversi, ma resta una funzione.

Spesso variabili aleatorie rappresentano un qualcosa che dipende dall’esito, questo valore può essere numerico come in questo caso (noi in questo corso resteremo al numerico), ma non è necessario che lo sia.

variabili aleatorie più interessanti per esempio il numero di lanci medio per avere 6, obboh, hai molte libertà di creare le funzioni.

**NOTA:** solitamente indichiamo il dominio della variabile aleatoria come da uno spazio di probabilità, ossia in cui  $$P$$ sia definita. Questa notazione ci risutlerà comodo quando andiamo a parlare di distribuzione di probabilità di uno spazio aleatorio.

### (Legge) Distribuzione di probabilità 🟩

Definiamo una funzione $$P_X$$ in questo modo:


$$
P_X(A) = P(\{\omega \in \Omega: X(w) \in A\}), A \subseteq E
$$


Possiamo dimostrare che questa è effettivamente una probabilità su $$E$$! Basta dimostrare la sigma additività e il fatto che $$P_X(E) = 1$$, l'ultimo è ovvio, perché per come è definito X, abbiamo che $$\Omega = \{\omega \in \Omega: X(w) \in E\}$$

Il secondo punto è leggermente più complicato, ma lascio al lettore.

Inoltre andiamo a definire questo insieme come **l’esito associato**


$$
\text{Esito associato a una variabile aleatoria X:} \\
\{\omega \in \Omega: X(w) \in A\}
$$


### Def: Funzione di ripartizione (CDF) 🟩

<img src="/images/notes/image/universita/ex-notion/Variabili aleatorie discrete/Untitled.png" alt="image/universita/ex-notion/Variabili aleatorie discrete/Untitled">

### Proprietà Fn ripartizione discreta (4) 🟨-

1. Monotòna crescente (tal cred lol)
2. Continua a destra
3. $$\lim_{x \to -\infty} F_X(x) = 0$$
4. $$\lim_{x \to +\infty} F_X(x) = 1$$
- Dimostrazione delle proprietà

    <img src="/images/notes/image/universita/ex-notion/Variabili aleatorie discrete/Untitled 1.png" alt="image/universita/ex-notion/Variabili aleatorie discrete/Untitled 1">


### Def: Densità discreta

La funzione di probabilità di massa o anche densità discreta ci dice nell’insieme di arrivo quanto sia probabile che si abbia quel valore, possiamo rappresentarlo in questo modo:


$$
p_X(x) = P(\{w\in \Omega: X(w) = x\}), x\in E
$$


### Variabili aleatorie discrete

Si parla di variabili aleatorie discrete quando il sottoinsieme $$S_X \subseteq E$$ degli elementi tali per cui $$P_X(S_X) > 0$$, è o finito o numerabile, allora in questi casi se $$\forall y \in S_X$$ definiamo una probabilità, abbiamo una probabilità!

### Teorema di caratterizzazione delle variabili aleatorie discrete

- Slide del teorema

    <img src="/images/notes/image/universita/ex-notion/Variabili aleatorie discrete/Untitled 2.png" alt="image/universita/ex-notion/Variabili aleatorie discrete/Untitled 2">


Questo teorema ci dice una cosa molto stupida sulle variabili aleatorie, una cosa che credo abbiamo già dimostrato in [Spazi di probabilita](/notes/spazi-di-probabilita), che in pratica è la stessa.

In pratica ci sta dicendo che tutte le variabili aleatorie discrete possono essere descritte secondo la probabilità di massa


# Variabili aleatorie continue

Le variabili aleatorie continue ci sono utili quando vogliamo descrivere qualcosa che è difficilmente discretizzabile, come per esempio l’emivita di una batteria. Fatto sta che il suo modello ha un sacco di peculiarità che lo rendono molto diversa rispetto a una variabile aleatoria normale:

## Introduzione

### Proprietà di VA continua (2)

1. $$\forall x \in \R, f_X(x) = 0$$
2.  $$\int_{-\infty}^\infty f_X(x)dx = 1$$

Si può poi dimostrare che

1. $$P(a \leq x\leq b) = \int_a^bf_X(x)dx$$

Si noti che non abbiamo più bisogno che $$f_X (x) \leq 1 \forall x \in \R$$, basta che l'integrale di tutto sia 1

Per la propreità 1 abbiamo questo fatto:

> la probabilità che una variabile aleatoria continua X assuma valori in un intervallo non dipende dal fatto che gli estremi dell’intervallo siano inclusi o esclusi,
>

### Non univocità della densità

la funzione f_X definita in precedenza sarebbe la funzione di densità continua della nostra probabilità. Fatto sta che così definita se cambiamo la nostra funzione in un numero finito oppure infinto numerabile di punti, allora l'integrale possiede ancora lo stesso valore, quindi è una densità valida (basta provare a spezzare la somma dell'integrale per tutti i punti in cui si è cambiato e si può verificare questo dato).



# References