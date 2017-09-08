Kata Zero 
=========
Sottotitolo 
-----------

### Perché il paradigma funzionale? ~~quel che segue è liberamente tratto dal primo paragrafo di Vitalij~~
* ~~esempio di assembly~~
* ~~esempio di codice moderno imperativo~~
* ~~esempio di classe verbosa: è importante iniziare a dire che la forma classica di programmazione OOP non è più leggibile di un linguaggio come Scala. Mostrando una classona e una piccola classe in scala si può dimostrare la verbosità dei linguaggi vecchio stile~~
* ~~esempio di oggetto Scala: Scala mi sembra il miglior rappresentante da prendere ad esempio È più vicino ai linguaggi imperativi classici, haskell e il lisp/clj sono troppo funzionali...~~
* La confluence del 2014 ~~la storia del FP potremmo raccontarla un po' per volta. Mi sembra interessante parlare della confluence in prima istanza per stimolare l'appetito. Qui in realtà bisognerebbe parlare del raggiunto limite della frequenza di clock dei procesori e citare un certo articolo che ha cambiato il corso della stora, ma potremmo farlo più avanti riprendendo l'argomento~~

### Cos'è il paradigma funzionale? ~~vorrei introdurre l'argomento dal generale al particolare nel corso degli eventi~~
* È un modo diverso di risolvere i problemi 
* È una collezione di buone pratiche in più
* Non richiede una Laurea in matematica!
* Non manda in pensione il vostro know-how, ma lo arricchisce! 
* Tutto sommato si potrebbe dire che il paradigma funzionale è una marcia in più, vedremo come dopo aver svolto i primi esercizi

### Kata imperativi
Esercizi  

### Toolbox! 
* Ad ogni Lambda-garden arricchiremo la nostra "cassetta degli attrezzi" con nuovi strumenti. Molti sono già nella vostra toolbox da tempo e li utilizzate giornalmente. Alcuni di voi potrebbero scoprire che stanno già sfruttando il paradigma funzionale senza saperlo! 
* Nella nostra toolbox oggi inseriamo le high order function principali:
  * Map
  * Filter
  * Reduce
* Le high order function sono funzioni che accettano almeno due parametri: una funzione anonima (lambda) e una lista di elementi. La lambda sarà applicata a ogni elemento della lista indipendentemente dalla high order function. La natura della high order function è determinata da come *decora* la lambda in input. 
* ~~esempio di map~~ Map applica la lambda ad ogni elemento della lista (la lambda ha in input l'elemento corrente) restituendo una nuova lista di elementi trasformati. 
* ~~esempio di filter~~ Filter restituisce una nuova lista creata da tutti quegli elementi che hanno soddisfatto un criterio. Il criterio è un'espressione booleana, risultato della lambda. 
* ~~esempio di reduce~~ Reduce ha un terzo argomento: l'accumulatore. Permette di *sintetizzare* gli elementi della lista "accumulando" un unico risultato all'interno dell'accumulatore. Vedremo che è possibile generare con reduce anche più risultati se l'accumulatore dovesse essere una lista o una mappa. 

### Kata funzionali

