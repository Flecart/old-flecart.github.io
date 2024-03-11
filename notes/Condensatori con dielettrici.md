---
layout: page
permalink: notes/condensatori-con-dielettrici
tags: italian
title: Condensatori con dielettrici
---

### introduzione ai dielettrici

#### Esperimenti metalli e dielettrici 🟩

Verso gli anni del 1840 Faraday ha fatto molti sistematici esperimenti per scoprire come si comportava il potenziale e il campo elettrico di fronte a certi materiali.
Sono stati principalmente posti delle sostanza (conduttrici o meno) in mezzo a lastre di [condensatori](/notes/condensatori-nel-vuoto), e hanno misurato come cambiava il potenziale elettrico fra le due lastre (che si può vedere attraverso il modo con cui cambiano sull'elettroscopio).
Così ha scoperto che

$$
V_{s} = (h - s) E_{0}
$$

Questo è vero perché semplicemente in mezzo al conduttore il campo elettrico è nullo, come spiegato in [Conduttori elettrici](/notes/conduttori-elettrici), quindi durante l'integrale, il percorso è semplicemente minore, esattamente di quella quantità.

Nel caso di condensatore con spessore $$h$$ e materiale conduttore di spessore $$s$$ in mezzo.
Ma questo non succedeva se metteva materiali isolanti!
In questi il potenziale cadeva più lentamente rispetto al metallo, ma comunque cadeva di un po', in modo lineare fino a riempire l'intero spazio.
Il potenziale in questo ultimo stadio lo chiamiamo $$V_{k}$$ e sperimentalmente hanno notato che vale sempre

$$
k = \frac{V_{0}}{V_{k}} < 1
$$

#### Costante dielettrica relativa 🟩
Questa quantità non è molto importante, forse semplifica i conti ma è utile a descrivere il nuovo campo elettrico, perché se si assume di avere un campo uniforme allora abbiamo:

$$
E_{k} = \frac{V_{k}}{h} = \frac{V_{0}}{kh} = \frac{E_{0}}{k} = \frac{\sigma_{0}}{k\varepsilon_{0}} = \frac{\sigma_{k}}{\varepsilon_{0}} = \frac{\sigma_{0}}{\varepsilon}
$$

L'ultimo valore possiamo scriverlo come se avessimo una carica intermedia, saltando i calcoli (un esercizio che trovi nel Mazzoldi p/128)
Abbiamo che 

$$
E_{k} = \frac{\sigma_{0}}{\varepsilon_{0}} - \frac{\sigma_{p}}{\varepsilon_{0}}
$$

Con

$$
\sigma_{p} = \frac{k - 1}{k} \sigma_{0}
$$

E si potrebbe definire anche

$$
\sigma_{k} = \sigma_{0} - \sigma_{p} = \frac{\sigma_{0}}{k}
$$

Qui si può giocare un po' senza nessun problema!


L'equazione del nuovo campo elettrico è utile per avere una intuizione, è **come se esistesse un campo contrario** creato dal dielettrico, che ne affievolisce l'intensità, questo sarà spiegato meglio dopo, esisteranno seriamente queste cariche!

#### Costante dielettrica assoluta del dielettrico 🟩
Si trova che le relazioni di sopra funzionano per condensatori rotondi, piani, di qualunque forma, basta che siano condensatori (quindi ci sia l'induzione completa e abbiano stessa carica).
Infatti abbiamo anche cose come 

$$
C_{p} = \frac{q}{V_{p}} = \frac{qk}{V_{0}} = k C_{0}
$$

Ma andando a definire la nuova costante dielettrica abbiamo:

$$
\text{costante dielettrica assoluta del dielettrico: }\varepsilon = k\varepsilon_{0}
$$

Che è il nostro nuovo valore!
Per i condensatori piani abbiamo

$$
C_{p} = kC_{0} = k \varepsilon_{0} \frac{S}{d} = \frac{\varepsilon S}{d}
$$

E notiamo che **cambia solamente il valore di dielettrico**, è ancora molto clean la relazione.

Secondo me non ha senso questa parte e possiamo soltanto dire che la **capacità cresce** col dielettrico

### Polarizzazione del dielettrico
#### Polarizzazione per deformazione/elettronica 🟨+
<img src="/images/notes/Condensatori con dielettrici-1698143952107.jpeg" alt="Condensatori con dielettrici-1698143952107">
Questa polarizzazione si spiega a un **livello atomico** perché intuitivamente si può dire che il punto medio delle cariche elettriche positive (nucleo) e negative (nube di elettroni) quando viene sottoposto a un campo elettrico si spostano, per cercare di bilanciare la piccola forza applicata dal campo elettrico, quindi è un valore direttamente proporzionale al valore del campo elettrico,
In questo caso:

$$
\vec{p}_{e} = Ze\vec{x}
$$

Con x il vettore della congiungente, $$Z$$ numero atomico $$e$$ la carica basilare dell'elettrone.
Da quanto studiato in [Dipolo elettrico](/notes/dipolo-elettrico), quando ho un momento, c'è un campo indotto.

Insieme a questo, i mini dipoli si **orientano** sul verso del campo elettrico.
#### Polarizzazione per orientamento (non fatta)
Questo viene usato per discutere a livello molecolare come avviene la polarizzazione. Se prendo molecole polari, come l'acqua, si avrà che più è sottoposta a campo intenso, più **in media** i dipoli saranno orientati sul campo, infatti se non lo sono allora ci sarà un momento di dipolo che proverà a riportarli in quello stato, come studiato in [Dipolo elettrico](/notes/dipolo-elettrico) nella sezione dei momenti di dipolo.

La differenza col precedente è che questo è solamente un effetto di media!

### Suscettibilità elettrica (!)
#### Definizione di suscettibilità elettrica 🟩
Andiamo a chiamare la quantità

$$
\text{ suscettività dielettrica: } \chi = k - 1 = \frac{V_{k}}{V_{0}} - 1
$$


Andiamo a definire un valore $$P$$ che spiega **quanto dipolo creato dal campo**, ed è in pratica **momento di dipolo per unità di volume**.
Solitamente assume questa forma:

$$

P = \varepsilon_{0}\chi E
$$

Se un dielettrico soddisfa questa relazione (solitamente è omogeneo) si dice che sia **dielettrico lineare**, solitamente materiali amorfi (senza forma), dotati di *isometria spaziale*, nei cristalli in genere questo non succede.

#### Dimostrazione valore 🟨
<img src="/images/notes/Condensatori con dielettrici-1698151009489.jpeg" alt="Condensatori con dielettrici-1698151009489">
NOTA: nell'immagine ho sbagliato a disegnare il verso dei singoli atomi allungati.

Assumiamo di immergere un dielettrico in un campo elettrico uniforme, allora abbiamo che

$$
\sigma_{p} = nq\delta
$$

Perché in pratica $$n = \frac{\Delta N}{\Delta \tau}$$ è la densità atomica (numeri di atomi per unità di volume), io con la relazione di sopra sto anche moltiplicando per la lunghezza del tratto considerato, quindi $$n\delta$$ rappresenta numero di atomi nella superficie (dato che $$n$$ è il numero di atomi per volume, moltiplicando per una lunghezza ho la densità superficiale), e $$q$$ gli do la carica, dimensionalmente torna l'idea. Ogni atomo ha $$q$$ di carica a causa della polarizzazione.

Ma allo stesso tempo il momento di dipolo di un singolo atomo è $$\vec{p} = q\vec{\delta}$$, e così che definisco il **momento di dipolo per unità di volume** come $$\vec{P} = nq\vec{\delta}$$ (sul libro è presentato come $$\vec{P} = n < \vec{p}>$$) allora abbiamo che

$$
\sigma_{p} = \lvert \vec{P} \rvert 
$$

Nel caso più generale (in immagine) in cui il campo elettrico non è perpendicolare al piano del dielettrico si ha

$$
\sigma_{p} = \vec{P} \cdot \hat{n}
$$


Applicando questo su una formula di sopra abbiamo:

$$
E 
= \frac{\sigma_{0} - \sigma_{p}}{\varepsilon_{0}} 
= \frac{\sigma_{0} - \lvert \vec{P} \rvert}{\varepsilon_{0}} \implies P = \sigma_{0} - \varepsilon_{0}E 
= kE\varepsilon_{0} - \varepsilon_{0} E = \varepsilon_{0}E(k - 1)
= \varepsilon_{0}E\chi
$$

#### Valore tensoriale 🟩
Solitamente per materiali non isotropi è un tensore, quindi lo abbiamo in una forma del genere

$$
\begin{pmatrix}
P_{x} \\
P_{y}  \\
P_{z}

\end{pmatrix}
=
\begin{pmatrix}
\chi_{11} & \chi_{12} & \chi_{13} \\
\chi_{21} & \chi_{22} & \chi_{23} \\
\chi_{31} & \chi_{32} & \chi_{33} \\

\end{pmatrix}
\cdot
\begin{pmatrix}
E_{x} \\
E_{y} \\
E_{z}
\end{pmatrix}
$$

Ma per qualche motivo che non conosco $$\chi$$ è una **matrice simmetrica reale** questo implica che è diagonalizzabile per cui esiste una base di autovalori, che permette di riscrivere la matrice di sopra come

$$
\begin{pmatrix}
P_{x} \\
P_{y} \\
P_{z}
\end{pmatrix}
=
\begin{pmatrix}
\chi_{11}' & 0 & 0 \\
0 & \chi_{22}' & 0 \\
0 & 0 & \chi_{33}'
\end{pmatrix}
 \cdot 
 \begin{pmatrix}
E_{x} \\
E_{y} \\
E_{z}
\end{pmatrix}
$$

Che è anche più veloce da calcolare.
La base di autovalori si chiama anche **asse ottico**
### Polarizzazione in materiali non omogenei
#### Caso dipolo omogeneo 🟩
Questo è come il caso di flusso esterno in una superficie qualunque.
Presa una qualunque superficie $$\Sigma$$, abbiamo che:

$$
\Delta Q = \oint_{\Sigma} \vec{P} \cdot d\vec{s} = 0
$$

Si può dire che è uguale a zero perché il flusso esce ed entra, per lo stesso valore.

#### Caso dipolo non omogeneo 🟩
sia $$\Delta Q'$$ la carica rimasta internamente al volume, dato che il dielettrico è neutro abbiamo che è uguale ed opposta a quella rimasta all'esterno, che chiamiamo $$\Delta Q$$
Quindi abbiamo che

$$
\Delta Q = \oint_{\Sigma}\vec{P} d\vec{s} = \int _{V(\tau)} \vec{\nabla} \cdot\vec{P} \, d\tau
$$

Dove abbiamo utilizzato il teorema della divergenza spiegato in [Divergenza e Circuitazione](/notes/divergenza-e-circuitazione)
Allora, motivati dal fatto che internamente $$Q' = \int _{V(\tau)} \rho \, d\tau$$
Possiamo definire 

$$
\vec{\nabla} \cdot \vec{P} = - \rho_{i}
$$

Ossia la divergenza del momento di dipolo per unità di volume è uguale a meno densità di volume elettrico indotto internamente.

#### Equazioni di Gauss rivisitate 🟩
Possiamo ora aggiornare le equazioni di gauss andando a contare gli effetti del dipolo in modo esplicito, abbiamo che

| Forma divergente                                            | Forma integrale                            |
| ----------------------------------------------------------- | ------------------------------------------- |
| $$\vec{\nabla} \cdot \vec{E} = \frac{\rho}{\varepsilon_{0}}$$ | $$\oint_{\Sigma} \vec{E} \cdot d\vec{s}$$     |
| $$\vec{\nabla} \times \vec{E} = 0$$                           | $$\oint_{\Gamma} \vec{E} \cdot d\vec{s} = 0$$ |
| $$\vec{\nabla} \cdot \vec{P} = -\rho_{p}$$                 | $$\oint_{\Sigma} \vec{P} \cdot d\vec{s} = Q_{p}$$   |
| $$\vec{\nabla} \cdot \vec{D} = \rho_{\text{libero}}$$ | $$\oint_{\Sigma} \vec{D} \cdot d\vec{s} = Q_{L}$$|

Andiamo ad osservare la forma divergente di Gauss, abbiamo che $$\rho = \rho_{libero} + \rho_{pol}$$ ossia della carica libera più quella indotta da polarizzazione, approfondendo quello deriviamo:

$$
\vec{\nabla} \cdot \vec{E} = \frac{\rho_{libero}}{\varepsilon_{0}} + \frac{\rho_{pol}}{\varepsilon_{0}} 
\implies \varepsilon_{0} \vec{\nabla} \cdot \vec{E} = \rho_{libero} - \vec{\nabla} \cdot \vec{P}
\implies \vec{\nabla}(\varepsilon_{0} \vec{E} + \vec{P}) = \rho_{libero}
$$


#### Vettore di spostamento elettrico/induzione dielettrica 🟩
Il vettore che abbiamo trovato poco sopra ha un significato speciale, proviamo ad analizzare proprietà di

$$
\vec{D} = \varepsilon_{0}\vec{E} + \vec{P}
= \varepsilon_{0}(\vec{E} + \chi \vec{E})
= k\vec{E}\varepsilon_{0} = \varepsilon \vec{E}
$$

Con questo poi possiamo ri-caratterizzare il vettore di momento di dipolo come

$$
\vec{P} = \frac{k-1}{k} \vec{D}
$$

Possiamo notare che il vettore di spostamento non è altro che il campo elettrico per un dielettrico differente.

Che saranno una conseguenza diretta delle equazioni di sopra:

$$
\vec{\nabla} \cdot \vec{D} = \rho_{libero}
$$


$$
\oint_{\Sigma} \vec{D} \cdot d\vec{s} = Q_{L}
$$

Ossia questo è un valore che **dipende solamente dalla carica LIBERA**, per questo vettore di spostamento posso ignorare il valore di polarizzazione indotta.


### Discontinuità nei dielettrici

Sappiamo che le componenti tangenti vengono conservate passando da una superficie all'altra (vedi [Campo elettrico](/notes/campo-elettrico)), e anche le discontinuità per componenti perpendicolari. Ora vogliamo vedere se vale la stessa cosa nei dielettrici, quando abbiamo solamente cariche di polarizzazione, ed entrambi valgono ancora (ma la sigma nel secondo caso è di polarizzazione)

#### Discontinuità superficiale 🟩--

$$
\oint_{\Sigma}\vec{E} d\vec{s} = \frac{Q_{T}}{\varepsilon_{0}}
\implies \Delta E_{\perp} = \frac{\sigma_{p}}{\varepsilon_{0}}
$$

Da quanto fatto col **vettore di spostamento** avrebbe senso vedere cosa succede in quel caso.
dato che dipende solamente da cariche libere abbiamo che


$$
\oint_{\Sigma}\vec{D} d\vec{s} = Q_{Libero} = 0
$$

Quindi il vettore di spostamento per il dielettrico è ancora *costante*, non varia diciamo passando da una superficie all'altra, quindi **è continua.**

Andiamo a fare la stessa analisi in immagine, assumendo che $$dh \to 0$$ quindi non abbiamo flusso verticale
<img src="/images/notes/Condensatori con dielettrici-1698655065772.jpeg" alt="Condensatori con dielettrici-1698655065772">

$$
\vec{D}_{1}d\vec{S}_{1} + \vec{D}_{2}d\vec{S}_{2} = 0
\implies \vec{D}_{1}\cos \theta_{1} + \vec{D}_{2} \cos \theta_{2} = 0
\implies D_{1}\cos \theta_{1} - D_{2} \cos \theta_{2} = 0
$$

Quindi

$$
\Delta D_{N} = 0
$$


#### Legge di Snell revisited 🟩--
Una volte descritte le equazioni di continuità ricavare questo è molto semplice, poi è molto molto simile (opposto) a quanto fatto per [Magnetismo nella materia](/notes/magnetismo-nella-materia) per la continuità dei campi magnetici nel passare su superfici con correnti.

<img src="/images/notes/Condensatori con dielettrici-1698655424494.jpeg" alt="Condensatori con dielettrici-1698655424494">
Sappiamo che $$E_{\parallel}^{1} = E_{\parallel}^{2}$$, che $$E_{\perp}^{1} = E_{\perp}^{2}$$ e che $$D_{\perp}^{1} = D_{\perp}^{2}$$
E che $$\vec{D} = \varepsilon_{0}k\vec{E}$$
Da quello sappiamo che 


$$
\varepsilon_{0} k_{1} E^{1}_{\perp} = \varepsilon_{0}k_{2}E_{\perp}^{2}
$$

Riscrivendo le relazioni precedenti abbiamo:

$$
\begin{cases}
E_{1}\sin \theta_{1} = E_{2}\sin \theta_{2} \\
k_{1}E_{1}\cos \theta_{1} = k_{2}E_{2} \cos \theta_{2}
\end{cases}
\implies
\frac{\tan \theta_{1}}{k_{1}} = \frac{\tan \theta_{2}}{k_{2}} 
\implies
\frac{k_{2}}{k_{1}} = \frac{\tan \theta_{2}}{\tan \theta_{1}}
$$

Quindi so esattamente in che modo il modulo e la direzione di $$E$$ cambia all'interno della superficie di separazione dei mezzi.
Quindi se passo da superficie con $$k_{2}$$ più alto i raggi tendono verso l'esterno (angolo più grande), e stessa cosa al contrario.
![ 500](/notes/condensatori-con-dielettrici-1698655976503.jpeg-)

NOTA: **il modulo del campo elettrico cambia sempre**.
NOTA-2: basta guardare le linee di campo per sapere se il materiale è conduttore o meno (perché per il conduttore cambia le linee di campo anche all'esterno).

### Energia nei condensatori con dielettrico (!)
#### Derivazione con dielettrico 🟩--
Sappiamo che l'energia totale è ancora

$$
U_{e} = \frac{1}{2} CV^{2} = \frac{1}{2} \frac{\varepsilon S}{d} V_{k}^{2} = \frac{1}{2} \varepsilon S E_{k}^{2}d = \frac{1}{2}\varepsilon E_{k}^{2} (Sd) = u_{e} \cdot \text{ Volume}
$$

Solo che è da considerare la $$E_{k}$$ presente con il dielettrico che è uguale a $$\frac{E_{0}}{k}$$
Possiamo calcolarlo anche in altro modo:

$$
U = \frac{1}{2} \frac{Q^{2}}{C} 
= \frac{1}{2} (\sigma S)^{2} \cdot \frac{d}{\varepsilon S} = \frac{1}{2} \varepsilon\frac{\sigma^{2}}{\varepsilon^{2}} \cdot Sd
= 
\frac{1}{2}\varepsilon E^{2} \cdot Sd
$$

E viene ugualmente come prima

#### Con vettore di spostamento 🟩
abbiamo, considerando che $$\vec{D} = \varepsilon \vec{E}$$, vale per dielettrico isotropo, ma per quello anisotropo, in cui non sono più paralleli come si fa?


$$
u_{E} = \frac{1}{2} \varepsilon E^{2}_{k} = \frac{1}{2} \frac{D^{2}}{\varepsilon}
$$


A parità di campo elettrico, spendo molta quantità di energia in più per caricarlo.

#### Materiale anisotropo 🟩--

$$
u_{E} 
= \frac{1}{2}\varepsilon E^{2}
= \frac{1}{2} \vec{E} \cdot \vec{D}
$$

Perché devo contare la parte parallela.