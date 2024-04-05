---
layout: page
permalink: notes/calcolo-differenziale
tags: en
title: Calcolo differenziale
---

Ripasso Prox: 24
Ripasso: June 2, 2022
Ultima modifica: October 8, 2022 12:08 PM
Primo Abbozzo: March 14, 2022 2:11 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

- DImostrare per benino la condizione sufficiente di differenziabilità perché probabile che alcuni passaggi non li fai per filo e per segno.

# 10 Calcolo differenziale

## 10.1 Derivata parziale

La derivata vuole descrivere quanto varia una funzione al variare dell'input. Ma ora siamo in più dimensioni, quindi vogliamo descrivere il variare dell'input come il variare della distanza euclidea

$$\dfrac{\delta f}{\delta x}(x,y) = \lim _{h \to 0} \dfrac{f(x + h, y) - f(x, y)}{h}$$ ovvero sto facendo variare solamente una variabile (la y in questo caso è come se fosse una costante!?) Questo è un **rapporto incrementale su una direzione**.

Se esiste il limite, è la derivata parziale rispetto a x.

In modo analogo puoi definire una derivata parziale rispetto a y

### 10.1.1 Gradiente

Se vogliamo considerare allo stesso momento la derivata parziale per ogni componente, possiamo farlo considerando un unico simbolo: (indica il gradiente della funzione).


$$
\nabla f(x,y) = (\delta_xf(x,y), \delta_y f(x,y))
$$


Se in ogni punto è derivabile allora possiamo proprio definire una funzione gradiente di questa, nel modo di sopra.

Questa definizione si può estendere per uno spazio n-dimensionale

### 10.1.2 Legame con la continuità

Si ha una relazione molto simile con la derivata a singola dimensione (cazzo non mi ricordo bene la dim????)

$$f:A \to \R$$ se $$f$$ è derivabile in $$x$$ allora $$f$$  è continua in $$x$$ in R normale, ma se a più dimensioni avessimo le derivate parziali **non abbiamo la continuità in quel punto**.

