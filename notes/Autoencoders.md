---
layout: page
permalink: notes/autoencoders
tags: italian
title: Autoencoders
---

In questa serie di appunti proviamo a descrivere tutto quello che sappiamo al meglio riguardanti gli autoencoders
[Blog di riferimento]([https://towardsdatascience.com/understanding-variational-autoencoders-vaes](https://towardsdatascience.com/understanding-variational-autoencoders-vaes)-f70510919f73)
[Blog secondario che sembra buono](https://mbernste.github.io/posts/vae/)
### Introduzione agli autoencoders

L'idea degli autoencoders è rappresentare la stessa cosa attraverso uno spazio minore, in un certo senso è la compressione con loss.
Per cosa intendiamo qualunque tipologia di dato, che può spaziare fra immagini, video, testi, musica e simili. Qualunque cosa che noi possiamo rappresentare in modo digitale possiamo costruirci un autoencoder.
Una volta scelta una tipologia di dato, come per gli algoritmi di compressione, valutiamo come buono il modello che riesce a comprimere in modo efficiente e decomprimere in modo fedele rispetto all'originale.
Abbiamo quindi un trade-off fra spazio latente, che è lo spazio in cui sono presenti gli elementi compressi, e la qualità della ricostruzione.
Possiamo infatti osservare che se **spazio latente = spazio originale, loss di ricostruzione = 0** perché basta imparare l'identità.
In questo senso si può dire che diventa sensato solo quando lo spazio originale sia minore di qualche fattore rispetto all'originale. Quando si ha questo, abbiamo più difficoltà di ricostruzione, e c'è una leggera perdita in questo senso.


### Proprietà interessanti
Vogliamo in un certo senso imporre una **regolarità nello spazio latente** perché questo ci permette di esprimere in un modo più coerente da quanto ci attendiamo le cose dello spazio:
1. Se prendiamo un punto vicino a un encoding noto, ci aspettiamo che sia simile al punto stesso
2. Se prendiamo un punto del nostro spazio latente ci aspettiamo che dia qualcosa di sensato

Rispettivamente queste proprietà sono state chiamate **continuità e completezza**.

## Variational Auto-Encoders

### Intuizione
L'idea sembra avere uno spazio regolarizzato, ossia un
$$z \sim \mathcal{N}(\mu, \sigma^{2}I)$$ con $$\sigma$$ vettore di dimensione spazio latente e $$\mu$$ degli offset che rappresentano media. 
Quindi il decoder parametrizzato secondo $$\theta$$ dovrà essere in una forma dipendente da questa.

Insieme a questo utilizziamo anche un encoder parametrizzato con $$\phi$$ che dovrà darci indicazioni su $$z$$, per esempio media e varianza.

Secondo Murphy-1, Questo dovrebbe essere molto simile a un lavoro di uno 95, vedi capitolo su VAE in que libro.

La formulazione dei VAE sembra molto simile ai Factor Analysis. Che è una caratterizzazione di un certo tipo sia spazio latente che quello normale.

### Setting del problema

In questo senso vogliamo cercare di regolarizzare il nostro spazio latente assumendo che

$$
p(x | z) \sim \mathrm{N}(media, varianza)
$$

Ossia i samples della parte condizionata nello spazio latente non sono altro che una media e varianza dipendenti solo dalla parte condizionale, mentre $$p(z) = N(0, 1)$$ multidimensionale (quindi varianza $$I$$)



### ELBO e derivazione
Se assumiamo questo, allora la loss di Kullback-Leibler diventa abbastanza carina, perché infatti abbiamo che


$$
KL(q_{x}(z), p(z|x)) = E_{x \sim q_{x} }(\log(q_{x}(z))) - E_{x \sim q_{x}}\left(\log( \frac{p(x, z)}{p(x)}) \right)
=
$$


$$
= E_{x \sim q_{x}}(\log(q_{x}(z))) - E_{x \sim q_{x}}(\log(p(x, z))) + E_{z \sim q_{x}}(\log(p(x))) 
= E_{z \sim q_{x}}(\log(p(x)))  - E_{z \sim q_{x}}\left( \log\left( \frac{p(x, z)}{q_{x}(z)} \right) \right) 
$$

Ora le ultime due si chiamano rispettivamente **evidence** e **ELBO** che sta per Evidence Lower Bound
Notiamo che la evidence non dipende da $$z$$, infatti avremmo che

$$
E_{z \sim q_{x}}(p(x))  = \int _{-\infty}^{+\infty} q_{x}(z) p(x) \, dz = p(x)  \int _{-\infty}^{+\infty} q_{x}(z) dz = p(x)
$$

Quindi se vogliamo minimizzare la divergenza, ci basta Massimizzare ELBO nel nostro caso.

#### Esplicitazione di ELBO
Possiamo lavorare ancora di più su ELBO, provando ad esplicitarne alcuni valori, infatti possiamo considerare


$$
ELBO = E_{z \sim q_{x}}\left( \log\left( \frac{p(x, z)}{q_{x}(z)} \right) \right) 
=E_{z \sim q_{x}}\left( \log\left( p(x|z) \right) \right)  + E_{z \sim q_{x}}\left( \log\left( \frac{p(z)}{q_{x}(z)} \right) \right) 
$$


$$
=
E_{z \sim q_{x}}\left( \log\left( p(x|z) \right) \right)  - KL(q_{x}(z), p(z))
$$


Ossia abbiamo il secondo termine che prova a regolarizzare la distribuzione $$q$$ trovata, e il primo termine che è un maximum likelihood, simile a quanto trovato per [Naïve Bayes](/notes/naïve-bayes) nel corso di Asperti.
Questo è la nostra loss per il VAE.

Ora l'ultimo passo sarebbe come esplicitare ELBO in modo che possa essere implementato come loss di una net?

#### Derivazione della loss per VAE
Vedere [qui]([https://mbernste.github.io/posts/vae/#appendix-derivation-of-the-kl-divergence-term-when-the-variational-posterior-and-prior-are](https://mbernste.github.io/posts/vae/#appendix-derivation-of-the-kl-divergence-term-when-the-variational-posterior-and-prior-are)-gaussian), è calcolosa, ma molto carina, e ti permette di impratichirti con gaussiane multivariabili.

Alla fine si avrà come risultato:


$$
KL(q_{x}(z), p(z)) = -\frac{1}{2} \sum_{j=1}^{J}(1 + \log \sigma^{2}_{j} - \mu^{2}_{j} - \sigma^{2}_{j})
$$

**Derivazione di KL** per la loss
Vedere [https://mr-easy.github.io/2020-04-16-kl-divergence-between-2-gaussian-distributions/.](https://mr-easy.github.io/2020-04-16-kl-divergence-between-2-gaussian-distributions/.)
E poi sostituire.
Per l'expectation della forma quadratica vedere qui [https://statproofbook.github.io/P/mean-qf.html.](https://statproofbook.github.io/P/mean-qf.html.)

Allora, sappiamo che $$p(z) = \mathcal{N}(0, \mathcal{I})$$ quindi ha una forma ben nota, dovremo cercare di fare questa piccolissima derivazione.



## Note di ripasso
- Ripassare proprietà della gaussiana multi-valore, che non mi sembra lo abbia benissimo in chiaro, serve nella derivazione.

| Data | Commenti |
| ---- | ---- |
| 06/02/24 | Praticamente non mi ricordavo niente di ELBO 🟥, molto male. ELBO è molto importante. |
| 08/02/24 | La derivazione non è ancora naturale, dovrei farlo ancora un paio di volte credo. |