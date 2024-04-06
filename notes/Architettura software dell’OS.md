---
layout: page
permalink: notes/architettura-software-dell’os
tags: italian
title: Architettura software dell’OS
---

Ripasso Prox: 22
Ripasso: June 6, 2023
Ultima modifica: May 23, 2023 10:19 PM
Primo Abbozzo: March 1, 2023 10:07 AM
Stato: 🌕🌕🌕🌕🌑
Studi Personali: No

# Elementi di ripasso

In teoria il ripasso era 28 maggio

# Architettura software dell’OS

A seconda dell'utilizzatore l’OS può essere molte cose, come solamente l’interfaccia se sei un programmatore, servizi (se sei un utente, ma gran parte dei servizi sono astratti e l'utente ne può anche essere a non-conoscenza).

Ma se sei un programmatore OS ti interessa capire le componenti principali dell’OS

- Slide componenti OS alto livello

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled">


## Introduzione sui componenti (salto)

Questa parte la salto perché è una descrizione molto generale di cosa si occupa L’os verso drivers, processi, filesystem I/O, quindi non è molto importante

### Gestione dei processi

All'interno del SO, il processo è rappresentato come un **processo control block**, che in linux è in **sched**, parte dello scheduler dei processi. Questo è importante perché per esempio per fare una fork, non faccio altro che duplicare questa struttura e settare bene i figli e genitori.

Questi sono solitamente messi un un **process table** o forse una lista per tenerne traccia.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 1.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 1">


nel parliamo in [Processi e thread](/notes/processi-e-thread).

### Gestione memoria principale e secondaria

**Principale**

È un array temporaneo(nel senso che non è mantenuto quando viene spento il PC.), indicizzato singolarmente a differenza del secondario, che è indicizzato a blocchi,

Una parte importante di questa parte è la gestione della memoria virtuale. Come allocare pagine di memoria, deallocarle e simili, ne parliamo in [Paginazione e segmentazione](/notes/paginazione-e-segmentazione)

**Secondaria**

La cosa buona è che questa memoria è permanente, efficienza (ordinare le richieste per non andare qui e lì quando si legge! **minimizare tempi per seek**) e partizionamento e reliability dei dischi sono problemi che interessano questa parte. Abbiamo parlato di raid in [Memoria](/notes/memoria). e di nuovo in [Devices OS](/notes/devices-os).

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 2.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 2">

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 3.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 3">


### I/O e filesystem

Principalmente per IO servono driver per interagire con specifici hardware, e un sistema di comunicazione che spesso sono buffer e cache.

- Slides

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 4.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 4">

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 5.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 5">


