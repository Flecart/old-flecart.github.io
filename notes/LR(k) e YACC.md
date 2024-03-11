---
layout: page
permalink: notes/lr(k)-e-yacc
tags: italian
title: LR(k) e YACC
---

Ripasso Prox: 70
Ripasso: May 26, 2023
Ultima modifica: June 9, 2023 3:22 PM
Primo Abbozzo: November 29, 2022 12:35 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# LR(k) e YACC

## LR(k)

### Grammatiche LR(k) 🟩

Anche in questo caso proviamo a generalizzare il concetto dei pirmi k caratteri, in modo da generalizzare in qualche senso il concetto di LR(k), quindi **andiamo a modificare la closure** considerando ora first k

Per ricordarti come si calcolava first k, andare a guardare [Top-down Parser](/notes/top-down-parser)

il problema che poi diventa pratico riguardo questo è l'impossibilità di gestire **stringhe lunghezza k** che sono una assurdità (esponenziale per la lunghezza)

### Grammatiche SLR(k) 🟩


Uguale a SLR(k), ma possiamo andare a fare il reduce solamente quando il nostro terminale di interesse **appartiene al follow k!**

### Grammatiche LALR(k)🟨+

Questo è esattamente identico a LALR, si va a considerare il concetto di nucleo, e questo concetto di nucleo è uguale al precedente speigato in [Bottom-up Parser -LR(1)](Bottom-up%20Parser%20-LR(1)%20c484cd325d19414ca5b2161065e82685.md)

## Classificazione dei linguaggi

### Gerarchia generale 🟨


Da qui si può creare una semplicissima gerarchia dei parser, che si possono riassumere in


$$
\forall k, SLR(k) \subset LALR(k) \subset LR(k)
$$


E oltre questo inclusioni per ogni k, rispetto al k minore e la non inclusione. Questo riassume il tutto. Con qualche intersezione con LL k

### Note sulla classificazione (!!) 🟨

È molto più facile classificare un **linguaggio invece che grammatica** potrei avere delle grammatiche che non siano LL(k), mentre il linguaggio che genera lo è


**Esiste grammatica non ambigua non deterministica!**

Questo è il punto motivatore per cui andiamo a concentrarci sui linguaggi invece che sulle grammatiche, ci possono essere delle miriadi di grammatiche per uno stesso linguaggio e il fatto che possano anche non essere deterministiche non ci aiuta molto in questa analisi:


$$
S \to aSa | bSb|\varepsilon
$$


Si può vedere subito il conflitto shift reduce al primo passo, persino con un parser LR(1).

**Teoremi sulla classificazione dei linguaggi**


Importante l'equivalenza del fatto che $$LL(k)  \equiv SLR(1)$$, qualunque sia k! posso andare a costruire una grammatica equivalente che sia in grado di fare ciò. (credo valga anche LR(k) = SLR(1), dato che è un sse per entrambi riguardo linguaggi liberi deterministici).

Una altra nota interessante è che **tutte le gramamtiche che sono SLR(1) oppure LR(k) allora sono non-ambigue e deterministiche**. la cosa importante di queste proposizione è che **ambiguità → impossibile LR o LL!**

Gli SLR(1) ci piacciono in modo particolare 🙂, hanno una grandissima capacità espressiva ma è probabile che la grammatica che è riconosciuta da questo sia estremamente complessa e difficile da modellizzare diciamo, per questo motivo conviene utilizzare grammatiche LR k con k alto, se mi crea un parser più carino.

### Proprietà di (non) chiusura (3)🟩-

Le osservazioni di maggior rilievo riguardo questo sono

1. Unione di linguaggi LL 1 può non essere LL 1
2. Union edi linguaggi LR 0 può non essere LR 0
3. Concatenazione di LL 1 può non essere LL 1

Quindi un sacco di nozioni negative!

## YACC

In modo simile a quanto presentato per Lex in Lex/Flex  e Yacc. Yacc è l'equivalente utilizzato per i Parser.

### Collaborazione con LEX

Solitamente YACC non è impiegato da solo, ma in stretta collaborazione col LEX.

Infatti esistono delle funzioni **yylex()** e la variabile **yylval** che sono spesso utilizzate per gestire il tempo di lettura diciamo.

yylex - chiedi il prossimo token
yylval - puntatore nella tabella dei simboli dell’ultimo lessema.

### Descrizione input e output 🟨

Prende un programma in questo linguaggio yacc, in cui è presente la descrizione della grammatica libera che si vuole andare a riconoscere, e dà in output un programma che sia in grado di riconoscere quella grammatica

Questo programma può essere compilato, e poi sarà in grado di ricevere in input alcuni token e crearci un albero di derivazione.

(ma alla fine dipende l’uso che vogliamo andare a farci:

1. Se vogliamo creare un interprete, possiamo dare la valutazione dell’albero
2. Se vogliamo andare a creare un compilatore potrebbe essere codice intermedio oppure l’albero di derivazione. (questa roba è descritta in **azione semantica** del matching.)

**In realtà**

Come abbiamo detto nel documento precedente, yacc lavora in strettissimo contatto con il lexer, al quale chiede di volta in volta altri token ogni volta in cui ne ha bisogno, quindi chiede sul momento!


**Condivisione di variabili!**

### Struttura di un file Yacc (4)

[https://www.ibm.com/docs/en/aix/7.1?topic=information-example-program-lex-yacc-programs](https://www.ibm.com/docs/en/aix/7.1?topic=information-example-program-lex-yacc-programs)


1. Prologo (defines)
2. Definizioni (token o operatori)
3. Regole con azioni semantiche
4. Funzioni ausiliarie (utilizzate in azioni semantiche spesso).
- Esempio di un file YACC

### Sintassi regole e funzioni ausiliarie

Le regole sono proprio nella forma

nonterm: corpo1 → azione semantica

corpo2 → azion sem 2… etc… molto simile a quanto faceva lex.

Riguardo alle funzioni ausiliarie di solito è compilato insieme a lex, e linkati assieme, altrimenti se non c’è viene generato in automatico un yylex().

### Azione semantica

È la parte di codice eseguito una volta che si è trovato un altro pezzo dell’albero (ricorda che vanno in contemmporanea).

Questo potrebbe dare un **valore semantico** diverso a seconda del metodo che stiamo andando ad utilizzare diciamo.

- Albero sintattico
- Valutazione
- Codice intermedio.

### Default risoluzione conflitti

- Slide



Come prima regola per la risoluzione dei conflitti si considera **l’associatività** degli operatori, poi **l’ordine di dichiarazione (precedenza**) se non sbaglio l’operatore dichiarato più tardi ha la precedenza su quelli dichiarati prima.

Se ci sono ancora delle ambiguità dopo queste dichiarazioni allora si va alla risoluzione di default.

Se ci sono alcune forme di conflitti shift/reduce o reduce/reduce vengono risolti in questo modo:

**Shift-reduce** viene sempre risolto in favore alla shift

**Reduce reduce** viene risolto col reduce listato prima (quindi una forma di precedenza).