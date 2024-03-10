---
layout: page
permalink: notes/modelli-lineari-di-sviluppo
tags: italian
title: Modelli Lineari di sviluppo
---

## Introduzione ai modelli lineari

### Processi di sviluppo
#### Definizione
> L’insieme strutturato di attività, eventi, documenti e procedure necessari per la costruzione di un sistema software

#### Cosa viene descritto (4) 🟩

Questo è proprio quanto vuole studiare l'ingegneria del software -> **metodi di sviluppo**, in modo da portare i migliori risultati possibile.

Nella formazione classica va a definire 4 concetti (soprattutto utili nel lavoro di gruppo, al fine di comunicare nella maniera più efficace):
1. Chi fa
2. Cosa viene fatto
3. Quanto la fa
4. Come la fa
In breve si vanno a definire **l'attività di persone** che collaborano allo sviluppo di un software, informazioni come:

- In che modo lavorano?
- Quali sono i ruoli e le responsabilità di ognuno?
- Come valutare la qualità del lavoro?
- Quali documenti produrre?

#### Ciclo di vita del software 🟨
Trattando il software come una entità viva, sono tutte le parti che partono dalla creazione fino alla sua *morte*, ossia dismission.
> Fasi della vita, da ideazione, sviluppo, rilascio, mantenimento e deprecazione.

Andiamo a capire quali sono i metodi principali 

### Altre note
#### Legge di Conway 🟨+
> Le organizzazioni che progettano sistemi ne progettano la struttura riproducendo le proprie strutture comunicative (es. l’organigramma)

Riformulando in qualche modo: l'architettura del prodotto finale rispecchierà il modo con cui i creatori hanno comunicato fra di loro.
Ossia **alcune proprietà del sistema vengono influenzate dal processo di costruzione**. Quindi non è trasparente questa parte, almeno è molto difficile renderlo tale.

Esempio:
> se 4 team collaborano a costruire un compilatore, la struttura finale sarà su 4 processi in pipeline

#### Legge di Brooks
> Aggiungere personale ad un progetto sw in ritardo lo farà ritardare ancora di più

Perché in altri campi aggiungere uomini lo fa andare più in fretta, ma nel nostro caso rallenta, perché dovrà esserci tempo per insegnare le conoscenze necessarie per cominciare.

#### Software come processo sociale 🟩

Data l'osservazione di sopra, è chiaro che il processo di sviluppo è **fortemente influenzato dai processi di comunicazione interni**, che sono un aspetto puramente sociale di questa disciplina. Ecco che entra in gioco questo aspetto delle persone e della comunicazione.
Dall'altro lato, se la costruzione ha un aspetto sociale in sé, anche l'effetto ha una parte sociale. Guarda per esempio i social, hanno cambiato radicalmente il nostro modo di comunicazione fra persone. (un esempio sulla slide è la banca per esempio)

#### Modello di processo software (4) (!) 🟩
>**Insieme di processi software** che provano a catturare un punto di vista specifico il processo software

TODO: approfondire? Sembra molto stupido
**Esempi di modelli**
<img src="/images/notes/Modelli Lineari di sviluppo-1698072618825.jpeg" alt="Modelli Lineari di sviluppo-1698072618825">
### Waterfall 🟩
Questo è uno dei modelli di processo più vecchi (ormai in disuso per il software), è un **processo lineare**.
#### Esempio sviluppo classico
<img src="/images/notes/Modelli Lineari di sviluppo-1698072676047.jpeg" alt="Modelli Lineari di sviluppo-1698072676047">

Una osservazione principale è che **alcuni ruoli** sono fermi in certi momenti del waterfall, per esempio lo sviluppatore dovrebbe aspettare di ricevere le specifiche sviluppate dall'architetto, che deve sapere ciò che il cliente vuole dal business analyst.

#### Positive e negative di waterfall 🟩-
- Chiara definizione dei requisiti fino all'inizio
- Feedback solamente finale dal cliente.
- **Fasi bloccanti** 
Il problema principale è che **il mercato cambia più velocemente** dello sviluppo, quindi altra probabilità che il requisito cambi prima della fine dello sviluppo.
Per il software questo non sembra proprio una strategia buona per dire!


## Note di ripasso

| Data | Commenti |
| ---- | -------- |
|      |          |