Kata Zero 
=========
Sottotitolo 
-----------

### Lambda-Roma
* Un po' di storia
  * Turing Machine 
    * foto di Benedict Cumberbach, magari in versione Dr Strange
    * foto di Turing e della ricostruzione della sua macchina bomb
  * Church e il lambda calculus
    * Foto di Church 
    * tesi Church-Turing
  * Von Neumann (architettura)
    * Foto di Von Neumann
* La Confluence
  * Citigroup "Pivotal Labs" ThoughtWorks "Bank of America Merril" Lynch Barclays Credit Suisse, "Deutsche Bank" "The New York Times" Qualcomm Verizon SAP "Morgan Stanley" ING Unicredit
  * LinkedIn Heroku "Red Hat" Groupon Zalando Starbucks Weightwatchers Accenture Wikidocs Zendesk "Hawlett Packard" Panasonic NVIDIA "Electronic Arts" "Ericsson AB" Walmart Salesforce
  * Facebook Amazon Google Apple Microsoft Netflix eBay Oracle IBM Spotify Atlassian Huawei AT&T Intel Paypal
* Frameworks & Libraries
  * Redux
  * Reflex
  * Immutable.php, Functional-php
  * Elm
  * Java 8+ 
  * DevOps: Serverless architecture - AWS Lambda - Immutable infrastructure (Docker)
  * Mobile: da Java e Objective-C a Kotlin e Swift
* Trend dei linguaggi funzionali? 
  * Surv 2017 stack overflow
    * grafico retribuzioni
    * grafico soddisfazione
  * Indeed
    * grafico richieste dev funzionali 
* Programma della community
  * Lambda-Garden - workshop
    * foto di Mosca vs foto di Totti - Insegnare le regole del calcio non fa giocatori
  * Talk sui linguaggi funzionali

