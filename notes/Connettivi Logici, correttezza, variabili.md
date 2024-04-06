---
layout: page
permalink: notes/connettivi-logici,-correttezza,-variabili
tags: en
title: Connettivi Logici, correttezza, variabili
---

Ripasso Prox: 15
Ripasso: December 22, 2021
Ultima modifica: September 30, 2022 3:19 PM
Primo Abbozzo: November 19, 2021 8:34 PM
Stato: 🌕🌕🌕🌕🌗
Studi Personali: No

# Elementi di ripasso

- Dubbi passati
    - Dimostrazione del teorema di invarianza
    - Proprietà dei connettivi logici
    - Dimostrazione della correttezza
- Dimostrazione delle variabili
- Teorema di compattezza, cosa è

# 8 Connettivi logici

## 8.1 Dimostrazione teorema invarianza

### 8.1.1 Introduzione

Basi: Due proposizioni sono equivalenti quando valgono sugli stessi mondi.

quindi $$\forall v, \llbracket F \rrbracket ^v \equiv \llbracket G \rrbracket ^ v$$.

Vogliamo dire che dati un buco presente in una proposizione, queste valgono sempre, sono in effetti equivalenti. Il buco la prendo come una variabile proposizionale.  (riempire = rimpiazare il buco)

### 8.1.2 Operazione di sostituzione

Si può notare che ci sono 4 casi base, mentre le altre 4 sono per ricorsione strutturale.

<img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled">

### 8.1.3 Enunciato

<img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 1.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 1">

La funzione di sostituzione ci permette di utilizzare una sostituzione anche nel profondo di un albero di deduzione naturale, però non è accettabile poi in sede d'esame utilizzare questo teorema per fare deduzione naturale.

La dimostrazione è per induzione strutturale abbastanza banale dopo aver definito la sostituzione, ma comunque resta un buon esercizio che dovresti fare.

### 8.1.4 Osservazione

## 8.2 Connettivi logici

### 8.2.1 Definizione semantica (denotazione)

- Enunciato

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 2.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 2">


