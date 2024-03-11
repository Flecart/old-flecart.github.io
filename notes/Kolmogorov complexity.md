---
layout: page
permalink: notes/kolmogorov-complexity
tags: italian
title: Kolmogorov complexity
---

Gran parte di quanto scrivo ora è tratto da @liIntroductionKolmogorovComplexity2019.
Chaitin, Kolmogorov e Solomonoff hanno elaborato il tema in modo indipendente e allo stesso tempo verso gli anni '60!

Solomonoff lo ha trovato sul problema dell'induzione all'età di 38 anni, Kolmogorov invece era già tardi, ha già trovato gli assiomi della probabilità e poi nel 65 cerca randomness. Mentre Chaiten Information = Computation e non probabilità, nel 68 all'età di 19 anni.
In AI teorico questo sembra un tema molto importante.

Ci sono degli esempi carini nella compressione di numeri naturali e stringhe binarie in [Introduction to Algorithmic Information and Complexity](/notes/introduction-to-algorithmic-information-and-complexity).
### Intuizione Kolmogorov
Per quanto ho capito io sulle motivazioni che sono state base alla creazione di questo concetto è il concetto che: *per descrivere cose complesse c'è necessità di più parole*.
Questa idea molto intuitiva la possiamo tradurre da un punto informatico come **il programma più corto per produrre un certo output**.

Un esempio classico è una comparazione fra una stringa *01010101010101* contro una altra del tipo *11101111111100101011110000010101*.
Intuitivamente potremmo dire che la prima stringa sia molto più semplice da descrivere rispetto alla seconda stringa, abbiamo però bisogno di un modo formale per descrivere questo concetto.

## Formalizzazione
### Definizione Kolmogorov
> Definiamo la complessità di Kolmogorov $$K_{L}(\omega )$$ per un certo linguaggio di programmazione $$L$$ come la minima lunghezza del programma tale per cui se eseguita sulla macchina astratta di $$L$$ dia come output $$\omega$$.

Questa definizione si può riscrivere come

$$
C(x) = \min_{p}\left\{ length(p) : U(p) = x \right\} 
$$

Ossia il programma più corto che se eseguito su una macchina di Turing completa ho $$x$$.

NOTA: questa definizione seppur meno informale di prima, non è ancora quella formalmente accettata, però fa il suo per trasmettere l'idea, vedere il libro [^2] per definizione matematicamente corretta (e anche molto più astrusa)

**Complessità condizionale**
> la complessità di Kolmogorov condizionale $$K_{L}(\omega | x)$$ è la lunghezza minima di un programma che prende in input $$x$$ e produce in output $$\omega$$. (si legge proprio come se fosse un qualcosa di condizionato)

**LEMMA**
Ora diventa chiaro che un programma che stampa una qualunque stringa, sia sufficiente per dare in output, per questo motivo vale che:

$$
K(x) \le \lvert x \rvert  + c \tag{1}
$$

