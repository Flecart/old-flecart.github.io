---
layout: page
permalink: notes/logica-del-primo-ordine
tags: en
title: Logica del Primo ordine
---

# Logica del primo ordine

Questa è la logica più utilizzata dai matematici

### Limitatezza della logica proposizionale
La logica proposizionale classica non è in grado di ragionare sull'infinito
<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled">


Fino ad ora abbiamo utilizzato una metalogica per giustificare il per ogni e l'esiste nelle dimostrazioni fin'ora.

Dobbiamo quindi dare una definizione più formale dei **quantificatori**.
### Obiettivo della logica del primo ordine

Si può quindi identificare come l'obiettivo della logica di primo ordine l'introduzione dei quantificatori dell'universale e dell'esiste

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 1.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 1">
## Sintassi

In questa sintassi stiamo dividendo in Termini e proposizioni (le proposizioni che si possono trovare nella logica proposizionale classica).

Definiamo i termini o vocabolario ossia gli **elementi del discorso come**

$$
t::= x \mid c \mid f^{n}(t_{1}, \dots, t_{n})
$$

### Def: Vocabolario
Ossia, *simboli di relazione n-arie* (ossia con $$n$$ argomenti) $$p, q$$ etc...
e simboli di funzione $$f, g, h$$ anche questi n-arie etc...
ricorda la differenza fra funzione e relazione fatta in [Relazioni fra insiemi](/notes/relazioni-fra-insiemi)

### Def: Termine
Lo facciamo in modo induttivo.
- Una variabile qualunque è un termine
- Poi caso induttivo: se $$t_{1}, \dots, t_{n}$$ sono termini, lo è anche $$f^{n}(t_{1}, \dots, t_{n})$$

NOTA: qui non facciamo uso di relazioni per definire i termini
### Def: Formula o proposizione
Anche qua definiamo per induzione:
- $$P(t_{1}, \dots, t_{n})$$ è un predicato $$n-ario$$ ed è una formula. (un predicato è una funzione che mappa in 0, 1)
- Se $$\varphi, \phi$$ sono formule, lo sono anche tutte le banali cose logiche, quindi $$\varphi \land \phi, \varphi \lor \phi, \varphi \to \delta, \forall x.\varphi, \exists x. \varphi$$

