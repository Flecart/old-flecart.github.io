---
layout: page
permalink: notes/modelli-agile
tags: italian
title: Modelli AGILE
---

### Socialità dello sviluppo del software (3) 🟨-
Si assume che
- È difficile assegnarsi i compiti, bisogni di utenti, tempi di consegna (+ persone difficile)
- È facile scrivere software (almeno software classico, e non computazione scientifica)
- La gente sia brava tecnicamente che socialmente è una cosa rara

### VS Waterfall (3) 🟨++
Pianificare tutto come viene descritto nel modello del waterfall non è possibile.
Per i seguenti motivi
- Non è chiaro cosa vuole l'utente finale (quindi sarebbe meglio avere feedback continuo).
- Non si sa già dall'inizio cosa è che interessa all'utente, per questo motivo si consegna il prodotto passo passo per **feedback continuo** dato che i requisiti cambiano nel tempo.

#### Giustificazione agile alto livello 🟩
Vorremo una metodologia che permetta una **iterazione** ossia un cambio continuo specifiche in funzione di un **utente**, vogliamo fare le cose a seconda di quanto vuole l'utente.

## Metodologia agile
La metodologia AGILE è nata basandosi sulla giapponese [Toyota system](https://en.wikipedia.org/wiki/Toyota_Production_System).
### Etica (!!!) (4) 🟨++
Creati verso l'anno 2000 [https://agilemanifesto.org/iso/it/manifesto.html](https://agilemanifesto.org/iso/it/manifesto.html)

1. **Individui e interazioni** più che a processi e strumenti
2. **Software che funziona** più che a documentazione completa
3. **Collaborazione col cliente** più che a negoziazione contrattuale
4. **Reagire al cambiamento** più che a seguire un piano

1. Umani :)
2. Dal punto di vista della burocrazia, dovrebbe essere sempre ben documentato il software.
3. Software è difficile da tutelare perché non è tangibile come cosa.
4. La possibilità di negoziare tutto, invece che seguire un piano di tre anni diciamo.

### Principi (12) 🟨

<img src="/images/notes/Modelli AGILE-1696862361773.jpeg" alt="Modelli AGILE-1696862361773">

