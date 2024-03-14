---
layout: page
permalink: notes/gruppi
tags: italian
title: Gruppi
---

Ripasso Prox: 15
Ripasso: July 1, 2022
Ultima modifica: July 7, 2022 4:00 PM
Primo Abbozzo: March 20, 2022 3:44 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No


## Definizione gruppo
Qualunque insieme più operazione tale per cui:
1. Esistenza dell'inverso per ogni elemento
2. Esistenza di un elemento neutro
3. Associatività.

### Unicità dell’elemento neutro
Supponiamo di avere un gruppo $$G$$ e due elementi neutri $$e, f$$
Allora abbiamo che
$$ae = a = af$$ però se moltiplichiamo per l'inversa abbiamo che
$$a^{-1}ae = a^{-1}af \implies e = f$$

### Unicità dell’inverso
Supponiamo di avere un gruppo $$G$$ e due elementi inversi per ogni $$a \in G$$
Sia $$a$$ un elemento e gli inversi $$a_{1}$$ e $$a_{2}$$, allora abbiamo:
$$aa_{1} = e = aa_{2}$$ ma se moltiplico a sinistra per l'inversa abbiamo

$$a_{1}aa_{1} = a_{1}aa_{2} \implies ea_{1} = ea_{2} \implies a_{1} = a_{2}$$
Dove abbiamo utilizzato anche l'associatività.

### Proprietà di cancellazione

<img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled.png" alt="image/universita/ex-notion/Gruppi/Untitled">
È ovvio se moltiplichiamo per le cose giuste.

### L’inverso del prodotto

Enunciato:
$$(ab)^{-1} = b^{-1}a^{-1}$$ e per gruppi abeliani abbiamo $$(ab)^{-1} = a^{-1}b^{-1}$$

La dimostrazione è molto semplice ed è lasciato al visitatore :D

## Test per gruppo

### Ordine di gruppo e di elemento

L'ordine di un gruppo è **la cardinalità dell'insieme**,
L'ordine dell'elemento del gruppo è **la potenza a cui si eleva questo elemento per avere il neutro**

### Test unico per il sotto-gruppo


$$
\forall a,b \in H ,H \subseteq G, ab^{-1} \in H \implies H \text{ is a subgroup of G}
$$

Se vale questa proprietà possiamo già avere un sottogruppo! Quindi è abbastanza comodo!

Dimostrazione:
1. Associatività si ha per $$G$$.
2. Se prendo $$a, a$$ come la coppia abbiamo che $$aa^{-1}=e$$ appartiene a $$H$$, quindi c'è l'elemento neutro.
3. Se prendo $$e, a$$ vedo che $$a^{-1} \in H$$.

Quindi abbiamo che vale.

### Test doppio per il gruppo

Mostrare che sia chiuso rispetto all'operazione e ci sia sempre l'inverso. Questo in pratica va per la [#Definizione gruppo](#definizione-gruppo) come espresso sopra!

### Test per gruppi finiti

Mostrare solamente che sia chiuso per l'operazione (nella dimostrazione di deve mostrare che è chiuso per l'inverso, cosa che si va per il terzo escluso

## Sottogruppi

### Sottogruppi generati da un elemento (ciclico)

<img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled 1.png" alt="image/universita/ex-notion/Gruppi/Untitled 1">

- Dimostrazione
    <img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled 2.png" alt="image/universita/ex-notion/Gruppi/Untitled 2">


**Osservazione:**

Ogni sottogruppo generato in questo modo è abeliano, perché è in isomorfismo con il gruppo additivo Z (si vedrà dopo di questo isomorfismo)

### Il centro di un gruppo è un sottogruppo

<img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled 3.png" alt="image/universita/ex-notion/Gruppi/Untitled 3">

- Dimostrazione enunciato in h3

    <img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled 4.png" alt="image/universita/ex-notion/Gruppi/Untitled 4">

- Esempio: centro di gruppi diedrali

    <img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled 5.png" alt="image/universita/ex-notion/Gruppi/Untitled 5">


### Centralizzatore di un gruppo è un sottogruppo

<img src="/images/notes/image/universita/ex-notion/Gruppi/Untitled 6.png" alt="image/universita/ex-notion/Gruppi/Untitled 6">

Osservazione: quando il centralizzatore è l'intero gruppo, l'elemento su cui stiamo centralizzando è esattamente il centro.

- Dimostrazione
    Analoga alla precedente del centro