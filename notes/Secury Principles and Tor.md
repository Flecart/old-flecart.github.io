---
layout: page
permalink: notes/secury-principles-and-tor
tags: italian
title: Secury Principles and Tor
---

## Security principles
We have already  outlined these principles in [Sicurezza delle reti](/notes/sicurezza-delle-reti) and talked about the concepts of authentication and integrity. Here we try to deepen these concepts and delve a little bit more on the attack vectors
These are acronyms, usually called CIA and AAA for infrastructure

### Confidentiality
This is one concerns about the secrecy of the sent message. We do not want others to be able to access and read what we are doing.

#### Eavesdropping 🟩
This is an example of attack of confidentiality. The setting is usually like this: Eve that intercepts the message sent by each other.
For example in network security, it is quite easy to eavesdrop with Wireshark or similars.
### Integrity
Integrity concerns with message tampering. The received message should be the same as the sent one (man in the middle are common attacks).


#### Authentication
Authentication is important when we **need to know** to whom we are talking to. We should need to be sure that that is exactly the person (or the machine) we are trying to connect (or talk to). In this framework it is about integrity.

#### Spoofing attacks 🟩
When an attacker authenticates as another user.

#### Manipulation attacks 🟩
This is tampering.

### Availability
The system should be available, that is accessible by its users.

#### Denial of service attacks 🟩
For example if you have limited number of ports, a common example of denial of service attack is the **Syn flooding** where multiple services ask to open a TCP connection, but it doesn't continue with the communication, leaving the port occupied but useless.




### Anonymity

On the internet we **are not anonymous** we are always tracked by ISP, cookies and many other strategies that I am not even aware of.
This is a problem we we want to be anonymous, so how can we reach this target??

#### Anonymity by proxy 🟩
We just use another computer to repeat my information, this computer doesn't have access to the underlying information, but it substitutes his IP to ours, so the end receiver doesn't exactly know where the initial message comes from.

#### Mix-based systems 🟨
Created in 1981 by David Chaum. 
Very similar to the previous one, in practice, in the end, it acts as a proxy but not only does it take and receive, but it also mixes together the packets it has received from the sources, applying its key.

<img src="/images/notes/Introduction to Cyber Security-20240326102655961.webp" alt="Introduction to Cyber Security-20240326102655961">

**Disadvantage:** 
The public-private mixing system is very slow. For this reason, a network of nodes is established, each having a symmetric key, making it much faster.

The important thing to note is that this system has been influential in modern tor networks.


#### Fullz dataleak

A fullz dataleak has the **minimum indispensable** to create bank accounts or pay with credit cards
- Name and Surname
- birthdate
- fiscal code
- phone number
- residence address

So its very important to keep this information private!

## The Tor Ecosystem