EG 
$$\begin{cases}
\dfrac{xy}{x^2 + y^2}  \text{ se diverso dall'origine }\\
0 \text { altrimenti }
\end{cases}$$

in questo esempio entrambe le derivate parziali in (0,0) esistono, ma non è continua in questo punto (tende a +- infinito in questo punto).

- Analisi della funzione sopra

    Si può dimostrare che la funzione di sopra ha entrambe le derivate uguali a 0 quando tende a 0. (applicare la definizione di derivata parziale).

    Dimostriamo che non è continua in (0,0) ovvero esiste una successione che tende a 0, ma non vale la definizione di continuità, ovvero non vale che $$f(a_n, b_n) \to f(0,0) = 0$$.

    Scegliamo la successione simile: $$(a_n,b_n) = (1/n, 1/n)$$ che ovviamente tende a 0.

    Ma .

    ```haskell
    (1/n * 1/n) / (2/(n*n)) != 0
    ```

    Quindi questa successione tende a 2, mentre dovrebbe tendere a 0. Un caso patologico di continuità, ma che comunque da l'idea di questo.


### 10.1.3 Derivabilità e differenziabilità (intuizione)

Si ricordi la definizione di derivata in $$\R$$. [Derivate](/notes/derivate).

Si ricordi anche come si è ricavata l'approssimazione con serie di taylor e gli o-piccoli in [Hopital, Taylor, Peano](/notes/hopital,-taylor,-peano)

Per descrivere la nozione di derivabilità vogliamo ricondurci a una formula di Taylor per il primo grado. (perché nelle derivate parziali sappiamo quando varia in due direzioni, ma mancano informazioni su quanto varia in tutte le direzioni, ed è per questo motivo che non ho la continuità).

Vorrei considerare un limite simile a  $$f(x + h, y+ h) - f(x, y)$$, che possiamo riscrivere in forma vettoriale $$f((x + y)+ (h,k)) - f(x,y)$$ e ricondurci a una forma di approssimazione con taylor.

**Def o-piccolo a più dimensioni:**

$$g: \mathbb{R}^2 \to \mathbb{R}$$ si dice che $$g(h,k) = o(\lvert(h,k)\rvert)$$ se ho che $$\lvert g(h,k)\rvert/ \lvert (h,k)\rvert < \epsilon$$ , con $$0< \lvert(h,k)\rvert  < \delta$$ per ogni epsilon maggiore di 0, quindi considero la norma (che mi da una nozione di distanza).  Ma i concetto di o-piccolo è ancora ben presente.

Possiamo anche scrivere la stessa definizione utilizzando le successione.
- Come qui
    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled">


Avendo questa nozione di approssimazione per taylor, posso dare una nozione di differenziabilità.
In questo modo riesco a dare una nozione di funzione che tende a zero più o meno velocemente della norma. (o potenze di esse).

## 10.2 Differenziabilità

Questa è la condizione molto più forte rispetto alla derivata, è il concetto che ci permette di avere subito la continuità.

La differenza principale con la derivata è che qui **non consideriamo una unica direzione** cerchiamo di prenderle tutte. Andiamo ora a vedere come definire questo fatto.

### 10.2.1 La funzione differenziabile

Sia $$f$$ una funzione da $$A \subseteq \R^2$$  aperto da $$f: A \to \R$$. Si dice che la funzione $$f$$ sia differenziabile se:

1. Esistono le derivate parziali per tutte le direzioni.
2. Se vale


$$
f((x + h, y + k)) = f((x, y) + (h,k)) = f(x,y) + \langle\nabla f(x,y), (h,k)\rangle + o(\lvert h,k \rvert )
$$


Possiamo scrivere questa cosa con una altra notazione equivalente:

$$f(x, y) = f(\bar{x}, \bar{y}) +\langle\nabla f(x,y), (x - \bar{x},y - \bar{y})\rangle + o((\mid x - \bar{x},y - \bar{y} \mid)$$  con $$(x,y) \to(\bar{x}, \bar{y})$$

E questo assomiglia di più rispetto al polinomio di taylor, perché effettivamente qui si ha l’approssimazione in bella vista.

Andiamo ora a dare una intuizione sul perché vogliamo la seconda condizione.

**Intuizione del punto 2**

Non stiamo facendo altro che dare la formula di taylor del primo ordine (vedi [Hopital, Taylor, Peano](/notes/hopital,-taylor,-peano)) sul punto (x, y) ma lo stiamo considerando a più dimensioni.

Quindi, ricordando che l’espansione con le serie di taylor ci permetteva di fare una approssimazione, questa condizione per il punto 2 non è altro che una approssimazione al variare in una qualsivoglia direzione.

### 10.2.2 Polinomio di taylor del primo ordine


$$
T_1(x,y) = f(\bar{x}, \bar{y}) +\langle\nabla f(x,y), (x - \bar{x},y - \bar{y})\rangle
$$


In particolare qui abbiamo una approssimazione dell’equazione tangente a un punto voluto (in R2 un piano, in R1 una retta, in R3 vedi che è uno spazio), il punto $$(\bar{x}, \bar{y}, f(\bar{x}, \bar{y}))$$

### 10.2.3 Differenziabilità implica continuità

$$f:A \to \R$$  aperto (perché così ho tutti gli intorni e questo mi semplifica prendere successioni a caso)) in R2.

se f è differenziabile in un punto $$(a,b) \implies f \text{ continua in } (a, b)$$

Dobbiamo dimostrare che per ogni successione che tende a (0,0) deve essere che $$f(a + h_n, b+ k_n) \to f(a,b)$$ se ho dimostrato questa cosa ho la continuità. Ma per il punto 2 della definizione di differenziabilità ho che $$f(a,b) + \langle\nabla f(a,b), (h,k)\rangle$$ ma con h e  k tendenti a 0 ho che il prodotto scalare del gradiente di esse è tendente a 0 (anche o piccolo lo è) , quindi ho la continuità.

### 10.2.4 Condizione sufficiente di differenziabilità (!!!)

> Se le derivate parziali esistono e sono continue (f di classe C1) , f è differenziabile in ogni punto
>

La definizione di differenziabilità non è molto maneggevole, per questo motivo ci è utile cercare una condizione di differenziabilità che sia più semplice da calcolare.

Questo è uno dei teoremi principali della differenziabilità. Collega questo con il concetto di derivata, già studiata in precedenza in R

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 1.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 1">

    Una volta definita la **funzione di classe C1** possiamo riscrivere questo enunciato in maniera più compatta. Queste funzioni sono tali per cui la derivata parziale in ogni direzione esiste , e questa derivata è anche continua (ricorda questa definizione di Classe k)

    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 2.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 2">

- Lemma preliminare (Lagrange multivariabile)

    Utilizziamo un lemma per dimostrare il punto di sopra.

    $$
    f \in C^1(\R^2),  \text{ siano } (a,b) \in \R^2,  h, k \in \R \implies \exists \alpha, \beta \in (0,1)  | \\f(a + h, b) - f(a,b) = \delta_x f(a + \alpha h, y) h
    \\ f(a, b + k) - f(a,b) = \delta_y f(a, b + \beta k) k
    $$

    La dimostrazione è analoga per i due punti, quindi lo facciamo solamnete per uno.
    Per il teorema di lagrange presente nei reali, mi costruisco la funzione $$g(x) = f(x, t)$$ con un t fissato (notiamo che g è continua e derivabile in quanto è costituito da f, che per ipotesi è continua e derivabile), allora esiste c appartenente al dominio di g tale per cui $$g'(c) \cdot h = g(a + h) - g(a)$$ ossia $$f(a + h,b) - f(a,b)$$. Ecco che appaiono i valori di cui abbiamo bisogno in RHS.

    Guardando LHS abbiamo che

    $$
    g'(x) = \lim_{s \to 0}\dfrac{g(x + s) - g(x)}{s} = \lim_{s \to 0}\dfrac{f(x + s, t) - f(x, t)}{s} = \delta_xf(x)
    $$

    Scrivendo c come prodotto di h  e un opportuno $$\alpha$$ possiamo dire che $$c = a + \alpha h$$ (tanto deve stare in questo intervallo $$(a, a +h)$$, quindi è possibile assumere che ci sia tale alpha compreso da 0 e 1).

    Riscrivendo il tutto per benino abbiamo la nostra tesi.

- Dimostrazione

    Per definizione di differenziabilità devo dimostrare che ciò sia vero.

    $$\langle\nabla f(a,b), (h,k)\rangle + o(|h, k|) = f(a + h, b + k) - f(a,b) = f(a + h, b + k) - f( a+h, b) + f(a+h, b) - f(a,b)$$

    Aggiungendoci e togliendo quel fattore dopo l’ultima equazione, posso mettermi ad utilizzare Lagrange multivariabile (ho per il primo che x è la stessa, per il secondo y è la stessa).

    Andiamo a utilizzare le derivate parziali allora:

     $$f(a + h, b + k) - f( a+h, b) = \delta_yf(a+h , b+\beta k)k$$

    e in modo simile

    $$f(a+h, b) + f(a,b) = \delta_x f(a + \alpha h, b) h$$

    Allora riscriviamo la equazione iniziale, e vediamo che sia corretta effettivamente:

    $$\langle\nabla f(a,b), (h,k)\rangle + o(\lvert h,k \rvert) = \delta_yf(a+h , b+\beta k)k + \delta_x f(a + \alpha h, b) h$$

    Ho $$h\delta_x f(x,y) + k \delta _yf(x,y) + o(\lvert h,k \rvert)$$ dal gradiente. Se riesco a dimostrare questo allora ho finito.

    Se riusciamo a dimostrare $$\delta_x f(a + \alpha h, b) h = h\delta_x f(x,y) + o(\lvert h, k \rvert)$$ allora ho finito (stessa cosa per l’altra).

    L’ultima proposizione è equivalente a dire che $$\delta_x f(a + \alpha h, b) h - h\delta_x f(a,b) = o(\lvert h,k \rvert)$$

    ovvero che (per definizione di o piccolo) quella cosa tenda a 0, ossia che.

    $$
    \lim_{h,k \to (0,0)} \dfrac{h}{\lvert h, k \rvert} [\delta_x f(a + \alpha h, b) - \delta_x f(a,b)] = 0
    $$

    $$\dfrac{h}{\lvert h,k \rvert} [\delta_x f(a + \alpha h, b) - \delta_x f(a,b)]   \leq  [\delta_x f(a + \alpha h, b) - \delta_x f(a,b)]$$  per le proprietà della norma.

    Ora utilizziamo la continuità della derivata, che si ha in ipotesi e possiamo concludere che quella differenza.

    - Conclusione con la continuità
        <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 3.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 3">

        E si può dimostrare che $$a + \alpha h, b) \in B(a,b),\delta)$$
        <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 4.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 4">

        <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 5.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 5">

        E l’ultimo dato è vero per ipotesi di continuità.


