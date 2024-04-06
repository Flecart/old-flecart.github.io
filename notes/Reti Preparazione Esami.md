---
layout: page
permalink: notes/reti-preparazione-esami
tags: en
title: Reti Preparazione Esami
---

Ultima modifica: May 1, 2023 10:37 AM
Primo Abbozzo: April 30, 2023 5:06 PM
Studi Personali: No

# Elementi di ripasso

# 2022-06-10

## Es 3 (sicurezza)

### Testo

[15] Alice spedisce a Bob un messaggio **M1 molto grande** con la sola
garanzia di non ripudiabilità (ovvero Alice non potrà mai dimostrare di
avere spedito un messaggio diverso da quello ricevuto da Bob), ma non
serve privacy (tutti possono leggere M1). Bob in seguito risponde ad
Alice con un messaggio **m2 molto piccolo** del quale deve essere però
data **garanzia di mittente** (solo Bob può averlo spedito), **di privacy**
(nessuno oltre ad Alice può leggerlo) e **non Replay** (ovvero Alice deve
accettarlo una volta sola da Bob).
Come può essere realizzato lo schema di cifratura di costo minimo (minimo
calcolo e massima efficienza) che garantisca tutti e solo i requisiti richiesti?
Spiegare.

### Soluzione proposta

Supponiamo di avere un sistema di cifratura a chiavi pubblica per Bob ha chiavi pubbliche presenti in CA (per evitare Man in the middle).

Per garantire la non ripudiabilità del messaggio grande di Alice, alice vuole firmare con la propria chiave privata il messaggio molto grande che si vuole mandare, ma non può cifrare il messaggio intero perché è grande, quindi calcola l’hash del messaggio, insieme a questo manda anche una Nonce, questo servirà per favorire il non replay.

Allo stesso tempo se Eve Conoscesse sia il messaggio sia l’hash sarebbe troppo semplice provare a fare tampering del messaggio, per questo motivo Alice oltre semplicemente a mandare l’hash crea una chiave simmetrica, cifra l’hash del messaggio e la nonce con questa chiave simmetrica, cifra la chiave simmetrica con la chiave pubblica di Bob presa da un CA, e manda questo pacchetto:

1. Messaggio in chiaro
2. Cifratura_pubblica_generata(H_A- (hash(messaggio)) + Nonce)
3. Cifratura con chiave_bob_ca(chiave_pubblica).

**QUESTA SOLUZIONE È ERRATA PERCHÉ NON SERVE CHIAVE PUBBLICA, DATO CHE BASTA NON RIPUDIABILITÀ!**

In quanto bob deve spedire un messaggio molto piccolo, gli basta direttamente creare $$H_B^- (Message)$$, per avere la garanzia del mittente, per privacy può cifrare tutto con la chiave simmetrica ricevuta da alice, e per non replay insieme al messaggio mette la nonce.

Verifica intanto con hash e chiave pubblica di alice presa da CA che sia stata effettivamente alice e che abbia scritto quel messaggio (due condizioni necessarie per non ripudiabilità)

E manda un pacchetto

1. $$H_S(H_B^-(Message) + Nonce)$$

Alice decifrerà con la chiave simmetrica generata da lei e la chiave pubblica presa da CA, verificherà che la Nonce effettivamente corrisiponde a quella mandata da lei, e decifrererà il messaggio.

## Es 7 wifi

### Testo

<img src="/images/notes/image/universita/ex-notion/Reti Preparazione Esami/Untitled.png" alt="image/universita/ex-notion/Reti Preparazione Esami/Untitled">

<img src="/images/notes/image/universita/ex-notion/Reti Preparazione Esami/Untitled 1.png" alt="image/universita/ex-notion/Reti Preparazione Esami/Untitled 1">

### Soluzione proposta

Se abbiamo un fade margin di 10 o 20 anche in periodi di nebbia dovremmo comunicare correttamente, quindi obiettivo buono sarebbe avere una RF che raggiunga il ricevitore a -82dBm.

Allora, calcoliamo la caduat di segnale pari alla distanza:

36.6  + 20 * log(1900) + 20 * log(5) = 116 decibel.

// Trova l’errore qui sotto (c’è un errore che direi che sia abbastanza greve (ed è anche stupido) e poi altro errore stupido nella conversione 😀

Quindi deve essere x - 116 + 7+ 7 + 97 = 15 ⇒ x = 102 + 97 = 102 + 97 = 199 dBm = 199 mW.

Si è possibile se la zona di fresnel resta libera, perderei circa 6dB di potenza (pari a una caduta del segnale di 4 volte , ma riuscirebbe a ricevere ugualmente)

Dalla formula il 100 per cento della zona di fresnel è

72.2 * sqrt(5 / 4 * 1.9) = 58.56 feet = 58.56 * 30.5 cm = 1786 cm = 17.86 metri.

## Es 8 (wifi)

### Testo

<img src="/images/notes/image/universita/ex-notion/Reti Preparazione Esami/Untitled 2.png" alt="image/universita/ex-notion/Reti Preparazione Esami/Untitled 2">

<img src="/images/notes/image/universita/ex-notion/Reti Preparazione Esami/Untitled 3.png" alt="image/universita/ex-notion/Reti Preparazione Esami/Untitled 3">

### Soluzione proposta (sembra completamente sbagliata)

1. Non ha senso parlare di anticipo o ritardo di fase, si può dire che la differenza di fase sia 90 gradi.

Non ha senso parlare di anticipo o ritardo perché il segnale potrebbe essere visto come in anticipo di 90 gradi e allo stesso tempo ritardo di 270, come il contrario. Non ho abbastanza informazioni per dire se è in anticipo o ritardo di 90, ma è uno dei due casi.

Una differenza di fase di 180 sarebbe distruttiva, di 0 sarebbe costruttiva, quindi ne sì ne nò perché è a metà.

La buona comunicazione dipende anche dalla sensibilità del ricevitore oltre alla potenza del segnale iniziale, possiamo calcolare quanta energia sia arrivata al ricevitore:

<img src="/images/notes/image/universita/ex-notion/Reti Preparazione Esami/Untitled 4.png" alt="image/universita/ex-notion/Reti Preparazione Esami/Untitled 4">

Ricordiamo che F è in Megaherz e D in miglia

Loss = 36.6 * (20 * log_10(37.5)) + (20 * log_10(29 * 0.000621371)) = maggiore di 1000, non credo che il segnale arriverà mai con quella frequenza. quindi nessuna delle precedenti.



# References