---
layout: page
permalink: notes/nomi-e-scope
tags: italian
title: Nomi e Scope
---

Ripasso Prox: 70
Ripasso: June 1, 2023
Ultima modifica: April 25, 2023 9:22 AM
Primo Abbozzo: February 20, 2023 8:45 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# Nomi e Scope

## I Nomi e oggetti

### Oggetti denotati e identificatori🟩

I nomi sono sequenze di caratteri o numeri aka: **token alfanumerico** (anche **IDENTIFICATORE** (per token guardare [Grammatiche Regolari](/notes/grammatiche-regolari)) utilizzate principalmente come **Astrazione sul controllo e sui dati** (quindi sono cose molto più facili da ricordare rispetto il suo encoding binario o a indirizzi). Infatti utilizziamo i nomi per evitare di interessarci di informazioni come l’indirizzo di memoria del nostro dato o per creare una interfaccia con visibili solo nome della procedura e parametri.

I nomi quindi possono essere utilizzati per cose come

- Elementi definiti al momento di progettazione del linguaggio:
    - Costanti predefinite
    - operazioni primitive (+, * etc)
    - Tipi di dato primitivi
- Elementi definiti da utenti
    - Variabili
    - Parametri
    - Indirizzi di memoria.
    - Procedure (le funzioni)
    - Costanti dell’utente
    - tipi dell’utente

### Bindings (4) 🟩-

Il binding è proprio il collegamento che si ha fra il nome e l’oggetto che viene denotato da essa.

Questo binding è creato in 4 momenti diversi:

- Progettazione del linguaggio
    - In questa fase possono venire definite le cose come elencate sopra
- Struttura del programma
    - In questa parte viene solamente iniziato il collegamento fra identificatore e variabile identificata (e.s. se identifica una zona di memoria non allocata, non è ancora completato il binding), per questo motivo possiamo dire che è iniziato il binding delle variabili definite dall’utente ma non è stata completata.
- In fase di compilazione
    - Per esempio in questa fase vengono allocate le variabili statiche (e.g. quelle globali su C/C++), quindi certe variabili effettivamente hanno finito di bindare in questa fase
- A runtime
    - Per esempio nelle allocazioni dinamiche, oppure allocazione su stack (che comunque è runtime), un identificatore come un indirizzo ha finito il binding con l’oggetto denotato solamente in questo momento.

Importante a questo punto è stabilire il concetto di **statico vs dinamico.**

Nell’esempio di sopra i primi 3 punti sono parte del binding statico, mentre il quarto è dinamico. Questo perché statico si intendono tutte le associazioni fatte dal compilatore prima dell’esecuzione del programma, mentre dinamico è solitamente fatto dalla macchina astratta al momento dell’esecuzione

### Lifetime 🟩

Bisogna in questa fase fare una distinzione della **vita dell’associazione** e **vita dell’oggetto denotato**.

In certi casi si può avere che la vita dell’associazione è minore di quella dell’oggetto denotato, questo può succedere per esempio quando l’associazione è cambiata (quindi distrutta e ricreata in altro modo), anche un cambio di ambiente (e quindi di blocco può avere lo stesso effetto).
(oppure un oggetto passato per riferimento nella chiamata di funzione, la vita del binding all’interno della funzione resta quella)

In altri casi può succedere che la vita dell’oggetto denotato sia minore dell’associazione, questo può capitare per esempio quando un oggetto allocato dinamicamente sia stato liberato, mentre l’associazione non lo sia, si parla in questo caso di dangling reference.

## Ambiente

> È l’insieme di associazioni fra identificatori e oggetti denotati in un certo momento dell’esecuzione a uno specifico punto.
>

In certi punti di esecuzione del programma può succedere che uno stesso oggetto è denotato da più nomi, in questo caso si dice che i nomi sono degli **alias** fra di loro.

### Tipologie di ambiente (3) 🟩

Facciamo distinzione fra tre tipologie principali di ambiente:

1. Locale (quelli creati dal blocco corrente)
2. Non Locale (quelli creati da blocchi superiori (quindi quelli che non sono dichiarati localmente in pratica).
3. Globale (quelli creati nel blocco più sopra possibile, solitamente all’inizio del nostro programma)
    1. Blocco più esterno
    2. Codice importato

### Operazioni sull’ambiente (5) 🟩

Dato che l’ambiente è l’insieme di associazioni, questo sono anche operazioni sui nomi.

- **Naming** Quando proprio viene creato un nuovo collegamento con un oggetto. (aka dichiarazione).
- **Unnaming** Quando il collegamento viene distrutto
- **Referencing** Quando viene utilizzato un nome per accedere a un oggetto (quindi nessuna creazione qui).
- **Attivazione binding** Quando il collegamento con un oggetto viene ricreato
- **Disattivazione binding**

### Operazioni sugli oggetti (4) 🟩

Queste operazioni sembrano le classiche che si fanno per i databases:

1. Accesso (sola lettura dell’oggetto)
2. Modifica (scrittura sull’oggetto)
3. Creazione
4. Eliminazione dell’oggetto.

Da notare la similitudine con il framework CRUD citato in [HTTP e REST](/notes/http-e-rest)

## Blocchi

### Definizione  🟨

> Un blocco testuale di codice, in cui sono dichiarate localmente delle variabili, che ha un inizio e una fine chiara.
>

In generale si fanno distinzione fra

1. Blocchi procedurali (come le funzioni in pratica)
2. Blocchi anonimi (sono blocchi in line che si possono mettere in qualunque posto del codice).

Però a volte è meglio creare delle regole specifiche del linguaggio che dipendano dal creatore del linguaggio. non vorremmo ad esempio poter utilizzare la variabile prima che fosse dichiarata. (ma dipende dalla pragmatica del linguaggio (oppure sintattica, dipende comunque da come è stato progettato questo linguaggio)).

e.g.

```cpp
{
a = 1;
int a;
}
```

Questo per molti linguaggi dovrebbe essere un errore, di **semantica statica**! ma a seconda delle regole sintattiche potrebbe essere corretto (potrebbe essere una a esterna, se esiste).

Un discorso simile si può fare per le funzioni, che possono essere visibili o meno prima della dichiarazione o meno. Ma non credo questi dettagli siano troppo importanti, dopo un pò capisci dai…

### Annidamento 🟩

L’annidamento dei blocchi deve soddisfare alcune caratteristiche, per esempio non possono esistere delle intersezioni parziali fra blocchi quindi che siano tipo ABAB (con primo A l’inizio del blocco, e secondo A la fine). In un certo senso la stringa che deve esserci deve essere palindroma.

### Visibilità 🟩

> Una dichiarazione locale ad un blocco è visibile in quel
blocco e in tutti i blocchi in esso annidati, a meno che non
intervenga in tali blocchi una nuova dichiarazione dello
stesso nome (che nasconde, o maschera, la precedente)
>

Questo principio di visibilità può essere espresso in maniere differenti, ecco così che si creano lo scoping statico e dinamico.

## Regola di Scope

La regola di visibilità non è definita in modo disambiguato, può essere interpretato in modo differente:

- Esempio

    <img src="/images/notes/image/universita/ex-notion/Nomi e Scope/Untitled.png" alt="image/universita/ex-notion/Nomi e Scope/Untitled">


A seconda di una interpretazione di Scoping, che è anche detta **regola di visibilità** che è qulel enunciata poco sopra, stampa risultati diversi. In questa parte proviamo a fare più chiarezza riguardo questo aspetto qui.

Per capire bene questa parte sullo scope sarebbe meglio andare a guardare come di solito è implementato, questo è spiegato in [Gestione della memoria](/notes/gestione-della-memoria)

### Statico (3) 🟩

3 Regole descrivono bene lo scoping statico

1. L’ambiente locale ha solamente in sé le dichiarazioni locali del blocco (direi che è una convenzione, poi col punto 2 ha più senso questo mini algo, che vai a cercarti te).
2. Se non viene trovato va a cercare nel blocco sopra, fino ad arrivare allo scope globale, se ancora qui non c’è allora vado nelle built-in, se nemmeno qui c’è allora errore (algoritmo stupido per fare la ricerca dell’associazione).
3. Per i blocchi con nome, il nome è anche presente nello scope sopra (così posso fare la ricorsione)

Da notare che nello scoping statico quello che importa è la **struttura del nostro programma**. Questo ci da alcuni vantaggi:

1. Facile comprensione (perché non dobbiamo eseguire, basta leggere il programma, capire la struttura e sappiamo il binding corretto)
2. Velocità (il compilatore si può tenere degli offset per capire quale è la variabile corretta a cui accedere).

Però per tenersi lo scoping statico è leggermente più difficile perché non basta una stack, come invece è per lo scope dinamico.

### Dinamico 🟩

Lo scope dinamico è molto più semplice da implementare rispetto lo scope statico, è guidato da questa unica regola.

> L’oggetto a cui si riferisce un nome X è quella dichiarata più recentemente a run-time, a patto che l’associazione sia ancora attiva.
>

Quindi se ci teniamo una stack di blocchi attivi (che poi vengono poppati, l’ultima ad essere poppata è il blocco globale, quello principale) è molto facile seguire il percorso creazione di tutte le variabili per un blocco, e distruzione quando si esce dal blocco.

Solitamente lo scope dinamico non viene mai utilizzato. (più lento e meno leggibile, bisognerebbe sempre leggere).

Ridefinizione di variabili globali per funzioni, questo si potrebbe considerare una possibilità dello scope dinamico di gestire input per variabili globali:

- Esempio in slide

    <img src="/images/notes/image/universita/ex-notion/Nomi e Scope/Untitled 1.png" alt="image/universita/ex-notion/Nomi e Scope/Untitled 1">


Il modo corretto per fare questa cosa è dichiarare la funzione in modo che accetti come parametro un altro colore.

# Registro ripassi

| 02/25/23 |  Sul blocco non ti ricordavi il dettaglio inizio e fine, resto mi sembra tutto perfetto |
| --- | --- |
| 11/03/23 | Tutto in modo perfetto. |
| 25/04/23 | Nessun problema direi. |

## Domande utili

### Sui nomi

- Cosa è un nome nel contesto dei linguaggi di programmazione come presentato da Gabrielli?
- Fai qualche esempio di più nomi che denotano uno stesso oggetto o più oggetti indicati da un singolo nome.
- Perché è utile avere il concetto dei nomi?
    - Abbozzo di answer

        Perché utilizzare nomi significa astrarre su alcuni concetti di livello più basso come l’indirizzo di memoria, oppure ci permette di avere una interfaccia che esegue un certo insieme di comandi (quindi più chiara al programmatore che lo utilizza).

- Fai alcuni esempi di oggetti denotabili
- Cosa è un binder?
- elenca e descrivi le 4 fasi in cui avvengono cose di bindings.

### Ambiente

- cosa è l’ambiente? dai la definizione in libro.

### Scopes
pi di oggetti denotabili
- Cosa è un binder?
- elenca e descrivi le 4 fasi in cui avvengono cose di bindings.

### Ambiente

- cosa è l’ambiente? dai la definizione in libro.

### Scopes