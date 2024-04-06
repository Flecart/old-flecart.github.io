---
layout: page
permalink: notes/semantica-di-un-linguaggio
tags: en
title: Semantica di un linguaggio
---

Ripasso Prox: 80
Ripasso: June 2, 2023
Ultima modifica: June 7, 2023 2:41 PM
Primo Abbozzo: October 1, 2022 10:15 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

- Domande

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled">


# Semantica di un linguaggio

## Vincoli sintattici contestuali

### Intro: dipendenze da contesto 🟩

I vincoli sintattici non sono esprimibili tramite BNF perché dipendono dal contesto, mentre le grammatiche libere sono per definizione libere da contesto, vogliamo quindi trovare una soluzione a questo problema. Vengono usati metodi Ad-Hoc nella fase di **analisi semantica** del programma.

**Grammatiche dipendenti dal contesto**

Queste grammatiche sono molto più complicate (e lente) rispetto a quelle libere da contesto, quindi è poco pratico e non utilizzabile (tempo esponenziale, quindi non finisce mai).

### Semantica statica 🟩

Facciamo differenza fra semantica statica e dinamica con il primo che è analizzato nella fase di compilazione del programma, mentre per dinamico è analizzato nella fase di run-time, ma è una forzatura del nome, perché storicamente sintassi è indicata solamente a grammatica libera, mentre semantica è tutto il resto, ma in verità **semantica statica è parte di sintassi**.

Principalmente questa parte riguarda **controlli ad-hoc sul programma durante la compilazione**. (ad hoc perché non è vista dall’albero di sintassi).

- Semantica statica def slide

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 1.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 1">


**Esempi di controlli semantica statica**

Sempre da tenere in mente che gli errori riportati in questa fase sono riguardanti la sintassi del programma (quindi ad esempio l’utilizzo di variabili non assegnate è possibile in C non in Java, questo è un controllo di semantica statica che dipende da questa sintassi del programma)

- Utilizzo dell’assegnamento a una variabile
- Le funzioni sono chiamate col giusto numero di variabili
- Divisione per zero (guarda esempio sul libro non è ben definita questa cosa sul fatto che sia statica o dinamica).
- Assegnamento di variabili dello stesso tipo.

Questi sono esempi di **vincoli sintattici contestuali**.

### Semantica dinamica (e utilizzi) 🟩—

- Def semantica dinamica slide

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 2.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 2">


Questa semantica è un **modello matematico** utile per ogni architettura! È una sorta di specifica che deve descrivere il concetto di **correttezza di un programma** dal punto di vista semantico. È una rappresentazione dell’esecuzione del programma!

Esempi di utilizzi:

- Slide utilizzi (!!!)

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 3.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 3">

- Dimostrazione di proprietà del programma
- Specifica formale del linguaggio
- Implementazione è corretta?

Questi utilizzi si possno distinguere se l'autore è un programmatore, un progettista del linguaggio, un implementatore di un linguaggio. (vedere le slides)

### Tecniche di definizione di semantica (4) 🟩

Questa parte descrive la semantica, ma per certi punti ha un sacco di roba in comune con [Classical Cyphers](/notes/classical-cyphers)

**Operazionale**

Si mostra **l’effetto di ogni istruzione** durante l’esecuzione, per dare enfasi su questo aspetto dobbiamo avere bene in mente la macchina astratta (registri stati etc..) (o mini automa).
In parole povere proviamo a far eseguire su una macchina astratta

Come calcola? questo è quello che andiamo a fare oggi.

**Denotazionale**

Si fa enfasi su cosa va a calcolare (in cui si fa enfasi sulla **funzione che viene calcolata**).

**Pragmatica**

Da ricordare la pragmatica in Pragmatica 🟩 in cui vengono trattati in generale principi per la descrizione di un linguaggio. In più si va a chiedersi sul come utilizzare un costrutto e sullo scopo del singolo comando.

Si parla di **stile di programmazione**.

- Esempi di pragmatica

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 4.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 4">


**Implementazione**

Si va a rispondere a domande come

