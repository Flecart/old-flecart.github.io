---
layout: page
permalink: notes/la-qualità-del-software
tags: italian
title: La qualità del software
---

Dato che il software sta diventando sempre più diffuso, diventa sempre più importante andare a definire delle metriche che possano garantirne la qualità, ossia la non frequenza di errori o bug che possono in qualche modo limitarne la qualità.

#### Error, Fault and Failure

Secondo la definizione esatta data da IEEE, questi tre termini hanno un significato ben specifico, molto diverso.

1. Error, sono comportamenti non previsti da un comportamento dell'utente, oppure il programmatore capisce male le specifiche.
2. Fault sono i bugs, degli errori nel codice che creano un comportamento non previsto
3. Failure, sono comportamenti non previsti da specifiche, che crea un **guasto** e non permette il funzionamento

### Qualità del software
#### Rating and Ranking
Il rating è l'assegnazione di un punteggio assoluto di qualità riguardo al prodotto.

Ranking è comparazione fra un prodotto rispetto all'altro per 

#### Condizioni necessarie (4)
<img src="/images/notes/La qualità del software-1701337359613.jpeg" alt="La qualità del software-1701337359613">


#### Qualità interna ed esterna

<img src="/images/notes/La qualità del software-1701337671439.jpeg" alt="La qualità del software-1701337671439">

Ci sono quei principi utili possono essere categorizzati in attributi
- operativi
- di manutenzione (modificabilità)
- adattabilità, ossia se il software può essere usato in ambienti diversi.

### Goal Question Metric
#### Principi di qualità (3)
1. Gli obiettivi del prodotto devono essere chiare
2. Metriche di qualità per sapere cosa esattamente andare a misurare
3. Le domande per vedere se un certo obiettivo è stato raggiunto, da quanto ho capito è un check midpoint per avere feedback, nello stesso modo per cui fatto in [Modelli AGILE](/notes/modelli-agile)

#### Tre livelli di analisi
- **Obiettivi** 
- **Domande**
- **Metriche per valutare domande**

Esempio:
<img src="/images/notes/La qualità del software-1701337045237.jpeg" alt="La qualità del software-1701337045237">

#### Verifica e validazione

Verifica = quanto viene implementato bene la specifica, che è anche ciò che deve essere testato in automatico o manualmente. a seconda del formato può essere **ispezione** (manuale) o **testing**. 

Validazione = accettazione da parte del cliente.

#### Aspetti da testare

Una idea molto presente in questo è la **copertura** ossia il programma dovrebbe funzionare a seconda del branch, dei moduli, in questo senso dovrebbe esserci una copertura più ampia possibile.


#### Black and white box testing
Il primo quando non si ha accesso al codice sorgente, ma si testa solametne la **specifica** come può essere una user story

White box quando abbiamo visibilità sul sorgente (ad esempio match diretto sul codice di ritorno, o fare i mocks).

#### Complessità ciclomatica di McCabe
Cerca di calcolare quanto sia affidabile un software, ed è fatto sul diagramma di flusso.
cc si calcola come

$$
cc(G) = e - n + 2 \cdot G
$$

G sono sottografi sconnessi.
$$e$$ sono gli archi, $$n$$ sono i nodi. così viene definito un valore di complessità ciclomatico, e ci dice il numero di test che bisogna avere per essere abbastanza sicuri.

E il diagramma di fllusso è calcolabile, quindi si può sempre fare, come rule of thumb se la complessità è alta, il rischio è alto.

### Manutenzione del software

#### Tipologie di correzione (3)
- Perfettiva
	- Per migliorare, ci sono **nuove funzionalità** tipo 1/2 sono questi
- Correttiva, circa 1/4 dei cambi.
- Adattiva
	- Per ambiente che cambia

Esiste anche uno standard IEEE per gestire questo cambiamento.


#### I costi nella manutenzione
- Personale instabile
- Progettisti non responsabili (bisogna rendere i progettisti)
- Inesperienza dei progettisti
- Il software vecchio.
## Note di ripasso

| Data | Commenti |
| ---- | -------- |
|      |          |