Proviamo a cercare di commentare questi principi uno per uno
1. È la regola per **user-centered** philosophy.
2. il fatto che il gruppo deve essere coeso al fine di fare un buon lavoro.
3. La **capacità di adattamento**.
4. Il fatto che **deve funzionare** perché alla fine questo serve all'utente finale.
5. Si ribadisce il punto 4 perché quello che deve essere misurato è il funzionamento del codice.
6. Ribadisce l'importanza del team, il fatto che devono essere motivati.
7. Regole imposte dall'alto sono il male, il team si dovrebbe organizzare da solo riguardo architetture e requisiti. (non sempre avere uno che fa tutto è di aiuto).
8. Faccia a faccia è meglio rispetto ad online.
9. Sostenibile nel senso di investimento di risorse, senza sprecare risorse e che siano sufficienti per fare quello che devi fare.
10. Lo interpreto come fare cose che dovrebbero essere modulari e facilmente estendibili.
11. Semplice è più facile da leggere e capire.
12. La capacità di cambiare e adattarsi a seconda di come si evolve la situazione. (scrum master proverà a far capire cosa c'è da fare capire diciamo).

## Extreme programming

#### The XP life-cicle (4) 🟩
Questa è stata una delle prime forme di *sviluppo iterativo* che sono esistite, si può dire che è un precursore di [Scrum Method](/notes/scrum-method).

In contrario rispetto: se funziona quanto basta, 
<img src="/images/notes/Modelli AGILE-1696866283947.jpeg" alt="Modelli AGILE-1696866283947">
- Defines features, che sono le cose che vorrebbe
- Poi il developer stima il costo per l'implementazione, si deve alla fine dare un prezzo al software.
- Customer sceglie fra quelle che può
- Poi si costruisce
### Valori XP (4) 🟨++
- semplicità (vedi 11 [#Principi (12) 🟨](/notes/#principi-(12)-🟨))
- comunicazione (ossia collaborazione internamente)
- feedback (comunicazione con l'utente)
- coraggio 
	- nel modificare comportamento non funzionato in passato, quindi sempre relazionato sulla capacità di cambiamento
	- Modificare e buttare parte del codice.

Che si traducono in modo effettivo in:
1. **Tutti devono capire** specifiche e cose riguardo il codice.
2. Usato per gruppi di piccola grandezza
3. Ci deve essere un rappresentante


## Other practices
### Minimum Viable Product 🟩
L'idea è non costruire alla fine un qualcosa di funzionante, ma partire con già con qualcosa di funzionante e reiterare, migliorando alcuni pezzi
<img src="/images/notes/Modelli AGILE-1697035462696.jpeg" alt="Modelli AGILE-1697035462696">

Quando si avrà un MVP, allora si potrebbe anche fare un **test di accettazione**, ossia mostrare quanto fatto al cliente e ricevere un primo feedback.

### User stories 
#### Definition of stories 🟩
<img src="/images/notes/Modelli AGILE-1696867096729.jpeg" alt="Modelli AGILE-1696867096729">

Vengono descritte ciò che gli utenti possono o non possono fare utilizzando le user stories diciamo.
Secondo il prof. Missiroli queste user stories devono anche avere un input e un output. (che non è sensato però.).
Poi devono essere **stimate** e **prioritizzate**

#### Priorità e story points 🟩
Queste storie solitamente sono caratterizzate da un **ordine di priorità** che descrive ciò che deve essere fatto e ciò che non dovrebbe diciamo.
Sono utili perché aiutano a definire un **ordine** in cui andare ad affrontare le varie task, *definito* dal singolo cliente.
Gli sviluppatori fanno poi una stima delle *risorse utilizzate* chiamate **story points** per cercare di dare una stima del costo in sforzo per sviluppare ciò.
Il processo di scelta delle task che dovranno essere fatte si chiama **planning game**, ed è fatta all'inizio di ogni iterazione.

#### Formato preferito (3) 🟩-
Questo è il formato preferito per andare a descrivere delle user stories (con l'aspetto della motivazione in più per aiutare il programmatore a capire meglio cosa deve andare a fare).

- Tipo di utente
- Obiettivo
- Motivazione (non funzionale per il codice, ma buono per immedesimarsi in quello che dovremo fare).

Questo è importante, ci aiuta a capire bene in che modo sia l'importante per il cliente, cioè quello che dovrà essere implementato.

#### Carpaccio di elefante
Secondo Missoroli è meglio che le storie siano **verticali** ossia che spaziano praticamente ogni campo (un po' di tutto per l'appunto, ma che allo stesso tempo siano molto specifiche), per me non ha molto senso perché sono due cose che vanno uno contro l'altro, non vogliamo che US tocchi tutto.
e hanno 
- stima
- priorità
- Condizioni di accettazione (test) oltre alle singole motivazioni

Ma secondo me non ci ha capito niente...

#### Moscow Method (4) 🟩--
Questo è un metodo utilizzato per **scegliere** quali user stories andare ad implementare.
- Must: funzioni che DEBBONO esserci nel prodotto 
- Should: funzioni che DOVREBBERO esserci 
- Could: funzioni che POTREBBERO esserci
- Wont: funzioni che NON INSERIREMO nella versione attuale
<img src="/images/notes/Modelli AGILE-1696871143749.jpeg" alt="Modelli AGILE-1696871143749">

[https://www.agilebusiness.org/page/ProjectFramework_10_MoSCoWPrioritisation](https://www.agilebusiness.org/page/ProjectFramework_10_MoSCoWPrioritisation)

#### Backlog 🟩
È **l'insieme** dei task (ossia delle #User stories 🟨) che devono essere fatte, e hanno delle *priorità*, che ad ogni iterazione possono cambiare l'ordine.

Questa parte viene *solitamente divisa in due* perché una è nel backlog, l'altro quello che si vuole implementare durante lo sprint.

#### Epiche 🟩
Saranno alla fine sempre delle **user-stories**, ma dato che sono *molto grandi* solitamente sono divisi in task più semplici.

#### Task 🟩
User stories sono richieste dall'utente, mentre le task sono dei pezzi utili per la production, qualcosa che è lecito per lo sviluppatore, ma non ovvio per il cliente.

#### Framework Invest
The INVEST framework is a set of criteria used to assess the **quality of user stories** in Agile development. It was introduced by Bill Wake as a reminder of the characteristics that good user stories should possess. The INVEST acronym stands for:

1. **Independent:** Each user story should be independent, meaning that it can be developed, tested, and delivered without relying on other stories. This helps in prioritizing and sequencing stories based on business value.
2. **Negotiable:** User stories should not be overly detailed or rigid. They should allow for negotiation between the development team and the product owner, fostering collaboration and adaptation as the project progresses.
3. **Valuable:** Each user story should deliver value to the end user or customer. It's important that the work being done is meaningful and contributes to the overall goals of the project.
4. **Estimable:** The team should be able to estimate the effort required to implement a user story. This helps in planning and prioritizing work effectively. If a story is too vague or complex to estimate, it may need to be broken down into smaller, more manageable pieces.
5. **Small:** User stories should be small enough to be completed within a single iteration or sprint. This helps in maintaining a steady and predictable pace of development, and it allows for frequent releases of working software.
6. **Testable:** There should be clear criteria for determining when a user story is complete. This ensures that the development team and stakeholders have a shared understanding of what needs to be done and can confirm that the story meets the specified requirements.

By applying the INVEST criteria, Agile teams aim to create user stories that are well-defined, manageable, and focused on delivering value to the customer. This, in turn, contributes to the overall success of the Agile development process.
### Casi d'uso

#### Descrizione casi d'uso 🟩
I casi d'uso sono un metodo per **descrivere i requirements** vedi [Requisiti e backlog del software](/notes/requisiti-e-backlog-del-software), tali per cui **abbiano il massimo valore possibile**.
Sono un modo diverso rispetto alle user stories descritte in [Modelli AGILE](/notes/modelli-agile) per fare questo.
Definisce un **scenario** dettagliato su esattamente cosa vuole del prodotto, il contesto in questo caso è molto importante.

Da quanto mi sembra di aver capito è proprio una descrizione passo passo per ogni cosa che vuole fare l'utente.

Solitamente questo viene rappresentato con una specie di UML, come descritto in [Unified Modeling Language](/notes/unified-modeling-language).

NOTA: non c'è nessun concetto di tempo all'interno di questo diagramma, a differenza di *sequence* e *collaboration* diagrams.

I casi d'uso sono più utili a **descrivere il contesto** in cui il software lavora, e per comprendere in che modo può aiutare i clienti con il sistema software.

#### L'attore 🟩
Sono enti, umani o macchine, che agiscono su un sistema e da questo ottengono valore (servizio, calcolo o simili).
Solitamente questi sono distinti in **business e tecnici**, i primi sono direttamente per clienti, i secondi sono operazionali, per far funzionare bene tutto, sono più interne come cose.

#### Estensioni e inclusioni di casi d'uso
Sono quando alcuni utilizzi devono avere delle funzionalità **necessarie** in questo caso includes, oppure funzionalità che sono estese da qualcosaltro, l'unica cosa che cambia è il verso da cui parte la freccia.

### Test driven development

#### Filosofia TDD 🟩
Solitamente il test per una funzione viene scritta dopo che il codice è già stato scritto. Questo porta a scrivere codice che spesso non è testabile
Un approccio alternativo è partire direttamente dalle specifiche ed andare ad implementare del **test prima del codice** in pratica il codice ci saranno solamente backbones diciamo.
<img src="/images/notes/Modelli AGILE-1701338289588.jpeg" alt="Modelli AGILE-1701338289588">
#### Test di accettazione 🟩
Sono dei test (quindi sempre nella verifica che il software *soddisfi i requisiti* o meno, non automatici, che **vengono fatti insieme al cliente**, in modo tale per cui alla fine la user story venga accettata, questo è solitamente chiamato **User acceptance testing** perché è fatto col cliente.

### Refactoring
> Migliorare il codice esistente mantenendo la funzionalità **inalterata**

Solitamente è una cosa necessaria, perché il codice evolve continuamente, utile a **diminuire il technical debt**.

#### Vantaggi refactoring (2) 🟩
Alcuni esempi possono essere
- renderlo più leggibile
	- Astrarre dove necessario
	- Buttare codice non necessario
	- Semplificare codice con stessa funzionalità. 
- semplicità di mantenimento
	- Astrazioni

#### Operazioni di refactoring classiche 🟩

- Aggiungere, cancellando o rinominando
- Spostare classi nel codice e nella *catena di derivazione*.
- Su classi, membri, funzioni statiche, data temporaneo.


### Pair programming

#### Dinamiche driver navigator 🟩
**Driver** and **navigator**, uno che scrive il codice e l'altro che legge e guarda se ci sono alcuni difetti o modi in cui si può scrivere il codice (solitamente sono *scambiati durante la stessa* giornata)
- Plus: **proprietà collettiva del codice**, dovrebbe essere famigliare a tanti nel progetto (forse tutti)
#### Proprietà collettiva del codice 🟨++
> Tutti dovrebbero essere in grado di capire e modificare secondo necessità una parte del codice.

Se codice è complesso non verrà mantenuto o usato.
### Altri argomenti
#### Convenzioni di codifica
TODO:
#### Sostenibilità dello sviluppo
TODO:
#### Integrazione del codice (!) 🟩
Ossia fare **small releases**, giorno per giorno viene integrata una nuova funzionalità che viene accettata e validata dal team.
Questo poi è una cosa normalissima in [Scrum Method](/notes/scrum-method), in cui si vanno proprio per piccoli rilasci.

#### Standing Meeting (3) (!) 🟩
1. Cosa fatto ieri
2. Cosa si vuole fare oggi
3. Quali sono i problemi maggiori, è per portare il team tutti sulla stessa pagina.

## Note di ripasso
- Quali sono i 4 principi di AGILE?
- Perché si può dire che l'ingegneria del software è una disciplina sociale
- Cosa sono le user stories? Perché sono utili
- Cosa è l'XP e perché è importante
- cosa è il backlog di un prodotto?
- Cosa è un planning game? Cosa è uno story point
- Definisci refactoring

| Data       | Commenti |
| ---------- | -------- |
| 10/22/2023 | Non mi ricordo esattamente tutti i valori e etica agile, quello sarebbe da migliorare ma per tutto l'altro lessico ci dovrebbe essere dai         |
| 11/21/2023| Dovrei provare a creare discorsi a riguardo, perché credo sia questa parte di esposizione quello che conta, non la conoscenza, per ora la maggior parte delle cose non le ho provate (poi i principi non me li ricordo a memoria, tipo non sai come descrivere la differenza fra XP e Agile, solo che uno è ili primo metodo, se devi fare orale, questo è messo un po' male.) |