This system tries to anonymize the user with principles similar to [#Anonymity by proxy](#anonymity-by-proxy). The initial user message goes through different relays before reaching the end destination. The system is a little bit more complex than this, so we are breaking down a connection example 

It's called onion because each relay has only an outer layer of the onion. The core is what the end user receives.

### How Tor Works
The Tor network sends the payload through three **random relay servers** in the network.
Information about what we are accessing, from who, is not accessible.
But some information is still accessible, for example:
1. Our ISP knows that we are trying to access the Tor network, because we need a listing of tor nodes.
2. The exit relay knows to whom we are talking to, as this information is needed to send the message.

As the exit node is often public, they are often **blocked** by institutions, like banks.

#### Overlay networks
> Rete “overlay”. Una rete **chiusa** al quale interno vengono distribuiti dati in **forma anonima**. Questo è il principio dei servizi onion.

### Service setup
When a service is put onto this network it connects to some **intro nodes** whose role is to introduce clients to the servers.
The map server->intro nodes is then saved into another node, which is called the **directory node**. This node contain mappings from services and intro points.

#### Client Connection
The client that wants to connect to an anonymous service needs to know who are the intro nodes. 
He asks the directory node who gives him the connections. Directory gives him a descriptor, that is verified with the original `.onion` address who acts as a secure key.

The the client asks a secret string from a **rendezvous** node. The secret string and rendezvous are then sent to the intro nodes, and these sent it to the original service that decides whether to accept or not that service.

If it accepts, it sends the secret to the rendezvous, who then creates a circuit between the client and the server. Now everything can be sent and received anonymously.




## Old section
### Some concepts
**Security** vogliamo impedire modi che un altro possa accedere ad informazioni riservate

**Obiettivo** solo qualcuno può leggere una password.

**Policy Threath models, and mechanism.** sono modi che potrebbero essere attaccati (permessi, provare a rompere la password, attaccare il sistema operativo e simili). Questo è un buon framework generale, ma nella pratica non è mai utilizzato. Utilizziamo questa pratica per introdurre al corso.

È molto difficile prevedere tutti i tipi di attacco, l’unica soluzione è **iterare** provare a sapere dal passato ed evolvere le policy che vengono messe. Da questo si può capire che non è perfetto. Cose da considerare sono

1. Costo dell’attacco
2. Big payoff: cose che costano poco da implementare per il difensore, ma che rendono l’attaccante molto inabilitato.
3. Recuperare fra gli attacchi.

Di solito gli attacchi sono fatti perché  è facile! È facile connettersi agli altri computer nel mondo.

### Policy flaws examples

- Business class airfare (tipo cambiare il biglietto dopo essere andati su, bisogna investire in un sistema che non permetta di fare questo).
- School system. (Students → nothing, Director → reads all, Teacher can add student and change password of students), un insegnante può aggiungere il director come studente e cambiargli la password, e uno studente può accedere al computer dell’insegnante 💀

- Yahoo recovery password asks questions! But it was listed in the wikipedia page of the persone, so breaked xD.
- Crazy gmail attack

    <img src="/images/notes/image/universita/ex-notion/Introduction to the course/Untitled.png" alt="image/universita/ex-notion/Introduction to the course/Untitled">


### Insecure defaults

Sono molto importanti perché è molto facile dimenticarsi di cambiare il default in caso sia molto debole come sistema.

- Default password! (pubblicati e.g. da un manuale riguardo qualcosa).
- Default permission. (e.g. amazon S3 bucket public by default).

### Threat model problems

Sono cose che un attaccante può utilizzare per entrare nel sistema.

- Clipper chips of the 90’
- Secret design /impl, non si può supporre che il design sia nascosto, si può sempre disassemblare col giusto tempo, quindi è facilmente rompibile diciamo, se diventa abbastanza importante da dover essere rotto. (per questo è meglio avere una chiave)

Prova a dare una occhiata al kerchoffs principle in [Classical Cyphers](/notes/classical-cyphers).
- Non assumere che l’utente sia conoscitore delle pratiche generali della sicurezza (e.g. dirgli che ciò che scarica può essere un virus).
- list of attack vectors!

### Soft dev

- Source git (add backdoor that is integrated!) so the compiling shipped the attacked version
- Xcode in china, compromised mirror.
- Sw Updates.
- Initialization of seed?
- (some checks, and in many places, probabilmente si dimentica qualche check!)
- Randomness in Virtual machines (molto limitato, poche fonti di randomness come tastiera e cose simili.
- Appunti prof

    ```
    Introduction
    ============

    Welcome to 6.858 -- Computer Systems Security

    Course structure
      Lectures will be MW1-2:30, in 32-123.
        One paper per lecture.
          Tentative schedule online.
          Likely stable up until spring break.
          Lectures after spring break may change.
        Read the paper before lecture, and submit before lecture:
          Answer to a short homework question (link from schedule page).
          Your own question about the paper (will try to answer in lecture).
          Some papers about production systems, others about research ideas
          Even if the overall system described in the paper didn't pan out, many of
          the ideas and techniques in the paper are important and useful.
        Interrupt, ask questions, point out mistakes.
        [http://es.csail.mit.edu:8080/room/6.858/2adb3e10](http://es.csail.mit.edu:8080/room/6.858/2adb3e10)
      One quiz, one final exam.
        Quiz during class, final during finals week.
      Assignments: Five labs.
        Defenses and/or attacks on fairly real systems.
        Not a lot of coding, but lots of non-standard thinking.
          Poke into obscure corners of x86 asm, C, Python, Javascript, ..
        Office hours for lab/lecture help.
        Lab 1, buffer overflows, first part due this Friday.  Start early.
        Two options for Lab 5:
          Ordinary lab,
          or your choice of final project, in groups.
        For projects:
          Presentations at the end of the semester.
          Think of projects you'd like to work on as you're reading papers.
          Both attack- or defense-oriented projects are possible.
          Discuss project ideas with course staff ahead of time.
      Two lecturers: Frans, Nickolai.
      4 TAs: Rayden, Noah, Cattalyya, Jonathan.
      Sign up for Piazza (link on course web site).
        Mostly questions/answers about labs.
        We will post any important announcements there.
      Warning about security work/research on MITnet (and in general).
        You will learn how to attack systems, so that you know how to defend them.
        Know the rules: [http://ist.mit.edu/network/rules](http://ist.mit.edu/network/rules)
        Don't mess with other peoples' data/computers/networks w/o permission.
        Ask course staff for advice if in doubt.

    6.858 is about building secure computer systems
      Secure = achieves some property despite attacks by adversaries.
      Systematic thought is required for successful defense.
        Details matter!
      High-level plan for thinking about security:
        Goal: what your system is trying to achieve.
          e.g. only Alice should read file F.
          Common goals: confidentiality, integrity, availability.
        Policy: some plan (rules) that will get your system to achieve the goal.
          e.g. set permissions on F so it's readable only by Alice's processes.
          e.g. require a password and two-factor authentication.
        Threat model: assumptions about what the attacker can do.
          e.g. can guess passwords, cannot physically steal our server.
        Mechanism: software/hardware that your system uses to enforce policy.
          e.g. user accounts, passwords, file permissions, encryption.
          policy might include human components (e.g., do not share passwords)
            that's outside of the scope of the security mechanisms
        Often layered: mechanism of one layer is policy of next level down.

    Building secure systems is hard -- why?
      Example: 6.858 grade file, stored on an Athena AFS server.
        Policy: only TAs should be able to read and write the grades file.
      Easy to implement the *positive* aspect of the policy:
        There just has to be one code path that allows a TA to get at the file.
      But security is a *negative* goal:
        We want no tricky way for a non-TA to get at the file.
      There are a huge number of potential attacks to consider!
        Exploit a bug in the server's code.
        Guess a TA's password.
        Steal a TA's laptop, maybe it has a local copy of the grades file.
        Intercept grades when they are sent over the network to the registrar.
        Get a job in the registrar's office, or as a 6.858 TA.
      Result:
        One cannot get policies/threats/mechanisms right on the first try.
        One must usually iterate:
          Design, watch attacks, update understanding of threats and policies.
          Post-mortems important to understand
            Public databases of vulnerabilities (e.g., https://cve.mitre.org/)
            Encourage people to report vulnerabilities (e.g., bounty programs)
        Defender is often at a disadvantage in this game.
          Defender usually has limited resources, other priorities.
          Defender must balance security against convenience.
        A determined attacker can usually win!
          Defense in depth
          Recovery plan (e.g., secure backups)
        Most of this lecture is about failures to make you start thinking in this way

    What's the point if we can't achieve perfect security?
      Perfect security is rarely required.
      Make cost of attack greater than the value of the information.
        So that perfect defenses aren't needed.
      Make our systems less attractive than other peoples'.
        Works well if attacker e.g. just wants to generate spam.
      Find techniques that have big security payoff (i.e. not merely patching holes).
        We'll look at techniques that cut off whole classes of attacks.
        Successful: popular attacks from 10 years ago are no longer very fruitful.
      Sometimes security *increases* value for defender:
        VPNs might give employees more flexibility to work at home.
        Sandboxing (JavaScript, Native Client) might give me more confidence
          to run software I don't fully understand.
      No perfect physical security either.
        But that's OK: cost, deterrence.
        One big difference in computer security: attacks are cheap.

    What goes wrong # 1: problems with the policy.
      I.e. system correctly enforces policy -- but policy is inadequate.

    Example: Business-class airfare.
      Airlines allow business-class tickets to be changed at any time, no fees.
      Is this a good policy?
      Turns out, in some systems ticket could have been changed even AFTER boarding.
      Adversary can keep boarding plane, changing ticket to next flight, ad infinitum.
      Revised policy: ticket cannot be changed once passenger has boarded the flight.
        Sometimes requires changes to the system architecture.
        Need computer at the aircraft gate to send updates to the reservation system.

    Example: Verifying domain ownership for TLS certificates.
      Browser verifies server's certificate to ensure talking to the right server.
      Certificate contains server's host name and cryptographic key,
        signed by some trusted certificate authority (CA).
      Browser has CA's public key built in to verify certificates.
      CA is in charge of ensuring that certificate is issued only to
        legitimate domain (hostname) owner.
      Typical approach: send email to the contact address for a domain.
      Some TLDs (like .eu) do not reveal the contact address in ASCII text.
        Most likely to prevent spam to domain owners.
      Instead, they reveal an ASCII image of the email address.
      One CA (Comodo) decided to automate this by OCR'ing the ASCII image.
      Turns out, some ASCII images are ambiguous!
        E.g., foo@a1telekom.at was mis-OCRed as foo@altelekom.at
        Adversary can register mis-parsed domain name, get certificate for
          someone else's domain.
      [ Ref: [https://www.mail-archive.com/dev-security-policy@lists.mozilla.org/msg04654.html](https://www.mail-archive.com/dev-security-policy@lists.mozilla.org/msg04654.html) ]

    Example: Fairfax County, VA school system.
      [ Ref: [http://catless.ncl.ac.uk/Risks/26.02.html#subj7.1](http://catless.ncl.ac.uk/Risks/26.02.html#subj7.1) ]
      Student can access only his/her own files in the school system.
      Superintendent has access to everyone's files.
      Teachers can add new students to their class.
      Teachers can change password of students in their class.
      What's the worst that could happen if student gets teacher's password?
        Student adds the superintendent to the compromised teacher's class.
        Changes the superintendent's password, since they're a student in class.
        Logs in as superintendent and gets access to all files.
      Policy amounts to: teachers can do anything.

    Example: Sarah Palin's email account.
      [ Ref: [http://en.wikipedia.org/wiki/Sarah_Palin_email_hack](http://en.wikipedia.org/wiki/Sarah_Palin_email_hack) ]
      Yahoo email accounts have a username, password, and security questions.
      User can log in by supplying username and password.
      If user forgets password, can reset by answering security Qs.
      Some adversary guessed Sarah Palin's high school, birthday, etc.
      Policy amounts to: can log in with either password *or* security Qs.
        No way to enforce "Only if user forgets password, then ..."
      Thus user should ensure that password *and* security Qs are
        both hard to guess.

    Example: Mat Honan's accounts at Amazon, Apple, Google, etc.
      [ Ref: [http://www.wired.com/gadgetlab/2012/08/apple-amazon-mat-honan-hacking/all/](http://www.wired.com/gadgetlab/2012/08/apple-amazon-mat-honan-hacking/all/) ]
      Honan an editor at wired.com; someone wanted to break into his gmail account.
      Gmail password reset: send a verification link to a backup email address.
        Google helpfully prints part of the backup email address.
        Mat Honan's backup address was his Apple @me.com account.
      Apple password reset: need billing address, last 4 digits of credit card.
        Address is easy, but how to get the 4 digits?
      How to get hold of that e-mail?
      Call Amazon and ask to add a credit card to an account.
        No authentication required,
        presumably because this didn't seem like a sensitive operation.
      Call Amazon tech support again, and ask to change the email address on an account.
        Authentication required!
        Tech support accepts the full number of any credit card registered with the account.
        Can use the credit card just added to the account.
      Now go to Amazon's web site and request a password reset.
        Reset link sent to the new e-mail address.
      Now log in to Amazon account, view saved credit cards.
        Amazon doesn't show full number, but DOES show last 4 digits of all cards.
        Including the account owner's original cards!
      Now attacker can reset Apple password, read gmail reset e-mail,
        reset gmail password.
      Lesson: attacks often assemble apparently unrelated trivia.
      Lesson: individual policies OK, but combination is not.
        Apple views last 4 as a secret, but many other sites do not.
      Lesson: big sites cannot hope to identify which human they are talking to;
        at best "same person who originally created this account".
        security questions and e-mailed reset link are examples of this.

    Example: Insecure defaults.
      Well-known default passwords in routers.
      Public default permissions in cloud services (e.g., objects in AWS S3 bucket).
      Secure defaults are crucial because of the "negative goal" aspect.
        Large systems are complicated, lots of components.
        Operator might forget to configure some component in their overall system.
        Important for components to be secure if operator forgets to configure them.

    Policies typically go wrong in "management" or "maintenance" cases.
      Who can change permissions or passwords?
      Who can access audit logs?
      Who can access the backups?
      Who can upgrade the software or change the configuration?
      Who can manage the servers?
      Who revokes privileges of former admins / users / ...?

    What goes wrong # 2: problems with threat model / assumptions.
      I.e. designer assumed an attack wasn't feasible (or didn't think of the attack).

    Example: assume the design/implementation is secret
      "Security through obsecurity"
      Clipper chip
        [ Ref: [https://en.wikipedia.org/wiki/Clipper_chip](https://en.wikipedia.org/wiki/Clipper_chip) ]
      Broken secret crypto functions

    Example: most users are not thinking about security.
      User gets e-mail saying "click here to renew your account",
        then plausible-looking page asks for their password.
      Or dialog box pops up with "Do you really want to install this program?"
      Or tech support gets call from convincing-sounding user to reset password.

    Example: computational assumptions change over time.
      MIT's Kerberos system used 56-bit DES keys, since mid-1980's.
      At the time, seemed fine to assume adversary can't check all 2^56 keys.
      No longer reasonable: now costs about $$100.
        [ Ref: [https://www.cloudcracker.com/dictionaries.html](https://www.cloudcracker.com/dictionaries.html) ]
        Several years ago, 6.858 final project showed can get any key in a day.

    Example: assuming a particular kind of a solution to the problem.
      Many services use CAPTCHAs to check if a human is registering for an account.
        Requires decoding an image of some garbled text, for instance.
      Goal is to prevent mass registration of accounts to limit spam, prevent
        high rate of password guessing, etc.
      Assumed adversary would try to build OCR to solve the puzzles.
        Good plan because it's easy to change image to break the OCR algorithm.
        Costly for adversary to develop new OCR!
      Turns out adversaries found another way to solve the same problem.
        Human CAPTCHA solvers in third-world countries.
        Human solvers are far better at solving CAPTCHAs than OCRs or even regular users.
        Cost is very low (fraction of a cent per CAPTCHA solved).
      [ Ref: [https://www.cs.uic.edu/pub/Kanich/Publications/re.captchas.pdf](https://www.cs.uic.edu/pub/Kanich/Publications/re.captchas.pdf) ]

    Example: all TLS CAs are fully trusted.
      If attacker compromises CA, can generate fake certificate
        for any server name.
      Originally there were only a few CAs; seemed unlikely that
        attacker could compromise a CA.
      But now browsers fully trust 100s of CAs!
      In 2011, two CAs were compromised, issued fake certs for many domains
        (google, yahoo, tor, ...), apparently used in Iran (?).
        [ Ref: [http://en.wikipedia.org/wiki/DigiNotar](http://en.wikipedia.org/wiki/DigiNotar) ]
        [ Ref: [http://en.wikipedia.org/wiki/Comodo_Group](http://en.wikipedia.org/wiki/Comodo_Group) ]
      In 2012, a CA inadvertently issued a root certificate valid for any domain.
        [ Ref: [http://www.h-online.com/security/news/item/Trustwave-issued-a-man-in-the-middle-certificate-1429982.html](http://www.h-online.com/security/news/item/Trustwave-issued-a-man-in-the-middle-certificate-1429982.html) ]
      Several other high-profile incidents since then too.
      Mistake: maybe reasonable to trust one CA, but not 100s.

    Example: assuming your hardware is trustworthy.
      If NSA is your adversary, turns out to not be a good assumption.
      [ Ref: [https://www.schneier.com/blog/archives/2013/12/more_about_the.html](https://www.schneier.com/blog/archives/2013/12/more_about_the.html) ]

    Example: assuming you are running the expected software.
      1. In the 80's, military encouraged research into secure OS'es.
        Surprise: successful attacks by gaining access to development systems
        Mistake: implicit trust in compiler, developers, distribution, &c
      2. Apple's development tools for iPhone applications (Xcode) are large.
        Downloading them from China required going to Apple's servers outside of China.
        Takes a long time.
        Unofficial mirrors of Xcode tools inside China.
        Some of these mirrors contained a modified version of Xcode that injected malware
          into the resulting iOS applications.
        Found in a number of high-profile, popular iOS apps!
          [ Ref: [https://en.wikipedia.org/wiki/XcodeGhost](https://en.wikipedia.org/wiki/XcodeGhost) ]
      Classic paper: Reflections on Trusting Trust.

    Example: decomissioned disks.
      Many laptops, desktops, servers are thrown out without deleting sensitive data.
      One study reports large amounts of confidential data on disks bought via ebay, etc.
      [ Ref: [https://simson.net/page/Real_Data_Corpus](https://simson.net/page/Real_Data_Corpus) ]

    Example: software updates.
      Apple iPhone software updates vs FBI.
        [ Ref: [http://www.apple.com/customer-letter/](http://www.apple.com/customer-letter/) ]
      Chrome extensions bought by malware/adware vendors.
        [ Ref: [https://arstechnica.com/security/2014/01/malware-vendors-buy-chrome-extensions-to-send-adware-filled-updates/](https://arstechnica.com/security/2014/01/malware-vendors-buy-chrome-extensions-to-send-adware-filled-updates/) ]
      Node.js library updated to include code that steals Bitcoin keys.
        [ Ref: [https://www.theregister.co.uk/2018/11/26/npm_repo_bitcoin_stealer/](https://www.theregister.co.uk/2018/11/26/npm_repo_bitcoin_stealer/) ]

    Example: machines disconnected from the Internet are secure?
      Stuxnet worm spread via specially-constructed files on USB drives.

    What to do about threat model problems?
      More explicit threat models, to understand possible weaknesses.
      Simpler, more general threat models.
        E.g., should a threat model assume that system design is secret?
        May be incrementally useful but then hard to recover.
        Probably not a good foundation for security.
      Better designs may eliminate / lessen reliance on certain assumptions.
        E.g., alternative trust models that don't have fully-trusted CAs.
        E.g., authentication mechanisms that aren't susceptible to phishing.

    What goes wrong # 3: problems with the mechanism -- bugs.
      Bugs routinely undermine security.
        Rule of thumb: one bug per 1000 lines of code.
        Bugs in implementation of security policy.
        But also bugs in code that may seem unrelated to security, but they are not.
          Good mindset: Any bug is a potential security exploit.
          Especially if there is no isolation around the bug.

    Example: Apple's iCloud password-guessing rate limits.
      [ Ref: [https://github.com/hackappcom/ibrute](https://github.com/hackappcom/ibrute) ]
      People often pick weak passwords; can often guess w/ few attempts (1K-1M).
      Most services, including Apple's iCloud, rate-limit login attempts.
      Apple's iCloud service has many APIs.
      One API (the "Find my iPhone" service) forgot to implement rate-limiting.
      Attacker could use that API for millions of guesses/day.
      Lesson: if many checks are required, one will be missing.

    Example: Missing access control checks in Citigroup's credit card web site.
      [ Ref: [http://www.nytimes.com/2011/06/14/technology/14security.html](http://www.nytimes.com/2011/06/14/technology/14security.html) ]
      Citigroup allowed credit card users to access their accounts online.
      Login page asks for username and password.
      If username and password OK, redirected to account info page.
      The URL of the account info page included some numbers.
        e.g. x.citi.com/id=1234
      The numbers were (related to) the user's account number.
      Adversary tried different numbers, got different people's account info.
      The server didn't check that you were logged into that account!
      Lesson: programmers tend to think only of intended operation.

    Example: poor randomness for cryptography.
      Need high-quality randomness to generate the keys that can't be guessed.
      Android's Java SecureRandom weakness leads to Bitcoin theft.
        [ Ref: [https://bitcoin.org/en/alert/2013-08-11-android](https://bitcoin.org/en/alert/2013-08-11-android) ]
        [ Ref: [https://www.nilsschneider.net/2013/01/28/recovering-bitcoin-private-keys.html](https://www.nilsschneider.net/2013/01/28/recovering-bitcoin-private-keys.html) ]
        Bitcoins can be spent by anyone that knows the owner's private key.
        Many Bitcoin wallet apps on Android used Java's SecureRandom API.
        Turns out the system sometimes forgot to seed the PRNG!
          A Pseudo-Random Number Generator is deterministic after you set the seed.
          So the seed had better be random!
        As a result, some Bitcoin keys turned out to be easy to guess.
        Adversaries searched for guessable keys, spent any corresponding bitcoins.
          Really it was the nonce in the ECDSA signature that wasn't random,
          and repeated nonce allows private key to be deduced.
        Lesson: be careful.
      Embedded devices generate predictable keys.
        Problem: embedded devices, virtual machines may not have much randomness.
        As a result, many keys are similar or susceptible to guessing attacks.
        [ Ref: [https://factorable.net/weakkeys12.extended.pdf](https://factorable.net/weakkeys12.extended.pdf) ]
      Casino slot machines.
        [ Ref: [https://www.wired.com/2017/02/russians-engineer-brilliant-slot-machine-cheat-casinos-no-fix/](https://www.wired.com/2017/02/russians-engineer-brilliant-slot-machine-cheat-casinos-no-fix/) ]

    Example: Moxie's SSL certificate name checking bug
      [ Ref: [http://www.wired.com/2009/07/kaminsky/](http://www.wired.com/2009/07/kaminsky/) ]
      Certificates use length-encoded strings, but C code often is null-terminated.
      CAs would grant certificate for amazon.com\0.nickolai.org
      Browsers saw the \0 and interpreted as a cert for amazon.com
      Lesson: parsing code is a huge source of security bugs.

    Example: buffer overflows (see below).

    Case study: buffer overflows.
      An important class of security problems,
        for which many attacks and defenses are known.
      This is the topic of Lab 1.
      Suppose your web server has a bug in the HTTP input parsing.
        On certain inputs, it crashes.
      Should you be worried?
      Let's take a look at a simplified example.

        % cat readreq.c

    #include <stdio.h>
    #include <stdlib.h>

    char *
    gets(char *buf) {
      int c;
      while((c = getchar()) != EOF && c != '\n')
        *buf++ = c;
      *buf = '\0';
      return buf;
    }

    int
    read_req(void) {
      char buf[128];
      int i;
      gets(buf);
      i = atoi(buf);
      return i;
    }

    int
    main() {
      int x = read_req();
      printf("x = %d\n", x);
    }

        % gcc -g -static -fno-stack-protector -fcf-protection=none readreq.c -o readreq
        % ./readreq
        1234
        % ./readreq
        AAAAAAAAAAAA....AAAA

      Why did it crash?
      We should think "this is a bug; could an attacker exploit it?"
      Let's figure out what exactly is happening.
        Need to know details of x86-64.

        % gdb ./readreq
        b read_req
        r
        disas $$rip
        info reg

      Where is buf[]?

        print &buf[0]
        print $$rsp
        print &i

      Aha, buf[] is on the stack, followed by i.
      The sub $$0x90, %rsp allocates space for buf[] and i.

      Let's draw a picture of what's on the stack.
                             +------------------+
                             |  main()'s frame  |
                             |                  |
                             |                  |
                             +------------------+
                             |  return address  |
                             +------------------+
                %rbp ------> |    saved %rbp    |
                             +------------------+
                             |        i         |
                             +------------------+
                             |       ...        |
                             +------------------+
                             |     buf[127]     |
                             |       ...        |
                %rsp ------> |      buf[0]      |
                             +------------------+
      The x86 stack grows down in addresses.
      push == decrement %rsp, then write to *%rsp

      %rbp is "frame pointer" -- saved stack ptr at function entry.

        x $$rbp
        x $$rbp+8

      Let's see what the saved return %rip refers to:

        disas 0x00401cf3

      It's the instruction in main() after the call to read_req()
      OK, back to read_req, just before gets()

        disas $$rip
        next
        AAAAAAA...AAA (190 times)

      What did gets() do to the stack?

        print &buf[0]

      Hmm, 190 is more than 128!
      How can that be?

        x $$rbp
        x $$rbp+8

      Saved frame pointer and return eip are 0x41414141!
      What's 0x41?

        next
        disas
        stepi
        stepi
        disas

      Now about to execute read_req()'s return instruction.

        x $$rsp
        note rip will be 0x41414141
        stepi -- crash, this is our seg fault

      Is this a serious problem?
        I.e. if our web server code had this bug,
          could an attacker exploit it to break into our computer?

      Is the attacker limited to jumping somewhere random?
        No: "code injection" attack.
        How does the adversary know the address of the buffer?
        Simulate attack:
          handle SIGSEGV nopass
          set{long}$rsp=<address of lea before call to printf in main>.

      What can the adversary do once they are executing injected code?
        If the process is running as root or Administrator, can do anything.
        Even if not, can still send spam, read files (web server, database), ..
        Can load bigger program from somewhere on the net.

      What happens if stack grows up, instead of down?
        Stack frame for read_req() has buf[] at highest address,
          so won't overflow onto read_req()'s return %rip.
        Can an attacker still exploit this bug?

    How to defend against buffer overflows?
      Use a language that checks array bounds automatically.
      For C:
        Don't call gets().
        Intel lets you mark the stack as non-executable.
          Is this a 100% solution for C?
        Randomize layout, canaries, &c
        Structure the application to limit damage from bugs (Lab 2).
        Good news: simple buffer overruns like this do not work any more.

    Buffer overflow lessons:
      Bugs are a problem in all parts of code, not just in security mechanism.
      Policy may be irrelevant if the implementation has bugs.
      But stay tuned; there is hope for the defense.
    ```