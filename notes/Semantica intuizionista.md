---
layout: page
permalink: notes/semantica-intuizionista
tags: italian
title: Semantica intuizionista
---

Ripasso Prox: 6
Ripasso: December 23, 2021
Ultima modifica: September 30, 2022 3:20 PM
Primo Abbozzo: November 26, 2021 9:35 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Vecchi dubbi
    - quali sono stati gli scopi della logica intuizionista?
- Gli effetti della compattezza

# 9 Semantica intuizionista

- Tutte le slides

    [slides10_202021.pdf](Semantica%20intuizionista%20552d686d80ac40d88992390fd72066ed/slides10_202021.pdf)


Molto importante questo documento per avere chiara la differenza fra la logica intuizionista e la [Logica Proposizionale](/notes/logica-proposizionale) classica.

Questa logica intuizionista non si preoccupa del noumeno platonico, ma solo di una prova reale.

**Introduzione:**

- wikipedia

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled">


### 9 11 Scopi di intuizionista (3)

1. Semantica dell'evidenza → costruzione della prova
2. Semantica della conoscenza diretta = conoscenza diretta
3. Semantica della calcolabilità = programma, algoritmo della soluzione

## 9.1 Invenzione o scoperta

La semantica intuizionista vede la matematica come una creazione (e questa cosa interessa molto all'informatico perché è una prova., mentre la semantica classica vede la matematica come una scoperta

- Caratteristica principale della logica intuizionista

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 1.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 1">

    Esempio il paradosso di Banach-tarksi non è calcolabile (nessuno ha duplicato una sfera doro diciamo :) )

    Seziono la sfera in 3 parti e faccio movimenti rigidi (non deformo, posso rotare, trasportare) e dimostro che da questi movimenti rigidi ottengo due sfere con lo stesso volume e con gli stessi punti.


### 9.1.1 Evidenza indiretta e diretta

Nelle due logiche il significato di esistenza è differente.

1. Classica: l'esistenza, ma non so esattamente che numero sia
2. Intuizionista: l'elemento che soddisfa, riesco proprio a trovare l'elemento tale che mi soddisfi le mie proprietà.

**NOTA:** il fatto che esista una prova intuizionista mi permette di avere un algoritmo per tirare fuori un elemento che me lo soddisfi, mentre dalla prova classica no.

### 9.1.2 Effetti dimostrazione per assurdo

Questo metodo di dimostrazione non è stato ben accettato nell'epoca in cui è stato creato perché non permetteva il buon calcolo:

1. No calcolo
2. Molto utile per dimostrare teoremi che non si potevano dimostrare in modo intuizionistico
3. Molto veloce perché rende le dimensioni delle prove minori (ma perché fa meno lavoro!)

## 9.2 Enunciati e semantiche della logica intuizionista

1. **Algoritmo** l'evidenza diretta è necessaria per la determinazione del valore di verità
2. Il valore di verità è potenzialmente determinabile (ossia può diventare fissata dopo un pò di tempo), ci deve essere una algoritmo o che non esista.
- Enunciato ed esempi

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 2.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 2">

    Analizzando la prima proposizione, per la logica classica dovrei avere un valore di verità fissato, invece sono in un mondo indeterminato.

    Per i numeri, l'algoritmo non riuscirebbe mai a finire a comparare due numeri periodici e non riuscirebbe a dare un risultato in tempo finito.

    Mentre l'ultimo esempio è stato dimostrato in [Logica meta-linguistica](/notes/logica-meta-linguistica)


Da questi si posso ricavare due semantiche:

### 9.2.1 Semantica di Kripke

La caratteristica principale di questa semantica è che le proposizioni possono avere un range da [0,1].

E che queste denotazioni possono evolvere da 0 a 1 col tempo. Bisogna quindi avere una funzione semantica che possa trattenere il tempo.

**0 è ignoto 1 è vero** e questi valori evolvono.

Questi valori sono dei valori di conoscenza ma non verità, e non algoritmico!

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 3.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 3">


### 9.2.2 Altro

Si tratterà anche della semantica di Brouwer-Heyting-Kolmogorov subito dopo

## 9.3 Semantica di Brouwer-Heyting-Kolmogorov

### 9.3.1 Introduzione

> Data una formula F, la sua denotazione è l'insieme delle prove esplicite (algoritmi) che risolvono quella formula.
>

