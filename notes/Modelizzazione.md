---
layout: page
permalink: notes/modelizzazione
tags: en
title: Modelizzazione
---

Ripasso Prox: 24
Ripasso: December 29, 2022
Ultima modifica: December 27, 2022 4:53 PM
Primo Abbozzo: September 30, 2022 9:34 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

- Stranamente ho ancora alcuni problemi a ricordarmi i modelli teorici per la modellizzazione di problemi, ma durante la modellizzazione di un problema concreto mi pare facile, semmai qualche esercizio a tempo settimanale può aiutare per questo.

Bisogna fare**esercizi pesanti** su sta roba, non la sai per niente bene dal lato pratico, che è quello che importa per l’esame…

# Programmazione lineare

Programmazione lineare contiene alcuni algoritmi utili per risolvere certi problemi di ottimizzazione.

## Introduzione

Andiamo in questa sezione a definire un problema di programmazione lineare

### Definizione 🟩-

- *Variabili reali* che saranno le variabili del nostro problema, sono in numero finito (eg. tutti in Rn)
- *Funzione obiettivo* che ci definisce il costo $$f: \R^n \to \R$$
- *Vincoli lineari* che limitano il dominio delle variabili reali e li mettono in relazione fra di loro

Se le variabili appartengono agli interi andiamo a parlare di **programmazione lineare intera**.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled.png" alt="image/universita/ex-notion/Modelizzazione/Untitled">


Rappresentazione della soluzione si può formalizzare sempre in questo modo:


$$
max\{cx | Ax ≤ b\} : A \in M_{m\times n}, c,b \in M_{n \times 1}
$$


## Programmazione lineare intera

In modo curioso la programmazione lineare è più facile rispetto alla PLI.

- Esempio di modelizzazione

    Ha fatto un esempio di modelizzazione di un problema introduttivo in classe, in effetti si deve fare attenzione a moltissime cose… (soprattutto costraints impliciti).


**Quantitative** rappresentano alcune quantità

**Logiche** rappresentano valori binari (di solito utilizzati per modellare l’*assegnamento*  ad un task)

### Relazioni logiche 🟨+

Possiamo codificare con relazioni fra variabili logiche il concetto di negazione, implicazione congiuzione e disgiunzione.

Le variabili $$x \in \{0, 1\}$$ in questo caso. La cosa interessante è che possiamo codificare relazioni logiche con relazioni lineari!

- Slide rappresentazione di relazioni logiche con relazioni lineari

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 1.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 1">


### Vincoli di (semi-)assegnamento 🟩

Abbiamo un insieme di $$N = \{1,..., n\}$$ oggetti da assegnare in $$V = \{1,...,m\}$$ luoghi.

Questo si può codificare con una matrice $$n \times m$$ e usare una variabile logica per specificare se è stato assegnato a quel luogo o meno.

(Secondo me si potrebbe anche utilizzare un numero per questo, ma magari l’algoritmo utilizzato è leggermente diverso, no forse specifica una possibilità di assegnamento, per questo una matrice è una cosa giusta).

**Vincoli di semiassegnamento**

> Ossia ogni oggetto è assegnato a un singolo luogo
>
- Slide semiassegnamento

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 2.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 2">


**Vincoli di assegnamento**

> Ogni oggetto ha un singolo luogo e ogni luogo un oggetto
>
- Slide assegnamento

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 3.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 3">


### Selezione sottoinsiemi 🟨+

Vogliamo selezionare il minimo fra certi sottoinsiemi (non per forza partizioni!)

Formulazione classica: sia $$F = \{F_1,..., F_m\}, F_i \in \N$$, voglia determinare $$D \subseteq F$$ tale che abbia il costo minimo fra tutti. Nella selezione di questi sottoinsiemi possiamo considerare insiemi di copertura, di riempimento o di partizione.

Esempio del costo classico $$\min\sum x_j c_j$$ cioè aggiungo il costo con la variabile booleana che decide se lo scelgo o meno, e poi chiamo $$a_{ij}$$ una matrice che dice se l'elemento i è in $$F_j$$

- Formalizzazione classica

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 4.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 4">

- Copertura, riempimento partizione

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 5.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 5">


### Variabili a Valori Discreti 🟩-

Questa parte tratta di valori vincolati a valori reali. (un esempio solito è una macchina che è stata costruita a lavorare entro voltaggi precisi).

Si indica per **un insieme di valori che una variabile può assumere**. Una rappresentazione classica è in silde sotto

- Slide

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 6.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 6">


### Minima Quantità Positiva Prefissata 🟨+

Di solito queste tipologie di variabili rappresentano valori di produzione di una macchina perché o è spenta, rappresentata da uno 0, oppure è accesa e presente in un intervallo

- Slide

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 7.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 7">


### Funzione a carico fisso 🟩

Indica costi 0 quando la macchina non è in produzione, mentre però è attiva, anche se fa poco, c'è un **carico fisso** ossia un costo che c'è sempre, e poi cresce in modo lineare

- Slide introduttive

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 8.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 8">

- Formalizzazione classica

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 9.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 9">


### Rappresentazione del valore assoluto 🟨

SI tratta di come rappresentare mediante vincoli la relazione di valore assoluto.

Un problema con questo metodo è che non sempre si riescono a gestire

Anche gestendolo in questo modo ci sono alcune ambiguità