## 10.3 Derivata direzionale

Il concetto di derivata direzionale generalizza il concetto di derivata parziale, perché ora invece di andare in una direzione di una base canonica, andiamo nella direzione di un vettore.

### 10.3.1 Definizione
Dato $$x \in \mathbb{R}^n$$ e $$v\in \mathbb{R}^n-\{0\}$$, consideriamo l'insieme $$\{x + tv | t \in \mathbb{R}\}$$, abbiamo l'insieme di una linea, passante per il nostro punto che abbia la direzione del vettore preso.

Allora con tutto questo iniziamo la definizione:

$$f:A \to \mathbb{R}, (a,b) \in A$$ e dato $$v = (v_1, v_2)$$ un vettore unitario, allora si ha che la derivata direzionale è


$$
\lim_{t \to 0} \dfrac{f((a,b) + tv) - f(a,b)}{t}
$$


In pratica stiamo andando in una direzione scelta di v. (da notare infatti che se preso il vettore in una direzione parallela alla base canonica, allora ho le derivate parziali).

**Osservazione 2**
Posso creare una funzione ausiliaria, e vedo che la derivata direzionale è uguale alla derivata (normale 1-variabile) della funzione ausiliaria:
$$g(t) = f(a + tv_1, b+ tv_2)$$
Si nota che $$D(g(t)) = \lim_{h \to 0} \dfrac{g(h) -g(0)}{h} = \dfrac{f(a + tv_1, b+ tv_2) - f(a, b)}{h}$$

