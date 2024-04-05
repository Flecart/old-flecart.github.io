---
layout: page
permalink: notes/reinforcement-learning,-a-introduction
tags: en
title: Reinforcement Learning, a introduction
---

Ripasso Prox: 40
Ripasso: May 20, 2023
Ultima modifica: April 10, 2023 2:32 PM
Primo Abbozzo: January 26, 2023 10:00 PM
Stato: 🌕🌕🌕🌑🌑
Studi Personali: No

# Reinforcement Learning

## Introduzione

Una delle idee migliori riguardanti questo campo del reinforcement learning è il focus sul processo decisionale del singolo agente, condizionato al reward che l’ambiente esterno gli dà (feedback). Il setting classico di questo genere di problemi è un caso speciale della caratterizzazione presente in [l’intelligenza](/notes/l’intelligenza).

Abbiamo in questo caso un agente all’interno del suo ambiente. L’agente è in grado di interagire col suo ambiente attraverso alcune azioni ben definite, e l’ambiente restituisce un feedback ad ogni azione. L’agente si regola di conseguenza, nel tentativo di massimizzare il reward che riceve.

È da notare che questa impostazione è molto diversa rispetto al machine learning classico, seppur si può comunque collocare al suo interno. Classifcamente nei modelli di machine learning supervised si cerca di minimizzare un errore con alcuni dataset etichettati, mentre qui non abbiamo nessuna etichetta, mentre nel unsupervised proviamo a trovare alcuni pattern nei dati, mentre qui non cerchiamo nessun pattern. Si potrebbe dire che questo sia un terzo paradigma di machine learning.

NOTA: questi appunti riassumono concetti dai primi 4 capitoli del Sutton and Barto 2020

### Un problema classico: n-bandit
Vedere [N-Bandit Problem](/notes/n-bandit-problem).

### Setting classico (Model Policy Reward)

Quando andiamo a parlare di Reinforcement learning andiamo a considerare un setting classico di agente che interagisce con un ambiente attraverso delle azioni, e l’ambiente che risponde attraverso i reward. L’agente osserva quindi lo stato (se è full-observable vede lo stato esterno, altrimenti partially observable vede solamente parte delle informazioni dello stato dell’ambiente) e insieme al reward percepito prova a eseguire delle altre azioni.

<img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled">

Sono particolarmente importanti quindi 3 parole chiave utili per descrivere una delle 3 frecce in immagine

#### Model

Il modello dell'ambiente lo indichiamo anche come dinamica o sistema di transizione dell’ambiente. nel modello sono definite tutte le distribuzioni di probabilità che portano uno stato a un altro: $$P(s'|s)$$, questo possiamo dire, ossia partendo da uno stato s, quanto è probabile finire in uno stato s’ ??

Questo è quello che ci dice il modello.

#### Policy

La policy è un indicatore delle azioni del singolo agente, ci dice quanto è probabile che l’agente esegua una certa azione, dato che sia sopra un certo stato s, lo indichiamo solitamente con $$\pi(a | s)$$. Nel caso in cui è una policy deterministica, nel senso che a uno stato corrisponde uno e un solo azione, potremmo scrivere qualcosa del tipo $$\pi (s) = a$$

#### Reward

Il reward descrive il feedback che l’ambiente ritorna al giocatore una volta che una azione è stata eseguita, spesso lo indichiamo in questi modi


