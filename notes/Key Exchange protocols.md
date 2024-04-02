---
layout: page
permalink: notes/key-exchange-protocols
tags: italian
title: Key Exchange protocols
---

Metodi di key exchange
- Trusted Key parties (sono come Certificate authorities studiati in [Sicurezza delle reti](/notes/sicurezza-delle-reti))
- Merkle Puzzles
- DH protocol

## Trusted Third parties

### Squared Key problem


Un problema abbastanza ovvio è che per storare le chiavi di tutti c'è una necessità $$O(n^{2})$$ on $$O(n)$$ users
Se c'è un trusted key parties il numero delle chiavi si riduce di molto, ritorna ad essere lineare!


### Protocols

#### Toy Exchange protocol 🟩
TTP = Trusted Third party (simile a quanto poi si avrà in [Asymmetric Cryptography](/notes/asymmetric-cryptography))
<img src="/images/notes/Key Exchange protocols-20240312110014411.webp" alt="Key Exchange protocols-20240312110014411">

Questa è la base del servizio di Kerberos!
Il servizio di sopra è sicuro su Choosen Plaintext, dato che Eve non capisce niente senza le chiavi!

## Merkle Puzzles
vogliamo cercare di risolvere problemi di origliamento (eavesdrop, senza modifiche varie sul messaggio. **Avversario passivo**.
Vogliamo farlo senza avere un [#Trusted Third parties](#trusted-third-parties).
#### Un Puzzle 🟨--
Prendiamo una stringa lunga 32, e la cifriamo con una chiave Scelta da noi. Questo è il puzzle, l'avversario ha la chiave, ma riceve tutti e $$2^{32}$$ messaggi per poter avere la chiave corretta.
Vedere slides.

Il primo crea un puzzle, il secondo risolve un puzzle a caso e manda la coppia $$x, k$$ che ha trovato, mentre l'attaccante non sa quale sia la coppia che ha risolto, e dovrebbe farlo a caso.

## Diffie-Hellman Protocol

### Introduzione DH 🟩
Questo è quello che abbiamo studiato anche a Olycyber quindi è più facile. È basato su una costruzione matematica molto simile a RSA.

In pratica così
1. Scelgo $$p$$ primo largo
2. Scelg $$g$$
3. Alice sceglie $$a$$, e manda $$g^{a}$$ a Bob
4. Bob fa lo stesso con $$b$$
5. Il segreto è $$g^{ab}$$ , che è difficile da capire con i moduli...

#### Attacco a DH 🟩
DH è insicuro dal punto di vista del **Man in the middle**. Perché se uno in mezzo intercetta, può usare la sua chiave privata al posto di quella dell'altro interlocutore. Tanto conosce il valore di $$g$$ e gli basta questo.
<img src="/images/notes/Key Exchange protocols-20240314093203133.webp" alt="Key Exchange protocols-20240314093203133">