Esiste un **file system virtuale** che mappa a tutto (quindi alcune cose non esistono realmente sul disco, potrebbe essere una astrazione utilizzata per esempio per comunicare con i devices.

Ci sono molti filesystem, che però posso gestire in modo differente la forma che hanno sul disco, Ed è per questo che possiamo dire che esistono dei filesystem diversi.

Anche i processi sono files, la cosa figa di questa astrazioen è che posso utilizzare gli stessi sistemi di protezione file per processi.

## Struttura dei sistemi

### Obiettivi di design dei SO (4) 🟨

- Slide obiettivi nella struttura dei sistemi (4)

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 6.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 6">

- Efficienza
- Modularità
- Mantenibilità
- Espansibilità

### Struttura del kernel 🟩

- Slide riassuntiva

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 7.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 7">


Il kernel è un unico processo, parte da un main che parte da un initialize in cui raccoglie tutte le risorse del sistema, fa partire tutti i device drivers e crea il PCB del primo processo, anche chiamato **init**, messo poi nella queue dello scheduler come spiegato in [Scheduler](/notes/scheduler). Fatta una volta non è mai più eseguito quel codice di init.

Lo stato kernel è la parte a sinistra dell’immagine, quella parte blu, tutto il giallo, a destra è lo stato user.

1. Scheduler scegliere il processo da eseguire nello user space
2. Il controllo è passato al processo user, che può fare traps (come fork) o fare I/O, a quel punto è rimesso a codice kernel.

### Tipologie di struttura OS (2) 🟨++

Solitamente i sistemi sono costruiti in due modi, sistemi **semplici senza struttura**, che praticamente c'è una prima versione, e poi viene ammassato roba senza struttura generale, fatti quando servono. Solitamente sono insieme di procedure che si chiamano fra di loro, e ben presto sono andate fuori dal loro ambito di interesse diciamo (fuori dal loro scope)

**Esempi di OS semplici:**

Un esempio è **free-dos** che è quanto installato su un computer senza sistema operativo.

In modo simile è MS-DOS, che è stato fatto per i primi personal computer, che non avevano un sistema kernel a livello hardware (non era quindi possibile fare queste protezioni).. In generale in questo ambiente un programma aveva accesso all'intera memoria, e poteva mandare in crash tutto.

- Struttura Free-DOS

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 8.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 8">


UNIX, è diviso diviso in due parti in kernel e programmi di sistemi, molto semplice, un kernel monolitico, un unico eseguibile, anche questo fu all’epoca limitato enormemente dal suo hardware, e una serie di programmi di sistema.

Dato che c'è una separazione, l’utente è separato dall’interfaccia dal codice kernel. Ma comunque il codice kernel resta vulnerabile, e potrebbe essere modificato e quindi attaccato, o cumunque vulnerabile a bug, anche colposi, distruttivi.

- Struttura UNIX

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 9.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 9">


**Stratificazione OS:**

La **struttura a stati** è più affidabile dell'altra e rende più facile la programmazione di tale sistema, utili, la logica è la stessa presentata in [Architettura e livelli 1, 2](/notes/architettura-e-livelli-1,-2), per la divisione a stack del sistema e dei vantaggi che si hanno con questo tipo di architettura.

- Esemplificazione struttura a strati

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 10.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 10">

- Strutture proposte classiche (non fatte, non importanti)

    Questi sono **rimasti accademici**

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 11.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 11">


Ma nella pratica questi strati sono rimasti solamente a livello accademico, perché **crea overhead** anche se si guadagnerebbe in manutentibilità e estensibilità e gestione, quindi molto meno efficiente, inoltre non erano ben chiare le API fra strati. Oggi c'è una forma intermedia (non c'è esattamente la gestione a strati come abbiamo per Web, ma abbiamo una divisione per componenti e responsabilità delle componenti).

### Politiche e meccanismi 🟩

La suddifivisione politiche e meccanismi è un pattern di software engineering che lo rende molto comodo da gestire.

Invece che una gestione a strati come per le reti, abbiamo una gestione di **politiche e meccanismi** ossia abbiamo qualcosa che decide cosa andare a fare e qualcosa che gestisce il come farla.

EG. un certo modo di memoria allocata per fare qualcosa, quindi indirizzare il sistema verso qualcosa, e MMU che attualmente implementa la decisione politica.

**Esempio Microkernel o MINIX:**

Il kernel è visto come il meccanismo quindi le parti di gestione e politica sono fuori dal kernel. Questo rende la struttura del SO molto mantenibile ed estendibile.

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 12.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 12">


**Esempio Mac OS ≤ 9 / Windows 9x:**

Politiche e meccanismi sono messi tutti nel kernel, perché così imponevo un feeling unico al look and feel suo (obbligato tutti ad avere questi elementi grafici). Questo è un problema praticamente di mercato.

Questo era brutto perché la grafica può mandare in crash tutto il sistema. Anche se i nuovi sistemi non dovrebbero avere questo problema.

### Categorizzazione dei Kernel (3) 🟨—

**Monolitici:**

Il kernel è un unico programma. Si possono creare moduli che poi vengono caricati. Il problema principale di questo tipo di kernel è che se un modulo bugga crolla l'intero sistema. Un vantaggio è che è molto efficiente perché non deve passare ad astrazioni come per lo stack, basta fare una chiamata di funzione, tanto siamo nello stesso programma. Ed è altamente modularizzabile per poter attaccare nuove funzionalità.

In breve:

Vantaggi

- Efficienza
- Modularità e mantenibilità (non devo ricompilare tutto, basta runtime).

Svantaggio

- Un modulo può mandare in crash tutto, perché è eseguito nello stesso spazio del kernel.
- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 13.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 13">


Esempi sono Linux o BSD.

**Microkernel:**

L’obiettivo del microkernle è isolare solamente le funzionalità essenziali e tenere solo quelli, tutto il resto interagisce con esso con system call (un esempio è il filesystem che potrebbe essere fuori dal kernel, e avrebbe syscall leggermente diverse rispetto a quelle di linux, per aprire un file allora si chiederebbe a questo processo in user space, che poi fa altre richeste per kernel space)