$$
r(s, a) \\ r(s, a, s') \\ r(s)
$$


A seconda di quanto vogliamo esprimere (quindi il reward atteso dopo aver fatto una azione da unc erto stato, il reward atteso dopo aver fatto una azione da un certo stato ed essere arrivati a un certo stao e così via

#### The Value function
Associamo ad ogni stato un reward $$r$$, si avrà una **history** ossia una sequenza di $$O, A, S$$ osservazione dall'ambiente, azione fatta e stato presente. Ad ogni stato avrò un reward.
quindi

$$
v_{i}(S_{j}) = \mathbf{E} [r_{i} + r_{i + 1} + \dots | S_{j}]
$$

Ossia se io al passo $$i$$ sono sullo stato $$S_{j}$$ la value function per quello stato è il valore atteso dei rewards tutti successivi.
Questo si può scrivere in maniera più compatta come

$$
v_{i}(S_{j}) = \mathbf{E} [r_{i} + v_{i+1}(S) | S_{j}]
$$

Con $$S$$ uno stato su cui puoi essere al passo successivo.

All components are functions: 
- Policies: $$\pi: S \rightarrow A$$ (or to probabilities over A) 
- Value functions: $$v: S \rightarrow R$$ 
- Models: $$m: S \rightarrow S$$ and/or $$r: S \rightarrow R$$ 
- State update: $$u: S \times O \rightarrow S$$

## Categorie di agenti
### Policy - Value categorization 
#### Value Based
ha solamente value based, la sua policy è basata sul suo valore (in modo greedy va a cercare quale sia lo stato con valore maggiore)

#### Policy based
Il contrario, non ha value function, ma solamente la policy

#### Actor Critic
Ha entrambi, ha sia policy (l'attore) e il critico che cerca di aiutare 
### Models

#### Model free
Se hanno policy o value, ma non hanno **nessun modello sull'ambiente** in cui sono presenti
#### Model based
Hanno il modello dell'ambiente, e non necessariamente hanno policy o value function.

### Prediction and control
**Prediction** è la capacità di sapere come sarà il futuro
**Control** è la capacità di ottimizzare la propria value function.
Solitamente sono molto legati fra di loro.

## Markov chains

Dovrebbe essere approfondito meglio in [Markov Chains](/notes/markov-chains)

### Markov property 🟩

Uno stato si può dire di godere della proprietà di markov se, intuitivamente parlando, possiede già tutte le informazioni necessarie per predire lo stato successivo, ossia, supponiamo di avere la sequenza di stati $$(S_n)_{n \in \N}$$, allora si ha che $$P(S_k | S_{k-1}) = P(S_k|S_0S_1...S_{k - 1})$$, ossia lo stato attuale in Sk dipende solamente dallo stato precedente.

Normalmente poche cose nel mondo reale si possono dire puramente Markoviane, però non si può negare che è un modello molto buono di partenza come modello di decisione.

ma potremmo sempre rendere Markoviano creando una nuova variabile che ci rappresenta tutta la storia (è qualcosa che non ho capito molto bene, ma credo si possa fare senza probbi).

### Markov processes 🟨-

Possiamo andare a definire un processo markoviano come un insieme di stati e il modello di transizione probabilistico: $$(S, P)$$, una coppia di stati e tutto il modello di transizione. mi sembra di aver letto che un processo markoviano sia molto buono per studiare i moti browniani in fisica. Praticamente a random abbiamo che ogni punto si può muovere

- Esempio di processo markoviano

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 1.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 1">


### Markov Reward Processes (!!!)

Quando andiamo a parlare di processo markoviano con reward indichiamo che associamo una funzione valore $$V(s)$$ che restituisce un certo valore a ogni stato. Di solito questo valore ci è ignoto a noi agenti che seguiamo iil modello, quindi diventa un buon problema in questo setting provare a stimare il valore dello stato in seguito a numerose osservazioni. Solitamente non vogliamo considerare tutti i reward con lo stesso peso. Vorremmo avere anche a disposizione un parametro che ci indichi quanto siano importanti i reward subito di ora, e i reward nel futuro. Con questo indichiamo un **discount factor** $$\gamma$$

Un tale processo viene formalizzato tramite una quadrupla   $$S, P, R,\gamma$$, con s stati possibili, P il modello di transizoine e R la funzione che ritorna il reward per ogni stato.

Solitamente viene definito **state value function:**


$$
V(s) = \mathbb{E}[R_t + \gamma R_{t + 1} + \gamma^2 R_{t + 2} + ... |  s = s _{t}]
$$


La parte dentro il valore atteso è solitamente indicata con $$G_t$$.

**Metodi di estimazione della funzione valore:**

Abbiamo abbastanza metodi per stimare il valore della funzione: metodi di sampling, metodi diretti (analitici) e metodi basati su programmazione dinamica.

Riguardo i metodi di sampling questi sono i più dinamici, nel senso che permettono l’applicazione a più problemi possibili, in generale hanno una precisione che va nell’ordine dell $$\dfrac{1}{\sqrt {n}}$$ anche se non so su quali basi in particolare.

I metodi diretti sono leggermente più lenti, perché si tratta di risolvere l’inversa della matrice, cosa che va in $$O(n^3)$$. Il motivo di questo è che possiamo **sfruttare la proprietà di V**

Ossia possiamo dire che


$$
V_k(s_t) = \mathbb{E}[R_t + \gamma G_{t + 1}  |  s = s _{t}] = R(s)  + \gamma \sum_{s'}P(s'|s)V_{k -1}(s')
$$


Questa osservazione permette di sviluppare un algoritmo iterativo per stivare il V fino a convergenza (sul perché converge sicuramente guardare altro, prolly idea degli operatori di bellman può essere utile)

- Algoritmo iterativo per valutazione della MRP

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 2.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 2">


**Soluzione analitica:**

Utilizzando la stessa proprietà (solamente ora scritta in modo analitico, possiamo risolverlo come se fosse una matrice

- Soluzione analitica

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 3.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 3">


### Markov Decision Process

Questo è molto simile alla MRP, solo che ora introduciamo una policy, ossia una funzione che ci dica quanto è probabile compiere una certa azione in un certo stato

$$(S, A, P, R, \gamma)$$, ossia ora abbiamo sia stato, sia azione possibile e la funzione di transizione deve contare entrambi: $$P(\cdot | s, a)$$, mentre le reward sono ancora come prima.

- S l’insieme di stati possibili
- A l’insieme di azioni possibili
- P probabilità di raggiungereun certo stato, dato uno stato inizial e una azione
- R reward di uno stato
- gamma: decadimento del reward.

È da notare che se possediamo una policy, allora possiamo ridurci al caso di Markov Reward Process, infatti possiamo dire che


$$
R^\pi(s) = \sum_{a \in A}\pi(a | s)R(s) \\

P^\pi(s'|s) = \sum_{a \in A}  \pi(a | s) P(s'|s, a)
$$


Quindi data una policy possiamo utilizzare gli argomenti fatti di sopra e **riuscire a dare una valutazione di essa**

- Algoritmo iterativo DP per policy evaluation

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 4.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 4">


## Policy Search

Cerchiamo ora la policy migliore possibile da applicare a un MDP, questo è il problema del **policy control** ora che sappiamo come fare **policy evalutation** è il momento giusto per introdurre soluzioni a questo problema.

Una soluzione **naïve** è semplicemente enumerare tutte le policy e utilizzare l’algoritmo di policy evaluation, poi andare a vedere quale sia la migliore. Questo è molto dispendioso perché assumento che posso applicare tutto l’insieme di azioni a tutti gli stati ho potenzialmente $$|S|^{|A|}$$ policy possibili,, che sono troppi , e troppo brutti.

È bene raggiunti questo punto provare a dare alcune definizioni utili.

### Definitions: state-action-value, optimal value policy

Sia $$\pi$$ una policy e $$V^\pi$$ la evaluation di quella policy, allora possiamo andare a definire la **state-action-value** function in questo modo:


$$
Q(s, a) = R(s, a) + \gamma \sum_{s'} P(s'|s, a)V^\pi(s')
$$


ossia ci dice più o meno il valore atteso dell’azione a un certo stato!

Possiamo anche definire la policy migliore:


$$
\pi^*(s) = argmax_{\pi} V^\pi(s)
$$


Ossia è la policy che rende massimo il valore in qualunque stato!

### Policy iteration and his monotonicity

Una volta creato una policy iteration, è una cosa molto sensata andare a definire una nuova policy $$\pi_{k + 1}$$ definita in questo modo:


$$
\forall s, \pi_{k + 1}(s) = argmax_a Q(s, a)
$$


Ossia andiamo proprio a crearci una nuova policy, cercando di rendere maggiore possibile il valore atteso a fare una certa azione a uno stato! Riusciremo a dimostrare che $$\forall s, V^{\pi_{k + 1}}(s) \geq V^{\pi_{k}}(s)$$

- Dimostrazione dal sutton e barto

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 5.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 5">

    l’idea principalmente è prendere sempre il massimo volta dopo volta, e dimostrarlo per induzione in pratica… Anche non ho capito come formalizzare e non ho capito se posso trarne vantaggi didattici nella formalizzazione di questa merda


### Value Iteration

L’idea di value iteration è sostituirla subito, cioè non stare a sviluppare fino in fondo la value evaluation, ma aggiornare la policy subito dopo.

- Pseudocodice value iteration

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 6.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 6">


### Bellman operator

- Slide

<img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 7.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 7">


Si può dimostrare che questo operatore è una contrazione, quindi value iteration converge qualunque sia il punto di partenza

Con questo operatore, possiamo anche riscrivere in modo migliore la **policy evaluation**

- Slide

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 8.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 8">


- Proof of contraction of bellman operator

    <img src="/images/notes/image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 9.png" alt="image/universita/ex-notion/Reinforcement Learning, a introduction/Untitled 9">