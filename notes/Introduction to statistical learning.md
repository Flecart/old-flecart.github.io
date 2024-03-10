---
layout: page
permalink: notes/introduction-to-statistical-learning
tags: italian
title: Introduction to statistical learning
---

#statistics

## Introduzione

This is a short introduction to statistical learning, made with the help of the book ISLP (mi sento positivo ad affrontare la lettura di questo libro, ora che sta in python non lo vedo più come un libro solamente per statistici)

>statistical learning refers to a set of approaches for estimating $$f$$ .


### Utilizzi del statistical learning

Solitamente sono due gli utilizzi **Predizione** e **inferenza**. Per predizione intendiamo il miglior modello che possa produrre le Y che ancora non conosciamo.
Per inferenza significa il miglior modello f per predire Y che conosciamo.

Nel primo caso la funzione migliore $$f$$ potrebbe benissimo restare sconosciuta, ci importa solamente che predica con accuratezza, mentre nel secondo caso vorremmo anche conoscere $$f$$. 

In un certo senso l'inferenza ci permette di calcolare una specie di *legge fisica*, (è incorretto chiamarlo in questo modo, ma credo dia l'idea), ossia permette la comprensione del *perché* avendo questi input, potrò avere quei output. NOTA: avendo questa comprensione potrei anche fare predizioni su dati che non esistono, credo.


## Errore riducibile e irriducibile

Questo è un concetto statistico abbastanza nuovo, utile per parlare di stima di modelli statistici.
Supponiamo di avere una serie di dati solitamente indicati con $$X$$ , vogliamo con questi andare a predire la variabile dipendente $$Y$$. Solitamente andiamo anche ad introdurre un errore rappresentato con $$\varepsilon$$ . Questo è un errore **indipendente da $$X$$**, ossia non possiamo predirlo utilizzando X.

La branca dell'apprendimento statistico vuole utilizzare X per andare a predire Y. Però il meglio che può fare resterebbe sempre solamente una funzione $$f$$ che abbia quell'errore che lo faccia variare. Quell'errore potrebbe essere dovuto a informazioni che non conosciamo oppure solamente a cose che non possono essere misurate (elementi che sono principalmente dovuti al caso, che difficilmente avremmo potuto utilizzare per misurarlo)

### Formalizzazione di sopra

Tutto si potrebbe formalizzare con questo ragionamento

$$
E[Y - \hat{Y}]^2 = E[(f(X) + \varepsilon) - \hat{f}(X)]^2 = [f(X) - \hat{f}(X)]^2 + var(\varepsilon)
$$

Osservando che X è una costante in questo caso, e ci interessa solamente la varianza.
Si potrebbe intendere che la prima parte è un errore riducibile (può essere fino a 0), mentre la varianza dell'errore è parte di errore irriducibile.

## Tipologie di modelli

Principalmente esistono due tipologie di modelli, proveremo a parlarne estensivamente qui sotto:

### Modelli parametrici

L'inferenza/predizione con questo genere di modelli si fa in due step:
1. Scelta del modello (lineare? Quadratico? rete neurale? allora architettura della rete)
2. Algoritmo di scelta dei parametri del modello
Vedere sul libro pagina 31 per degli esempi.

La caratteristica negativa di questo è che è fortemente dipendente dal nostro modello scelto, che non sempre può risultare essere la migliore per stimare la funzione che abbiamo:

>The potential disadvantage of a parametric approach is that the model we choose will usually not match the true unknown form of $$f$$ .

### Modelli non parametrici

>Non-parametric methods do not make explicit assumptions about the functional form of $$f$$ . Instead t*hey seek an estimate of $$f$$ that gets as close to the data points as possible without being too rough or wiggly*.

Un esempio di questo genere di modelli potrebbero essere splines, che sono molto più variabili di un modello parametrico

#### Vantaggio principale sui parametrici
> by avoiding the assumption of a particular functional form for f , they have the potential
to accurately fit a wider range of possible shapes for f .

#### Svantaggio principale
Dato che non devo imparare solamente dei parametri, ho bisogno di molto più dati affinché io sia accurato nella predizione

## Lessico importante
- Variabile dipendente e indipendente
- Predittori, input e output e response
- Errore riducibile ed irriducibile
-