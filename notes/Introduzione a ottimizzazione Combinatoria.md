---
layout: page
permalink: notes/introduzione-a-ottimizzazione-combinatoria
tags: en
title: Introduzione a ottimizzazione Combinatoria
---

Ripasso Prox: 23
Ripasso: December 28, 2022
Ultima modifica: December 27, 2022 5:09 PM
Primo Abbozzo: September 23, 2022 9:32 AM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Elementi di ripasso

Misa di dicembre, po’ tolgo perché è poco importante il modulo di introduzione

# Introduzione (prolly non chiede niente di questo)

L’ottimizzazione combinatoria è un altro nome per la ricerca operativa. È uno **strumento** utile a prendere le decisioni migliori, fatto sta che è anche molto utile al machine learning e si potrebbe dire che ne sia una base, questa è una cosa molto buona.

## Ricerca operativa

Questo è un campo a **forte impatto economico** perché prova a minimizzare i costi e massimizzare i profitti.

### Steps 🟩, 🟨

1. Individuazione del problema (almeno riconoscere che ci sia un problema)
2. Raccoglimento dei dati
3. Modellizzazione del problema
4. Ricerca di una soluzione
5. Analisi dei risultati della soluzione

La ricerca operativa si interessa principalmente degli step 3 e 4, nonostante gli steps non sempre vengono eseguiti in maniera lineare, ma c’è un ciclo di feedback a riguardo.

### Modelli (3) 🟩

> Un **modello** è una *descrizione astratta*, e scritta nel
*linguaggio della matematica*, della parte di realtà utile al
processo decisionale
>

**Giochi**

Ci sono una serie di agenti in un ambiente con alcune regole precise, i risultati sono visti come causati dall'interazione fra gli agenti. (Abbastanza recente, presente nel secolo scorso)

*Equilibrio Strategia* sono due concetti molto interessanti per questo tipo di modellizzazione.

**Simulazioni**

Si cerca di capire cosa succede facendo una simulazione, è certo che la possibilità di generare numeri casuali è fondamentale in questo passo. Eg metodi monte-carlo

**Analitici**

Questi sono i modelli interessanti alla ricerca operativa perché tratta in modo matematico il modello, cercando il minimo o massimo di una funzione (si vede qui che ci sarebbe biosgno dianalisi, fa strano che non lo abbia messo nei prerequisiti).

Sono **fedeli** al problema, e devono essere **astratti**.

## Un problema

> Un problema non è nient’altro che una *domanda*,
espressa in termini generali, ma la cui risposta dipende da
un certo numero di *parametri e variabili*.
>

Quindi possiamo affermare che un problema di ricerca operativa venga descritta tramite:

1. Parametri e variabili che sono in gioco
2. Quanto la soluzione deve soddisfare per essere valida

Sembra un pò come se fosse un problema di CSP

### **Parametri e variabili** 🟩

È importantissimo fare una distinzione fra parametri e variabili.

- Variabile è un valore ignoto che vorremmo trovare, spesso in funzione di parametri.
- Parametri sono valori, che possono essere conosciuti o meno, che supponiamo essere conosciute.

eg. $$ax^2 + bx + c=d$$ i parametri sono  $$a,b,c,d$$ e la variabile è solo $$x$$, perché noi vorremmo trovare x in funzione dei parametri.

### Istanza di un problema 🟩

Con la definizione di parametri è variabili si fa una distinzione fra una istanza di un problema, oppure il problema in senso generale. Quando i parametri non sono più simbolici, allora è una istanza, perché effettivamente ora possiamo andare a calcolare la soluzione.

Quindi una sostituzione di tutti i parametri simbolici, con valori reali (probabilmetne ottenuti da osservazione, da dati) si ha una istanza di una soluzione.

### Ammissibilità delle soluzioni 🟩

Vogliamo cercare ora di definire da un punto di vista matematico cosa sia l'insieme delle soluzioni ammissibili.

Ossia, vorremmo trovare gli $$x$$, le variabili prese in un campo grande, come può essere $$\R$$. Quindi un primo step è trovare l’insieme delle soluzioni in funzione dei parametri.

Le variabili che soddisfano tutti i costraints sono $$x \in \mathbb{F}_p \subseteq \mathbb{G}$$., con G un insieme in cui vivono le variabili.

Le variabili $$x \in \mathbb{G} - \mathbb{F}$$ sono non ammissibili.

### Funzione obiettivo !! 🟩

