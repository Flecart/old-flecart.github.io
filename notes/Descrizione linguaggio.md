---
layout: page
permalink: notes/descrizione-linguaggio
tags: en
title: Descrizione linguaggio
---

Ripasso Prox: 79
Ripasso: June 10, 2023
Ultima modifica: June 4, 2023 3:33 PM
Primo Abbozzo: September 27, 2022 12:18 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled">

- Non sembra che abbia capito molto bene i concetti di pragmatica e linguaggio eseguibile per i linguaggi formali
- Dimostrazione numerabilità delle grammatiche.

Questo insieme di appunti riassume gli appunti 1-2-3 del professor Gorrieri.

# Descrizione di un linguaggio

## Introduzione

Per questa parte c’è un sacco di roba in comune con [Tecniche di definizione di semantica (4) 🟩](/notes/tecniche-di-definizione-di-semantica-(4)-🟩)

Trattiamo alcune caratteristiche che descrivono ad alto livello un linguaggio di programmazione. È da notare che questa parte della spiegazione del linguaggio non è limitante al solo linguaggio di programmazione, è utile per analizzare tutti i linguaggi (tranne la parte di implementazione)

### Sintassi 🟩-

*Relazione fra segni*. si occupa di decidere quando una frase è corretta.

**Aspetto lessicale**

Il lessico per una sintassi descrive le parole legali, In un linguaggio naturale il lessico è descritto solamente da dizionari. Se un vocabolo non esiste nel lessico di interesse, allora è erroneo, poi andremo a descrivere questo aspetto in modo formale

Vedere Scanner in appunti dopo

**Aspetto grammaticale**

Descrive la descrizione di frasi corrette a partire dal lessico, può essere utile in questo passo ricordarsi delle BNF [Sintassi e RI strutturali](/notes/sintassi-e-ri-strutturali) del corso di logica

Principalmente sono delle **regole** per costruire delle frasi che hanno un senso

### Semantica 🟩

Ossia riguardo il significato di una frase sintatticamente corretta→ relazione fra segni e significato.

**Linguaggio di appartenenza**

Una stessa parola, a seconda della lingua di interpretazione, può avere significati diversi → FAME (fama, oppure fame?)