Bisogna fare un messaggio, la syscall diventano Send! Che sarebbe unico modo per raggiungere il processo che offre il servizio che mi serve.

Vantaggi: 🟥

- Altissima modularità e mantenibilità del sistema e semplice da realizzare
- Assenza di danni di sistema, perché moduli e kernel sono eseguiti in spazio differente.
- Sicuro e affidabile per la divisione (non ho propagazione di errori e guasti)
- Molto portabile, che ho solo il microkernel.

Svantaggio:

- Fortemente Inefficienza rispetto al monolitico, che devo fare message passing e comunicazione.
- Slide di comparazione

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 14.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 14">


**Kernel Ibridi**

Sono dei microkernel modificati, con qualcosa in più forse (aziende per pubblicizzarsi dicevano di avere microkernel, ma con un ibridone, mettendo le cose inefficienti del microkernel dentro il kernel).

- Esempio windows

    Ci sono diversi server, che fanno parte di un sottosistema d’ambiente che è in grado di emulare certe cose (sono nascoste le syscall reali del sistema così).

    Il codice per un certo ambiente funziona anche nel sottosistema, un esempio è un WSL.

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 15.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 15">

    La parte grafica importante per fare i videogiochi, è dentro il kernel, questo ad esempio per MACOS, perché volevano imporre la grafica simile


## Macchine virtuali

> Virtualization allows a single computer to host multiple virtual machines, each poten-
tially running a completely different operating system.
>

È virtuale nel senso che la macchina virtuale ha la stessa percezione della realtà di una macchina reale. Qualcosa che non è la realtà ma appare molto simile ad essa.

Storicamente parlando le macchine virtuali erano un primo approccio al multitasking.

L’idea principale è creare un sistema che possa apparire al sistema operativo come hardware, in questo modo posso utilizzare un programma per emulare un altro sistema operativo. È **hypervisor, VMM (virtual machine monitor)**.

Ovviamente ho uno fortissimo svantaggio in velocità, perché la simulazione software è molto meno efficiente della simulazione hardware. Un collegamento carino è con strange loops, una macchina che sia abbastanza espressiva da poter emulare sé stesso.

### Analisi vantaggi svantaggi 🟨

- Slide

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 16.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 16">

- Posso avere sistemi operativi differenti sulla stessa macchina o SO, quindi posso sperimentarli senza installarli veramente.
- Posso simulare architetture differenti, e quindi supporre di avere istruzioni differenti di architettura altra!
- SO monotask in sistemi multitask???
- Maggiore sicurezza a bug software, è efficienza energetica

**Svantaggi**:

1. fortemente inefficiente
2. Difficile condividere risorse fra una macchina virtuale o all’altra.

### Livello processo o sistema 🟩

Le macchine virtuali di cui abbiamo parlato ora virtualizzano solamente l’hardware, cioè fa finta di avere un sistema hardware???

Mentre altre macchine virtuali provano a virtualizzare a livello di ABI (application binary interface) (che è livello di processo).

- Macchina virtuale a livello di processo (**process VM)**: permette ad un programma di essere eseguito allo stesso modo su qualsiasi piattaforma.
Viene eseguita come una normale applicazione all’interno di un SO ospite e supporta un singolo processo. Il suo scopo è fornire un ambiente indipendente dalla piattaforma hardware e dal SO ospite. Vengono virtualizzati sia l’hardware che il sistema operativo.
- Macchina virtuale a livello di sistema (**system VM**): permette l'esecuzione di un completo SO, anche con un ISA diverso da quello della macchina reale. Viene virtualizzato esclusivamente e completamente l’hardware

**Differenza type 1 and 2 hypervisors**

type 1 hypervisor and a type 2 hypervisor is that a type 2 makes uses of a host operating system and its file system to create processes, store files, and so on. A type 1 hypervisor has no underlying support and must perform all these functions itself (it runs on the bare metal, come se fosse lui stesso un sistema operativo, è infatti un sistema operativo che non fa altro che fare sistemi operativi!)

### Qemu 🟩

**qemu** è un traduttore dinamico come se fosse un compilatore fra una architettura in una altra, fatta a runtime (quindi è un interprete, tipo 10x più lento rispetto esecuzione normale, ma un ordine di grandezza più veloce rispetto altri emulatori).

