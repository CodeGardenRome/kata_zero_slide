Kata Zero 
=========
Sottotitolo 
-----------

### Lambda-Roma
* Un po' di storia
  * Turing machine 
  * Church e il lambda calculus - tesi Church-Turing
  * Von Neumann (architettura)
* La Confluence
  * Amazon, Citigroup, eBay, Facebook, Groupon, Heroku, Netflix, Oracle, Pivotal Labs, Red Hat, Salesforce, Spotify, ThoughtWorks, Wikidocs, Atlassian, Zalando, Zendesk, AT&T, Bank of America Merril Lynch, Barclays, Credit Suisse, Deutsche Bank, Ericsson AB, Google, Intel, Microsoft, The New York Times, NVIDIA, Qualcomm Inc, IBM, Starbucks, Weightwatchers, Accenture, LinkedIn, Verizon, Walmart, Hawlett Packard, SAP, Morgan Stanley, ING, Electronic Arts, Panasonic, Huawei, Apple, Unicredit
* Frameworks & Libraries
  * Redux
  * Reflex
  * ImmutableJs
  * Elm
  * Java 8+ 
  * PHP rfc
  * DevOps: Serverless architecture - AWS Lambda - Immutable infrastructure (Docker)
  * Mobile: Swift e Kotlin
* Trend dei linguaggi funzionali? 
  * Surv 2017 stack overflow
  * Indeed
* Programma della community
  * Lambda-Garden - workshop
  * Talk sui linguaggi funzionali (?) 

### Ma che ce famo cor funzionale? 
* First Class Citizen
  * abstraction
  * favor composition over inheritance
  * composition di funzioni 
  * esempio codice
* immutability
  * l'immutability come buona pratica - PHP, Java, Javascript stanno implementando l'immutability
  * Alan Key - The Early History of Smalltalk 1993
  * Effective Java - Joshua Bloch 2001 
  * Esempi: 
    * Perché facciamo defensive copying? 
    * Date, Valute
    * Concurrency
  * Lo stato dell'immutability nei linguaggi (php, js, java)
* side-effects (e side-causes), gli input e gli output celati nel sistema
  * leggibilità: gli input e gli output nascosti ci impongono di interpretare completamente il codice
  * test integrativi
* purezza
  * atomicità
  * testabilità
  * autodocumentale

### Toolbox! 
* Concetti
  * Function Composition
  * Immutability
  * Purity
  * Side Effects
  * Side Causes
* Nella nostra toolbox oggi inseriamo le high order function principali:
  * Map
  * Filter
  * Reduce
* Le high order function sono funzioni che accettano almeno due parametri: una funzione anonima (lambda) e una lista di elementi. La lambda sarà applicata a ogni elemento della lista indipendentemente dalla high order function. La natura della high order function è determinata da come *decora* la lambda in input. 
* ~~esempio di map~~ Map applica la lambda ad ogni elemento della lista (la lambda ha in input l'elemento corrente) restituendo una nuova lista di elementi trasformati. 
* ~~esempio di filter~~ Filter restituisce una nuova lista creata da tutti quegli elementi che hanno soddisfatto un criterio. Il criterio è un'espressione booleana, risultato della lambda. 
* ~~esempio di reduce~~ Reduce ha un terzo argomento: l'accumulatore. Permette di *sintetizzare* gli elementi della lista "accumulando" un unico risultato all'interno dell'accumulatore. Vedremo che è possibile generare con reduce anche più risultati se l'accumulatore dovesse essere una lista o una mappa. 

### Katas