Voglio utilizzare questo linguaggio per calcolare la semantica di questo linguaggio basandomi su qualcosa che già esiste. (alla fine, per l'architettura esistente attuale, saranno sempre 0 e 1 di bits).

### Pragmatica 🟩

Si occupa di studiare in quale modo le frase corrette sono utilizzate. Quindi va a rispondere a domande come “A cosa serve un costrutto?”, “Come si utilizza il comando”

> Insieme di regole per dare un indirizzo di uso
>

Esempio: *stile*: non usare goto, *scopo*: questo comando fa quello e questo quindi usalo per….

Dato che principalmente la pragmatica non è presente al momento della creazione del linguaggio ma si evolve con l’uso di esso, non è molto interessante da questo punto di vista (+ sull'ingegneria del software).

Un altro esempio è tipo utilizzare lei, invece del tu in contesti formali

Esiste anche una pragmatica per la semantica **Pragmatica**

### Il linguaggio eseguibile 🟨+

Un linguaggio formale deve soddisfare alcune regole in più rispetto al linguaggio naturale, in particolare → **l'implementazione.**

> Eseguire una frase sintatticamente corretta in modo semanticamente corretto.
>

Quindi si occupa dell'implementazione vera e propria del compilatore o dell’interprete del linguaggio. (In questo corso si faranno solo cenni, dato che non si implementerà tale linguaggio).

## Lessico e frasi di un linguaggio

### Alfabeto lessico e frasi 🟩

Definiamo ora alcune parole fondamentali per poter parlare di linguaggi in modo formale:

**Alfabeto**: a non-empty set of symbols/glyphs, typically thought of as representing letters, characters, or digits. (tipicamente finito, ma può essere anche infinito)

**Lessico**: un insieme di parole finite formate da lettere dell'alfabeto che consideriamo validi

**Frasi**: seguenze finite (o countably infinite, non vale per il lessico CREDO) di parole del lessico

### Il linguaggio formale 🟩

Sia $$A$$ il nostro alfabeto, e $$A^0 = \{ \varepsilon \}$$, e  $$A^{n + 1} = A \cdot A^n$$ con dot un operazione di concatenazione, allora L è un sottoinsieme solitamente finito di tutte le parole su $$A$$, ossia

$$L \subseteq A^*$$, $$A^* = \bigcup_{n \geq 0}A^n$$. Questo insieme si può creare con un insieme di regole, ma anche come elenco è corretto.

- Esempi di linguaggi

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 1.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 1">


### Numerabilità per alfabeti

Si può dimostrare che $$A^*$$ formato da alfabeti infiniti è ancora un infinito numerabile, si utilizza un argomento simile a Cantor spiegato in [R e Intervalli](/notes/r-e-intervalli) e in [Relazioni fra insiemi](/notes/relazioni-fra-insiemi).

- Dimostrazione numerabilità di A-star
    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 2.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 2">

Questo dimostra che **ogni unione di insiemi numerabili è numerabile.**
C'è una altra dimostrazione molto più semplice rispetto a questa costruzione di funzioni.

Praticamente numeriamo l'alfabeto finito che abbiamo, in ordine $$\sigma_{1} \sigma_{2}, \dots, \sigma_{n}$$
Allora questi hanno valore $$1, \dots, n$$, poi per le stringhe nella forma $$\sigma_{1}\sigma_{2}, \sigma_{1}\sigma_{3}, \dots \sigma_{n}\sigma_{n}$$ li metto anche ora in ordine di indice e inizio a contare da $$n + 1$$ e così via. Così so che ogni singola stringa del linguaggio ha un intero associato e posso dire che $$A^{*}$$ è numerabile.

### Definizioni operazioni di base (6) 🟩

**Lunghezza**

Viene definita in modo ricorsiva in questo modo:

- Slide

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 3.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 3">


**Concatenazione**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 4.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 4">


Deve soddisfare principalmente 3 proprietà

1. La lunghezza della stringa risultante è uguale alla somma della lunghezza delle singole stringhe
2. prima parte della stringa risultato è uguale alla prima stringa
3. seconda parte della stringa risultato è uguale alla seconda stringa

**Sottostringa, suffisso e prefisso**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 5.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 6.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 6">


È abbastanza banale dai, credo (in pratica posso prendere v in mezzo alla stringa di partenza mettendoci qualcosa prima e dopo

**Potenza n-esima**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 7.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 7">


Ossia provo a concatenera sé stesso più volte

### Operazioni di base su linguaggi (6) 🟩

**Complemento**

<img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 8.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 8">

**Unione**

<img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 9.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 9">

**Intersezione**

<img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 10.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 10">

**Concatenazione**

Questo è la concatenazione a livello linguaggio, mentre prima era la concatenazione a livello stringa

<img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 11.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 11">

**Potenza**

<img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 12.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 12">

**Chiusura / stella di Kleene / Ripetizione**

<img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 13.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 13">

### Rappresentazione del linguaggio (2) 🟩-

**Generativo - sintetico**

Non posso rappresentare un alfabeto infinito di caratteri! Ma posso memorizzare le regole che la generano. Per esempio posso memorizzare i numeri naturali con solamente gli assiomi di peano (in particolare mi bastano 2 delle 5 regole di peano

**Riconoscimento - analitico**

Sono le stringhe che vengono riconosciute da un automa che vedremo in seguito.

Ma non tutti i linguaggi sono riconoscibili da AUTOMI, resta il finito contabile come limite massimo, il motivo per cui è questo è perché le grammatiche sono equipotenti a $$\N$$, mentre tutti i linguaggi sono sottoinsieme di  $$\R$$ e quindi non riesco a detectarlo.

- Slide grandezza di grammatiche ed alfabeti

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 14.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 14">


## Grammatiche e BNF

### Def grammatica libera (4) 🟩

È una quadrupla di

1. Non terminali (insieme finito, indicato di lettere maiuscole)
2. Terminali (insieme finito, indicato da lettere minuscole)
3. Simbolo iniziale (simbolo speciale non terminale)
4. Produzioni (ricorda qui che la grammatica libera si può rappresentare con questa)

### Backus Naur-Form 🟩

In questa sezione cerchiamo di definire in modo più dettagliato le BNF introdotte nella lezione di logica di [Sintassi e RI strutturali](/notes/sintassi-e-ri-strutturali) trattati in logica.

- Slide esempio di una BNF per palindromi

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 15.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 15">

- Stesso precedente, ma scritto tramite la sintassi delle grammatiche

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 16.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 16">

- Definizione tramite assiomi

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 17.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 17">

- Definizione in via ricorsiva

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 18.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 18">


Indichiamo con $$L(P)$$ il linguaggio generabile a partire da un P, con le regole di inferenza di sopra

> L’unica differenza con le grammatiche libere è la sintassi differente per la descrizione di essa (utilizzo delle <>), ma storicamente credo che si siano evolute in modo distinto, e poi si sono accorti che erano la stessa cosa
>

### Derivazioni (leftmost e rightmost) 🟩—

**Definizione di derivazione immediata**

Sia $$G = (NT, T, R, S)$$ una grammatica libera da contesto, si dice che $$v$$ deriva immediatamente da $$w$$, indicato con $$w \implies v$$, quando $$\exists (A \to z) \in R$$, con $$R$$ le produzioni e $$A \to z$$ una produzione, e $$w = xAy$$, e $$v = xzy$$

In altre parole posso dire che una stringa è derivata in modo immediato da una altra stringa quando posso ricavarla con una singola operazione di una funzione presente in produzione.

- Slide definizione derivazione immediata

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 19.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 19">


**Definizione derivazione “generale”**

Posso affermare che da $$v$$ si deriva  $$w$$ quando esiste una sequenza finita (anche vuota) di derivazioni immediate tali che


$$
v \implies w_0 \implies ... \implies w
$$


Tale cosa è riscritta come $$v \Rightarrow^* w$$

- Slide Definizione di Derivazione generale (!!!)

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 20.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 20">


**Derivazione left e rightmost**

- Concetto di derivazione left e right most

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 21.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 21">

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 22.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 22">

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 23.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 23">


Il concetto più generale è che nel processo di derivazione di una stringa in un linguaggio viene sempre espanso il non terminale più a sinistra.

**Check appartenenza**

Si può verificare che una stringa appartiene a un certo linguaggio descritto in modo formale come sopra se si può creare un albero di derivazione

- Esempio di derivazione

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 24.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 24">


### Linguaggio generato da grammatica 🟩

Data una grammatica $$G = (NT, T, R, S)$$ a contesto libero definiamo il linguaggio libero $$L(G)$$ generato dalla grammatica come


$$
L(G) = \{ w \in T^* : S \Rightarrow ^* w\}
$$


Ossia in parole umane, tutte le stringhe terminali generabili da quella grammatica.

- Slide definizione

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 25.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 25">


## Alberi di derivazione

Un albero di derivazione è una rappresentazione molto utile per un compilatore per comprendere la struttura interna intermedia. fornisce informazioni semantiche!

[Definizione albero di derivazione (5) + 1 🟨+](/notes/definizione-albero-di-derivazione-(5)-+-1-🟨+) presenta alcune proprietà dell’albero, che è invariante rispetto all’albero, questa osservazione ci dà anche un hint per la definizione del concetto di ambiguità per grammatiche e linguaggi.

Una altra osservazione importante è che **possiamo associare un albero di derivazione a ogni Derivazione**.

### Definizione albero di derivazione (5) + 1 🟨+

Vogliamo descrivere la struttura di un albero di derivazione generale

1. La radice è il non-terminale iniziale ossia $$S$$
2. Tutti i nodi hanno simboli in $$NT \cup T \cup \{\varepsilon \}$$
3. I nodi interni hanno solo simboli $$NT$$
4. Esiste una relazione diretta fra padre e figli definiti da una produzione, più in generale se $$A\in NT$$ e  $$x_1,..., x_n$$ sono nodi figli, esiste una produzione $$A \to x_1, ..., x_n$$
5. Se $$\varepsilon$$ è su un nodo, allora quella è una foglia ed esiste la produzione $$A \to \varepsilon$$, con A l’etichetta per il parent

Inoltre andiamo a chiamare **albero di derivazione COMPLETO** se ogni foglia è un terminale.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 26.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 26">


### Relazione con derivazione 🟨+

Si può dimostrare che una stringa appartiene a un linguaggio, solo se esiste un albero di derivazione per essa in quel linguaggio, quindi è un buon metodo per descrivere la derivabilità in modo non-ambiguo.

- Idee per la **bigezione**

    Chiaramente se vado Derivazione → Albero è una cosa abbastanza ovvia perché è il modo con cui si crea l’albero

    Se vado nella direzione Albero → Derivazione (dx, sx) sto facendo in pratica una DFS che espande sempre il primo a sinistra o primo a destra di non terminali, e ho anche bisogno di una funzione che sia in grado di restituirmi una stringa data dalle foglie, fatto ciò dovrebbe essere easy.


### Alberi sintattici 🟩

Quando abbiamo un albero di derivazione completo, possiamo estrarre l’albero formato dalle foglie, come in figura, per avere un albero che abbia qualche **informazione riguardo la semantica** di quanto descritto.

- Esempio estrazione albero sintattico

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 27.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 27">


### Albero di sintassi concreta o Astratta

C’è una leggera differenza fra sintassi astratta e concreta.

Di sotto, durante la risoluzione delle ambiguità facciamo uso delle parentesi per disambiguare, questo utilizzo delle parentesi è presente nell’albero di sintassi concreta, anche chiamato **parse tree**.

Invece l’albero di sintassi astratta può essere ambigua, rappresenta una astrazione sulla sintassi concreta del linguaggio e spesso è ambigua.

- Email mandata, in TODO

    **Albero di derivazione**

    È l'albero che soddisfa le 6 proprietà presentate (radice è il non terminale iniziale, i nodi

    interni sono etichettati come non terminali, etc..).

    **Albero di sintassi concreta**

    È l'albero che rappresenta tutta la sintassi del programma (con anche zucchero sintattico)

    Questo albero inoltre è un albero di derivazione perché soddisfa tutte le proprietà.

    **Albero di sintassi astratta**È formato solamente dalle foglie dell'albero di sintassi concreta, senza le foglie dovute allozucchero sintattico, quindi non è un albero di derivazione perché non soddisfa le proprietàdi essa (e.g. nodi interni non terminali) e contiene informazioni semantiche riguardo al programma.


## Ambiguità

### Tipologie di ambiguità (con esempi 2) 🟩-

**Ambiguità nella grammatica**

Si può dire che una grammatica è ambigua se esistono due alberi di derivazione differenti per una stessa stringa.

- Esempio di ambiguità per alberi di derivazione

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 28.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 28">

- Esempio di grammatica ambigua

    $$
    S \to A | \varepsilon \\
    A \to \varepsilon
    $$

    Questo linguaggio genera solamente dei vuoti, ma lo può fare in modi diversi eg:

    $$S \to \varepsilon$$, o $$S \to A \to \varepsilon$$

    Una altra grammatica che descrive il linguaggi equivalente non è però ambiguo

    $$S \to \varepsilon$$


**Ambiguità nel linguaggio**

Si può dire che un linguaggio è ambiguo se ogni sua grammatica è ambigua.

- Esempio di linguaggio ambiguo

    <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 29.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 29">


### Risoluzione delle ambiguità 🟩

In modo simile a quanto trattato in [Sintassi e RI strutturali](/notes/sintassi-e-ri-strutturali) bisogna stabilire:

1. Ordine di precedenza degli operatori
    - Esempio di problema di precedenza

        <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 30.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 30">

2. Associatività sinistra o destra
    - Esempio di necessità di associatività dx e sx

        <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 31.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 31">

3. Parentesi
    1. Questo è un zucchero sintattico che non ha nessun valore semantico che aiuta a disambiguare la precedenza. (L'albero semantico non serve avere le informazioni sulle parentesi)
    2. Questo è necessario per essere **equivalente semanticamente** ossia possono generare ora gli stessi alberi semantici
    - Aggiunta parentesi

        <img src="/images/notes/image/universita/ex-notion/Descrizione linguaggio/Untitled 32.png" alt="image/universita/ex-notion/Descrizione linguaggio/Untitled 32">


**Grammatica ambigua:**


$$
S = a|b...|S + S|S\times S
$$


**Soluzione ambiguità**


$$
E = E + T | T \\
T = A \times T | A \\
A = a|b ...| (E)
$$




# References