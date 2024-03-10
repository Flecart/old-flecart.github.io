---
layout: page
permalink: notes/the-neuron
tags: italian
title: The Neuron
---

### La struttura del neurone

<img src="/images/notes/The Neuron-1704379209888 1.jpeg" alt="The Neuron-1704379209888 1">
#### Parti strutturali principali (2) 🟩

Possiamo identificare tre parti principali per quanto riguarda la struttura di un singolo neurone
1. **Assoni** che si occupano di mandare *activation potential* signal all'esterno, a comunicare con altre cellule. Il segnale che parte dall'assone inizia da una sezione che viene chiamato **segmento iniziale**.
2. **Dentriti** che si occupano di ricevere segnali da altri neuroni.

Gli assoni e dentriti non sono connessi, ma c'è un piccolo spazio in mezzo a questi che si chiama *Synaptic cleft*, (la scoperta di questo è stato di stupore, in passato pensavano che fosse una cosa continua il cervello, invece abbiamo qualche piccola unità discreta, scoperto con la *colorazione d'argento* metodi di **Golgi**) l'informazione in questo spazio *pre* e *post* sinaptico è gestito da neurotrasmettitori.

Solitamente per un singolo neurone siamo nell'ordine di grandezza dei *micrometri*

Possiamo anche analizzare il neurone da un punto di vista delle parti **funzionali** principali, in tal caso diventano 4, come espressi in immagine, per tipologie di neuroni differenti.
<img src="/images/notes/The Neuron-1704381047236 1.jpeg" alt="The Neuron-1704381047236 1">
La cosa magicamente interessante è che i collegamenti possono essere tanto diversi, ma rispettare alla fine un concetto simile abbastanza coerente delle parti (in un certo senso anche qui troviamo il ragionamento per astrazioni comune in informatica, probabilmente dal punto di vista fisico dei neurotrasmettitori ci saranno cose diverse, ma offrono la stessa interfaccia in cui attaccarsi per così dire).

#### Classificazioni dei neuroni 🟩
Ci sono molte tipologie di neuroni in natura, specialmente differiscono a seconda se stiamo parlando di vertebrati o invertebrati.
In generale possiamo caratterizzarli in 
- *Unipolar*
- *Bipolar*
- *Multipolar*

Che viene riassunto dal diagramma sottostante.
Solitamente i multipolar sono dei vertebrati.
<img src="/images/notes/The Neuron-1704379569293 1.jpeg" alt="The Neuron-1704379569293 1">

#### Convergenza e divergenza 🟩

Questa è una cosa che probabilmente non abbiamo in modo naturale nelle reti, si parla di **divergenza** del segnale neuronale nel momento in cui un singolo neurone eccitato va a comunicare con molti neuroni, potenzialmente attivandone molti.
**Convergenza** invece quando un neurone, prendiamo caso quello incaricato per fare contrarre il muscolo, deve prendere input da molti neuroni sensoriali, e quindi decidere se si deve contrarre o estendere a seconda di questa informazione.

#### Ramón two principles 🟨
Veder 24 del KANDEL
**Principle of dynamic polarization**: afferma che l'eccitazione di un neurone va linearmente in un verso (prolly per escludere il fatto che torni indietro)

**Connectional specificity**: afferma che c'è un senso, una semantica per così dire, sul perché certi neuroni sono connessi assieme.


### Cellule Gliali
#### Funzione ed etimologia 🟩
Solitamente queste cellule, come dice il nome stesso latino, simile all'inglese *glue*, sono cellule di collegamento, ossia permettono la comunicazione corretta fra un neurone all'altro.

#### Tipologie di cellule gliali (3) 🟨
<img src="/images/notes/The Neuron-1704379717680 1.jpeg" alt="The Neuron-1704379717680 1">
I primi formano la mielina per gli assoni nel sistema centrale, i secondi in quello periferico (è un burrito, molti avvolgimenti).
I terzi non si conosce la funzione.

### Circuiti neuronali

Sono dei pattern di collegamento che si possono trovare fra i neuroni. In modo naturale si sviluppano dei piccoli sistemi che inibiscono o eccitano i propri vicini in qualche modo speciale.
TODO: capire perché sono importanti.
#### Feedforward inhibition

