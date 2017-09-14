Kata Zero 
=========
Sottotitolo 
-----------

### Lambda-Roma
* Brevissima introduzione alla storia di FP
* La Confluence - citiamo i big che sono passati, anche solo parzialmente, al funzionale
* Sarebbe interessante anche citare le librerie come Redux e ImmutableJs
* Citerei anche Java Lambda e le novità in arrivo, se ce ne sono, dell'ecosistema JVM
* Trend dei linguaggi funzionali? 
* Programma della community
  * Lambda-Garden - workshop
  * Talk sui linguaggi funzionali (?) 

~~il titolo non mi piace~~
### Cosa può fare il funzionale per voi? 
* immutability
  * introduzione del concetto
  * immutability nei linguaggi (php, js, java)
  * vorrei citare anche le rfc di php aperte sull'immutability 
* side-effects (e side-causes), gli input e gli output celati nel sistema
  * leggibilità: gli input e gli output nascosti ci impongono di interpretare completamente il codice
  * test integrativi
* purezza
  * atomicità
  * testabilità
  * composizione
  * autodocumentale
  * modularità

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