### 10.3.2 Formula del gradiente (!!!)

Presa una funzione differenziabile con dominio opportuno e codominio R2, e un vettore in R2, possiamo definire con precisione la derivata direzionale su questo vettore in particolare è:

$$\dfrac{\delta f}{\delta v} (a,b) = \langle \nabla f(a,b), (v_1,v_2)\rangle$$

**Osservazione**

Questa è una cosa forte, perché mi dice che se conosco le derivate parziali riesco a trovare il valore della derivata in qualunque direzione. Ma da notare che deve essere *differenziabile!*.
- Dimostrazione
    $$
    f(a + tv_1, b+ tv_2) - f(a, b) = \langle\nabla f(a,b), tv\rangle + o(\lvert tv \rvert)
    $$
    Questo vale per la formula di Taylor, noi siamo però interessati al limite, quindi siamo interessati a questo:
    $$
    \lim_{t \to 0} \dfrac{ \langle\nabla f(a,b), tv\rangle + o(\lvert tv \rvert )}{t}
    $$
    Ed è abbastanza ovvio che la soluzione di questo limite è $$\langle\nabla f(a,b), v\rangle$$ (basta portare fuori la t e dividerla con la t di sotto), mentre l'o-piccolo tende a 0 per definizione di o piccolo.


### 10.3.3 Direzione massima e minima di crescita (!!)

Il problema corrente è stabilire la direzione massima di crescita per una funzione differenziabile definita in dominio di dimensione maggiore di 0.