Questa semantica è molto utile per l'informatico perché le formule sono descrizioni di problemi e l'altro soluzione.

osservazioni:

Questa semantica è molto utile per comporre delle soluzioni (grazie ai connettivi). L'insieme vuoto è l'inesistenza di soluzioni algoritmiche (che potrebbe essere non più vuoto in futuro).

Qui ha senso introdurre il concetto di **dedicibilità** ovvero la possibilità di costruire un algoritmo che me lo risolva.

### 9.3.2 Enunciato e definizione semantica

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 4.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 4">

- Definizione semantica

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 5.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 5">


### 9.3.3 Nota sul VOID:

con void in c starei restituendo la stellina (valore vero), ovvero sto restituendo sempre una sequenza giusta (eliminazione del top è inutile quindi non ci faccio caso).

### 9.3.4 EM e RAA in semantica intuizionista

Queste dimostrazioni valide in logica classica non hanno più senso in questo caso

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 6.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 6">


### 9.3.5 Correttezza e completezza

Potrebbe essere un buon esempio confrontare la correttezza e completezza intuizionistica con quella classica.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 7.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 7">


**Completezza forte e debole**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 8.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 8">

- Abbozzo di ragionamento per queste completezza

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 9.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 9">

    Un algoritmo in un tempo finito non può analizzare un input infinito, quindi non potrebbe dimostrarlo un algoritmo. Esiste però una dimostrazione classica.


### 9.3.6 Conclusioni

- Questa semantica si può evolvere nel tempo (trovando nuovi algoritmi che mi risolvano il problema)
- Si ha una completezza debole per logiche senza RAA
- Se ho una prova intuizionista riesco a costruire un algoritmo che mi risolvi un problema
- EM non ha molto senso qua, se fosse una tautologia sarebbe un risultato molto forte
- Slide

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 10.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 10">


### 9.3.7 La negazione

Le formule negate non hanno informazione al loro interno.

Partiamo dalla regola del not, ovvero per dimostrare nonF devo dimostrare che F implica l'assurdo.

Ovvero devo dire che ci sia una funzione che parta da F e che arrivi a nulla.

Le soluzioni possibili sono solamente vuoto e singoletto di vuoto (in altri termini possiamo dire che abbiamo 0 e 1). chiaramente queste funzioni non sono affatto utili per cui non esiste un algoritmo che mi da cose utili.

**Negare due volte** è equivalente a distruggere una informazione (devi fare una tabellina con la regola per vedere che c'è questo)

| notF | Stato di F | notnotF |
| --- | --- | --- |
| singoletto vuoto |  Uguale a Vuoto |  vuoto |
| vuoto | Diverso da vuoto |  singoletto vuoto |

perché nonF mi può dare solamente due output, mi ha distrutto tutto l'algoritmo iniziale!

Dimostrare che non esiste significa dire che non esiste informazione.

Prova a dimostrare queste:


$$
\neg(F_1 \vee F_2) \Vdash \neg F_1 \wedge \neg F_2
$$


Mentre per quello sopra invertito (invertendo or e and di sopra) non è intuizionista, perché l'output ha più informazioni per qualche motivo strano.

## 9.4 Teorema di compattezza

Questo teorema è una conseguenza molto utile della proprietà di completezza, come in slide:

- Enunciato e dimostrazione del teorema

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 11.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 11">

    Questo teorema è molto forte, perché se ho un insieme infinito di filtri, vuol dire che ho bisogno solamente di limiti finiti. E il fatto che l'infinito si possa ridurre al finito è un fatto sorprendente.


### 9.4.1 Conseguenze della compattezza (4)

La cosa che era sorpredente della compattezza in questi casi è la possibilità di ritrovare in un caso infinito un caso finito da cui è possibile poter ricavare la cosa voluta!.

- Conseguenze

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 12.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 12">


### 9.4.2 Fallimento della compattezza per logiche complesse (3)

- Slide

    <img src="/images/notes/Semantica intuizionista/Untitled 13.png" alt="Semantica intuizionista/Untitled 13">
ze

    <img src="/images/notes/Semantica intuizionista/Untitled 12.png" alt="Semantica intuizionista/Untitled 12">


### 9.4.2 Fallimento della compattezza per logiche complesse (3)

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semantica intuizionista/Untitled 13.png" alt="image/universita/ex-notion/Semantica intuizionista/Untitled 13">