Dove $$c$$ è una costante per codificare le istruzioni per stampare.
Più intuitivamente un programma di questo genere può stampare il carattere (dimostreremo in seguito, in [#Teorema dell'invarianza](#teorema-dell-invarianza) che idea simile vale per ogni linguaggio)

Questo lemma giustifica anche la seguente definizione
#### Stringhe incomprimibili

> una stringa $$\omega$$ si dice *incomprimibile* nel momento in cui $$K(\omega) = \lvert \omega \rvert + O(1)$$

Che insieme all'upper bound di sopra, si avrà che è il massimo di complessità che può avere.

#### Kolmogorov condizionato
Condizionato $$K(A|B)$$ significa che diamo alla nostra macchina di turing in input anche $$B$$ per codificare $$A$$. Puoi vedere subito che la complessità di $$K(A|A)$$ è $$0$$ perché la macchina di turing può non fare nulla $$\varepsilon$$ è il programma diciamo, e avere subito un risultato.
Intuitivamente avere qualcosa in più non fa altro che ridurre il codice necessario, quindi possiamo dire che $$K(A|B) \leq K(A)$$. E qui si può creare anche una nozione di indipendenza.

#### Chain Rule
Afferma che per qualunque oggetto vale che

$$
K(A|B) \geq K(A, B) - K(B)
$$

Ossia la codifica di entrambi, sia $$A$$ che $$B$$ è necessariamente minore di codificare prima $$B$$ e poi usare questa per codificare $$A$$. Si può dimostrare ma intuitivamente questa legge sembra parlare in modo chiaro.

Questo vale se assumiamo che tutte le parole godano della *Prefix Property* [Bottom-up Parser LR(1)](/notes/bottom-up-parser-lr(1))[Algorithmic Probability](/notes/algorithmic-probability).
Se non vale la regola diventa

$$
C(s_{1}) \leq C(s_{2}) + C(s_{1} | s_{2}) + O(\log(C(s_{2})))
$$

Il motivo di questo $$O$$ grande strano è che 
> $$\log(C(s_{2}))$$ is the maximal length of the information needed to separate the program that computes $$s_{2}$$  from what comes next (as we cannot guarantee that this program is uniquely decodable, contrary to the prefix case).

Ma non lo ho capito ancora bene.

#### Incomputabilità di Kolmogorov

Dimostrazione:
Supponiamo che sia computabile, allora abbiamo un programma $$P$$ che calcola il programma minimo.
Ora possiamo usare questo programma per trovare una stringa la cui complessità di Kolmogorov sia più lunga di un certo $$n$$. Questo si può fare provando ad aggiungere roba (probabilmente qui mi serve un lemma che dice che è crescente stretto e non lasco).
Ma la complessità di questa nuova stringa trovata deve essere uguale alla complessità di $$n$$, che gli dò in input! (più costante per la ricerca che ignoro per Kolmogorov).
Questo significa che $$K(n) > n$$ che è assurdo perché $$K(n) \approx \log_{2}(n)$$ che è strettamente minore di $$n$$.

Possiamo però approssimare il valore, e per molte cose questo basta!

> Kolmogorov complexity is an ideal notion that can be approximated, but that is not computable.

Un pseudocodice di esempio per computare una cosa più complessa (anche se non ho la dimostrazione che fa quello che deve fare, perché in teoria credo può continuare in modo arbitrariamente lungo, solo che la probabilità che non finisca tende a 0)
```python
def MoreComplex(n):  
    i =1  
    while True:  
        for m in range(2**i):  
            s = bin(m)[2:]      
            if cc(s) > n:    return s  
        i += 1
```
### Teorema dell'invarianza

Questo è un teorema fondamentale (e anche di base) per quanto riguarda la definizione della teoria inerente a questa complessità. Ci permette di affermare che il concetto di complessità è **indipendente dal linguaggio di programmazione utilizzato**, e ci darà presto anche alcuni risultati interessanti sulla computabilità di questa funzione (in modo diverso rispetto alle classiche dimostrazioni che si possono trovare in teoria della computabilità). Quindi questo teorema è *fondamentale* per stabilire **l'oggettività** della proprietà. Così possiamo dire che è una proprietà dell'oggetto, non di come lo stai valutando. Quindi non dipende dalla capacità/architettura di chi sta valutando il linguaggio.

> Siano $$L$$ e $$L^{'}$$ due linguaggi Turing completi, allora per ogni stringa $$\omega$$ si ha che $$K_{L}(\omega) = K_{L^{'}}(\omega)  + O(1)\tag{2}$$

**Dimostrazione**:
Essendo $$L$$ e $$L^{'}$$ dei linguaggi Turing completi, allora posso scrivere un programma in $$L^{'}$$ che esegua la macchina astratta di $$L$$ e quindi mantenga tutta la semantica del linguaggio $$L$$ (vedere [Macchine Astratte](/notes/macchine-astratte) per la definizione di interprete).  
Allora si avrà che 

$$
K_{L^{'}}(w) = K_{L}(\omega) + |I| \tag{2.1}
$$

ossia il costo per esprimere la complessità della string $$\omega$$ in $$L^{'}$$ è equivalente al costo per esprimere il programma $$p$$ in $$L$$, ed eseguirlo con un interprete (che avrà una lunghezza finita, e costante una volta fissato i due linguaggi).
L'interprete esiste perché stiamo usando macchine di Turing universali per la descrizione della lunghezza.

NOTE:
Grazie a questa proprietà da ora in poi potremo parlare di  $$K(\omega)$$ **indipendentemente da linguaggio** su cui è stato scritto, dato che tanto distano di una costante uno dall'altro.

NOTE2:
È una cosa molto curiosa il fatto che sia dipendente dall'osservatore, anche se abbiamo una differenza, perché cose importanti per qualcuno, sono codificate in modo differente da ognuno. Questo è un pensiero molto deep, e l'esempio della versione della macchina è chiaro.

#### Esistenza di stringhe complesse

Un risultato importante che sarà utile alla dimostrazione della non computabilità della funzione di complessità di Kolmogorov è la seguente:> 

$$
\forall n \in \mathbb{N}, \exists \omega : K(w) \geq n
$$


che è un risultato che non sembra avere molto senso perché ci sta dicendo che esistono delle stringhe di complessità infinita (forse queste stringhe sono quelle non computabili, perché il programma che lo descrive dovrebbe avere lunghezza infinita).

**Dimostrazione**:
La dimostrazione di questo teorema non è altro che una applicazione del pigeonhole principle. In un certo senso salta fuori dalla relazione fra il finito e l'infinito, come quelle cose assurde che $$2n$$ è in bigezione con i numeri naturali.
Siamo nel mondo di Turing, quindi i programmi saranno anch'esse delle stringhe binarie.
Consideriamo tutti i programmi di lunghezza zero. Questo produrrà la stringa vuota, ossia la stringa di complessità zero.
Supponiamo ora tutti i programmi di lunghezza uno. Al massimo potremo avere due stringhe con questa complessità.
E così via. Intuitivamente: dato che il numero delle stringhe $$\omega$$ che possono esistere sono infinite, anche i la lunghezza dei programmi utilizzati per generare queste stringhe sono infinite, perché banalmente un programma di lunghezza $$n$$ può generare al massimo $$2^n$$ stringhe diverse, un numero finito, anche se enormemente ampio.

#### Non calcolabilità della funzione di Kolmogorov
> La funzione di Kolmogorov non è calcolabile su un macchina di Turing

**Dimostrazione**:
Supponiamo che esista una macchina di Turing $$M$$ che prenda in input una stringa $$\omega$$ e ritorni $$K(\omega)$$. Utilizzeremo il teorema [#Esistenza di stringhe complesse](#esistenza-di-stringhe-complesse)

Allora utilizziamo questa macchina di Turing $$M$$ per costruirne una altra $$M^{'}$$ che si comporti in questo modo:
```
input n
for each string w in alphabet:
do
	if K(w) >= n:
		return w
done
endfor
```
In pratica vado a scorrere tutte le parole nell'alfabeto infinito, so che prima o poi troverò una stringa tale per cui $$K(w) \geq n$$ perché ne abbiamo dimostrato l'esistenza precedentemente. Questa macchina allora descriverà la stringa $$\omega$$ che viene in output, dato l'input $$n$$.

Ma allora abbiamo che

$$
n \leq K(\omega) \leq \lvert \langle M^{'}, n \rangle    \rvert + O(1) = O(1) + \lvert n \rvert = O(1) + O(\log(n)) = O(\log(n))  
$$


Ed è assurdo perché afferma che $$O(n) \leq O(\log(n))$$ che sarà vero per $$n$$ abbastanza alto.


#### Upper bound con entropia
Kolmogorov si può vedere come una cosa più generale dell'entropia di Shannon [Entropy](/notes/entropy), si può vedere come una **approssimazione di essa** perché basta prendere
$$L \approx \log_{2}\left( \frac{1}{p} \right)$$ e si ha l'entropia Shannoniana.
La cosa carina è che Kolmogorov ha senso anche in assenza di frequenze e probabilità.
## Cose che non ho capito
Per qualche motivo la complessità di un oggetto scende quando l'entropia è massima (ah, quando sono tutti uguali le probabilità, la complessità scende)

## Parte vecchia dal libro di complexity
Questo è il teorema fondamentale di questo campo, che ricordiamo prova a cercare di creare una teoria sulle descrizioni di minima lunghezza per qualcosa, questo dovrebbe essere in grado di risolvere il problema del limite della probabilità, e cose di teoria dell'informazione che non ho ancora ben compreso.

Comunque si è notato che si può definire una classe di equivalenza, e fra queste esiste una classe speciale che è quello di descrizione minima. Partiamo però dalla definizione di di complessità diciamo:

$$
 C_{f}(x) = min\{l(p) : f(p) = n(x)\}
$$

$$f$$ è una macchina di turing.

Una volta definito questo e creato un insieme fisso di *macchine* o funzioni si può estendere questo modello in classi di equivalenza, perché possiamo utilizzare $$\langle n, p \rangle$$ on $$n$$ l'index alla macchina corretta e $$p$$ il nostro programma (anche se non ho capito perché si assume che il programma sia comprensibile a qualunque macchina, e non ho capito perché la funzione la si può intendere come se fosse una macchina, questa è una parte di teorica che mi dovrei recuperare).

Comunque fatto questo, si può mostrare come data una sequenza contabile di funzioni $$\phi_{1}, \phi_{2}, \dots, \phi_{n}$$ allora posso andare a definirmi $$\phi_{n}(p) = \phi_{0}(\langle n, p \rangle)$$ anche se non ho capito cosa voglio dire qui, con $$\phi_{0}$$ la funzione computata da una macchina di Turing universale $$U$$ . Indicheremo 
$$
C_{\phi_{0}}(x) = C(x)
$$
 per ogni programma $$x$$. 


[^1]: [https://jeremykun.com/2012/04/21/kolmogorov-complexity-a-primer/.](https://jeremykun.com/2012/04/21/kolmogorov-complexity-a-primer/.)