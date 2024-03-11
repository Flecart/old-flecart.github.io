---
layout: page
permalink: notes/problemi-di-accoppiamento
tags: italian
title: Problemi di accoppiamento
---

Ripasso Prox: 12
Ripasso: January 4, 2023
Ultima modifica: December 30, 2022 12:31 PM
Primo Abbozzo: November 23, 2022 4:26 PM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

# Problemi di accoppiamento

## Introduzione (defs)

### Grafo bipartito 🟩

Un grafo bipartito è un insieme $$(O \cup D), (A)$$ di nodi e di archi. Tutti i nodi sono o fra i nodi di origine oppure fra i nodi di destinazione, e gli archi sono solamente collegati fra nodi di origine e nodi di destinazione.

### Accoppiamenti (lessico) 🟩

Consideriamo $$M$$ archi che non abbiano nodi in comune, vogliamo cercare in questo senso di fare un accoppiamento fra i nodi di origine e i nodi di destinazione.

diciamo **accoppiamento perfetto** se tutti i nodi sono stati accoppiati

**Arco di bottleneck** è l'arco di costo massimo, che si dice **costo di bottleneck**.

## Accoppiamento di massima cardinalita

### Trasformazione del problema 🟩

Vogliamo cercare di utilizzare gli algoritmi noti sui flussi di costo minimo e flusso massimo, algo di flusso massimo. In questo caso se giriamo il problema in modo opportuno possiamo renderlo un problema di flusso massimo

1. Creo nuovo nodo fittizzio di origine e destinazione, in modo simile a quanto fatto in precedenza in [Reti di flusso](/notes/reti-di-flusso)
2. Capacità degli archi sono tutti 1, se c'è flusso lo prendo, altrimenti no. (in questo senso i flussi devono essere interi!

### Osservazioni sulla tipologia di path 🟩

La path che viene in questo modo creata dovrà essere per forza **alternanti**, che vanno a rimbalzare fra i nodi interni!

Ricorda cosa sono gli archi interni e gli archi estermi.

Dato un insieme $$M$$ di tutti gli archi del nostro grafo bipartito che andiamo a prendere, consideriamo archi interni questi, ed archi estermi l'insieme $$P - M$$, con P tutti gli archi.

Chiaramente devo passare dalla sorgente alla destinazione, e lo posso fare solamente una volta per ecco che si può dire che


$$
|P_e| - |P_i| = 1
$$


con Pe l'insieme degli archi esterni che prendo e Pi l’insieme degli archi interni che vado a prendere, vado poi solamente a considerare la cardinalità di questo robo.

Questa osservazione è importante per poter mettere in relazione molto stretta il fatto che **i cammini aumentanti ↔ cammini alternanti con quella proprietà**, perché in questo modo il cammino alternante inizia e finisce in un nodo esterno, cioè un nodo che non è mai stato utilizzato per l’accoppiamento.

## Accoppiamento di costo minimo

Possiamo utilizzare gli algoritmi di MCMF per risolvere questo problema qui!

Importante notare che **gli accoppiamenti devono essere perfetti**, ossia non ho nessun nodo libero.

### Accoppiamento di minimo bottleneck

Anche qui deve esere fra **tutti gli accopiamenti perfetti**.

In questo caso si cerca di avere il minimo arco maggiore possibile, non per forza il minimo di costo.