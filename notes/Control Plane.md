---
layout: page
permalink: notes/control-plane
tags: italian
title: Control Plane
---

### Tipologie di control plane

La control plane è la parte al livello di rete che si occupa di **riempire le tabelle di istradamento dei router**. In questo caso si possono in generare dividere gli algoritmi in due grandi famiglie

- **Centralizzati**, anche chiamati **algoritmi LS( Link state)** perché devono conoscere in che modo sono collegati i router fra di loro. Solitamente le **SDN** ossia software defined networking di cui abbiamo parlato in [Data Plane](/notes/data-plane) utilizzano questi metodi, c'è un server centralizzato (che per ragioni di tolleranza può anche essere distribuito, però diciamo che è esterno al router la decisione)
- **Distribuiti** in cui nessuno ha informazioni complete sulla rete, ma è possibile scambiarsi informazioni sui vicini e congiungere così al percorso più breve. Vengono in questa sede utilizzati algoritmi di **distance vector**.

Possono anche essere **statici**, ma dato che la topologia della rete è spesso dinamica è difficile che vengano utilizzati. Sono molto più preferibili gli algoritmi dinamici che vanno ogni tot ad aggiornare le tabelle.

Si possono anche differenziare secondo la **sensibilità al carico**. Anche se gli algoritmi moderni sono insensibili.

## Algoritmi per Control Plane

### Link state e Dijkstra

Questa è la parte più importante per il prof

Con grafo indiretto ad archi pesati. questo l'abbiamo già studiato in [Cammini](/notes/cammini), ad algoritmi, ed è stato fatto bene.

NOTA: ci potrebbero essere problemi di **oscillazione dei percorsi calcolati** se utilizziamo solamente il carico come unica metrica per misurare il peso di un nodo. Attualmente il metodo migliore per evitare questo è calcolare il percorso migliore in tempi randomici.

- Esempio di oscillazione dei percorsi

    <img src="/images/notes/image/universita/ex-notion/Control Plane/Untitled.png" alt="image/universita/ex-notion/Control Plane/Untitled">


### Distance vectors

- Non hanno visto Bellman ford e distance vector routing, però sarebbe carino farle
- TODO:

## Autonomous systems

### Definizione AS

Alcuni vorrebbero essere in grado di gestire un blocco di router come vogliono loro, ossia vogliono avere una *autonomia amministrativa* su un insieme di router. Possiamo quindi **dividere tutti i router in delle AS**, alcune grandi, di primo livello, più piccole, decide l’ISP in che modo gestirsele. (ad ogni AS è associato, sembra, un numero). La cosa importante però è che

- Tutti i router all'interno di una AS eseguono lo stesso protocollo di instradamento.

### Intra e inter routing

Algoritmi di routing a due livelli diversi (BGP Border Gateway protocol per inter, che non chiede, ma sa che esiste. e altri per Intra.)

Intra sono algoritmi di routing omogenei.

Inter in cui ci interessa solamente capire in che modo si interfaccia in altri sistemi.

In pratica non ha fatto niente di control plane…

### Open Shortest Path first (intra)

OSPF è un algoritmo link state che regola il routing all'interno di un sistema autonomo. Per il resto non ci importa sapere altro.

- Utilizza Dijkstra
- I pesi possono essere messi a mano seguendo certi criteri
    - Minimum hop (peso 1)
    - Inversamente proporzionale alla banda (quindi favorire l’utilizzo di connessioni di banda maggiori)
- Supportano un protocollo a livello IP per scambiarsi informazioni sulla congestione (ogni 30 min tipo)
- Supportano protocolli per la sicurezza e l’autenticazione (così possono ripudiare altri router che non possiedano la chiave di sicurezza).

## Border Gateway Protocol (!)

### Introduzione al protocollo BGP

Border Gateway Protocol è uno dei protocolli più importanti insieme a IP. È il protocollo che ci permette di comunicare fra AS divers, si può dire infatti che sia un protocollo **inter-AS** per questo motivo.

Ha due funzioni principali:
- Annunciare che un host o un router è raggiungibile a tutti gli AS
- Trovare il percorso più veloce per raggiungere quell’host

In generale qui vengono utilizzati algoritmi Distance Vector decentralizzati sui singoli AS.

Per far questo in generale ci teniamo una coppia (**prefisso, interfaccia**) ossia il prefisso contiene un range di indirizzi, e interfaccia è l’interfaccia del router che possiede quei prefissi.

### Annuncio presenza

In questa fase facciamo distinzione ai messaggi **eBGP** annunci di messaggi fra router di AS diversi fra di loro e di **iBGP** annunci fra router degli stessi AS.

Per dare l’intuizione generale, quando un nuovo router si connette, manda un messaggio iBGP a tutti i router dell’AS, quando il messaggio viene a un **router gateway,** così chiamati i router che hanno connessioni con AS diverse, questa manda una **eBGP** al router dell’altro BGP, con informazioni sulla presenza di x e di come raggiungere x, il processo di ripete finché non è stato recepito da tutte le AS.

### Ricerca del percorso più breve (2)

Ricordiamo prima che le rotte sono delle coppie (”percorso fra sistemi autonomi”, primo router fuori dall'AS attuale).

Una volta che un sistema autonomo è a conoscenza di tutte le rotte verso un certo router può utilizzare questi due algoritmi:

- Hot potato
    - Quando provo a **uscire più in fretta possibile dall'AS attuale**. Sfruttando protocolli di intra-routing per sapere dove andare.
- Selezione delle rotte
    - Ho delle regole da seguire che eliminano tutte le rotte fino ad avere una singola
    1. Preferenza locale (impostata manualmente da un operatore solitamente)
    2. Numero minimo di hop
    3. minimo costo di intra routing.
    4. Identificatori BGP (che non trattiamo)

    Quindi uno dopo l’altro utilizzo quelle per discriminare le routes e scegliere, quindi al passo 2 saranno rimaste tutte le routes con stessa preferenza locale, al numero 3 ho tutte le routes con stesso numero di hops, al passo 4 ho tutte le routes con stessa preferenza locale, stesso numero di hops, e stesso costo interno.