- Slide, formalizzazione classica e funzione costo

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 10.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 10">


### Funzioni lineari a tratti 🟨+

L'idea è utilizzare una variabile logica che ci dice in quale tratto è presente, poi utilizzare la funzione per calcolare il valore corretto.

In pratica questa è una forma di generalizzazione dei problemi con funzioni a carico fisso, in cui vengono introdotte delle variabili per dire dove sei, e poi utilizzare la funzione di costo del carico fisso.

Questo metodo è buono perché posso utilizzarlo per quanti tratti mi pare

- Formalizzazione

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 11.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 11">

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 12.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 13.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 13">


## Modellizzazione per Problemi noti

### Problema della fonderia

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 14.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 14">

- Soluzione fonderia

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 15.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 15">


### Problema pianificazione della produzione

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 16.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 16">

- Soluzione pianificazione produzione

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 17.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 17">


### Problema dello zaino (!)

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 18.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 18">

- Soluzione del modello

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 19.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 19">


### Albero di copertura di costo minimo

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 20.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 20">

- Soluzione

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 21.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 21">


### Problema del commesso viaggiatore

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 22.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 22">

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 23.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 23">

- Note sulla path hamiltoniana

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 24.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 24">

- Soluzione modellizzazione

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 25.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 25">


### Problema dell’agenzia matrimoniale (!)

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 26.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 26">

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 27.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 27">

- Soluzione modellizzazione

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 28.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 28">


### Problema allocazione dei lavori alle macchine (!)

**Descrizione del problema**

- Dal libro

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 29.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 29">

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 30.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 30">


Abbiamo dei lavori che devono essere svolti in questi intervalli : $$t_i, t_i + d_i$$, che sono certi valori che svolgono qualcosa, vogliamo cercare di massimizzare il numero di cose svolte, avendo un certo numero di macchine. Una macchina può avere solo un lavoro (o dipendente).

Questo è un problema di **semiassegnamento**.

**Modellizzazione**

poniamo $$x_{ij} = 1$$ se il lavoro $$i$$ è svolto dalla macchina $$j$$, altrimenti 0

vincoli necessari *semi-assegnamento* $$\forall i, \sum_{j = 1} ^mx_{ij} = 1$$, ora dobbiamo andare a modellizzare il concetto dell’intervallo.

Quindi mi definisco un insieme $$S(i)$$ che contiene tutti i lavori *incompatibili* a $$i$$.

Allora il vincolo diventa $$x_{ij} + x_{hj} \leq 1$$ con $$h \in S(i)$$, Cioè vogliamo che una macchina esegua solamente un lavoro, o nessun lavoro. E questo vincolo ci dà il concetto di vincolo.

Ora passo alla discussione della funzione obiettivo, quindi introduco una nuova variabile che mi conta le macchine utilizzate

$$f(obiettivo) = \sum y_j$$, per tutte le macchine, e poi questa $$y_j$$ è maggiore di tutti gli $$x_{ij}$$ per una macchina j fissata.. Così provo ad utilizzare meno macchine possibili

- Soluzione dal libro

    https://www.notion.so


### Problema docente di informatica (!)

Questo problema è rappresentato nel libro come di minimizzazione del tempo per lavori di macchina a pagina 37 del pdf delle dispense

**Descrizione del problema**

Ho $$t_1...t_n$$ progetti da compilare su $$m$$ pc, voglio che ci mettano meno tempo possibile.

**Modellizzazione**

Sia la variabile $$x_{ij}$$ la variabile logica se il progetto $$t_i$$ è data alla macchina $$j$$

*Semi-assegnamento* al massimo assegno il progetto a una singola macchina

$$\sum_{j = 1} x_{ij} = 1$$. Ora entra la parte difficile, introdurre delle variabili che siano utili  per avere questo concetto di tempo.

Sia $$y_j = \sum_i t_i x_{ij}$$, questo rappresenta il tempo di utilizzo del singolo PC. Quello che noi dobbiamo minimizzare è

Ma questo vincolo non è lineare, quindi è un problema $$\min (\max Y), Y = \{y_j : j = 1,...,m\}$$

Quindi introduco un valore che $$z : \forall j \sum_i x_{ij} t_i \leq z$$ e provo a minimizzare solamente z, quindi sarà il suo valore più basso. (minimo upper bound)

### Problema assegnamento delle frequenze

<img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 31.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 31">

- Soluzione problema assegnamento

    <img src="/images/notes/image/universita/ex-notion/Modelizzazione/Untitled 32.png" alt="image/universita/ex-notion/Modelizzazione/Untitled 32">


### Problema della commesse 🟥-

Ho n dipendenti, devo evadere m pacchi, un sottoinsieme $$D_j$$ che indica da chi può essere eseguito questo pacco j, può essere da luogo a un ricavo di $$r_j$$. Un dipendente può lavorare su un solo pacco per un intervallo di tempo. Può essere che non tutti i pacchi siano da evadere.

**Inizio modello**

$$F_j = boh$$

$$x_j = 1$$  se la commessa j è selezionata, altrimenti 0

$$a_{ij}$$ boh

$$x_i \in \Z, 0 \leq x_i\leq1$$

$$\forall i \sum a_{ij} x_j \leq 1$$

**Funzione obiettivo $$\max \sum _{j = 1} ^m x_j r_j$$**



# References