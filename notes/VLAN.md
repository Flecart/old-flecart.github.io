---
layout: page
permalink: notes/vlan
tags: italian
title: VLAN
---

Ultima modifica: May 17, 2023 3:14 PM
Primo Abbozzo: May 17, 2023 1:48 PM
Studi Personali: No

# Elementi di ripasso

# VLAN

## Introduzione

Quando abbiamo una switch, ma vogliamo allo stesso momento andare a creare più LAN, allora abbiamo bisogno delle VLAN. Questi switch che hanno delle VLAN si chiamano **managed switches**

Queste vlan sono numerate (ricorda l’espericomento cn LUCA!).

### Il problema

Sono un protocollo livello 2 (Link-Layer, di collegamento), non vorremmo per esempio che un broadcast di una certa rete vada anche in altre reti che non centrino praticamente nulla, come possiamo vedere in figura.

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled.png" alt="image/universita/ex-notion/VLAN/Untitled">

Esempio problema di vlan

### Implementazione: porte

Posso andare a raggruppare alcune porte come se fossero in una unica network separata rispetto al resto. Posso andare a numerare certe porte e proprio andare a taggarli come se sono parte di una altra rete.

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 1.png" alt="image/universita/ex-notion/VLAN/Untitled 1">

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 2.png" alt="image/universita/ex-notion/VLAN/Untitled 2">

Si noti che per comincare fra VLAN in switches diverse, bisogna che il pacchetto possieda **informazioni riguardo la VLAN** in modo che quando viene ricevuto venga correttamente interpretato essere nell vlan corretta.

### Vantaggi delle VLAN (3)

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 3.png" alt="image/universita/ex-notion/VLAN/Untitled 3">

### Formato pacchetto VLAN

È una estensione del pacchetto livello MAC classico con informazioni riguardo le vlan

1. Preable: sincronizzare chi trasmette e chi riceve
2. Dest e source sono gli stessi classici livello 2, quindi con MAC.
3.

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 4.png" alt="image/universita/ex-notion/VLAN/Untitled 4">

### Multiprotocol Layer switching MPLS

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 5.png" alt="image/universita/ex-notion/VLAN/Untitled 5">

<img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 6.png" alt="image/universita/ex-notion/VLAN/Untitled 6">

- Esempio

    <img src="/images/notes/image/universita/ex-notion/VLAN/Untitled 7.png" alt="image/universita/ex-notion/VLAN/Untitled 7">


## Data center networks

### Load balancers

Cerca di equalizzare il carico di lavoro di tutti.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |
/Untitled 7.png]]


## Data center networks

### Load balancers

Cerca di equalizzare il carico di lavoro di tutti.

# Registro ripassi

|  |  |
| --- | --- |
|  |  |
|  |  |