Con qemu posso anche dire al processo emulato di utilizzare il mio stesso kernel, nel caso che condivida l'architettura, questo rende la cosa molto più veloce del normale! e.g. KVM (che è il nome dell’Hypervisor per linux). Questo è anche una tipologia di **type-2-hypervisor** perché attingo al kernel della macchina ospite per fare funzionare più in fretta, e non faccio simulazione sistema totale.

Utile o per runnare programmi per architettura differente (in questo senso program VM), oppure per emulare un sistema operativo dentro un sistema operativo

- Comando per caricare una macchina virtuale con qemu e utilizzare KVM

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 17.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 17">

    senza vga, non starebbe sullo schermo senza quella flag.

    hda gli specifica il file con cui emulare il disco, k il layout del keyboard

    m è la memoria ram

    monitor è per poter mandare interrupt dal terminale in cui ho lanciato il mio comando di emulazione.

    Quando installa prima è installato nella RAM disk, e poi viene utilizzato per l’installazione vera e propria.


### XEN 🟩

XEN è hypervisor livello 1 (SO che permette di fare altri SO virtuali), e utilizzare paravirtualizzazione (si fanno trap and emulate principalmente) , e utilizza una gestione diversa dei drivers che possiede, ossia il **Domain0** possiede tutti i drivers fisici (le interazioni con i device le manda alla macchina 0, perché per restare un sistema operativo semplice non riesce a gestire sistemi operativi).

**Paravirtualizzatione**

In questo caso il SO virtuale è a conoscenza che esiste un hypervisor quindi può fare delle **hypercall** per eseguire delle istruzioni sensitive, e in generale è un approccio più veloce invece della virtualizzazione totale di cui abbiamo parlato prima.

**Esempio di maggiore efficienza**

Per il type 2 hypervisor il SO installato pensa veramente di stare in una macchina sé, quindi fa cose per minimizzare i seek del disco ma in questo caso non deve fare veramente seek, quindi è meno efficiente, facendo una assunzione errata.

Si utilizzano paravirtualizzazione, ossia devices virtuali più efficienti per questa cosa, ed effettivamente non assumo di stare utilizzando device fisici, ma sono a conoscenza di utilizzare device virtuali, e posso fare ottimizzazioni del caso (che non so quali siano forse per il disco non faccio cose strane per il seek ad esempio).

Il problema è che essendo a conoscenza, dovrei fare il mio SO in modo che sia compatibile con le hyper all offerte dall hypervisor

### Parametrizzazione SO 🟩

Essendo libero linux, è molto comodo poter cambiare alcuni parametri e poi **ricompilare il kernel seguendo quei parametri**. Tanto è tutto open source, quindi si potrebbe fare. Questo permette al kernel di essere molto portabile.

Una cosa molto importante da capire è che **il kernel è una cosa diversa della distribuzione**, il kernel è il primo programma che viene caricato dal bootloader e carica il FS e tutto il resto (quindi le cose iniziali), il secondo sono tutte le utility per il kernel che lo rendono utilizzabile da un utente normale.

- Comando runnato per la emulazione kernel/distribuzione

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 18.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 18">

- Slide parametrizzazione ++ portabilità (che deve runnare per hardware differentI)

    <img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 19.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 19">


### Istruzioni di virtualizzazione 🟥

Abbiamo aggiunto delle istruzioni di emulazione come `VMX ON, VMX OFF, VMLAUNCH, VMRETURN`  in cui il processore sa di stare emulando, e quindi è più veloce perché esegue l'istruzione in altro modo, forse con istruzione nativa. Pagina [wiki](https://en.wikipedia.org/wiki/X86_virtualization)

fa pensare di essere in kernel mode, ma non è in kernel mode, è come se stesse in un livello di priviliegio intermedio.

VMLAUNCH

Queste sono quelle principali istruzioni che permettono la virtualizzazioen a livello software, il fatto che rende l'esecuzione molto più veloce, quindi invece di simulare tutto sopra il sistema operativo attuale (e syscalls attuali) posso accedere ad istruzioni hardware molto più veloci.

### Memoria Virtuale (non fare)

C'è una MMU del sistema operativo che mappa alla VM fisica, che si deve basare all'indirizzo logico, che deve essere risolto dalla MMU reale fino ad avere un indirizzo fisico.

<img src="/images/notes/image/universita/ex-notion/Architettura software dell’OS/Untitled 20.png" alt="image/universita/ex-notion/Architettura software dell’OS/Untitled 20">

MINI SCHEMA



# References