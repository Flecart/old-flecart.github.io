---
layout: page
permalink: notes/massimi-minimi-multi-variabile
tags: italian
title: Massimi minimi multi-variabile
---

Ripasso Prox: 6
Ripasso: May 18, 2022
Ultima modifica: October 8, 2022 12:07 PM
Primo Abbozzo: April 5, 2022 4:23 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Elementi di ripasso

074179

- gli utilizzi della matrice jacobiana
- Riguardarsi come la continuità finisce la dimostrazione di schwarz
- Rivedere i calcoli e l'idea principale per taylor al secondo ordine di coso.

# Massimi e Minimi multivariabile

## Matrice Jacobiana

È un modo per scrivere il gradiente di una funzione quando è in una certa forma.

Data una funzione $$f: \R^n \to \R^p$$

ossia per esempio $$x=(x_1,...,x_n) \to(f_1(x),...,f_p(x))$$

Se le p funzioni di arrivo sono differenziabili, allora la matrice jacobiana è definita in questo modo:

$$J_f(x) = \begin{pmatrix}
\delta_{x_1} f_1(x) & ... & \delta_{x_n} f_1(x)\\
. & . & . \\
\delta_{x_1} f_p(x) & ... & \delta_{x_n} f_p(x)

\end{pmatrix}$$

Una matrice con p righe e n colonne, che rappresentano **tutte le derivate parziali possibile**

**Osservazione**

Da una funzione differenziabile f(r(x)) in modo simile a quanto fatto prima, abbiamo che

$$J_f(r(t)) J_r(t)$$ è uguale al prodotto scalare!


$$
(\delta_1f(r(t)), ..., \delta_nf(r(t))) \cdot \begin{pmatrix}
\delta_{s} r_1(t) \\
. \\
\delta_{s} r_n(t)
\end{pmatrix}
$$