Dalla definizione di connettivo unario si può dedurre che esistono $$2 ^{2^n}$$ connettivi possibili ($$2^n$$ funzioni possibili per scelte dominio e 2 scelte posssibili per codominio.

Es, per tutte le $$2^n$$ righe, devo dare in output un numero. Quindi posso dare una funzione che passa tutti 0 per tutte le righe, fino alla righa che da tutti uno per tutte le $$2^n$$ righe, finendo per avere $$2^{2^n}$$ funzioni possibili.  Dobbiamo ora scegliere il perché abbiamo scelto questi connettivi fra tutti quelli presenti

### 8.2.2 Giustificazione delle scelte

**Zero:** Abbiamo preso tutti i connettivi zeroari, identificano il concetto di giusto o falso.

**Uno:** abbiamo preso solamente il connetivo not. (uno è uguale all'input, gli altri due la ignorano, uno la ribalta, per questo abbiamo scelto solo il not).

**Binari** questi sono tanti, ma non abbiamo dato una connotazione solo ad alcuni (eliminando tutti quelli banali tipo uguale a input, o inverso di input, o bot e top).

### 8.2.3 Riduzione fra connettivi (classico)

Questo concetto è molto simile al ruolo di equivalenza fra due regole diverse (l'eliminazione dell'and e e1 e2). in [Deduzione naturale](/notes/deduzione-naturale).

- Definizioni

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 3.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 3">


Qui viene introdotto il concetto di **funzionalmente completo** che abbiamo utilizzato in [Porte Logiche](/notes/porte-logiche).

E anche il concetto di **riduzione** indicato con $$\rhd$$

Studiamo quali connettivi sono necessari, scopriamo che nor e nand sono sufficienti, tutto si potrebbe ridurre a questi. Sono completi anche $$\vee, \wedge, \neg, \bot, \top, \implies$$ ridondante, ma funzionalmente completo

### 8.2.4 Motivi della scelta dei connettivi (3)

- Lista motivi

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 4.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 4">


Poi c'è una lunghissima [lista](https://virtuale.unibo.it/pluginfile.php/963360/mod_resource/content/1/slides8.pdf) di proprietà possibili. Il prof. in classe ha dato l'intuizione del conceto di dualità fra top e bottom e and e or (basta ordinare la retta fra -1 e 0 per verificare che corrispondono, in pratica per la definizione attuale della nostra semnatica si hanno questi valori)

### 8.2.5 Proprietà dei connettivi (9)

Queste scelte sono **"funzionalmente complete"** per la relazione di equivalenza.

CAIDANA

- Proprietà

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 5.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 5">

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 6.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 6">


Infatti grazie a questo si può creare un **teorema di completezza** per le regole, ovvero si può dimostrare che

$$P \equiv Q$$ partendo solamente da queste regole, però non servono spesso per il calcolo. (a volte queste regole complicano la forma originale perché la forma di assorbimento di dovrebbe espandere).

Altre cose sono

**Modus barbara e risoluzione.**

## 8.3 Correttezza e completezza

La correttezza la saltiamo, perché è troppo complicato ed enunciata in breve sul teorema di completezza di sopra.

### 8.3.1 Correttezza

$$\Gamma \vdash F \implies \Gamma \Vdash F$$

- Enunciato più corretto

    Localmente corrette significa che devono essere delle regole valide (che creano conseguenze logiche).

    Ovvero significa che ho una ipotesi che funziona localmente ma non globalmente e lo scrivo come un implica.

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 7.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 7">


**Intuizione**

Ogni regola metto in un foglietto diverso (anche l'ipotesi scaricata è presente di un foglietto sopra).

Voglio dire che quella regola non è una regola scaricata per un foglietto sotto. (viene scaricata solamente da un foglietto sopra.

- Dimostrazione

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 8.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 8">


I **Passi principali di dimostrazione**

1. Caso base A e caso impossibile [A]
2. Ipotesi induttiva: i sotto-alberi sono conseguenza logica di ipotesi globali e ipotesi locali (localmente corrette).
3. Per utilizzo di regole locali so che F è conseguenza logica di molti implica.
4. Per il teorema di deduzione semantica trasformo l'ipotesi induttiva con implica in RHS e LHS solo ipotesi globali del ramo principale.
5. Unisco con transitività della conseguenza logica.

### 8.3.2 Perché correttezza più semplice di completezza

Affinché abbia la correttezza, mi bastano delle regole che siano localmente corrette, se invece ho una regola incorretta riesco a derivare bottom da top, e quindi mi creerebbe una teoria inconsistente (tutto che valga).

Vorrei dire che **ho tutte le regole per catturare un concetto semantico** utilizzando un concetto sintattico (finito). Come faccio a usare una quantità finita per catturare l'infinito? Quindi per le logiche semplici come la logica proposizionale classica si può, per le altre no.

È sorprendente che un insieme finito di regole sia sufficiente a dimostrare infinite ipotesi, questo in matematica è catturato il concetto di **compattezza**.

Due ingredienti

1. Devo avere tutte le regole, queste sono sufficienti per dimostrare tutte le conseguenze logiche.
2. Da un insieme finito di regole devo essere in grado di dimostrare tutto.

### 8.3.3 Completezza in logica classica

- Non è possibile dimostrare queste classiche tautologie RAA, EM

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 9.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 9">

    Nel caso due, posso dimostrare A oppure non A per introduzione dell'OR. Però poi non ho niente per continuare, in certi mondi non funziona A, perché non ho ipotesi, e non ho niente per dimostrare bottom con l'introduzione della negazione.
    Quindi queste non sono dimostrabili.


Ma questi valori sono validi se i valori di verità sono solamente due! **le regole che ho non colgono la dualità (vero falso) della logica classica**. infatti queste si dimostrazione solamente con l'introduzione della regola RAA.

Ma l'introduzione di questa regola **toglie l'algoritmicità della dimostrazione** quindi non è da fare.

Per avere dimostrazione della correttezza della regola [qui](/notes/qui)

## 8.4 Variabili

- Definizione funzione Var

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 10.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 10">


Costruiamo una funzione Variabile definita per ricorsione strutturale che ritorni tutte le variabili esistenti in una formula logica.

Cerchiamo di creare una sintassi che possa essere utilizzabile **tutta l'infinità dei mondi.**

Riesco quindi a introdurre il concetto di equivalenza di mondi in funzione di una proposizione.

### 8.4.1 Teorema: var(F) finito per ogni F

La dimostrazione (intuizione) per induzione strutturale è abbastanza easy. Nel caso dei casi finiti dovrei dimostrare che il singoletto e il vuoto sono finiti. Nel caso di parti composte, devo supporre che siano finite per le espansioni, allora l'unione di insiemi finiti è ovvia

In realtà la dimostrazione vera devi formalizzare prima il concetto di finito e non finito, che è in teoria degli insiemi, quindi hai bisogno di molte altre cose.

### 8.4.2 F in v usa restrizione di v al dominio Var(F)

Posso creare una relazione di equivalenza se per ogni X in Var(F) ho che v(X) = v2(X) e ho che i due mondi sono uguali.

Chiamo solamente delle variabili di un mondo?

- Dimo

    <img src="/images/notes/image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 11.png" alt="image/universita/ex-notion/Connettivi Logici, correttezza, variabili/Untitled 11">


**Dimostrazione**

In pratica sto collassando in una classe di equivalenza con il

Il fatto che siano finiti mi permette di costruire tabelle di verità.

**Nota**

Grazie a questo teorema posso dire che una variabile (proposizione) sia valida in tutti i mondi dipendentemente solamente dal valore di verità di una variabile al caso base.

Questo significa che le proposizioni logiche sono valide per tutti i mondi che soddisfino le precodizioni e non solamente nel mondo specifico!
l valore di verità di una variabile al caso base.

Questo significa che le proposizioni logiche sono valide per tutti i mondi che soddisfino le precodizioni e non solamente nel mondo specifico!

# References