È una misura di una *bontà* della soluzione. spesso definita come $$c_p : \mathbb{F}_p \to \R$$, ossia dalle soluzioni ammissibili ai Reali. Vorremmo cercare di minimizzare o massimizzare la soluzione a questo problema con questa *funzione di valutazione* o obiettivo. Si può vedere molto facilmente che il problema di massimo è equivalente al problema di minimo invertendo.

**Soluzione ottima** è il valore di $$x \in \mathbb{F}_p : x = min \{c_p(y) : y \in \mathbb{y}_p \}$$, definiremo questa x come $$Z_p = x$$

**Valore ottimo è $$c_p(x) \in \mathbb{F}_p$$**  con $$x$$  il valore di sopra.

## Catalogazione dei problemi

### Ottimizzazione, decisione e certificato 🟩

**Problema di ottimizzazione**

Vogliamo trovare il minimo in qualcosa. Ma questo di solito è un problema molto difficile perché bisogna prima trovare le soluzioni possibili, e poi bisogna anche trovare la migliore fra queste soluzioni possibili

**Problema di decisione**

Si tratta di cercare una soluzione $$g: g \in \mathbb{F}_p$$

**Problema di certificato**

Vogliamo cercare di *verificare* se una soluzione è nell'insieme che ci piaccia.

si tratta di verificare  che se data $$g$$ si ha che $$g \in \mathbb{F}_p$$

### C**onversione da certificazione e ottimizzazione** 🟨

Possiamo dire che un problema di certificazione dare dei valori fissati, quelli che ci piacciono sono di valore basso, in questo modo converto subito il valori che ci piacciono in questo caso come soluzioni del problema di ottimizzazione:

$$c_p(x) = 0 : x \in F_p$$, $$c_p(x) = 1: x \not\in F_p$$

Possiamo anche convertire un problema di ottimizzazione in un problema decisionale, se conosciamo il costo ottimo è semplice formalizzarlo, altrimenti si fa $$\leq k$$ un valore fisso scelto

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a ottimizzazione Combinatoria/Untitled.png" alt="image/universita/ex-notion/Introduzione a ottimizzazione Combinatoria/Untitled">


---

### Tipi di soluzione ai problemi 🟩-

**Vuoto**

Non c'è nessuna soluzione, faremo finta che il costo per implementare la soluzione a questo problema sia infinito

$$Z_p = \infty$$

**Illimitato (inferiormente o superiormente)**

Ossia ho troppe soluzioni ammissibili,e possono prendere sempre una soluzione che abbia un costo minore:

In questo caso posso dire che $$Z_p = -\infty$$ nel caso di un problema di minimizzazione.

Di solito sono problemi artificiosi, nel mondo reale non succede quasi mai, anch emeno volte del vuoto.

**Ottimo Finito, soluzione ottima non finita**

Nel caso in cui esiste un costo finito, ma non esiste nel nostro insieme di partenza una soluzione che abbia questo costo

esempio:

$$\inf \{ x \in \R : x > 0\}$$, il minimo è in 0, ma nessuno ci arriva.

Ad esempio utilizzare delle relazioni lasche evita questo problema.

**Ottimo finito e soluzione finita**

Caso che ci piace

### Algoritmi esatti e euristici 🟩-, 🟨

Ossia descriviamo **l’algoritmo esatto** e sappiamo che in output sarà la soluzione perfetta, solo che la maggior parte dei casi è troppo lento.

**L’algoritmo euristico** deve restituire un valore che sia simile al valore ottimo, quindi spesso è molto più efficiente. Possiamo in questo caso definire un concetto di approssimazione inferiore e superiore

La qualità dell’algoritmo euristico si può misurare col concetto di errore, quindi sia $$R_p(g)$$ l’errore relativo rispetto al valore ottimo per questo problema, allora si può dire che l’algoritmo è  $$\varepsilon$$-**approssimato** quando produce soluzioni $$g :$$ $$R_p(g) \leq \varepsilon$$

### Rilassamenti 🟩, 🟨

Vogliamo cercare di applicare le soluzioni del problema per permettere l’esistenza di algoritmi di complessità inferiori ( e per i problemi di minimo provare ad approssimare al ribasso, in modo tale che la soluzione ottima reale non è meno della soluzione trovata

- Slide

    <img src="/images/notes/image/universita/ex-notion/Introduzione a ottimizzazione Combinatoria/Untitled 1.png" alt="image/universita/ex-notion/Introduzione a ottimizzazione Combinatoria/Untitled 1">


La nota principale è quando la soluzione del problema rilassato è esattamente uguale al problema iniziale, in questo caso posso concludere di aver già trovato la soluzione ottimale per il problema iniziale.



# References