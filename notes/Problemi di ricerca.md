---
layout: page
permalink: notes/problemi-di-ricerca
tags: italian
title: Problemi di ricerca
---

Ripasso Prox: 36
Ultima modifica: December 29, 2022 3:24 PM
Primo Abbozzo: June 30, 2022 2:38 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

September 10, 2022

- Mi sono scordato gli stati possibili.
- - Quasi niente sulla ricerca per algoritmi non deterministici e non osservabili.

# 2 Problemi di ricerca

In questa prima parte si tratta di ricerca semplice, ossia si utilizza un modello basato su obiettivi, di struttura atomica, in un ambiente che risulti singolo-agente, episodico, totalmente osservabile, deterministico, statico, discreto, conosciuto.

## 2.1 Il problema

Vogliamo cercare di enunciare in un modo che possa essere formale, senza nessuna ambiguità il concetto di problema di ricerca.

### 2.1.1 Framework di soluzione

Individuiamo 4 fasi principali per un problema di ricerca, questo è un framework molto generico.

1. Formulazione dell'obiettivo (si cerca di individuare l'obiettivo della nostra ricerca).
2. Individuazione del problema (in cui si va a trascrivere il problema utilizzando una impostazione formale, solitamente astraendo dettagli non interessanti, il formato è descritto subito dopo nella sezione articolazione)
3. Ricerca della soluzione (in cui si cerca una effettiva soluzione per il problema di ricerca, probabilmente è la parte più dispendiosa di algoritmica).
4. esecuzione della soluzione (in cui gli attuatori eseguino la soluzione del problema trovato)

### 2.1.2 Articolazione

Vogliamo cercare di formalizzare il problema di ricerca nel modo più chiaro possibile, lo facciamo separando le funzioni e dati necessari per definire tutti gli aspetti di un problema di ricerca:

