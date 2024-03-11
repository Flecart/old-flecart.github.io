---
layout: page
permalink: notes/spazi-di-probabilita
tags: italian
title: Spazi di probabilita
---

Ripasso Prox: 40
Ripasso: May 29, 2023
Ultima modifica: April 29, 2023 10:09 AM
Primo Abbozzo: June 5, 2022 3:43 PM
Stato: 🌕🌕🌕🌕🌕
Studi Personali: Yes

Questi sono appunti che mi faccio durante lo studio individuale estivo per probabilità e statistica.

# Introduzione

## La probabilità

## Termini

### Esito ed esperimenti aleatorio

**L’evento** è quello che accade, mentre un esperimento aleatorio qualcosa di cui vogliamo andare a misurare la probabilità diciamo.
**Esperimento aleatorio:** esperimento di cui non conosciamo il risultato con certezza.
**Esito**: risultato dell’esperimento aleatorio

### Spazio campionario ed evento

**Spazio campionatorio**
Lo spazio campionatorio è l'insieme di tutti gli stati possibili per una certa cosa da misurare (ossia di un esperimento aleatorio), gli stati sono talvolta anche chiamati *sample points* oppure *outcomes* in modo più semplice.

**Evento**
È un sottoinsieme dello spazio campionatorio. Se qualcosa della cosa che stiamo misurando è dentro questo sottoinsieme, all'ora diciamo che *l'evento è accaduto* altrimenti no.

NOTA: dato che stiamo parlando di sottoinsiemi, valgono tutte le operazioni di intersezione unione, complementare studiate durante [Teoria assiomatica degli insiemi](/notes/teoria-assiomatica-degli-insiemi).

Uno spazio di probabilità di solito è definito come $$\Omega, F, P$$, con F sigma algebra e P una misura di probabilità, ossia tale per cui $$P(\Omega) = 1,$$ è additiva, che descriviamo leggermente meglio in seguito.
Si può dire che $$P$$ sia una funzione dall'insieme delle parti di $$\Omega$$ ai reali in $$[0, 1]$$.

Una cosa particolare da osservare riguardo $$P$$ è che questa probabilità **non è osservabile**, non riusciamo ad osservare il fatto che il singolo evento abbia una certa probabilità, questa probabilità è qualcosa che nasce dopo un numero molto alto di trials che si susseguono per uno stesso processo stocastico.

### Assiomi sugli eventi

Vogliamo cercare di dire cosa è un evento su uno spazio campionatorio, possiamo dire che è un subset dell'insieme delle parti tali per cui:
1. se $$E$$ è un evento, anche $$E^{c} := \{x \in P(\Omega) : x \not\in E)$$ è un evento
2. L'unione infinita di eventi è un evento
3. $$\Omega$$ è un evento.

### Assiomi della probabilità

Questi assiomi si potrebbero giustificare in modo molto migliore partendo dalla teoria della misura, proverò a dire qualcosa partendo da quella nelle prossime sezioni.

Intanto enuncio qui in modo molto informale gli assiomi principali che abbiamo.

**Assioma 1**
La probabilità di qualunque evento è maggiore di 0

$$
\forall E \in \mathcal{P}(\Omega), \mathbb{P}(E) \in \mathbb{R}, \mathbb{P}(E) \geq 0
$$


**Assioma 2**
La probabilità dello spazio campionatorio è 1

$$
P(\Omega) = 1
$$


**Assioma 3**
la probabilità è additiva per insiemi disgiunti.

$$
\mathbb{P}(\cup_{i = 1}^{\infty}E_{i}) = \sum_{i=1}^{\infty}\mathbb{P}(E_{i})
$$


### Conseguenze principali degli assiomi (4)

**Valore dell’insieme vuoto**

Possiamo considerare una successione infinita di elementi vuoti, questi sono tutti disgiunti, e sono anche tutti uguali perché sono applicati sullo stesso insieme.

Se fosse diverso da 0 allora sarebbe infinito, ma deve essere compreso fra 0 e 1, quindi deve essere 0.

**Unione disgiunta finita**

Basta andare a considerare una successione con 0, questa è infinita, ma i vuoti non danno nessun contributo quindi vale ancora:


$$
\mu(\bigcup^n A_n) = \mu(\bigcup^\infty A_n) = \sum^\infty \mu(A_n) = \sum^n \mu(A_n) =
$$


**Valore dell’inverso**

deve essere che, basta considerare che $$\Omega = A_n \cup A_n^c$$ e l’unione disgiunta.