Ossia è proprio $$\delta_t(f(r(t))$$ il prodotto scalare, ossia $$J_{f \cdot r}(t)$$ e la cosa bella è che **vale per dimensione qualsiasi**. (vedere gli appunti lezione 11, ci dovrebbe essere l'enunciato di questo).

**Composizione di funzioni**

Si può dimostrare che la Jacobiana si comporta bene per le composizione di funzioni ossia:

E questo vale per funzioni definite per qualunque dimensione.


$$
J_{g \cdot f}(v)= J_g(f(v)) J_f(v)
$$


### Studio del massimo e del minimo

In più dimensioni non possiamo più applicare lo studio del segno della derivata come nella prima dimensione, in questo momento abbiamo più derivate, e non abbiamo nemmeno il concetto di funzione crescente. Vogliamo affidarci al concetto delle derivate seconde (concavità e convessità)

Vedere che $$f'(x) = 0 \land f''(x)>0$$ oppure minore. Andremo a generalizzare questa idea.

### Condizione di stazionarietà

Andiamo a definire una condizione di stazionarietà a più dimensione, che ci sarà molto utile per trovare il minimo locale (o massimo locale).(è anche chiamato fermat, come ti ricordi qui [Teoremi Base Analisi](/notes/teoremi-base-analisi))

sia $$f:A \to \R, \bar{x} \in A$$ è minimo locale, f è differenziabile in xbar, allora si ha che $$\nabla f(\bar{x}) = 0$$

Quando il gradiente si annulla, quel punto in cui si annulla si chiama **punto critico o stazionario**.

- La stazionarietà non permette di distinguere massimi e minimi (valeva anche per R dim 1

**Punto di sella**

È la generalizzazione di un punto di flesso (in cui 2 derivata seconda si annullava).

sia f una funzione ben definita differenziabile tale che il suo gradiente sia 0 in un punto a. Allora si dice che il punto a è di sella se esistono due punti per ogni intorno di a, tali per cui f(x0) < f(a) < f(x1).

In pratica mi sta dicendo che comunque io mi avvicini a questo punto, riesco sempre a trovare un punto la cui immagine è minore, e riesco sempre a trovare un punto la cui immagine è maggiore.

Questo è la terza possibilità, nel caso questo punto stazionario non sia né massimo né minimo.

**Necessarietà della differenziabilità**

Affinché valga la condizione di stazionarietà devono sempre esistere almeno le derivate parziali in OGNI direzione.

Questo è utile per le considerazioni dell'inverso, in quanto per f(x) = |x| , nel punto 0 non è differenziabile, ma è un punto di minimo.

- Dimostrazione

    Sia f ben definita e a un punto di minimo locale, vogliamo dimostrare che ogni derivata parziale in questo punto sia 0. (ovvero che il gradiente sia 0).

    Consideriamo $$g(t) = f(a + te_1)$$, ovvero incrementato solamente nella direzione 1.

    Poiché f ha minimo in a, ho che per t=0 ho un minimo locale di g (dato che g è scritta in funzione di f).

    Ho che la derivata di g è la derivata parziale di f (per come è definita), quindi g è differenziabile poiché per ipotesi f è differenziabile. Per fermat, in quanto t=0 è un punto di minimo, ho che la derivata di g in t = 0 è 0, quindi applicando questa idea per ogni direzione ho che l'intero gradiente è 0.


### Derivata seconda

Possiamo derivare parzialmente in più direzioni

**Derivate seconde pure** se derivo rispetto alla stessa variabile anche la seconda volta

**Derivate seconde miste** se derivo rispetto a una variabile differente.

## Matrice Hessiana

Questa matrice contiene tutte le derivate seconde possibili per una certa funzione da Rn a R (sarà di dimensione n x n


$$
Hf(x) = \begin{pmatrix}
\delta_{11} f(x) & ... & \delta_{1n} f(x)\\
. & . & . \\
\delta_{n1} f(x) & ... & \delta_{nn} f(x)

\end{pmatrix}
$$


### Teorema di Schwarz

Sia f una funzione ben definita, con dominio multidimensionale.

Siano tutte le derivate seconde ben definite.

Allora $$\forall ij \in \{1,..,n\}, i \neq j$$ si ha che $$\delta_{ij}f = \delta_{ji}f$$, ossia è un altro modo per dire che la **matrice hessiana è simmetrica**.

- Dimostrazione
    l'idea principale è utilizzare qualcosa di simile alla differenziabilità per continuità e derivabilità parziale.
    Considero
    $$g(h) = f(x + h, y+h) + f(x, y) - f(x + h,y) - f(x, y + h)$$

    poi considero
    $$u(t) = f(x + t, y+h) + f(x, y) - f(x + t,y) - f(x, y + h)$$ e utilizzando lagrange due volte ottengo che
    $$g(h) = \delta_{xy}f(x + ah, y + bh)h^2$$
    - Come usare Lagrange due volte
        Noto che $$u(h) = g(h)$$ e che $$u(0) = 0$$.
        Per lagrange noto che $$u(h) - u(0) = h\cdot u'(\theta_1 h)$$ con theta da 0 a 1.
        Facendo la derivata prima di $$u$$ ottengo che è uguale a
        $$\delta_x f(x + t, y+ h) - \delta_x f(x + t, y)$$ perché il resto è costante in t.
        Utilizzando di nuovo taylor su questo (su y) ottengo che
        $$
        \delta_x f(x + t, y+ h) - \delta_x f(x + t, y) = h \delta_y(\delta_x f(x + t, y + \theta_2 y))
        $$
        mettendo tutto all'inizio, ottengo che
        $$g(h) = u(h) - u(0) = h^2 \delta_y(\delta_x f(x + \theta_1h, y + \theta_2 h))$$


    Lo faccio ancora per il simmetrico  (cioè costruendomi una funzione v(t) che vari a seconda della y e mi trovo che
    $$g(h) = \delta_{yx}f(x + ah, y + bh)h^2$$

    Faccio il limite per h tendente a 0, dividendo per la stessa variabile, e trovo che sono esattamente uguali.
    cioè
    $$\lim_{h \to 0} \dfrac{\delta_{yx}f(x + ah, y + bh)h^2}{h^2} = \lim_{h \to 0} \delta_{yx}f(x + ah, y + bh)=  \delta_{yx}f(x,y)$$  l'ultimo uguale è giustificabile per la continuità della funzione f (basta aprire e controllare 🙂).


### Forma Hessiana

Conoscendo le forme quadratiche, possiamo andare a definire una forma Hessiana di una funzione di classe $$C^{2}$$.

La forma hessiana di una funzione di class $$C^2$$ è la funzione così definita:

$$h\to \langle Hf(x) h, h\rangle$$

## Taylor di ordine 2

### Resto secondo Peano
Questa è una analisi **multivariabile** vedere sotto per il caso univariabile col resto espresso in altro modo.

Possiamo andare a definire una funzione di taylor per funzioni do ordine superiore, lo facciamo utilizzando la matrice hessiana (per definire la derivata seconda 😀)  Possiamo andare in teoria anche a definire formule di taylor di ordine superiore al 2 ma per questo corso finiamo qui. (probabilmente ci saranno matrici più complicate, e di dimensioni maggiori).

Vogliamo dimostrare che $$\forall v \in \R^n$$


$$
f(w + tv) = f(w) + \langle\nabla f(w), tv\rangle + \dfrac{1}{2}\langle H(f(w)) tv, tv\rangle + o(|t^2|), \\t \to 0_v, v\in Dominio
$$


- Osservazione paraboloide

    Scriviamolo in maltro modo:

    $$f(w) = f(v) + \langle\nabla f(v), w - v\rangle + \dfrac{1}{2}\langle H(f(v)) w - v, w - v\rangle + o(|(w - v)^2|), w \to v$$

    Questa è una funzione al secondo ordine in w, è un **paraboloide** in cui possiamo andare a cercare la miglior funzione in questa classe di funzioni quadratiche.

- Dimostrazione
    definiamo $$g(t) = f(w + tv)$$, la derivata è uguale a
    $$g'(t) = \delta_t f(r(t))$$ con $$r(t) = w + tv$$ che per il teorema della derivata di funzioni composte è
    $$\langle \nabla f(w + tv), v \rangle$$
    Calcoliamo la derivata seconda di questo, ovvero si va ad ottenere: (praticamente sto applicando la 10.4.4 estensivamente.

    $$
    \sum \delta_t (\delta_k f) (r(t))v_k = \sum  \langle(\nabla\delta_k f) (r(t)), r'(t)\rangle v_k \\
    = \sum \langle(\nabla\delta_k f) (r(t)), v\rangle v_k = \sum\sum \delta_j \delta_k f(r(t) v_jv_k = \\ \langle Hf(r(t))v,v\rangle
    $$

    In quanto $$g: \R \to \R$$ possiamo utilizzare taylor classico per affermare che

    $$g(t) = g(0) + g'(0) t + \dfrac{1}{2}g''(0)t^2 + o(t^2)$$, che per dimostrazione precedente, sostituendo pezzo per pezzo, si ottiene che

    $$f(w + vt) = f(w) + \langle \nabla f(w), v \rangle t + \dfrac{1}{2}\langle Hf(w)v,v\rangle t^2 + o(t^2)$$ il che finisce la dimostrazione


### **Resto secondo Lagrange (univar)**

Questo è equivalente al precedente, col resto secondo Peano.

Sia $$f:\R \to \R$$ f derivabile due volte, allora

$$\forall  x, \bar{x} \in \R , \exists c \in [x, \bar{x}]$$ tale per cui


$$
f(x) = f(\bar{x}) + f'(\bar{x})(x - \bar{x}) + f''(c) \dfrac{(x - \bar{x}) ^2}{2}
$$


- Note sulla dimostrazione
    Noto che l'unica cosa che cambia è la parte finale della somma, quindi vorrei in qualche modo dimostrare che queste due cose siano uguali.

    Io aggiungo e tolgo questo valore : (imprecisato) e riesco a dire la funzione ottenuta è un opiccolo per la continuità della derivata seconda. questo nella direzione lagrange $$\implies$$peano

    Non so esattamente cosa stia facendo in questo momento il prof. Quindi la ometto, dico solo che stranamente sta cercando dimostrare che esiste un valore $$k \in R$$ tale che

    $$f(x) = f(\bar{x}) + f'(\bar{x})(x - \bar{x}) + k{(x - \bar{x}) ^2}$$ e lo dimostra utilizzando Rolle presente in [Teoremi Base Analisi](/notes/teoremi-base-analisi) costruendosi una funzione che prenda la roba di sopra.

    Ossia mi creo $$g(\bar{x}) = f(x) - f(\bar{x}) -f'(\bar{x})(x - \bar{x}) - k{(x - \bar{x}) ^2}$$
    In secondo momento calcolandosi il valore della derivata della funzione così creata si ottengono altri valori.

- Nel caso in cui derivata seconda è continua
    Allora posso dimostrare quanto sopra, semplicemente utilizzando la continuità della derivata seconda, perché cambiano di poco le due cose.

### **Resto secondo Lagrange in Rn (multivar)**

Sia $$A \subseteq \R^n$$ aperto e  $$f$$ di classe $$C^2(A)$$ ovvero con le derivate seconde continue.

Sia $$a, a+h \in A$$ e il segmento $$[a, a+h] \subseteq A$$ allora esiste $$\theta \in (0,1)$$ tale che


$$
f(a + h) = f(a) + \langle\nabla f(a), h\rangle + \dfrac{1}{2}\langle H(f(a + \theta h)) h, h\rangle
$$


- Dimostrazione

    considero la parametrizzazione data dalla funzione

    $$g(t) = f(a + th)$$, notiamo che $$g(0) = f(a)$$ e $$g(1) = f(a + h)$$ che sono le cose da cui eravamo partiti. se prendiamo $$r(t) = a + th$$ si ha che $$g(t) = f(r(t))$$ e allora possiamo utilizzare la derivata di funzioni composte e riscriverla.

    Poi si procede in modo equivalente alla dimostrazione del teorema di lagrange con resto di peano (però si parte con lagrange con resto lagrange in R).


### Polinomio di Taylor
È un taylor senza opiccolo, però di devi andare a cercare l'appunto giusto.

## Forme quadratiche

Queste cose sembrano essere un buon utilizzo della matrice hessiana.
Comunque vediamo cosa sono:
prendiamo una matrice $$A \in \R^{n \times n}$$ tale che sia simmetrica, consideriamo una funzione
$$q_A : \R ^n \to \R$$ definita in questo modo :
$$q_A(h) =  \langle Ah, h\rangle = h^TAh$$. Scopriremo che c'è una equivalenza (forse isomorfismo) fra un polinomio di grado n e una matrice n per n.
Si può dimostrare che è uguale a una forma quadrata questa matrice, questo perché
$$\sum^n_{k,j=1} a_{kj}h_jh_k = \sum^n_{k=1}a_k h^2_k + 2 \sum_{ 1\leq j < k \leq n} a_{jk} h_j h_k$$ ed è qualcosa di molto comodo perché questo non è altro che  (ricordando che $$a_k$$  è un modo semplice per scrivere $$a_{kk}$$


$$
\langle Ah, h\rangle = (a_1h_1 + ...+ a_nh_n)^2
$$


Ma questo vale nel caso solo in cui $$a_ia_k = a_{ik}$$, da ricordare!. Comunque c'è questa buonissima corrispondenza e ci piace molto.

<img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled">

### Segno della forma quadratica

<img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 1.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 1">

**Positivo**
Se per ogni h diverso da zero la forma quadratica è sempre positiva
esempio se ho solo numeri sulla diagonale, probabilmente è di segno positivo

**Negativo**
Se per ogni h diverso da zero la forma quadratica è sempre negativa

**Indefinita**
Se esistono due h diversi fra loro per cui la forma della prima è minore di 0, la forma della seconda è maggiore di zero.

**Altro**
Ci sono anche altre caratterizzazione della forma quadratica.
ad esempio q(h1, h2) = h2^2 non è né indefinita, né positiva questa è **semidefinita**

### Classificazione del segno n-dimensionale

Vogliamo una forma quadratica in Rn, con n≥3 ora.(fino ad ora abbiamo solamente considerato il caso in cui forma quadratica è 2).

<img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 2.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 2">

**Determinanti**

Mi sono costruito molte sottomatrici.

<img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 3.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 3">

- Lavagna prof

    <img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 4.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 4">


**Autovalori**

<img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 5.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 5">

### Teorema criterio classificazione 2x2

Consideriamo la matrice

$$
\begin{pmatrix}
a & b \\
b & c \\
\end{pmatrix}
$$

Allora possiamo individuare i seguenti casi:

**Positivo**
Una forma quadratica è positiva sse $$a > 0 \land ac - b^2 > 0$$

**Negativa**
Una forma quadrata è negativa sse  $$a < 0 \land ac - b^2 > 0$$

**Indefinita**
sse il determinante è negativo., se il determinante è 0 si dice che è una **matrice singolare**.

- Dimostrazione primo caso
    vogliamo dimostrare un sse, andiamo per le due frecce.
    $$\implies$$
    Se pongo h = (1, 0) ottengo $$a > 0$$ quindi deve essere così altrimenti assurdo.

    se pongo h = (h,1)  (nota questi due h sono diversi) ottengo $$ah ^2 + 2bh + c$$ che è sempre positivo quando il determinante è negativo, quindi verificato

    $$\impliedby$$
    Se $$h_2 = 0$$ ottengo $$ah^2_1 > 0$$ vero perché a > 0 e ho un quadrato in R

    Se $$h_2 \neq 0$$, allora raccogliendo un h2 e ponendo $$e = \dfrac{h1}{h2}$$, ottengo

    $$q(h) = ae^2 + 2be + c > 0$$ (già diviso per h2 alla seconda), prendendo il determinante ho che è $$b^2 - ac$$ , che è sempre minore di 0, quindi sempre vera.


**Semidefinito**

Quando ho il determinante che è 0

### Caratteristica positività negatività della Forma Quadratica

Possiamo trovare una caratteristica fondante per le matrici positive e negative (sono uguali ma inverse, enunciamole).

Sia $$A = A ^t \in \mathbb{R} ^{n \times n}$$  allora se $$A$$ è positivo si ha che  $$\exists m > 0$$

$$\langle Ah, h\rangle \geq m \lvert h \rvert^2$$

- Hint di dimostrazione (osservazione)
    Questo è vero perché se consideriamo un $$h \neq 0$$, possiamo riscrivere l'equazione in tesi come
    $$\langle A \dfrac{h}{\lvert h \rvert}, \dfrac{h}{\lvert h \rvert}\rangle \geq m$$, che è equivalente a dire che comunque prendo un vettore unitario, si ha che la forma quadratica è maggiore di un numero m.

- Dimostrazione
    Allora scrivo h con coordinate polari, apro A in dimensione 2 e raccolgo questo $$r ^2$$.
    Allora ho in tesi qualcosa di questo tipo
    $$r ^2 f(\theta) \geq r^2 m$$ e devo dire che esiste questo m.
    utilizziamo 2 cose per terminare.
    1. $$r^2 f(\theta) > 0$$ in quanto la forma quadratica è positiva
    2. f è una funzione continua, e limitata in $$[0, 2\pi] \in \R$$, quindi possiamo usare weierstrass per concludere che esiste un minimo. è proprio questo il minimo!

    Concludo dicendo che $$r^2 f(\theta) \geq r^2 m$$ per ogni theta, in particolare il minimo è maggiore di 0 in quanto per ipotesi la hessiana è positiva, quindi ho finito qui

- Dimostrazione con autovalori

    <img src="/images/notes/image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 6.png" alt="image/universita/ex-notion/Massimi minimi multi-variabile/Untitled 6">


### Condizione sufficiente per minimo e massimo e sella

Questa cosa ci piace per calcolare i punti di massimi e minimi!

**Massimo**
Se il gradiente è 0 e la hessiana è positiva, ho un punto di massimo

**Minimo**
Grandiente 0 e hessiana negativa, ho un punto di minimo.

**Indefinita**
Se gradiente è 0 e la hessiana è indefinita è un punto di sella

- Dimostrazione (minimo)

    Consideriamo una funzione $$f :A \subseteq \R^n \to \R$$  di classe $$C^2$$ consideriamo un punto $$a \in A$$ tale che $$\nabla f(a) = 0$$ e so che $$Hf(a) >0$$.
    Voglio dimostrare che sia un minimo locale, ovvero che $$\exists \delta >0$$  tale che
    $$f(a + h) \geq f(a)$$ per ogni $$h \in B(0, \delta)$$, ossia $$|h| < \delta$$
    Espando con taylor, e utilizzo l'ipotesi di punto critico e ottengo che
    $$f(a + h) - f(a) = \dfrac{1}{2} \langle Hf(a),h,h \rangle + o(|h^2|)$$ voglio dimostrare che per un delta opportuno RHS sia maggiore di 0, se ho questa cosa ho finito, in qualche modo voglio utilizzare la positività della matrice hessiana.

    Per il teorema caratterizzante della matrice della forma quadratica, so che
    $$\exists m >0 \in \R :\langle Hf(a),h,h \rangle \geq m \lvert h^{2} \rvert, \forall h \in \R^n$$
    Allora continuando il ragionamento
    Ottengo che $$\dfrac{1}{2} m \lvert h^{2} \rvert+ o(\lvert h^{2} \rvert) = \lvert h^{2} \rvert(\dfrac{m}{2} + \dfrac{o(\lvert h^{2} \rvert)}{\lvert h^{2} \rvert})$$
    Ragioniamo ora sull'o-piccolo.
    Allora per definizione di o piccolo, so che posso prendere questa cosa piccola quanto mi pare.
    In particolare scelgo un intorno in cui questo o piccolo sia compreso fra $$m/4$$, allora l'intorno delta è definito da questo momento.
    Scelto questo intervallo allora finire la dimostrazione è veloce, ottengo che
    $$
    f(a + h) - f(a) \geq |h^2|(m/2 - m/4) \geq 0
    $$
    (abbiamo anche dimostrato che dipende da h) però è finito, questa cosa vale per ogni h nell'intorno scelto sopra.


**Semidefinita**

Nel caso in cui il determinante della hessiana è 0, non posso utilizzare i metodi precedenti, quindi in questo caso devo dividere il processo analizzando le derivate parziali.

### Condizione necessaria per minimo e massimo

È molto simile alla condizione sufficiente, solo è abbiamo ora che la hessiana può anche essere semidefinita positiva.