Dato il gradiente (consideriamo questo diverso da 0 perché nell'altro caso è qualcosa di abbastanza banale). Se è diverso da 0, posso allora normalizzare il vettore (e scriverlo con coordinate polari in un modo simile a quanto fatto in [Analisi multi-variabile](/notes/analisi-multi-variabile).


$$
\nabla f(a,b) = \lvert \nabla f(a,b) \rvert \cdot (\cos\theta, \sin \theta)
$$


Ricordiamo per punto sopra che la derivata direzionale è

$$\langle \nabla f(a,b), (v_1,v_2)\rangle$$, (notiamo che v è definito come versore, quindi possiamo passare alle cordinate polari anche lì, allora il valore di questa derivata direzionale è


$$
\langle \nabla f(a,b), (\cos\gamma,\sin\gamma)\rangle = \lvert \nabla f(a,b) \rvert \cdot \cos(\theta - \gamma)
$$


Che è massima quanto il valore nel coseno è 1 (coseno 0), minima quando è 0.

Ma esiste solamente un unico vettore unitario per cui succede, questa è la direzione che rende massima la derivata. dunque $$\theta = \gamma$$ e quindi


$$
v_{max} = \dfrac{\nabla f(a,b)}{ \lvert \nabla f(a,b)  \rvert }
$$


**Osservazione:**

Avendo il vettore di direzione per il massimo possiamo calcolare effettivamente il valore della derivata direzionale massima, questa è effettivamente uguale al gradiente:


$$
\langle \nabla f(a,b), v_{max})\rangle = \mid\nabla f(a,b)\mid
$$


## 10.4 Derivate di curve

Consideriamo le curve (anche chiamati cammini in Rn)

Due funzioni

1. Scalari da Rn a R
2. Cammini parametrizzati (da un sottoinsieme di ab a Rn)

In seguito saranno utili per comprendre gli insiemi di livello di f.

### 10.4.1 Cammini

I cammini sono una funzione da R a Rn.

Sono utili in fisica per descrivere il concetto di percorso (traiettoia) e simili

**Velocità di un cammino**

possiamo definire una dimensione di velocità di un cammino in questo modo:

<img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 6.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 6">

**Nota:** non è il gradiente, perché qui la derivata è una sola, solo per funzioni differenti.

Quella derivata (il vettore) è **velocità al tempo t**.

### 10.4.2 Nozioni di fisica(velocità e accelerazione)

**Velocità scalare:**

<img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 7.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 7">

Quando la derivata è nulla in tutti i punti si dice che quel punto della traiettoria è un **punto singolare**

**Accelerazione:**

<img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 8.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 8">

### 10.4.3 Taylor per curve

<img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 9.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 9">

- Altro

    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 10.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 10">


### 10.4.4 Derivata lungo una curva (!!)

<img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 11.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 11">

- Introduzione intuitiva della derivata

    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 12.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 13.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 13">


Come si nota, la curva non è detto che sia derivabile, quindi prima la parametriziammo, e poi calcoliamo la derivata della funzione composta, e nient’altro.

### 10.4.5 Ortogonalità del differenziale (!)

<img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 14.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 14">

- Dimostrazione veloce veloce

    <img src="/images/notes/image/universita/ex-notion/Calcolo differenziale/Untitled 15.png" alt="image/universita/ex-notion/Calcolo differenziale/Untitled 15">


### Calcolo di queste derivate (idea)

Se dobbiamo calcolare qualcosa di complesso, tipo

f una funzione differenziabile, e voglio la derivata di $$f(h_1(s),..., h_n(s))$$ posso crearmi una funzione di appoggio, che possiamo anche chiamare la **parametrizzazione della funzione** come

$$r(s) = (h_1(s),...,h_n(s))$$ e calcolarmi la derivata di $$f(r(s))$$ che abbiamo discusso sopra, alla fine avrò qualcosa del tipo

$$\delta_{e_1}f(r(s))\delta_s(h_1(s)) + ... + \delta_{e_n}f(r(s) \delta_s(h_n(s))$$