- **L’implementazione è corretta**? (veramente il sorgente e l'output implementano la stessa semantica?)
- Come è implementato?
- **Il codice in output è efficiente o meno**? Le strutture di dati utilizzate sono troppo pesanti o sono ok?

## Struttura del compilatore

- Slide struttura del compilatore

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 5.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 5">


### Analisi lessicale (Scanner) 🟩

Viene **generata e riempita** una tabella di simboli, questa fase vengono identificati ogni singola parola (o **token**) che incontra nel nostro programma.

In breve fa queste cose

1. Genera i token (il lessico ammissibile)
2. Riporta errori se trova token non legali
3. Riempie parzialmente la tabella dei simboli

Se qualche parola non è valida viene utilizzato un gestore dell'errore

I token sono spesso

- identificatori
- Numeri
- operatori
- Parentesi
- Parole riservate

Sono usati in questa parte  grammatiche regolari espressioni regolari automi NFA DFA

### Analisi sintattica (Parser) 🟩

In input riceve i token, utilizza la grammatica del linguaggio per **verificare se è corretto** in output restituisce un albero di sintassi astratta del nostro programma. (quindi riporta errori sintattici del nostro programma) e aggiunge informazioni alla tabella dei simboli.

Quindi in breve

- Generazione albero di derivazione
- Report degli errori sintattici (al livello di frase)

Sono usati in questa parte grammatiche libere da contesto pushdown automata (DPDA)

### Analisi semantica 🟩

Controlla se tutta la sintassi libera da contesto sia coerente con la semantica del contesto (quindi verifica tipi, verifica chiamate o moltiplicazioni che abbiano senso o meno)

In breve

1. Controlli di semantica statica  (verifica dei tipi, parametri etc) vedi sopra
2. Aggiorna la tabella dei simboli con informazioni sui tipi
3. Espande l’albero con cose sui tipi

### Codice intermedio 🟩-

Scrive questo codice intermedio più semplice

- Si segue la struttura sintattica, quindi spesso genera del codice molto verboso
- Produce codice molto semplice ,spesso *three-address code*.
- Esempio di codice intermedio

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 6.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 6">


### Ottimizzazione (4) 🟩

Ottimizza il codice nella forma intermedia

- Codice inutile è rimosso
- Ottimizzazioni varie
    - Espansione delle chiamate in linea (inline)
    - Fattorizzazione di sottoespressioni
    - Mettere fuori cicli sottoespressioni che non variano

### Generazione codice 🟩

- Ottimizzazione specifica all’architettura
- Generazione del codice specifico (quindi a livello del singolo registro, o gestione stack e simili

### La tabella dei simboli 🟩

Contiene informazioni riguardo tutti i simboli all'interno del programma, quindi molto utile nella fasi di analisi.

Quindi contiene metainformazioni riguardo ai simboli di interesse.

## Semantica Operazionale strutturata

> The meaning of a program in the strict language is explained in terms of a hypothetical computer which performs the set of actions that constitute the elaboration of that program. ([Algol68]([https://en.wikipedia.org/wiki/Operational_semantics](https://en.wikipedia.org/wiki/Operational_semantics)#algol68), Section 2)
>

### Intro: insiemi di riferimento 🟨

Ha un **linguaggio** definito con la sintassi astratta solita (qualunque stringa è parte dell’albero di sintassi valido)

Agisce principalmente su 3 insiemi

1. Booleani
2. Numeri
3. Variabili (simbolici)

Con questi dati primitivi definiamo delle espressioni

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 7.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 7">

1. Espressioni aritmetiche (che agiscono su numeri o variabili)
2. Espressioni booleane
3. Comandi (control flow, gestione memoria, move di variabili)

La descrizione di questi insiemi con le BNF sono ambigue ma per l'analisi della semantica non ci serve che abbiano un senso vero per questa roba. Non ci interessa di farlo in modo dis-ambiguo ci interessa questa parte solo per la semantica dinamica

I parser danno in output degli alberi in sintassi astratta

### Sistema di transizione (!) 🟩—

- Slide di definizione

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 8.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 8">


Questo sistema di transizione ci è utile per descrivere al meglio la semantica.

È una tripla $$\Gamma, T, \to$$ dove il primo è l’insieme degli stati, il secondo l’insieme degli stati terminali e il terzo una relazione di transizione (che più o meno ci dice in che modo possiamo muoverci all’interno di questi stati).

Indichiamo con **computazione** da uno stato $$\gamma_o$$ di partenza una seguenza (possibilmente infinita) di transizioni.

Indichiamo con $$\to^*$$ la **chiusura riflessiva e transitiva** della relazione di transizione.

### Interna sinistra, destra, ed esterne 🟩

Questo concetto di definizione di operazioni interna sinistra,destra ed esterne è solamente un metodo che piace al prof per descrivere questo, però mi sembra che sia praticamente inutile lmao.

Comunque una operazione la descrivi come interna se valuti entrambi gli operandi, sinistra se valuti prima il sinistro e poi il destro e poi viceversa.

La definisci come esterna se è possibile valutare soltanto l’operatore sinistro (quindi esterna sinistra) o destro.

Oltre IS, esistono anche ID, ES, ED e Interna Parallela = IP (in cui posso utilizzare in modo alternato il destro o sinistro, e quindi mi basta solo sum1 o sum1’, quindi questa è **non-deterministica**), perché posso avere delle derivazioni diverse (ad ogni step posso avere più di un unico assioma da utilizzare!), e potrei anche farli in parallelo.

### Semantica delle espressioni aritmetiche (!) 🟩

<img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 9.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 9">

- Assiomi per le relazioni (3 tipi)

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 10.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 10">

    **Var** sostituzione con variabile con un numero terminale

    **Sum1** mi dà una sorta di idea di equivalenza per la somma per alberi che si derivano.

    **Sum2** mi dà una equivalenza quando la somma è su un numero

    **Sum3** mi dà una equivalenza nella somma nei naturali.

    **Sub{1,2,3}** sono esattamente equivalenti ma per la sottrazione.


**Osservazioni**

- Lo store **non viene mai modificato**.
- Per la valutazione si preferisce valutare l’operando più a sinistra. →**Interna sinistra** in modo analogo esiste l’interna destra.

- **Costruzione solita, con store**

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 11.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 11">


### Funzione di transizione è deterministica (non richiesta) 🟥

Questa è una caratteristica importante della funzione di transizione, si fa uso della ricorsione strutturale presente in 4.6 Ricorsione strutturale.


$$
y \to y', y \to y'' \implies y' =y''
$$


Ossia ho **una sola possibile** mossa

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 12.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 12">

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 13.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 13">


### Eval 🟩

Il fatto che sia deterministica ci permette di definire un concetto di **eval** tanto è unica!

<img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 14.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 14">

È definita con le funzioni di valutazione interne sinistre!

Essere esterno significa che a volte non valuto tutti gli operandi nella nostra operazione, mentre le interne devono valutare tutte.

<img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 15.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 15">

In generale valgono queste valutazioni

### Equivalenza (!!) 🟩-

Possiamo anche definire un concetto di **equivalenza di espressioni** come proprietà di questo eval.

- Definizione di equivalenza per espressioni

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 16.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 16">


### Semantica delle espressioni booleane (!) 🟩

<img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 17.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 17">

- Assiomi per la semantica delle espressioni booleane

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 18.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 18">


Valgono le proprietà per le espressioni aritmetiche

- Store non cambia
- La relazione è deterministica.

### Semantica dei comandi (statements) (!) 🟨+

<img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 19.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 19">

- Assiomi per la semantica dei comandi

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 20.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 20">

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 21.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 21">


**Commenti sugli assiomi**

*Skip* non faccio niente, lascio la funzione di valutazione esattamente la stessa

*Assign* viene fatto uno step di sostituzione (e quindi bisogna anche creare una funzione di sostituzione, ma è definita bene in logica in questo blocco 8.1.2 Operazione di sostituzione.

*Seq* cerca di far andare avanti la computazione

*If* decide in quale ramo andare, quindi due regole easy

*While* in modo molto simile, decide se rieseguire il corpo del while oppure andare fuori.

---

Si può notare che anche questa semantica è **deterministica**! In modo simile si può dimostrare per ricorsione strutturale insieme le altre, dato che è deterministica possiamo **definire una funzione *exec**. che è definita solo se è terminale

---

**Divergenza e deadlock sono EQUIVALENTI** (Ossia computazione ch enon può andare avanti e cicli infiniti, non si distinguono con questa semantica, bisogna introdurre delle cose in più).

### Errori dinamici (runtime) 🟨

<img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 22.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 22">

- Regole di generazione e propagazione dell’errore

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 23.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 23">

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 24.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 24">

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 25.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 25">

- Altre regole per errori (che in un linguaggio solitamente esistono)

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 26.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 26">


### Non determinismo e parallelismo 🟨

Non deterministico perché si può eseguire in mondi diversi e ritornare cose diverse a seconda di quei mondi.

Parallelismo perché può eseguire in contemporanea le istruzioni (in questo senso l’ordine di esecuzione può essere ben differente).

- Slide

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 27.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 27">

- Esempio di esecuzione non deterministica

    <img src="/images/notes/image/universita/ex-notion/Semantica di un linguaggio/Untitled 28.png" alt="image/universita/ex-notion/Semantica di un linguaggio/Untitled 28">




# References