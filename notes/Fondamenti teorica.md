---
layout: page
permalink: notes/fondamenti-teorica
tags: en
title: Fondamenti teorica
---

Ripasso Prox: 40
Ripasso: May 30, 2023
Ultima modifica: June 9, 2023 2:56 PM
Primo Abbozzo: December 10, 2022 11:39 AM
Stato: 🌕🌕🌕🌗🌑
Studi Personali: No

# Elementi di ripasso
<img src="/images/notes/image/universita/ex-notion/Fondamenti teorica/Untitled.png" alt="image/universita/ex-notion/Fondamenti teorica/Untitled">


# Elementi di computabilità

[https://virtuale.unibo.it/pluginfile.php/1295166/mod_resource/content/0/Lez18-Gorrieri.pdf](https://virtuale.unibo.it/pluginfile.php/1295166/mod_resource/content/0/Lez18-Gorrieri.pdf)

## Halting problem

Questo asserisce che **non esiste nessun programma che sia in grado di decidere la terminazione di un altro programma**

Questo è un problema che ci è interessante perché vorremmo costruire un compilatore che  sia in grado di osservare **tutti gli errori possibili** del programma. Come vedremo tra poco la risposta sarà negativa.

### Dimostrazione tesi 🟨++

Supponiamo che questo programma esista, lo chiamiamo `check(P)` che restituisce 0 se termina 1 se non termina, allora devo poter essere in grado di scrivere un programma di questo genere

```jsx
process ABSURD(x):

if (check(ABSURD(x))):
	return 0;
else:
	while (true);

endprocess
```

Allora se il processo ABSURD con x in input termina, si avrà che non termina e vale anche il contrario. E questo è un chiarissimo assurdo. In questo modo **troviamo una funzione non calcolabile** ed è stato uno dei primi episodi storici di non calcolabilità (Turing 1936) in quello storico paper.

<img src="/images/notes/image/universita/ex-notion/Fondamenti teorica/Untitled 1.png" alt="image/universita/ex-notion/Fondamenti teorica/Untitled 1">


> NOTA: questa sezione non è molto formale, è utile però per dare l’intuizione, per andare in modo formale è bene andare a guardarsi le slide del prof (c’è un errore di input di funzioni).
>

### Non calcolabilità dell’eguaglianza 🟥+

Si può dimostrare che **non esiste un programma che decida se due programmi calcolano la stessa cosa**, altrimenti ci potremmo ricondurre a un caso molto simile a quello di sopra.

**Dimostrazione**

Se esistesse tale funzione, potrei costruire la funzione che decide se quanto calcolato è uguale alla funzione costante 0. Se ho questa funzione allora posso costruire una funzione

F(P) che prende in input una funzione e un dato, e calcola 0 se converge, e diverge con essa se diverge. Con questa funzione posso costruire la funzione check perché se converge posso dire con sicurezza che è 1, e se diverge posso dire che è 0

### Costruzioni del prof. (3) 🟨++

**Assurdo che esista un programma che mi dica se un programma si stoppi o meno**

Questa sezione è utile se vuoi ripetere quello che dice il prof.


$$
H(P,x) =
\begin{cases}
1\, P(x)\downarrow \\
0 \, P(x) \uparrow
 \end{cases}
$$



$$
K(P) = H(P,P)
$$



$$
G(P) = \begin{cases}
1\, K(P) = 0 \\
\uparrow, K(P) = 1
\end{cases}
$$


Ma se proviamo a calcolare $$G(G)$$ vediamo che se $$G(G)$$, che è quello che va a calcolare K, termina, allora non terminerà, per come ho costruito G, se non terminerà allora termina per come ho costruito G.

**Nessun programma mi può dire se una funzione calcola una costante o meno** 🟥


$$
Z(P) =
\begin{cases}
1, \forall x, P(x) = 0 \\
0, \exists x, P(x) \neq 0
 \end{cases} \\
F(P,x) = \begin{cases}
0, P(x) \downarrow \\
\uparrow, P(x) \uparrow
\end{cases}
$$


Si noti che entrambe le funzioni di sopra sono calcolabili, allora se vale questo vale che


$$
K(P) = H(P, P) = Z(F(P,P))
$$


Il trucco non sta altro che sfruttare il fatto che Z termina lo stesso anche se una funzione può divergere talvolta, senza restituire qualcosa (allora so che non darà mai la costante), ma se funzione normalmente fa sempre 0.

**Nessun programma può dire che due programmi sono equivalenti**


$$
Equiv(P, Q) =
\begin{cases}
1, \forall x, P(x) = Q(x) \vee P(x) = \uparrow = Q(x) \\
0, \text{altrimenti}
 \end{cases} \\
Z(P) = Equiv(P, zero)
$$


E quindi avrei una funzione che calcoli se una funzione è 0.

## Decidibilità
Vedere [La macchina di Turing#Problemi di decisione](/notes/la-macchina-di-turing#problemi-di-decisione) per definizione più adatta e corrente.

### Introduzione 🟨+

**Decidibilità (2)**

Dati certi input, devo rispondere con 1 o 0 in tempo finito, questo è l’unico output che posso dare. Un esempio di problema di decidibilità è dire se appartiene o meno a un certo insieme.

Un problema che non è decidibile è indecidibile.

**Semidecibilità**

Quando in tempo finito riesce a dirmi 1, ma per dire 0 diverge. Un esempio di programma con questa proprietà è la funzione check che stavamo sviluppando prima, che dice 1 se converge e 0 se non converge.

Notare che il caso contrario, quello che per 1 diverge, e per 0 converge, non è semidecidibile (il problema della divergenza non è semidecidibile).

### Esempi di problemi indecibili ! (5)

1. Se la funzione calcola una costante
2. Se la funzione termina
3. Se la funzione diverge (il suo contrario)
4. Se due programmi sono equivalenti
5. Se esistono errori run-time del programma

## La macchina di turing

### Introduzione (6) 🟩

Una macchina di turing può essere determinata da 6 variabili.

- Stati
- Alfabeto in input
- Alfabeto del nastro infinito
- Stato iniziale
- stato finale
- FUnzione di stransizione da (stato, simbolo nastro) → (stato, simbolo nastro, spostamento sinistra/destra)
- Slide

    <img src="/images/notes/image/universita/ex-notion/Fondamenti teorica/Untitled 2.png" alt="image/universita/ex-notion/Fondamenti teorica/Untitled 2">


In modo analogo a quanto fatto in precedenza possiamo andare a definire un **alfabeto riconosciuto dalla macchina di turing**.

### Calcolabilità secondo Turing 🟨+

**Definizione di calcolabilità**

Molto easy, Calcolabile secondo turing se esiste una macchina di turing (quindi definita da quelle 6 cose) che calcola quella funzione

- Slide

    <img src="/images/notes/image/universita/ex-notion/Fondamenti teorica/Untitled 3.png" alt="image/universita/ex-notion/Fondamenti teorica/Untitled 3">


**Osservazioni**

Si può notare che il numero che le funzioni che sono turing calcolabili sono **solamente numerabili** quindi c’è una stragrande maggioranza delle funzioni che non possiamo nemmeno andare a calcolare!

### Jacopini-Böhn e l’equivalenza 🟩

Si può dimostrare che molti formalismi sono **turing-completi** ossia sono in grado di calcolare esattamente le stesse funzioni della macchina di turing. (basta che il programma abbia tutta la memoria di cui necessita).

Il teorema di JB ci dice che se un linguaggio di programmazione possiede

- If-then-else
- While
- statements e assegnamento

→ Turing completo.

Come conseguenza di questo teorema ci fu, storicamente parlando, uno sviluppo della programmazione strutturata, in cui andiamo solamente a guardare i parametri locali per decidere e capire cosa faccia la funzione.

### Tesi di church turing
Vedere [La macchina di Turing#Tesi di Church-Turing](/notes/la-macchina-di-turing#tesi-di-church-turing)

> Se una funzione può essere calcolata algoritmicamente in un qualche formalismo allora è calcolabile con il formalismo della macchina di turing
>

Questo non è un teorema è solamente una tesi che è riuscita a resistere al tempo, che da grande valore al significato della macchina di turing.

La nota informale di questa tesi che non permette ancora un attacco matematico-formale è che

1. il concetto di algoritmo non è ancora stato ben formalizzato, e non si può applicare per tutti i formalsimo
2. Questa cosa deve essere vera per ogni formalismo, ma come formalizzare il formalismo stesso e poter parlare subito per tutti i formalismi?

## Note finali (modulo 1)

### Comparazione fra le macchine 🟥

- Slide comparazione

    <img src="/images/notes/image/universita/ex-notion/Fondamenti teorica/Untitled 4.png" alt="image/universita/ex-notion/Fondamenti teorica/Untitled 4">


Abbiamo visto che

1. Macchina di turing è la più generale, utilizza grmamatiche generali (quindi senza vincoli) e calcola cose semidecibili
2. PDA, libera, calcola cose decidibili, anche se non sono in grado di dire cose riguardanti ugualgianza boh.
3. DFA può essere utilizzata per modellizzare tante cose come
    1. Vending machine
    2. Circuiti logici
    3. Find/replace

    principalmente è tutto decibile per questo qua.




# References