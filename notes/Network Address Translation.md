---
layout: page
permalink: notes/network-address-translation
tags: italian
title: Network Address Translation
---

Ripasso Prox: 60
Ripasso: July 12, 2023
Ultima modifica: May 13, 2023 11:33 PM
Primo Abbozzo: December 13, 2022 10:36 AM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: No

# Elementi di ripasso

# NAT Network address translation

## Introduzione

Col il NAT possiamo avere tutto lo spazio degli IP di cui abbiamo bisogno, che però non sono esposti. All'esterno vengono esposte solamente l’IP del NAT.

- Schema classico NAT

    <img src="/images/notes/image/universita/ex-notion/Network Address Translation/Untitled.png" alt="image/universita/ex-notion/Network Address Translation/Untitled">


Quindi in breve

**All'esterno è esposto solamente l'indirizzo del router**, il router, a seconda della porta giusta, dà in risposta al computer giusto, quindi all'interno della nostra rete conosciamo tutti gli indirizzi IP giusti.

### Addr translation table 🟩

Sembra che ad ogni richiesta ci sia una table di transizione all'interno del router che matcha porta → indirizzo locale corretto!.

### Esempio funzionamento 🟩

- Slide

    <img src="/images/notes/image/universita/ex-notion/Network Address Translation/Untitled 1.png" alt="image/universita/ex-notion/Network Address Translation/Untitled 1">

1. Un client locale fa una richiesta esterna, viene inviato al router
2. Il router salva la porta all’IP interno e invia fuori
3. Il server fuori ritorna la risposta alla porta corretta del router
4. Il router manda questa risposta al client con l'indirizzo corrispondente  a quella porta

### Controversie NAT (3) 🟨+

- Slide

    <img src="/images/notes/image/universita/ex-notion/Network Address Translation/Untitled 2.png" alt="image/universita/ex-notion/Network Address Translation/Untitled 2">


il router dovrebbero lavorare solamente sul livello 3 (IP), qui sta andando anche livello trasporto, per capire come mandare (infatti ha bisogno di un **socket** spiegato in [Socket (!!!) 🟩](/notes/socket-(!!!)-🟩)), dato che ha bisogno anche del livello di porta).

L’obiettivo di avere più indirizzi Ip non dovrebbe essere risolto con questa sorta di hack, dovrebbe essere risolto con IPv6 utilizzare il NAT sembra una specie di Hack.

Inoltre tutte le richieste devono passare da questo router e manipolate per poter accedere alla rete dietro il NAT, **non abbiamo il pretesto per parlare di end-to-end**. (il prof. parla di lato porcherie (dietro il nat) e il lato bello che è il fuori, e il router sembra quasi l’ambiente di cambio vestiti, in modo che tutti si possano comprendere, lol).

Una cosa molto brutta è fare NAT di NAT. Dall'altra parte i NAT sembrano un modo per isolare computer di cui non mi fido (che conoscono **un falso IP proprio** che non è raggiungibile esternamente.).

# Registro ripassi

| 21/12/22 | Decente. |
| --- | --- |
| 27/01/23 | Non mi ricordavo esattamente delle controversie del NAT |
| 02/03/23 | Anche qui le contro verse non me le ricordo, ma sul funzionamento del NAT mi sembra molto ok |
| 01/04/23 | Bruh, lo ho guardato e mi sono detto chissene frega lol. |
| 12/05/23 | Troppe volte, sembr asemplice salto. |
erse non me le ricordo, ma sul funzionamento del NAT mi sembra molto ok |
| 01/04/23 | Bruh, lo ho guardato e mi sono detto chissene frega lol. |
| 12/05/23 | Troppe volte, sembr asemplice salto. |