#### Feedback inhibition

### Sinapsi
Sono il collegamento che esiste fra un neurone e un altro, quindi potremmo intenderlo come il **canale di comunicazione** fra un neurone e un altro.
#### Gap Junction 🟩
<img src="/images/notes/The Neuron-1704441720132.jpeg" alt="The Neuron-1704441720132">
Sono dei collegamenti più diretti fra i neuroni, e permettono di passare ioni di eccitazione in modo abbastanza diretto (questa è la differenza con quelli basati su cose chimiche), è un circuito più simile a quello elettronico, perché è **più veloce**.

Solitamente è necessario per cose veloci, quando vogliamo fare andare dei neuroni assieme, come i *arc reflexes*.

#### Chemical based🟩
Sono delle porte più lente, i classici, quelli che poi andiamo a chiamare **neurotrasmettitori**, quando abbiamo un potenziale di azione, le vesicles vengono rilasciate nello spazio intracellulare, sull'altro neurone ci sono dei recettori che prendono questi neurotrasmettitori e si attivano di conseguenza.

La cosa interessante di questo metodo è che il **recettore può cambiare porte** per capire quanto gli importa questa nuova informazione. (quindi se gli importa quel segnale, può aumentare il numero di porte altrimenti diminuirle, almeno questa è la teoria).



La corteggia cerebrale consiste in una fra le parti più importanti del cervello. Consiste in **6 strati uniformi** di neuroni che seguono un pattern simile.

1, 4 hanno input da *higher* cortical areas, 4 da parti sottocorticali, 6, con quelle interne come talami.

#### Correlazioni con tempo di action potential
Fra due neuroni che comunicano, c'è una correlazione abbastanza evidente che implica un aumento della forza della connessione (*synaptic strength*)  con il tempo degli spykes.
<img src="/images/notes/The Neuron-1704442181344.jpeg" alt="The Neuron-1704442181344">
**Long Term Depression** e **Long Term Potentiation** si chiamano.

EPSP è **Excitatory Post-Synaptic potentiation**, nell'immagine vediamo che se il secondo neurone si attiva dopo che si è attivato il primo neurone, allora tendono a potenziare il segnale, altrimenti diminuire.

Per la diminuzione ha senso perché è come se io ti dessi indietro il segnale (anche se non necessariamente connessi), oppure l'altro è stanco lol.


## Note di ripasso

| Data | Commenti |
| ---- | -------- |
| 07/01/2024     | Ok.         |

# Tabella degli studi
Kantel ha tantissimi capitoli, provo a dare un ordine di importanza ad ognuno in modo da strutturare lo studio.
Alla fine mi interessano le cose comuni con AI, non mi interessa la biologia, ma solamente i **processi**.

