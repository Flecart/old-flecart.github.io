---
layout: page
permalink: notes/entropy
tags: italian
title: Entropy
---

### Entropy
Questo è stato creato da 1948 Shannon in @shannonMathematicalTheoryCommunication. Questa nozione è basata sulla nozione di probabilità, perché le cose rare sono più informative rispetto a qualcosa che accade spesso.
[Kolmogorov complexity](/notes/kolmogorov-complexity) è un modo diverso per definire la complessità.
Legato è [Neural Networks#Kullback-Leibler Divergence](/notes/neural-networks#kullback-leibler-divergence).

We can model the classical view of entropy as the from [^1]
> Expected value of **Surprisal** which is the uncertainty of a random variable $$X$$ taking a certain value which is $$p(X = x) = P(x)$$, but we want to measure it using log-likelihood.


$$
H(\cdot) = - \sum p(x)\log(p(x)) \tag{1.1}
$$

Ossia, possiamo dire in modo intuitivo quanto sarebbe sorprendente vedere che si avverasse quell'evento. 

Oppure come descritto da [^2]

$$
\begin{align*}
H(X) := E[I(X)] &= \sum_{i=1}^n P(x_i)I(x_i) \\
&= \sum_{i=1}^n p_i \log(1/p_i) \\
&= -\sum_{i=1}^n p_i \log(p_i) \tag{1.2}
\end{align*}
$$

#### Conditional Entropy

$$
H(Y|X) = \sum_{x \in \mathcal{X}}p(x) H(Y|X=x)
= \sum_{x \in \mathcal{X}, y \in \mathcal{Y}} p(x, y) \log \frac{1}{P(y|x)}
= \mathbf{E}\left[ \log\frac{1}{p(Y|X)} \right] 
$$

La nozione con il valore atteso è la più semplice anche in questo caso.
#### Chain Rule
Una proprietà random è

$$
H(X, Y) = H(X) + H(X|Y)
$$

La dimostrazione è abbastanza banale una volta che si conoscono le definizioni....
La cosa interessante è che si può generale per qualunque numero di variabili aleatorie:

$$
H(X_{0}, X_{1}, \dots, X_{i}) = \sum_{i}H(X_{i}|X_{i-1}\dots X_{0})
$$


#### Upper bound

$$
H(X) \leq \log \lvert \mathcal{X} \rvert 
$$

Con $$\mathcal{X}$$ l'insieme immagine della variabile aleatoria **discreta** $$X$$. Importante in questo caso che la nostra variabile sia discreta, altrimenti il teorema provvisto in @coverElementsInformationTheory2012 2.6.4 non funziona.
Non è molto banale l'idea di utilizzare la uniforme per modellare il numero di elementi. e usare la positività di KL per finire l'upper bound.
#### Entropy is concave
Uso l'upper bound e il fatto che KL è convesso per dimostrare questa cosa.

#### Functional dependency
Se $$Y = f(X)$$ per qualche funzione, allora $$H(Y|X) = H(X|Y) = 0$$ si può risolvere con qualche ragionamento sul supporto di entropia.
Interessante vedere che ha una piccola relazione con [Normalizzazione dei database#Dipendenze funzionali](/notes/normalizzazione-dei-database#dipendenze-funzionali).

### Relative Entropy or Kullback-Leibler
<img src="/images/notes/image/universita/ex-notion/Neural Networks/Untitled 2.png" alt="image/universita/ex-notion/Neural Networks/Untitled 2">
In modo praticamente equivalente possiamo definire una versione condizionata. e si può applicare anche in questo caso una chain rule


$$
DL(P(x, y) \mid\mid Q(x, y) = DL(P(x) \mid\mid Q(x)) + DL(P(x|y) \mid\mid Q(x|y))
$$


#### KL is positive
Ossia per ogni distribuzione $$p$$ o $$q$$ si ha che

$$
DL(X \mid\mid Y) \geq 0
$$


E ricordandoci che $$\log$$ è una funzione concava, quindi si può utilizzare Jensen.
#### KL is convex
$$DL(p\mid\mid q)$$ è convesso sulla coppia $$(p, q)$$, 2.7.2 di @coverElementsInformationTheory2012.
### Mutual information
Questa nozione definisce quanta informazione hanno in comune due variabili aleatorie
#### Definizione

$$
I(X;Y) = \sum_{x}\sum_{y} p(x, y) \log\left(  \frac{p(x, y)}{p(x)p(y)} \right)
= H(X) - H(X|Y)
$$

Si può fare dopo un po' di calcoli che qui ho omesso, ma non dovrebbe essere difficile farlo.888

Si può intendere la mutual information anche come KL fra le distribuzioni $$p(x, y)$$ e $$p(x)p(y)$$ si può notare che queste due sono uguali quando le due sono indipendenti, che è coerente con la nostra nozione che abbiamo dell'indipendenza.
#### Proprietà
<img src="/images/notes/Entropy-20240229150751912.webp" alt="Entropy-20240229150751912">
<img src="/images/notes/Entropy-20240229150807093.webp" alt="Entropy-20240229150807093">

### Sufficient Statistics

Possiamo rappresentare il sampling da una certa famiglia di distribuzioni $$f_{\theta}(x)$$ , rappresentato da $$X$$, e una sua statistica a caso (media varianza etc, che credo basti una funzione sul valore) come T, allora possiamo rappresentarlo come una [Markov Chains#Catena di 3 variabili](/notes/markov-chains#catena-di-3-variabili) $$\theta \to X \to T(X)$$
E vale il teorema di information processing


$$
I(\theta; T(X)) \leq I(\theta; X)
$$

Si può chiamare una statistica per $$\theta$$ sufficiente se $$X$$ contiene tutta l'informazione di $$\theta$$. Non so bene cosa significhi.
La cosa importante è che la statistica sufficiente **preserva la mutua informazione** ossia si ha una uguaglianza in quella relazione di sopra. Vedere 2.9 di @coverElementsInformationTheory2012 per esempi .

Questa cosa potrebbe permettere di dire che usando quella statistica io posso dimenticarmi del parametro, perché riesco a ricavarmelo senza problemi credo....
> The purpose of sufficiency is to demonstrate that statistics that satisfy this property do not discard information about the parameter, and as such, estimators that might be based on a sufficient statistic are in a sense "good" ones to choose.

Da [https://math.stackexchange.com/questions/1186645/understanding-sufficient-statistic.](https://math.stackexchange.com/questions/1186645/understanding-sufficient-statistic.)

### Fano's inequality
L"idea principale è utilizzare una variabile aleatoria per stimarne una altra, usando l'entropia condizionale fra le due.

#### Enunciato fano

Per ogni estimantore $$\hat{X}$$ tale per cui $$X \to Y \to \hat{X}$$ sia una catena di markov, e con $$P_{e} = Pr(X \not= \hat{X})$$ ossia la probabilità di errore, abbiamo che vale

$$
H(P_{e}) + P_{e}\log \lvert \mathcal{X} \rvert \geq H(X|\hat{X}) \geq H(X|Y)
$$

Ci sono forme più deboli che possiamo considerare in un certo senso corollari, ossia che

$$
1 + P_{e} \log \lvert \mathcal{X} \rvert  \geq H(X|Y)
$$


#### Dimostrazione Fano
Questa è una bomba da fare. Poi però ha un sacco di conseguenze non applicabili in modo immediato (cioè non ci arrivi subito se non le fai un po' prima).

### Maximum Distribution entropy
Un problema classico nella teoria dell'informazione è trovare la distribuzione che massimizzi l'entropia (quindi l'informazione contenuta credo) dati certe conoscenze a priori,
Ossia data una funzione $$f$$  e certe condizioni che deve rispettare, massimizzare l'entropia.

SI può dimostrare (lo si può vedere da una reference di sopra) che la distribuzione che massimizza l'entropia, avendo solamente la condizione di probabilità, ossia che $$\sum_{x}p(x) = 1$$ è la distribuzione uniforme.
Mentre se assumo anche media $$\mu$$ e varianza $$\sigma^{2}$$ allora è la gaussiana.
In un certo senso possiamo dire che queste distribuzioni sono molto ricche di informazioni.


### Codewords
#### Jensen's Inequality
Questo è un teorema fondamentale per moltissime cose, e da un certo punto di vista è una cosa banale per le cose convesse/concave.
Allora, sia data una funzione in $$[a, b]$$ tale che sia convessa (concava) in questo intervallo, allora vale che

$$
f\left( \sum_{i} \lambda_{i} x_{i} \right) \leq \sum_{i}\lambda_{i}f(x_{i})
$$

Con $$\sum_{i}\lambda_{i} = 1$$. Questa cosa si estende in modo molto semplice a variabili aleatorie e $$E$$ quando al posto di $$\lambda_{i}$$ mettiamo una probabilità in un punto.

La dimostrazione non dovrebbe essere molto difficile. La strategia è utilizzare l'induzione in modo abbastanza classico. Non so in che modo si estende su funzioni continue, ma quelle sono cose tecniche matematiche non interessantissime.
#### Log sum inequality
Siano $$a_{1}, a_{2}, \dots a_{n}$$ e $$b_{1}, b_{2}, \dots, b_{n}$$ numeri non negativi, allora vale che

$$
\sum_{i=1}^{n}a_{i} \log\left( \frac{a_{i}}{b_{i}} \right) \geq \left( \sum_{i=1}^{n}a_{i} \right)\log \frac{\left( \sum_{i=1}^{n} a_{i} \right)}{\sum_{i=1}^{n}b_{i}}
$$

Con uguaglianza se vale che $$\forall i, \frac{a_{i}}{b_{i}}= const$$

#### Krafts Inequality
[https://en.wikipedia.org/wiki/Kraft%E2%80%93McMillan_inequality](https://en.wikipedia.org/wiki/Kraft%E2%80%93McMillan_inequality)
Questo teorema interessa cose dei codewords, perché ci interessano dei **set** di prefixfree che sono molto più gestibili probabilmente dal punto di vista dell'interpretazione.
La cosa interessante è:

Siano $$l_{1}, l_{2}, l_{3}, \dots, l_{n}$$ lunghezze di code-words all'interno del nostro alfabeto, allora vale che esistono dei code-words (stringhe binarie) che hanno quelle lunghezze **se e solo se** viene soddisfatta la proprietà

$$
\sum_{x} 2^{-l(x)} \leq 1
$$


Il motivo è abbastanza semplice, questo si spiega in modo grafico in maniera praticamente immediata quando facciamo il disegno.
Si può vedere dall'albero binario corrispondente di un insieme di set binari con prefissi che se un parente è scelto (colorato nel disegno), allora nessun discendente può essere scelto perché altrimenti avresti un prefisso. Inoltre se colori quelli sopra, significa che al massimo se sommi tutti quei valori otterrai 1 sse hai utilizzato tutti i rami a tua disposizione (meaning, che non puoi scegliere altri code-work, altrimenti perdi la prefix property).
<img src="/images/notes/Entropy-20240212162407876.webp" alt="Entropy-20240212162407876">


#### Relazione con Kolmogorov
1.11.3 di @liIntroductionKolmogorovComplexity2019, allora se prendiamo un set di code-words con $$L$$ il minimo prefix code che possiamo mai avere
Ossia $$L = \sum_{x} P(x)l(x)$$, con $$l$$ scelto il minimo possibile. Allora vale che

$$
H(P) \leq L \leq H(P) + 1
$$

Ossia la lunghezza migliore possibile è boundata da valori di entropia. Che è una cosa abbastanza forte perché relaziona come deve essere fatto il code-words, con la complessità dell'informazione che vogliamo andare a utilizzare.
La dimostrazione non la facciamo qui, ma è fattibile con le tue conoscenze credo, ti serve la Gibbs inequality qui sotto per una freccia

#### Gibbs Inequality
Afferma che l'entropia è minore rispetto alla cross-entropy di qualunque cosa, ossia

$$
\sum_{x} P(x) \log\left(  \frac{1}{P(x)} \right) \leq \sum_{x} P(x) \log\left( \frac{1}{Q(x)} \right)
$$

Qualunque sia l'altra distribuzione.
Si può dimostrare in modo abbastanza diretto utilizzando il fatto che la Kullback Leibler divergence, presentato in [Neural Networks](/notes/neural-networks), è sempre positiva o uguale a 0.