### Ma che ce famo cor funzionale? 
* First Class Citizen
  * abstraction
  * favor composition over inheritance [inserisci una funzionalita' come componente innestato, ma puo' essere semplicemente una funzione cfr. $Esempi]
  * composition di funzioni [senza nemmeno creare l'oggetto contenitore, posso creare una funzione da altre, come pipeline di elaborazione cfr. $Esempi]
  * esempio codice
* immutability
  * l'immutability come buona pratica 
    * PHP 
      * RFC https://wiki.php.net/rfc/immutability
      * https://github.com/tightenco/collect
      * https://github.com/jkoudys/immutable.php
    * Java 
    * Javascript 
      * ImmutableJs
  * Alan Key - The Early History of Smalltalk 1993
    * foto con citazione da ImmutableJS.com
  * Effective Java - Joshua Bloch 2001 
    * citazione ~~manca citazione~
  * Perché l'immutability? 
    * Defensive copying

``` 
public final class Planet {

  private final Date fDateOfDiscovery;

  public Planet (double aMass, String aName, Date aDateOfDiscovery) {
     fMass = aMass;
     fName = aName;
     fDateOfDiscovery = new Date(aDateOfDiscovery.getTime());
  }
  
  ...
  
  /**
   * defensive copying
   */ 
  public Date getDateOfDiscovery() {
    return new Date(fDateOfDiscovery.getTime());
  }
}
```
    * Date, Valute
    * Value Objects
    * Concurrency
* side-effects (e side-causes), gli input e gli output celati nel sistema
  * leggibilità: gli input e gli output nascosti ci impongono di interpretare completamente il codice
  * dependency injection 
  * test integrativi
* purezza
  * atomicità
  * testabilità
  * autodocumentale
  * principio di singola responsabilità
    * state changes


```
$a = 1;
$b = 2; 
$c = $a; 
$a = $b; // $a = 2
$b = $c; // $b = 1 


class ImpurityExample
{
  private $sideCauseBase;
  private $sideCauseExp;
  private $sideEffectResult;
  
  public function setBase(int $base)
  {
    $this->sideCauseBase = $base;
  }
  
  public function setExp(int $exp)
  {
    $this->sideCauseExp = $exp;
  }
  
  public function pow(): int 
  {
    $res = 1; 
    for($i = 0; $i < $this->exp; $++) {
      $res = $res * $this->base;
    }
    
    $this->result = $res;
  }
  
  public function getResult(): int 
  {
    return $this->sideEffectResult;
  }
}

// usage
$impureObj = new ImpurityExample();
$impureObj->setBase(2); 

// in another part of the code
$impureObj->setBase(3);
$impureObj->pow();

// inconsistence 
$res = $impureObj->geResult(); // $res = 6


class PurityExample
{
  static public function pow(int $base, int $exp): int
  {
    $res = 1; 
    for($i = 0; $i < $exp; $++) {
      $res = $res * $base;
    }
    
    return $res;
  }
}

//usage 
$res = PurityExample::pow(2, 2); // $res = 4 
``` 
  * leggibilità: gli input e gli output celati ci impongono di interpretare completamente il codice
  * testabilità: richiedono test integrativi e mocks
  * dependency injection
  * il codice impuro può essere inconsistente 
  * le funzioni impure necessiterebbero di documentazione
* purezza
  * atomicità
  * consistenza
  * principio di singola responsabilità
  * testabilità: test unitari e stubs
  * Le funzioni pure sono auto-documentali

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
* Map applica la lambda ad ogni elemento della lista (la lambda ha in input l'elemento corrente) restituendo una nuova lista di elementi trasformati. 
  * esempio
* Filter restituisce una nuova lista creata da tutti quegli elementi che hanno soddisfatto un criterio. Il criterio è un'espressione booleana, risultato della lambda. 
  * esempio
* Reduce ha un terzo argomento: l'accumulatore. Permette di *sintetizzare* gli elementi della lista "accumulando" un unico risultato all'interno dell'accumulatore. Vedremo che è possibile generare con reduce anche più risultati se l'accumulatore dovesse essere una lista o una mappa. 
  * esempio 

### Katas

---

### Esempi
#### Composizione di un oggetto per il calcolo IMU
*Soluzione a oggetti*
```scala
//Imponibile di imposta
trait BaseComputation {
  def baseFor(revenue: Double): Double
}

trait CityRatesTable
trait BuildingCategory

//Aliquote
trait RateComputation {
  def cityRates(cityName: String): CityRatesTable
  def rateFor(city: CityRatesTable, cat: BuildingCategory): Double
}

//Riduazioni
trait DiscountComputation {
  def discountMultiplier: Double
  def applyDiscount(value: Double): Double = value * discountMultiplier
}


class Base extends BaseComputation {
  override def baseFor(revenue: Double) = revenue * (1.05)
}

case class FreeUseToNearParents extends DiscountComputation {
  override val discountMultiplier = 0.5
}

case class ArtisticHistorical extends DiscountComputation {
  override val discountMultiplier = 0.5
}

case class Inaccessible extends DiscountComputation {
  override val discountMultiplier = 0.5
}

case class AgreedRateRent extends DiscountComputation {
  override val discountMultiplier = 0.25
}


case class IMUComputation(
  base: BaseComputation,
  baseDiscount: Option[DiscountComputation],
  rate: RateComputation,
  rateDiscount: Option[DiscountComputation]
) {
  
  def compute(revenue: Double, category: BuildingCategory, cityName: String): Double = {
    var taxable = base.baseFor(revenue)
 
    if (baseDiscount.isDefined) taxable = baseDiscount.get.apply(taxable)
 
    var taxed = taxable * rate.rateFor(rate.cityRates(cityName), category)
 
    if (rateDiscount.isDefined) taxed = rateDiscount.get.apply(taxed)
 
    taxed
  }

}
```
*Soluzione con funzioni*
```scala
// with 1st-class functions as components
case class IMUComputation(
  baseOnRevenue: Double => Double,
  baseDiscount: Option[Double => Double],
  cityRates: String => CityRatesTable,
  rate: (CityRatesTable, BuildingCategory, Double) => Double,
  rateDiscount: Option[Double => Double]
) {
  
  def compute(revenue: Double, category: BuildingCategory, cityName: String): Double = {
    var taxable = baseOnRevenue(revenue)

    if (baseDiscount.isDefined) taxable = baseDiscount.get(taxable)

    var taxed = rate(cityRates(cityName), category, taxable)

    if (rateDiscount.isDefined) taxed = rateDiscount.get(taxed)

    taxed
  }

}
```
*usando una pipe di funzioni*
```scala
// functions pipeline
case class IMUComputation(
  baseOnRevenue: Double => Double,
  baseDiscount: Option[Double => Double],
  cityRates: String => CityRatesTable,
  rate: (CityRatesTable, BuildingCategory) => Double => Double,
  rateDiscount: Option[Double => Double]
) {

  val id: Double => Double = identity
  
  def apply(revenue: Double, category: BuildingCategory, cityName: String): Double =
    baseOnRevenue
      .andThen(baseDiscount.getOrElse(id))
      .andThen(rate(cityRates(cityName), category))
      .andThen(rateDiscount.getOrElse(id))(revenue)

}
```
*Usando solo funzioni*
```scala
//or with simple plain functions
val baseOnRevenue: Double => Double
val baseDiscount: Option[Double => Double]
val cityRates: String => CityRatesTable
val rate: (CityRatesTable, BuildingCategory) => Double => Double
val rateDiscount: Option[Double => Double]
val id: Double => Double = identity

val computeIMU: (BuildingCategory, String) => Double => Double = 
  (category, cityName) =>
    baseOnRevenue
      .andThen(baseDiscount.getOrElse(id))
      .andThen(rate(cityRates(cityName), category))
      .andThen(rateDiscount.getOrElse(id))
```