$$
\mu(A_n) = 1 - \mu(A_n^c)
$$


**Monotonia della probabilità**

Ossia se vale


$$
A \subset B  \implies \mu(A) \leq \mu (B)
$$


**Principio di inclusione esclusione**

<img src="/images/notes/Spazi di probabilità/Untitled.png" alt="Spazi di probabilità/Untitled">

### Probabilità uniforme 🟩

<img src="/images/notes/Spazi di probabilità/Untitled 1.png" alt="Spazi di probabilità/Untitled 1">

<img src="/images/notes/Spazi di probabilità/Untitled 2.png" alt="Spazi di probabilità/Untitled 2">

Il primo è vero perché


$$
\forall i, n \cdot P(w_i) = \sum_{i  =1}^n P(\omega_i) = P(\bigcup_{i = 1} ^n \omega_i) = P(\Omega) = 1  \implies \forall i, P(w_i) = 1/n
$$


L’altro è la **formula di laplace**, perché siano il numero di eventi di A, posso scriverlo come unione di quegli elementi, abbiamo detto che sono n, per questo riesco a ricostruire quel numero.

## Probabilità discreta

Se abbiamo una distribuzione di probabilità, cioè una probabilità definita su tutti gli elementi singoletto, allora possiamo avere una probabilità discreta, ossia probabilità ben definita che sia finito o numerabile.

### Definizione probabilità discreta 🟩

<img src="/images/notes/Spazi di probabilità/Untitled 3.png" alt="Spazi di probabilità/Untitled 3">

**Densità discreta**

<img src="/images/notes/Spazi di probabilità/Untitled 4.png" alt="Spazi di probabilità/Untitled 4">

Per 1.7 si intende che p deve essere compreso fra 0 e 1 e la somma per tutti gli elementi dello spazio campionario deve essere 1

<img src="/images/notes/Spazi di probabilità/Untitled 5.png" alt="Spazi di probabilità/Untitled 5">

### Caratterizzazione probabilità discrete 🟩

<img src="/images/notes/Spazi di probabilità/Untitled 6.png" alt="Spazi di probabilità/Untitled 6">

### Continuità della probabilità discreta 🟨+

<img src="/images/notes/Spazi di probabilità/Untitled 7.png" alt="Spazi di probabilità/Untitled 7">

- Dimostrazione

    <img src="/images/notes/Spazi di probabilità/Untitled 8.png" alt="Spazi di probabilità/Untitled 8">

    <img src="/images/notes/Spazi di probabilità/Untitled 9.png" alt="Spazi di probabilità/Untitled 9">


Ossia se ho uno spazio di probabilità allora posso avere delle caratteristiche (brutte secondo lollo) riguardo la continuità della funzione.

Anche se per questa parte che non utilizza teoria della misura questo teorema non è che sia molto utile.

Comunque per questa parte forse è meglio farlo dalla misura definita sulle algebre, che è fatta in maniera più generale e ho anche la sigma sub-additività all'interno, non so, forse più difficile??

## Impostazione classica della teoria della probabilità (non fare)

### Spazi di misura e di probabilità

Dico che ho uno **spazio misurabile** una coppia $$(\Omega, F)$$, tale che F sia un insieme di sottoinsiemi di omega, chiamato spazio campionario, e F insieme di eventi. Deve essere che F è una sigma algebra, ossia tali per cui siano chiusi per complementazione e per unione contabile.

Si parla di **spazio di misura** quando allo spazio misurabile associamo una funzione di misura.

Parliamo di **spazio di probabilità** se ho anche una funzione di misura tale per cui $$P(\Omega) = 1$$, . Si ricorda che la funzione di misura è tale se ha come codominio 0 to infty, e ha vuoto = 0, e che sia sigma additiva.

### Continuità dall’alto e dal basso.

Se ho che la funzione di misura sia finita, allora vale che $$A_n \uparrow A, \lim_{n \to \infty} \mu(A_n) = \mu (A)$$ , e che

$$\forall i, i < n, A_i \subseteq A_n$$

In modo simile è definito la continuità dal basso, solo che ora sono insiemi uno incluso l’altro. Attualmente non so cosa implichi questo fatto, né in che modo è utilizzata questa continuità… Forse per Borel Cantelli, ma poi non so cosa farmene di borel cantelli…

**Evento complementare**

**Sommatoria finita di eventi disgiunti**

**Principio di inclusione-esclusione** 🕳️