1. Stati possibili
2. Stato iniziale
3. Stati obiettivo
4. Funzione di azioni (da quale stato posso muovermi a quale stato)
5. Funzione di costo (il movimento da questo stato a quello quanto mi costa ?)
6. Funzione di transizione (mi muovo da uno stato all'altro)

### 2.1.3 Problemi standarizzati e reali

Questi problemi sono standarizzati proprio perché rappresentano un modello su cui comparare altre soluzioni che verranno in seguito sviluppate. Sono un cardine per vedere l'efficienza di una propria soluzione, e simili.

Invece i problemi reali possono avere una formulazione vaga, che cioè è dipendente dal contesto, o comunque da ciò che sia necessario al momento.

**Esempi di standard problems:**

1. 15/8 tile problem
2. Knuth factorial problem (partendo da 4, e applicando fattoriale e radici, si può fare qualunque numero)

**Esempi problemi reali**

1. Travelling salesman
2. Chip VSLI

## 2.2 Note generali

### 2.2.1 Percorsi ridondanti

Possiamo andare a definire un percorso ridondante, ogni percorso per cui se togli una tappa, il costo è minore (ricordiamo che in questo libro parliamo sempre di percorsi con un peso positivo), quindi ridondanti sono cicli, o percorsi con qualche tappa in più. Si può considerare come se fosse un concetto più generale di ciclo questo.

**Ovviare alle ridondanze**

Non vogliamo trovare percorsi che siano alla fine ridondati, vogliamo in qualche modo ricordare il nostro percorso:

1. Avere una tavola che ci dica se abbiamo già fatto quel percorso o meno
2. Avere una struttura, o formulazione del problema che non abbia questo problema di ridondanze (ad esempio una ricerca tipo-albero)
3. Ovviare solo ai cicli, e non alle ridondanze in generale, come vi adi mezzo.

### 2.2.2 Valutazione dell'algoritmo

In generale si valuta l'algoritmo secondo le risorse utilizzate, nel caso della ricerca in AI potrebbe essere il costo in soldi e in carburante, oltre alla classica memoria e tempo. Si propongono quindi 4 valori su cui valutare ciò:

1. Completezza (se esiste una soluzione perfetta la trovo sempre? Se non esiste so che non c'è?)
2. Ottimalità del costo della soluzione (es soldi etc).
3. Costo in tempo
4. Costo in memoria

Di particolare interesse sarebbe valutare la completezza dell'algoritmo.

## 2.3 Algoritmi disinformati

- Pseudocodice best-first-search

    <img src="/images/notes/image/universita/ex-notion/Problemi di ricerca/Untitled.png" alt="image/universita/ex-notion/Problemi di ricerca/Untitled">


### 2.3.1 Perché sono disinformati

Chiamiamo questi algoritmi come disinformati perché non hanno idea di come è fatta la struttura del campo di ricerca.

In pratica cercano con informazioni fortemente limitate sulla topologia del proprio ambiente.

Direi che vadano a cercare valutando solamente il costo, o indiscretamente nodi quasi casuali dell’ambiente circostante.

### 2.3.2 Carrellata di algos

Non mi è piaciuto molto questa parte, perché la maggior parte degli algoritmi esposti è presente nel corso di Algoritmi e Strutture fanno all'uni.

- BFS
- DFS
- Dept-limited dfs
- Dijkstra/uniform-cost-search
- Iterative deepening

## 2.4 Algoritmi informati

Questi algoritmi informati sono molto più interessanti rispetto agli algoritmi scorsi, per cui ne diamo più larga discussione

Il fatto che siano informati ci sta a significare soltanto che utilizzano un euristica per decidere meglio in che modo espandersi.

### 2.4.1 Euristiche

Bisogna cercare di definire in modo migliore le caratteristiche che ci potrebbero interessare delle euristiche: euristica ammissibile significa che la funzione di euristica è sempre minore del costo effettivo.

Consistente invece è in pratica soltanto una forma della disuguaglianza triangolare.

**Trovare un euristica è come risolvere una versione più rilassata del problema**, questa è una delle osservazioni fondamentali per quando si va a trattare di euristiche.

Altre soluzioni possibili sono Landmarks e pattern databases di cui rispettivamente i primi sono dei punti cardine, in cui si calcola tutto passando prima di quelli (come se mi chiedessi tipo: quanto ci metto se per andare da A a C, passo prima per il landmark B?) prima si calcolano questi landmark e si prendono decisioni in funzione di quanto mi danno ciò.

I pattern databases sono solamente un modo per cercare soluzioni già *precomputate* di pattern che ci sono solito. Si è utilizzato un pattern database per 8-puzzle e funzionava distintamente bene.

**Contours**

Come se fossero dei piano di livello di una montagna, anche per dijkstra si potrebbe disegnare un contour, ci indica in pratica in modo semplice in che modo si sta espandendo l’algoritmo di ricerca.

### 2.4.2 Carrellata algoritmi informati

quella più bella, usata in tutte le salse è l’algoritmo di A* Search, che in pratica è un uniform cost search, che invece di utilizzare solamente la funzione costo g(n) che rappresenta quanto effettivamente si paga per raggiungere il nodo n, tiene in considerazione anche una funzione h(n) che cerca di stimare il costo da n a un goal.

Una variante studiata è il greedy-first-search che praticamente tiene in conto solamente dell’euristica, senza la funzione di costo.

Altre varianti come WEIGHTED A* search applicano un fattore di peso sull’euristica, spesso rendendola non ammissibile o perfino inconsistente (non ho capito bene in che modo l’ammissibilità e la consistenza modificano le caratteristiche dell’euristica).

**Tecniche che tengono molto in conto la memoria**

Altre studiate possono essere la RBFS (Recursive best first search, che è simile a un MINIMAX con pruning, ma singolo agente, in pratica si espande sempre il nodo migliore, tenendo in conto il secondo valore migliore tra questi vicini, io continuo ad esplorare in profondità finché non mi converrebbe di più cominciare ad esplorare qualcosa a un livello molto meno profondo).

Oppure la SMA* la simple memory A star, che in pratica tiene in considerazione un numero massimo di nodi in memoria, se nel momento in cui va ad espandere lo ha finito, rimuove il nodo più vecchio, tenendo però un informazione riguardo quando costava esplorare quella via. (questo comunque può condurre a problemi simili al thrashing, in cui continua a switchare percorsi, restando così quasi bloccato).

BEAM SEARCH va in modo molto focalizzato verso una direzione sviluppando solamente i primi k nodi migliori sulla frontiera, invece A* si sviluppa nel suo territorio (quindi ++ sui contorni)

## 2.5 Interesse stato finale

In questi problemi non ci importa più di avere un percorso che ci porta alla soluzione, ma solamente la soluzione stessa. Non ci conviene più utilizzare gli algoritmi di ricerca presentati al capitolo precedente in [Problemi di ricerca](/notes/problemi-di-ricerca). Quindi si sono sviluppati algoritmi che si comportassero bene per massimizzare anche gli obiettivi di questi.

Termini importanti per parlare di questi ambienti:

1. Massimo locale
2. Ridge (che rende algoritmi greedy molto difficili da essere efficienti)
3. Plateau, parti piatte

### 2.5.1 Hill Climbing

- Hill Climb in breve (pseudoalgo)

    <img src="/images/notes/image/universita/ex-notion/Problemi di ricerca/Untitled 1.png" alt="image/universita/ex-notion/Problemi di ricerca/Untitled 1">


Questo è uno degli algoritmi più semplici per quanto riguarda la ricerca in questi ambienti, l’idea principale è scegliere il migliore fra i propri successori, e seguire quella strada finché si può migliorare.

Il problema principale è che questa versione semplice di Hill Climbing si blocca molto facilmente su minimi locali, o piani. Poi l’ambiente di Ridge è una cosa di difficilissima navigazione.

Quindi si sono inventati variazioni che tentavano di risolvere questo problema:

1. Random restart, ricominciare da un punto random, prendendo alla fine la migliore fra tutte
2. Local beam search, in cui si tengono ogni step i k migliori successori fra i k punti iniziali.
    1. Stochastic local beam search in cui randomicamente si considerano alcuni nodi anche lontani rispetto a questi, per cercare di sfavorire il fatto che tutti i punti migliori si ammassino su uno stesso punto.
3. Stochastic hill climbing, in cui in cui si seleziona un punto a caso, e lo si segue sempre se è migliore, e solo a volte se è peggiore
    1. Simulated Annealing in cui la probabilità di scegliere il punto peggiore dall’altra parte scende col tempo, con una funzione che decade esponenzialmente.

### 2.5.2 Algoritmi genetici

- Pseudoalgo

    <img src="/images/notes/image/universita/ex-notion/Problemi di ricerca/Untitled 2.png" alt="image/universita/ex-notion/Problemi di ricerca/Untitled 2">


Le caratteristiche generali di un algoritmo genetico sono in breve queste:

1. Dimensione della popolazione
2. Rappresentazione della stringa genetica in caratteristiche della popolazione
3. Funzione scelta dei n elementi più adatti tra la popolazione
4. Generazione di un figlio da coppie, o singola persona, o anche più persone di queste. (crossover)
5. Mutazione randomica di caratteri così generati
6. Elitismo o abbattimento di individui non adatti (a volte aiuta a velocizzare il processo).
7. Ripetizione di ciò fino a tempo finito o caratteristiche cercate trovate.

La differenza principale con lo stochastic local beam search è il momento di generazione di un nodo successore, che in questo caso, in quanto *giustificato dalla biologica*, o almeno da una forma contorta di biologia perché io personalmente credo che sia una forma eccessivamente semplificata, nonostante riconosco che è un buon punto di partenza) è generata da una ricombinazione di più individui.

**SCHEMAS**

Si è notato nel tempo (e lo si è anche dimostrato) che gli algoritmi genetici hanno un senso solo se pattern vicini codificano informazioni importanti cioè se i caratteri vicini non hanno nessuna relazione, è totalmente inutile utilizzare un algoritmo genetico.

Poi si è notato che se un pattern specifico aiuta il progenito a sopravvivere, effettivamente è probabile che si mandi alla generazione successiva. Ciononostante è doveroso tenere a mente che non tutti i pattern necessari vengono trasferiti, e non tutti i pattern inutili vengono eliminati, leggere l’approfondimento in biologia a pagina 136 dell’edizione cartacea che possiedi.

### 2.5.3 In ambienti continui

Se l’ambiente è continuo, è di gran lunga di più di interesse matematico. Si può vedere come un problema di calcolo numerico nella ricerca di un punto di minimo come il **Newton-Raphson-method**, che si può estendere anche a più dimensioni.

Oppure si può vedere come un problema di ottimizzazione-constrained, che si può risolvere con programmazione lineare, cose che riguardano analisi di superfici convesse. In pratica idee e cose altamente tecniche che non conosco ancora.

L’idea principale di questa parte comunque resta il fatto che si può discretizzare l’ambiente continuo, o cercando di aggiornarlo con passi piccoli, delta alla volta, in ogni direzione, o campionando lo spazio, dividendolo in tanti quadrettini lunghi delta, alla fine credo che questi approcci siano equivalenti.

## 2.6 non-deterministiche e not-fully observable

Introduciamo ora il concetto di belief state ossia una rappresentazione interna degli stati possibili dell’ambiente. Per gli algoritmi presentati in [Problemi di ricerca](/notes/problemi-di-ricerca) ogni singolo stato esterno corrispondeva lo stato di belief state interno, ossia c’era una corrispondenza, invece in questo caso andiamo a rilassare questo assunto, il *determinismo*, ossia il fatto che a una singola azione vada a corrispondere un singolo stato, ossia andiamo a dire che a singola azione, possono risultare una serie di stati differenti, maggiori di 1.

### 2.6.1 And-Or tree (non-det)

Con la possibilità di avere più stati a seguito di una singola azione cerchiamo di dividere cose che sono sotto il controllo dell’agente e cosa non lo è

1. OR-node, è una cosa che dipende dall’azione dell’agente
2. AND-node, è una cosa che dipende dalla reazione dell’ambiente in seguito ad azioni dell’agente.

Avendo questi due tipologie di nodi, possiamo andare a rappresentare l’intero ambiente attraverso un albero, per cui si possono utilizzare gli algoritmi di trasverse di alberi per trovare una soluzione che ora chiamiamo piano condizionale in quanto sarà constituito da un array di azioni, nel caso si è andato su un or-node, oppure di if-then, nel caso si stia andando avanti per un and-node.

**Nota: soluzioni cicliche**

A volte converrebbe cercare di *ragionare sui motivi della non-determinatezza* perché in questo modo sappiamo se una soluzione ciclica, ossia una soluzione che ha per foglie solamente un obiettivo, ma nel suo percorso può avere anche delle foglie che vadano in loop, sia effettivamente una soluzione: ossia il non-raggiungimento sia dovuto al caso, oppure a una sistematicità dell’ambiente in cui si è presenti.

### 2.6.2 Osservabilità parziale

Un aspetto che colpisce è che in ambienti in cui l’osservabilità è parziale, si possono ricavare delle informazioni semplicemente muovendosi, non per forza stando ad osservare l’ambiente! diciamo in questo caso che lo stato è **coerced**

Per ricondurci da tale ambiente a un problema di ricerca trattato in [Problemi di ricerca](/notes/problemi-di-ricerca), possiamo fare una cosa molto simile a quanto è fatto per Non-deterministic automata convertito a deterministic automata, ossia si ha una esplosione esplonenziale, ma comunque ben definita degli stati e delle funzioni di transizione che li legano.

**Ricerca incrementale**

A volte conviene, invece di esplorare tutto insieme, come fa il non-determinismo, causando computazioni impraticabili, di provare a cercare una soluzione in via incrementale, buildando prima una soluzione che funzioni per un nodo, poi per il secondo, cambiando leggermente la soluzione trovata, e poi via.

Si ha il risultato di trovare una soluzione o una assenza di essa in modo molto veloce.

### 2.6.3 Percezione nell’osservabilità parziale

Essendo un ambiente parzialmente osservabile, possiamo dare per scontato che esista una funzione Perceipt(state) che restituisce un insieme di stati osservati. Questa è una funzione stretttamente legata all’ambiente in cui agisce l’agente.

Allora in un ambiente non-deterministico ad osservabilità parziale dovremmo approfondire la funzione di transizione, che non si può considerare più l’unione o l’intersezione dell’azione che viene applicata a tutti gli stati, ma qualcosa di meno perché deve prendere in conto anche la percezione (ad ogni azione corrisponde uno stato che corrisponde subito una percezione).

La dividiamo in 3 parti

1. *Predizione* di quello che succede se applico l’azione a (ritorna un insieme di stati possiibili)
2. *Percezioni possibili* lista delle percezioni possibili per tutti gli stati raggiunti.
3. *Aggiornamento* degli stati di belief a un sottoinsieme a seconda degli stati raggiunti e delle percezioni possibili.

In questo modo si forma sempre un albero di ricerca, di azioni non-deterministiche.

### 2.6.4 Ricerca online

La ricerca online ci fa avvicinare a come sia l’esplorazione in un mondo vero, in pratica ora lo stato del mondo è dinamico, e dipende dalla presenza fisica dell’agente osservatore che non può più saltare da un nodo o un altro, oltre al fatto che lo stato può cambiare anche se non sta facendo niente. (c’è un problema riguardo punti di non ritorno, in cui le azioni sono irreversibili, ma questo lo tratteremo in capitolo seguenti).

- Pseudocodice per DFS-online

    <img src="/images/notes/image/universita/ex-notion/Problemi di ricerca/Untitled 3.png" alt="image/universita/ex-notion/Problemi di ricerca/Untitled 3">

    La cosa stupida di questo algoritmo è che non conosce le azioni che può fare in un determinato stato, e potrebbe ripetere azioni che si cancellano fra di loro (es. UP e DOWN uno di seguito all’altro).
    Le azioni qui dipendono dallo stato in cui si è presenti!


**Hill Climbing online (LRTA*)**

Un osservazione che si è fatto con la DFS è che ora si ha un oggetto fisico che si sposta, e non può fare voli dall’altra parte del labirinto per vedere come si sviluppa quel nodo di ricerca, per questo motivo possiamo affermare che c’è bisogno di un algoritmo di ricerca locale, questo era HILL CLIMBING!

Ma avevamo discusso in precedenza che si poteva bloccare molto facilmente questo algoritmo! Ma non possiamo più utilizzare random restart, dato che non esiste il teletrasporto, allora utilizziamo il **random walk**, in modo randomico scegli una direzione e la esplori.

Questa cosa adattata con anche una euristica che ti direzioni verso la parte giusta diventa un **LRTA**

- Pseudocodice Learning RealTime A*

    <img src="/images/notes/image/universita/ex-notion/Problemi di ricerca/Untitled 4.png" alt="image/universita/ex-notion/Problemi di ricerca/Untitled 4">


In pratica riaggiorna l’euristica del costo a seconda delle proprie mosse.