| Capitolo | Importanza | Studiato | Commento? |
| ---- | ---- | ---- | ---- |
| 1 | 🌗🌑🌑 |  |  |
| 2 | 🌕🌕🌕 | 🟩 |  |
| 3 | 🌑🌑🌑 |  |  |
| 4 | 🌗🌑🌑 |  |  |
| 5 | 🌗🌑🌑 |  |  |
| 6 | 🌕🌗🌑 |  | Come caratteristiche elettriche permettono il neurone di comunciare |
| 7 | 🌕🌑🌑 |  |  |
| 8 | 🌕🌑🌑 |  |  |
| 9 | 🌗🌑🌑 |  |  |
| 10 | 🌑🌑🌑 |  | bleah, troppo sui recettori specifici. (GABA?) |
| 11 | 🌑🌑🌑 |  | Ancora cose biologiche, sembra più sui neurotrasmettitori |
| 12 | 🌑🌑🌑 |  | Come vengono rilasciati i neurotrasmettitori |
| 13 | 🌗🌑🌑 |  | Neurotrasmettitori in modo approfondito, solo per cultura personale questo è figo. |
| 14 | 🌑🌑🌑 |  | Malattie del sistema motorio, inutile per me. |
| 15 | 🌕🌑🌑 |  | Come è strutturato il sistema nervoso centrale, anche se noioso, sembra necessario |
| 16 | 🌗🌑🌑 |  | Come viene processato le informazioni sensoriali, questo nice. |
| 17 | 🌕🌕🌑 |  | Come movimento viene mappato, anche pensiero interno |
| 18 | 🌕🌗🌑 |  |  |
| 19 | 🌑🌑🌑 |  |  |
| 20 | 🌑🌑🌑 |  | functional imaging bleah |
| 21 | 🌕🌕🌗 |  | Sensory coding, questo sembra molto importante per representation learning. |
| 22 | 🌗🌑🌑 |  |  |
| 23 | 🌑🌑🌑 |  |  |
| 24 | 🌗🌑🌑 |  | Sui recettori del dolore, può essere interessante ma inutile per AI i suppose?! |
| 25 | 🌕🌗🌑 |  | Come siamo organizzati noi per gestire informazioni visive. |
| 26 | 🌗🌑🌑 |  | Come manda informazioni sulle cose visive al cervello. |
| 27 | 🌗🌑🌑 |  |  |
| 28 | 🌗🌑🌑 |  |  |
| 29 | 🌑🌑🌑 |  | relazione con azione |
| 30 | 🌑🌑🌑 |  | Connessioni nervose orecchio interno!? |
| 31 | 🌑🌑🌑 |  | udito |
| 32 | 🌑🌑🌑 |  | sapore |
| 33 | 🌕🌗🌑 |  | Come pianifichiamo il movimento, questo magari per robotica è interessante |
| 34 | 🌑🌑🌑 |  |  |
| 35 | 🌑🌑🌑 |  |  |
| 36 | 🌑🌑🌑 |  |  |
| 37 | 🌑🌑🌑 |  |  |
| 38 | 🌑🌑🌑 |  |  |
| 39 | 🌗🌑🌑 | 🤔<br> | Parla di coordinazione occhi, questo può essere interessante, ma inutile per noi. |
| 40 | 🌑🌑🌑 |  |  |
| 41 | 🌑🌑🌑 |  |  |
| 42 | 🌗🌑🌑 |  | Sul cervelletto, non so perché potrebbe interessarmi, ma anche questo inutile |
| 43 | 🌑🌑🌑 |  |  |
| 44 | 🌑🌑🌑 |  | Malattie genetiche, proprio no direi. |
| 45 | ? |  |  |
| 46 | 🌗🌑🌑 | 🤔 | Sulle funzioni automatiche (tipo sleep-wake) mi può interessare |
| 47 | 🌑🌑🌑 |  |  |
| 48 | 🌕🌗🌑 |  | Controllo emozioni |
| 49 | 🌕🌕🌑 |  | Sulle dipendenze |
| 50 | 🌑🌑🌑 |  | bleah, epilessia. |
| 51 | 🌕🌕🌗 |  | Sonno e sogni |
| 52 | 🌗🌑🌑 |  | Sviluppo del cervello |
| 53 | 🌑🌑🌑 |  |  |
| 54 | 🌗🌑🌑 | 🤔 | Come cresce la cellula neuronale |
| 55 | 🌕🌗🌑 |  | Come tolgo e rimetto i collegamenti di assoni |
| 56 | 🌕🌗🌑 |  | Come vengono modificati i collegamenti nel tempo. |
| 57 | 🌕🌗🌑 |  | Come viene gestito il danno all'architettura (riconfigurazione) |
| 58 | 🌗🌑🌑 | 🤔 | differenze neuronali in sessi diversi |
| 59 | 🌑🌑🌑 |  |  |
| 60 | 🌕🌕🌗 |  | Controllo sul linguaggio |
| 61 | 🌕🌕🌑 |  | Su cose conscie ed inconscie, e malattie a riguardo. |
| 62 | 🌑🌑🌑 |  |  |
| 63 | 🌑🌑🌑 |  |  |
| 64 | 🌑🌑🌑 |  |  |
| 65 | 🌕🌕🌕 |  | Memoria ed apprendimento. |
| 66 | 🌕🌕🌗 |  | Memoria a livello neuroni. |
| 67 | 🌕🌕🌗 |  |  |