### Def: Teoria
È un insieme di formule come definito di sopra, basate su un certo vocabolario fissato.
È interessante la roba di [(Choi 2022)](https://direct.mit.edu/daed/article/151/2/139/110627/The-Curious-Case-of-Commonsense-Intelligence) che dice che non è possibile usare la logica per problemi real world.


- Riassunto sintassi:
    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 2.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 2">


Come si può osservare nella sintassi di logica del primo ordine estende la logica proposizionale classica perché per P 0 ho le singole proposizioni

Quindi si divide in un **dominio di discorso**, ossia l'insieme dei termini possibili come costanti e le**formule o proposizioni** che possiedono un valore di verità.

### Perché primo ordine

Si chiama logica di primo ordine perché non si possono utilizzare le funzioni sulle variabili nel dominio di discorso.

Questa è l'ultima logica in cui vale ancora la completezza, e la correttezza, nelle logiche superiori non sarà più possibile catturare tramite un concetto sintattico il valore semantico.

Questa è la logica di primo ordine che basta ai matematici per fare tutto (questo perché le funzioni dei matematici in realtà sono degli insiemi, non qualcosa che calcola).

### Possibili denotazioni
<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 3.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 3">

1. Oggetti ignoti nel dominio
2. Oggetti fissati
3. Connotazioni di denotazioni oggetti
4. Connotazioni di denotazioni di valori di verità

## Semantica

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 4.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 4">

Questa parte è approfondita dopo con mondo ed interpretazione

## Binder

I binder sono un concetto fondamentale nell'informatica (soprattutto a chi andrà a fare i compilatori). Quindi stiamo astraendo un livello di semantica! Connettivi ancora più astratti.

> I binder legano una **variabile** e uno **scope** (Cattura una variabile (o serie di varaibile) in uno scope che viene valutato più e più volte).
>
1. Formula matematica (uno scope nel senso di derivata, integrale sommatoria e simili)
2. I Simboli logici per ogni esiste.

Vado a valutare una unica formula all'interno di uno scope (e continuo ripetutamente a sostituire e calcolare su tanti valori, e restituisco il risultato sintetizzato).

### Shadowing

Nei binder non si può accedere alle variabili esterne se hanno lo stesso nome, si dice **shadowing** (quello interno nasconde l'esterno, quindi fa ombra, nasconde).

Un esempio è ridichiarare un parametro formale in una funzione.

### Diagrammi di legame

Sono molto utili per capire le variabili del binder e lo scope di queste variabili

Cose da fare:
1. Legare variabile a ogni binder e lo scope
2. Esistono le variabili che non vengono mai legate, si dicono variabili libere queste (come libreria o variabili globali), queste si indicano con una freccia all'infinito con il nome

### Variabili libere

Queste variabili non sono modificabili (come provare a cambiare il nome di una funzione di libreria esterna).

- Definizione per induzione strutturale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 5.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 5">


## alfa-convertibilità

Si chiama alfa perché una branca dell'informatica che studiava i lambda, cuore del linguaggio di programmazione funzionale. (io lo chiamo anche sostituzione idiota, ma attento che in linguaggi normali c'è il fenomeno dell'opacità che non ci permette di farlo!)

> Si dice che una serie di formule sono alfa-convertibili se il diagramma di legame creato dalle formule è uguale → **relazione di equivalenza**
>

Essendo una relazione di equivalenza possiamo lavorare su una classe di equivalenza, quindi sarebbe bene ragionare al livello di **insieme quoziente delle formule**.

- Esempi

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 6.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 6">

    Nell'esempio in giallo, la Z fa shadowing, ha cambiato una variabile che in primo momento apparteneva a uno scope esterno.

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 7.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 7">


### Sostituzione in logica primo ordine

Praticamente questa nozione ci dice che una funzione ha lo stesso output anche se quello che ci va dentro è una variabile con un nome diverso. Questa nozione ha una certa similitudine con la funzione di sostituzione, in quanto entrambi parlano di invarianza sulla sostituzione di variabili.

La differenza principale è che questa parla di binder mentre quella di prima parla di stesso valore di verità di una proposizione.

Possiamo allora definire una funzione di sostituzione anche per la logica del primo ordine che faccia attenzione anche ai diagrammi di flusso e i binder

- Sostituzione

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 8.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 8">


## Mondo o interpretazione

Non è più sufficiente avere un mondo indicato solamente come una v, ma **è necessaria una coppia ordinata**: (A, l) dove A è l'insieme non vuoto di denotazioni, mentre l è simile alla vecchia funzione semantica v, però associa degli elementi in A altri elementi in A, non dice niente sulle connotazioni.

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 9.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 9">


### Def: Modello
Questo è anche chiamato **mondo** in questo caso.

Un simbolo non ha significato finché non ne diamo uno, questo è la parte della semantica, che vuole cercare di dare senso al mondo. Uno stesso simbolo può avere diverse interpretazioni (diversa semantica) in modelli diversi

Dato un [vocabolario](#def-vocabolario) $$(f_{1}, \dots, f_{j}, p_{1},\dots, p_{i})$$ un modello è 
- Un insieme $$U$$
- Le funzioni $$f_{1}^{U},\dots, f_{j}^{U}$$ e similmente definite $$p$$ tali per cui se $$f_{1}$$ ha arietà n, allora $$f_{1}^{U} : U^{n} \to U$$, ossia è una relazione n-aria.
- Per $$p_{1}$$ si ha che $$p_{1}^{U} \subseteq U^{n}$$.
- 

### Def: Interpretazione
Con un insieme $$V$$ possiamo definire interpretazione una funzione $$I: V \to U$$ con $$U$$ l'insieme del modello definito [#Def Modello](#def-modello).
Solitamente questo è definito in modo induttivo.

### Nozione semantica di per ogni ed esiste

- Esempi di formalizzazione sintattica errata

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 10.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 10">

    Per esempio: elefante è una connotazione, mentre la denotazione è quell'animale in carne ed ossa, non posso manipolare delle denotazioni in questo caso, quindi non avrebbe senso utilizzarlo.

    Nel secondo caso sto testando molte più cose (connotazioni sono molti di più rispetto alle denotazioni in quanto esistono i sinonimi)


L'idea principale è tenersi una lista (una mappa) che associ nomi (connettivi) e denotazioni del mondo, questa è **l'ambiente** indicata con la lettere csi.

### Semantica della logica primo ordine
La funzione di interpretazione va per ricorsione strutturale in tutte le sotto-formule, per cui basta definirlo nell'insieme dei termini e la ho per tutto il modello.

- Ricorsione strutturale
    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 11.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 11">


### Conseguenza logica in Primo ordine

Dobbiamo prendere in questo caso considerazione della definizione più complessa del mondo (ricordarsi che nelle logiche di ordine superiore è proprio questa ulteriore complessità che non permette di avere una completezza).

Quindi dobbiamo tenere conto del significato di **(A, l), $$\xi$$.**

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 12.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 12">

### Def: Verità
Possiamo definire che una proposizione è vera se:

$$
U, I \models P(t_{1}, \dots, t_{n}) \text{ se } \langle I(t_{1}), \dots, I(t_{n}) \rangle \in P_{I}^{U}
$$

ossia se il termine usando tutta l'interpretazione presente è dentro il nostro modello. È un modo leggermente differente per sopra
Si può continuare a definirlo per tutti i quantificatori:

$$
U, I \models \varphi \land \phi \text{ se } U, I \models \varphi \land U, I \models \phi
$$


$$
U, I \models \varphi \lor \phi \text{ se } U, I \models \varphi \lor U, I \models \phi
$$


$$
U, I \models \neg \varphi \text{ se } U, I \not \models \varphi
$$


$$
U, I \models \exists x. \varphi \text{ se esiste } \alpha \in U \mid U, I\left[ x \to \alpha \right]  \models \varphi
$$


$$
U, I \models \forall x. \varphi \text{ se per ogni } \alpha \in U \mid U, I\left[ x \to \alpha \right]  \models \varphi
$$

NOTA: se andiamo a considerare una formula chiusa, ci basta il modello, perché l'interpretazione è utile quando andiamo a trattare formule libere.

## Proprietà esiste e per ogni

Queste proprietà espandono la lista CAIDANA delle proprietà presenti in [Connettivi Logici, correttezza, variabili](/notes/connettivi-logici,-correttezza,-variabili).

### Completezza debole

- Slide

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 13.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 13">


### Commutatività e non
<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 14.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 14">


chiaramente se Sono gli stessi x e y in due per ogni es $$\forall A, \forall B$$ questo è uguale a dire $$\forall B, \forall A$$, stessa cosa per l'esiste.

Ma il senso della frase cambia nel caso in cui abbia un per ogni e in seguito un esiste.

### Semidistributività

In certi casi (non per tutti) posso spostare (addirittura eliminare!) i quantificatori

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 15.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 15">
### De morgan

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 16.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 16">

### Equivalenze notevoli

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 17.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 17">

<img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 18.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 18">

## Deduzione naturale

In questa sezione di appunto andiamo ad indagare le regole della deduzione naturale per la logica di primo ordine, per questo motivo linko la deduzione naturale in ambito proposizionale [Deduzione naturale](/notes/deduzione-naturale)

Vogliamo utilizzare delle cosa uguali a meno di alfa conversione.

### Introduzione Per ogni

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 19.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 19">

    Attento che Y non deve affatto appartenere alle variabili libere delle foglie!

    Questo mi dice che devo utilizzare solamente solamente una variabile che non è stata già presa (quindi libera, data dall'esterno)

    **Suggerimento:** per non sbagliare mai ti basterebbe prendere una variabile mai presa prima.

    /to

- Correttezza ed invertibilità intuizionista

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 20.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 20">

- Correttezza classica

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 21.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 21">

    Io sintatticamente ci metto y e il mondo mi risponde xi y. Ora l'ambiente xi mi dice che x vale xi di y e quindi è la stessa. Ma lo devo dimostrare per induzione strutturale.

- Invertibilità classica

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 22.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 22">


### Eliminazione per ogni

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 23.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 24.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 24">

    Dovrei passare per la formula più complessa a volte! A volte è più semplice dimostrare il generale che il particolare perché possiedo induzione strutturale e simili.

- Correttezza intuizionista e classica

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 25.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 25">

    Anche da questo possiamo sapere che non possiamo andare a cercare tutte le variabili, sono infiniti! L'algoritmo non concluderebbe mai.


### Introduzione Esiste

Questa dimostrazione è praticamente uguale all'eliminazione del per ogni, mentre l'eliminazione è simile all'introduzione

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 26.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 26">


### Eliminazione dell'esiste

In questa forma io non ho nessuna informazione sulla x, non posso prendere una x che è già stata utilizzata nella conclusione C oppure nelle foglie.

**Deve essere una variabile libera!**, non deve avere nessuna altra ipotesi presa da altro.

- Forma generale

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 27.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 27">


## Completezza ed incompletezza di Godel

- Angelo was here 18/10/22, and 20/03/24 too!

###  Primo teorema

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Logica del Primo ordine/Untitled 28.png" alt="image/universita/ex-notion/Logica del Primo ordine/Untitled 28">

    Gamma voglio identificare un singolo mondo.

    Se contiene l'aritmetica ho i numeri la somma i prodotti e simili. Se gamma è consistente (quindi interessante, sennò tutto e dimostrabile, è anche un modo per dire che non ho più mondi).
    Allora **non posso filtrare in maniera da tenerne solamente uno.** il gamma deve tenere anche dei mondi in più.

    Quindi quando gamma parla di artimetica non si può filtrare fino a un singolo mondo.

    Quindi qualunque aritmetica prendo, non posso mai filtrare fino a singolo mondo!

    è una incompletezza di Gamma, ma non è una incompletezza delle regole!

- Abbozzo

    È una delle prime assolute codifiche!

    bigezione fra formule ed alberi, e la sintassi dimostrazione e poi utilizza il paradosso del mentitore (io mento) crea un numero che dice che non è dimostrabile, quindi fonde livello e metalivello per cui non può né essere dimostrabile né essere indimostrabile (altrimenti sarebbe inconsistente). Entrambe sono false

    Io sono dimostrabile se e solo se io non sono dimostrabile, quindi entrambe devono essere false.


Uno dei teoremi più storpiati dai divulgatori scientifici. Ma allo stesso tempo è uno dei teoremi più profondi della logica.

Se abbiamo abbastanza ipotesi da poter identificare solamente un singolo mondo, allora vale il concetto di terzo escluso, quindi o vale F conseguenza logica del mondo oppure not F è conseguenza logica

(nel caso contrario posso avere sia non G sia G  non sono conseguenze logiche di più mondi).

Godel **trova la P**, però quel singolo P è ben conosciuto, non è molto interessante.
  
Questo è stato introdotto per la prima volta in [Incompletezza nella logica del primo ordine](/notes/logica-del-primo-ordine#completezza-ed-incompletezza-di-godel). È importante qui conoscere sia la

- [Sintassi](/notes/logica-del-primo-ordine#sintassi) della logica del primo ordine.
- [Semantica](/notes/logica-del-primo-ordine#mondo-o-interpretazione) della logica del primo ordine.
### Panoramica della dimostrazione

- Supponiamo di avere una logica del primo ordine ben definita sintatticamente.
- Consideriamo l'insieme $$\mathbb{N}, +, \times$$
- Definiamo la prima teoria dell'altro di $$(\mathbb{N}, + , \times)$$ in questo modo
	- $$Th(\mathbb{N}, +, \times) = \left\{  \varphi \mid \varphi \text{ è una formula vera della logica del primo ordine su } (\mathbb{N}, +, \times) \right\}$$

Il nostro obiettivo è dimostrare che $$ETH$$ è riducibile tramite mappatura a questo insieme. Vedere [Halting Theorem and Reducibility](/notes/halting-theorem-and-reducibility)].

Curiosità: La teoria $$Th(\mathbb{N}, +)$$ è decidibile, ma è meno espressiva rispetto all'altra teoria aritmetica. Questo è chiamato [aritmetica di Presburger](https://en.wikipedia.org/wiki/Presburger_arithmetic). E per l'analisi aritmetica è piuttosto importante dal punto di vista computazionale.

### Dimostrazione dell'Incompletezza

Dato un vocabolario arbitrario e una teoria su quel vocabolario, l'insieme $$\left\{ \varphi \mid \varphi \in T \text{ ed è valido} \right\}$$ non è un insieme decidibile. Questo approccio è più computazionale.

Supponiamo di avere una macchina di Turing che decide sopra, vogliamo ridurre il linguaggio $$ETH$$ su questo.

#### Codifica della Macchina di Turing
Vedere [La macchina di Turing](/notes/la-macchina-di-turing) per definizione di TM. Andremo a codificare il comportamento di una macchina di Turing utilizzando  la logica di primo ordine. E poi dato che questa codifica è possibile si può dire che non è decidibile quel problema.
Il processo che usiamo è chiamato **gödelizzazione** perché andiamo ad utilizzare codifiche per risolvere questo problema.

Consideriamo questo vocabolario:
- Simboli di funzione sono $$O^{0}, S^{1}, P^{1}$$ che sono il 0, il successore e il precedessore.
- Simboli di relazione
	- $$head(n,m)$$ se al passo $$n$$ è sulla cella $$m$$
	- $$state(n, m)$$ se al passo $$n$$ è sullo stato $$q_{m}$$
	- $$cell_{i}(n, m)$$ se al passo $$n$$ la cella $$i$$ contiene $$m$$

Poi diamo gli [assiomi di peano](/notes/algebra-logica#assiomi-di-peano) al nostro sistema logico, poi codifichiamo con le relazioni questa affermazione:
"Al passo $$0$$ la cella è $$1$$ , lo stato è $$q_{0}$$ e tutte le celle sono vuote."
abbiamo che

$$
state(0, 0) \land head(0, 1) \land \forall y(\neg head(0, 0) \land \neg head(0, S(S(y))))
$$

<img src="/images/notes/Logica del Primo ordine-20240320130152196.jpg" alt="Logica del Primo ordine-20240320130152196">
Qui vediamo come la logica è molto molto verbosa, sostanzialmente inutile per applicazioni molto più pratiche.

Poi possiamo codificare la caratteristica della macchina di Turing principale ossia che
"Ad ogni passo la macchina è solo in uno stato, testina su una unica cella, che contiene al più un simbolo"
Molto molto verboso scriverlo in modo logico anche questo.
<img src="/images/notes/Logica del Primo ordine-20240320130115976.jpg" width="425" alt="Logica del Primo ordine-20240320130115976">

<img src="/images/notes/Logica del Primo ordine-20240320130208140.jpg" width="437" alt="Logica del Primo ordine-20240320130208140">

Poi possiamo andare a definire anche le regole di transizione e la regola dello stato finale, una volta fatto questo abbiamo **codificato interamente una TM** con le formule di Turing.
<img src="/images/notes/Logica del Primo ordine-20240320130252051.jpg" width="501" alt="Logica del Primo ordine-20240320130252051">

#### Riconoscibilità di un sistema deduttivo
Vedi [Deduzione naturale#Il sistema deduttivo](/notes/deduzione-naturale#il-sistema-deduttivo), dato questo sistema deduttivo, vogliamo che
1. È corretta, ossia $$P \vdash \varphi \implies \varphi \text{ è corretta}$$ sound, se lo dimostro allora è vero.
2. L'insieme $$\left\{ \langle \varphi, \pi \rangle \mid \pi \text{ è una dimostrazione di } \varphi \right\}$$ è un insieme decidibile

Possiamo subito dire che l'insieme 

$$
\left\{  \varphi \mid \varphi \in T \land P \vdash \varphi \right\} 
$$

È riconoscibile, data una teoria $$T$$ e un sistema deduttivo come sopra. Basta usare la schematizzazione di sopra, ed enumerare tutte le dimostrazioni per vedere se risolve questo. Potrebbe non finire, ma se è valido mi fermo!

#### Indecibilità di un sistema aritmetico
Usando la costruzione di sopra possiamo vedere che chiaramente abbiamo fatto la riduzione
$$ETH \leq Th(\mathbb{N}, +, \times)$$ quindi non è decidibile.
Ossia non esiste un metodo algoritmico (sistema deduttivo) che ci dice se una data formula è nel sistema.
La codifica è più complicata, però è possibile.

#### Proposizioni indimostrabili
Questo è il secondo teorema di Gödel, che ci dice che esistono formule che in nessun sistema deduttivo sono dimostrabili.

Ossia: $$\exists \varphi \in Th(\mathbb{N}, +, \times) \mid \forall P \not\vdash \varphi$$
Esiste una formula nella teoria dei numeri naturali tale per cui non esiste nessun sistema deduttivo che lo dimostri.

Supponiamo per assurdo che tale proposizione esiste, allora abbiamo un sistema deduttivo che lo prova. Ma vogliamo dire che se vale questa proprietà $$Th(\mathbb{N}, + , \times)$$ è decidibile, contraddicendo [#Indecibilità di un sistema aritmetico](#indecibilità-di-un-sistema-aritmetico).

L'algoritmo per deciderlo è abbastanza semplice:
1. Uso una TM non deterministica che ci permette di verificare in parallelo se $$P \vdash \varphi$$ oppure se $$P \vdash \neg \varphi$$, per ipotesi sappiamo che esiste una prova per $$\varphi$$ o $$\neg\varphi$$. Tanto so che $$P$$ esiste per ipotesi.
2. A seconda se sia vera $$\varphi$$  o $$\neg\varphi$$ possiamo rispondere sì o no, e quindi decidere il termine.
Fine.





### Secondo teorema di incompletezza

Questo ha un apporto molto maggiore, molto importante, la base dell'informatica.

- Enunciato

    <img src="/images/notes/Logica del Primo ordine/Untitled 29.png" alt="Logica del Primo ordine/Untitled 29">

    Non riesco mai a concludere la consitenza della logica, dovrei rimettermi al metalivello continuamente, senza finire mai.

    Non possiamo **mai essere sicuri della consistenza di una teoria**, e alla fin fine la logica, la matematica si può paragonare alla religione da questo punto di vista. Noi non siamo sicuri che sia vero. Serve l'atto di fede.
a di una teoria**, e alla fin fine la logica, la matematica si può paragonare alla religione da questo punto di vista. Noi non siamo sicuri che sia vero. Serve l'atto di fede.

# Registro Ripassi

- Vecchi dubbi
    - Definizione per induzione strutturale delle variaibli libere
    - Cosa sono le due funzioni n-arie definite nella sintassi?
    - Riguardare registrazione 09/12 (10 minuti iniziali in cui riassume tutta la logica del primo ordine)
    - i nomi tecnici per dire termini e proposizioni
- Ancora da definire
    - Le proprietà delle equivalenze logiche notevoli
    - Quali sono le equivalenze notevoli del per ogni e dell'esiste?
    - Rivedere sostituzione in logica di primo ordine
    - Registrazione 16/12  per prove di sostituzione o dim con primo ordine.


Ripasso Prox: 4
Ripasso: December 14, 2021
Ultima modifica: October 18, 2022 6:01 PM
Primo Abbozzo: December 1, 2021 9:56 AM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# References

[1] Choi [“The Curious Case of Commonsense Intelligence”](https://direct.mit.edu/daed/article/151/2/139/110627/The-Curious-Case-of-Commonsense-Intelligence) Daedalus Vol. 151(2), pp. 139--155 2022