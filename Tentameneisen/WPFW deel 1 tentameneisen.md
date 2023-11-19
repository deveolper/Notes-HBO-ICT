**Documentversie: 27-okt-2023 12:45**

**Author: Laurens Frensen (22106189)**

De wegingen en wat we moeten kennen heb ik van de [toetsmatrijs](https://brightspace.hhs.nl/d2l/le/lessons/56633/units/567017) verkregen. Deze informatie heb ik vervolgens gesorteerd om de zwaarst wegende dingen bovenaan te zetten en heb ik anders geformatteert. Ook heb ik de kennis er bij gezet conform mijn aantekeningen en online onderzoek (bronnen zijn vermeld):

# C# (D-1) Weging: 16 %
Bron: [BrightSpace](https://brightspace.hhs.nl/d2l/le/lessons/56633/units/567017)
> Je bent bekend met de volgende elementen uit de taal C#. Je kunt de volgende C# technieken toepassen, je weet waarom het bestaat, en je weet wanneer het wordt gebruikt:

## Method hiding
### Wat is het?
Bron: [GeeksForGeeks](https://www.geeksforgeeks.org/method-hiding-in-c-sharp/)

Method-hiding (ookwel bekend als method-shadowing) maakt het mogelijk om tijdelijk een methode van de basisklasse (superklasse of parentklasse) te verbergen door een andere implementatie ervoor in de plaats te zetten.

### Hoe pas je het toe?
Als je een methode wil verbergen, dan kan je een methode aanmaken met dezelfde naam en het `new`-keyword gebruiken voor het return-type.

```cs
class NaamGenerator
{
    public string genereerNaam()
    {
        return "Alice";
    }
}

class NepNaamGenerator : NaamGenerator
{
    public new string genereerNaam()
    {
        return "Bob";
    }
}
```
In dit voorbeeld is de methode `genereerNaam` verborgen in `NepNaamGenerator`.

### Waarom bestaat het?
Bron: [StackOverflow](https://stackoverflow.com/questions/14461725/what-scenarios-does-it-make-sense-to-use-method-hiding)

Stel, een library voegt een methode toe en method-hiding bestaat niet. Alle gebruikers van die library die toevallig zelf ook een methode hebben met die naam, krijgen ineens errors. Daarom is het handig om method-hiding te hebben.

### Wanneer wordt het gebruikt?
Een plek waar method-hiding vaak wordt gebruikt is volledig per ongeluk. Namelijk als een library een update geeft die een methode toevoegt, en iemand anders had een subclass gemaakt die deze methode implementeert, dan is dat nu een method-hiding-geval.

Het keyword `new` is niet noodzakelijk. Je kan het keyword weglaten en de code zal precies hetzelfde werken. Je krijgt hooguit een compiler-warning om je erop te attenderen dat je method-hiding gebruikt zonder expliciet aan te geven dat dat de bedoeling was.

### Syntactisch voorbeeld
Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/6f90ba00-4986-4227-851d-17df96c962c3)

```cs
using System;

class BaseClass
{
    public void Display()
    {
        Console.WriteLine("This is the method from the BaseClass");
    }
}

class DerivedClass : BaseClass
{
    public new void Display()
    {
        Console.WriteLine("This is the method from the DerivedClass");
    }
}

class Program
{
    static void Main()
    {
        BaseClass baseObj = new BaseClass();
        baseObj.Display(); // Calls the method from the BaseClass

        DerivedClass derivedObj = new DerivedClass();
        derivedObj.Display(); // Calls the method from the DerivedClass

        // If we upcast to the base class, it still calls the base class method
        BaseClass upcastedObj = new DerivedClass();
        upcastedObj.Display(); // Calls the method from the BaseClass

    }
}

```

Hierbij is `ShowMessage` van de `BaseClass` verborgen als je een instantie van de `DerivedClass` gebruikt.

## Properties
Bron: [Microsoft - Learn](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)

Maakt het mogelijk om het gedrag van het lezen en schrijven van velden te veranderen.

### Wanneer wordt het gebruikt
Als je de manier waarop een veld gelezen of geschreven wordt wilt aanpassen. Dit kan bijvoorbeeld zijn als je wil dat het aanpassen van een veld, gelijk een wijziging in de database doorvoert.

En wanneer je de getter wil implementeren is als je bijvoorbeeld de waarde ergens vandaan moet ophalen.

### Syntactisch voorbeeld
Automatisch implementeren
```cs
class Klas
{
    public int aantalStudenten { get; set; }
}
```
Nu kan `aantalStudenten` worden opgevraagd en geschreven als een nogmaal veld.

Handmatig implementeren
```cs
class Klas
{
    private List<string> studentVoornamen; // Geen zin om een student-class te maken.

    public int aantalStudenten
    {
        get
        {
            return studentVoornamen.Count;
        } 
    }
}
```
Nu kan je het aantal studenten opvragen en dan telt die het aantal studenten.

## Contra variance en covariance
Bron: Leerjaar 2 > 31-8-2023 > HC WPFW

### Covariant
```cs
class Base {}
class Derived : Base {}

class Program
{
    static void Main()
    {
        IEnumerable<Base> myValue = new IEnumerable<Derived>();
    }
}
```
Dit voorbeeld werkt omdat `IEnumerable<T>` covariant is voor `T`.

Als type `MyClass<T>` covariant is voor `T` dan is `MyClass<Child>` een *child* van `MyClass<Parent>`.

### Contravariant
Bron: [Microsoft - Learn](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/covariance-contravariance/)

Als type `MyClass<T>` contravariant is voor `T` dan is `MyClass<Child>` een *parent* van `MyClass<Parent>`.

```cs
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}
```

## Generic type constraints
Als je gebruik maakt van een generic-type wat wel aan bepaalde eisen moet voldoen.

Voorbeeld:
```cs
public class Program
{
    public static T findMax(T[] items) where T : IComparable<T>
    {
        T max = items[0];

        for (T item in items)
        {
            if (item.CompareTo(max) > 0)
            {
                max = item;
            }
        }

        return max;
    }
}
```
In dit voorbeeld is `where T : IComparable<T>` een generic type constraint die aangeeft dat `T` een type moet zijn wat het `IComparable`-interface moet ondersteunen.

## Object en list initializers
Een voorbeeld van een object-initializer zegt denk ik meer dan een definitie:
```cs
class Cat
{
    public string name { get; set; }
    public string sentMsg { get; set; }
}

public class Program
{
    static void Main(string[] args)
    {
        Cat cat = new Cat { name = "Kiki", sentMsg = "/7//////////////////////////////,.r6"};
    }
}
```
En een voorbeeld van een list-initializer is denk ik ook beter dan een definitie:
```cs
public class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int> { 1, 2, 3 };
    }
}
```

## Operator-overloading
Bron: [TutorialsPoint](https://www.tutorialspoint.com/csharp/csharp_operator_overloading.htm)

```cs
class Box
{
    public int length;
    public int breadth;
    public int height;

    public Box()
    {
        this(0, 0, 0);
    }

    public Box(int length, int breadth, int height)
    {
        this.length = length;
        this.breadth = breadth;
        this.height = height;
    }

    /**
     * Overload the + operator for Box-types.
     */
    public static Box operator+ (Box b, Box c) {
        Box box = new Box();
        box.length = b.length + c.length;
        box.breadth = b.breadth + c.breadth;
        box.height = b.height + c.height;
        return box;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Box box1 = new Box(1, 2, 3);
        Box box2 = new Box(2, 3, 4);

        Box box3 = box1 + box2; // This is now possible.
    }
}
```

In dit voorbeeld wordt de + operator overschreven.

## Impliciete typen
Bron: [GeeksForGeeks](https://www.geeksforgeeks.org/c-sharp-implicitly-typed-local-variables-var/)

```cs
var x = 0;
```
De variabele `x` heeft nu impliciet het type `int` gekregen.

## Extensiemethoden
Bron: [Microsoft - Learn](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)

Voorbeeld:
```cs
namespace ExtensionMethods
{
    public static class MyExtensions
    {
        public static int WordCount(this string str)
        {
            return str.Split(new char[] { ' ', '.', '?' }, StringSplitOptions.RemoveEmptyEntries).Length;
        }
    }
}
```
In dit voorbeeld is `WordCount` een extension-method voor de class `string`, dit maakt het mogelijk om het volgende te doen:
```cs
public class Program
{
    static void Main(string[] args)
    {
        string mystring = "Hallo, hoe gaat het?";

        int aantalWoorden = mystring.WordCount();
    }
}
```

## Value en referencetypen, structs
Bron: [Microsoft - Learn](https://learn.microsoft.com/en-us/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)

### Valuetype
Een valuetype is een type waar de volledige data in de eigen memory-allocation past.

Hieronder valt:
- nummerieke types
- boolean, char, date
- structs
- enumerations

### Referencetype
Een referencetype is een type die alleen een referentie naar de data opslaat (en niet de data zelf).

Voorbeelden:
- string
- arrays
- classes
- delegates

# ORM & LINQ (D-1) Weging: 16 %
## Je kunt LINQ queries schrijven in methode syntax.
Bron: [TutorialsTeacher](https://www.tutorialsteacher.com/linq/linq-method-syntax)

```cs
// string collection
IList<string> stringList = new List<string>() { 
    "C# Tutorials",
    "VB.NET Tutorials",
    "Learn C++",
    "MVC Tutorials" ,
    "Java" 
};

// LINQ Method Syntax
var result = stringList.Where(s => s.Contains("Tutorials"));
```

### Aggregate
Aggregate doet eigenlijk dit: `f(item10, f(item9, f(item8, f(item7, f(item6, f(item5, f(item4, f(item3, f(item2, item1)))))))));`

```cs
IList<int> items = new List<int>() {
    1, 2, 3, 4
};

var result = items.Aggregate((a, b) => a + b);  // int result = 10;
```

## Je begrijpt welk probleem een ORM oplost, en tegen welke problemen je aan loopt bij het gebruik van een ORM.
### Welk probleem lost een ORM op?
Bron: [ChatGPT-conversatie](https://chat.openai.com/share/7c2e7796-fec9-4334-b8fe-6ca42d31997a)

- Databases gebruiken rijen en kolommen om data op te slaan en programmeertalen gebruiken classes en attributen.
- Een ORM zorgt ervoor dat de programmeur veel minder code hoeft te schrijven.
- Dezelfde code kan voor veel verschillende databases worden gebruikt.
- Een ORM handelt ook de beveiliging tegen aanvallen zoals SQL-injectie af.
- Maakt het makkelijker aanpassingen aan de database-structuur te maken zonder dat de applicatie daar problemen van ondervind.
- Ingewikkelde queries zijn overzichtelijker.
- Relaties (een-op-veel, veel-op-veel, etc) blijven overzichtelijk omdat het grootste deel achter de schermen wordt afgehandeld.

### Welke problemen kun je tegenkomen bij het gebruik van ORM?
- De applicatie wordt iets minder snel door de overhead van de functies die ORM bied.
- Ingewikkelde queries zijn vaak wel overzichtelijker, maar soms ook minder overzichtelijk.
- Kost tijd om ervaring mee op te doen.
- Minder controle over wat er gebeurd.
- En meer, zie de bron.

## Je kent de verschillende manier van laden: explicit loading, eager loading en lazy loading.
Bron: [HashNode](https://corree.hashnode.dev/understanding-lazy-loading-eager-loading-and-explicit-loading-in-entity-framework-core)

### Explicit loading
Laad als we expliciet de `Load` methode aanroepen.

### Eager loading
Als we al een beetje weten welke data we nodig gaan hebben, kunnen we gerelateerde data in een keer ophalen. Mogelijk wanneer we de data nog niet echt nodig hebben.

### Lazy loading
Zodra bepaalde informatie voor de eerste keer nodig is, dan pas halen we de waarde op.

# Internet (C-1 en C-8) Weging: 16 %
## Je kent de client-server architectuur en je begrijpt hoe HTTP werkt.
### Client-server architectuur
Bron: [SimpliLearn](https://www.simplilearn.com/what-is-client-server-architecture-article)

De client-server architectuur verwijst naar een systeem dat de meeste van de middelen en diensten die de client aanvraagt host, levert en beheert. In dit model worden alle verzoeken en diensten via een netwerk geleverd, en het wordt ook wel het netwerkcomputingmodel of het client-servernetwerk genoemd.

De client-server architectuur, ook wel een client-servermodel genoemd, is een netwerktoepassing die taken en werkbelasting verdeelt tussen clients en servers die zich op hetzelfde systeem bevinden of zijn verbonden via een computernetwerk.

De client-server architectuur omvat doorgaans meerdere werkstations, pc's of andere apparaten van gebruikers, die zijn verbonden met een centrale server via een internetverbinding of een ander netwerk. De client stuurt een verzoek om gegevens, en de server accepteert en verwerkt het verzoek, waarbij de gegevenspakketten worden teruggestuurd naar de gebruiker die ze nodig heeft.

Dit model wordt ook wel een client-servernetwerk of een netwerkcomputingmodel genoemd.

**Samenvatting**

1. Eerst stuurt de client hun verzoek via een netwerkgeschikt apparaat.
2. Vervolgens accepteert en verwerkt de netwerkserver het verzoek van de gebruiker.
3. Tenslotte levert de server het antwoord aan de client.

### Werking HTTP
Bron: [ChatGPT-conversatie](https://chat.openai.com/share/cfecd06c-8a61-4fe3-878c-5ff0fd6f6ae2)

Bron: Leerjaar 2 > 5-10-2023 > HC WPFW

HTTP staat voor Hypertext Transfer Protocol. Dit vormt de basis voor de communicatie op het web. Het is een client-server model (zie hierboven). De request die je doet heeft een methode (GET, POST, PUT, UPDATE, DELETE, PATCH, HEAD, OPTIONS), een URL (Universal Resource Locator), headers (info over waar de request heen moet, waar die vandaan komt, welke browser gebruikt wordt, etc), en een body met de data (payload).

De server verwerkt de request en zend een HTTP-response met een statuscode, headers, en een body met de opgevraagde data. De client (meestal een browser) toont de response of gebruikt dit in het geval van een applicatie.

HTTP is stateless, elke request en response zijn onafhankelijk vann elkaar, dus om iets van een staat van de pagina bij te houden heb je technieken zoals cookies nodig.

## Je kent de technieken om websites te beveiligen tegen aanvallen van hackers (XSS, CORS, HTTPS, JWT tokens, DDOS).
### XSS (Cross-site scripting)
Bron: [Wikipedia](https://en.wikipedia.org/wiki/Cross-site_scripting)

**Wat is het?**

Een kwetsbaarheid die een aanvaller in staat stelt om client-side scripts op pagina's te stoppen die door andere bezoekers wordt uitgevoerd.

Voorbeeld:
Stel, we hebben een forum die het toelaat om HTML-formatting in je post te gebruiken en je post het volgende bericht:
```html
<script>
// Some malicious code
</script>
```
Dan wordt de gewenste code door alle clients die de pagina bezoekt gewoon uitgevoerd. Dat is een XSS-kwetsbaarheid.

**Beveiliging**

Valideer alle invoer of encode het op een veilige manier.

### CORS (Cross-origin resource sharing)
Bron: [Wikipedia](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)

Cross-origin resource sharing (CORS) is een mechanisme dat beperkte bronnen op een webpagina toestaat om te worden gebruikt vanaf een domein buiten het domein waaruit de bron oorspronkelijk werdt gebruikt.

Een webpagina kan cross-origin afbeeldingen, stijlbladen, scripts, iframes en video's embedden. CORS is een manier waarop een client en een server kunnen communiceren om te bepalen of het veilig is om het cross-origin verzoek toe te staan. Het biedt meer vrijheid en functionaliteit dan puur same-origin verzoeken, maar is veiliger dan simpelweg alle cross-origin verzoeken toe te staan.

### HTTPS (HyperText Transfer Protocol Secure)
HTTP maar dan met cryptografische beveiliging (encryptie, digital-signatures, etc.)

### JWT tokens (JSON Web Token)
Bron: [Wikipedia](https://en.wikipedia.org/wiki/JSON_Web_Token)

Een manier om data met een optionele digitale handtekening en optioneel gebruik van encryptie die een aantal claims doet (bijvoorbeeld, ik ben ingelogd als admin).

Dit token wordt digitaal ondertekent door de server.

### DDOS (Distributed Denial Of Service)
Bron: [Wikipedia](https://en.wikipedia.org/wiki/Denial-of-service_attack#Distributed_DoS)

Een denial of service attack die vanaf meerdere aanvallende apparaten tegelijkertijd wordt uitgevoerd.

Een denial of service attack is een aanval waarbij je het doelwit aanvalt door een gigantische hoeveelheid requests te doen.

## Je begrijpt elke regel code in de opdracht die wordt gegeven. 
Ik kan hier helaas geen goede hulp bieden vrees ik. Oefening baart kunst.

# Testen mocks (D-2) Weging: 15 %
## Je kunt dependency injection toepassen en je begrijpt welk probleem het oplost.
### Toepassen dependency injection
Bron: [ChatGPT-conversatie](https://chat.openai.com/share/c99c7de9-e520-4531-a164-eff11006fff0)

Dependency Injection (DI) is een software design pattern wat vaak in C# en andere OOP talen wordt gebruikt om betere code te produceren. In DI, worden afhankelijkheden van de class meegegeven van buitenaf in plaats van dat die worden aangemaakt in de class. Dit maakt het makkelijker om een andere implementatie te gebruiken (bijvoorbeeld bij testen) en zorgt voor meer flexibiliteit.

Voorbeeld:
1. **Definieer je services of dependencies:**

    Identificeer alle services en dependencies die je class nodig heeft. Dit zijn vaak de interfaces en classes die je class gebrukt.
    
    Voorbeeld:

    ```csharp
    public interface IMyService
    {
        void DoSomething();
    }

    public class MyService : IMyService
    {
        public void DoSomething()
        {
            // Implementation here
        }
    }
    ```

2. **Maak de class die de afhankelijkheden vereist:**

    Maak de class die de afhankelijkheden vereist, maar maak **niet** de afhankelijkheden aan inn de class, geef in plaats daarvan een argument mee aan de constructor.

    ```csharp
    public class MyClass
    {
        private readonly IMyService _myService;

        public MyClass(IMyService myService)
        {
            _myService = myService;
        }

        public void SomeMethod()
        {
            _myService.DoSomething();
            // Additional logic here
        }
    }
    ```

3. **Configureer de Dependency Injection Container:**

    Je moet een dependency injection container definieren. Een populaire keuze is `IServiceProvider` van Microsoft:

    ```csharp
    IServiceCollection services = new ServiceCollection();
    services.AddSingleton<IMyService, MyService>();
    services.AddTransient<MyClass>();

    IServiceProvider serviceProvider = services.BuildServiceProvider();
    ```

4. **Bepaal en gebruik de dependencies:**

    ```csharp
    var myClass = serviceProvider.GetRequiredService<MyClass>();
    myClass.SomeMethod();
    ```

    De container zorgt dat de vereiste dependencies worden meegegeven aan je class.

Door Dependency Injection toe te passen verminder je de koppeling tussen de classes en de afhankelijkheden, dit maakt het makkelijker om deze te testen en te onderhouden.

### Welk probleem het oplost
Dependency Injection maakt het makkelijker om software te testen dankzij de mogelijkheid om een MockClass mee te geven als dependency.

Ook maakt Dependency Injection het makkelijker om later te wisselen van dependency.

## Je weet wat dependency inversion is. Je kunt je eigen mock klassen schrijven.
### Wat dependency inversion is
Bron: Leerjaar 2 > 5-9-2023 > WPFW

- Onderscheidt hoge-niveau classes en lage-niveau classes
- Mogen niet afhankelijk van elkaar
- Beide moeten afhankelijk zijn van abstracties (interfaces en abstract classes), niet van concrete implementaties

### Voorbeeld eigen mock klassen
Bron: Noah Gram

Bron: [TeleRik](https://www.telerik.com/blogs/how-to-simplify-your-csharp-unit-testing-mocking-framework)

Hier hebben we een `ICalculator` interface die een `Sum` method heeft. De `Calculator` class zorgt voor de verwerking en berekening van de meegegeven parameters.

```cs
public interface ICalculator
{
    int Sum(int a, int b);
}

public class Calculator : ICalculator
{
    public ICalculator calc;

    public Calculator(ICalculator calc)
    {
        this.calc = calc;
    }

    public int Sum(int a, int b)
    {
        return this.calc.Sum(a, b);
    }

    public static void Main(string[] args)
    {

    }
}
```

Deze Moq test test of de `Sum` method de goede output returned.

```cs
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Moq;

namespace Tests
{
    [TestClass()]
    public class CalculatorTests
    {
        [TestMethod()]
        public void MockTest1()
        {
            var m = new Mock<ICalculator>();
            m.Setup(c => c.Sum(3, 2)).Returns(5);
            var res = new Calculator(m.Object);

            // Act
            int resultaat = res.Sum(3, 2);

            // Assert
            Assert.AreEqual(5, resultaat);
            m.Verify(c => c.Sum(3, 2), Times.AtLeastOnce());
        }
    }
}
```

## Je kent de best practices voor testen die gegeven worden in het hoorcollege.
Bron: Leerjaar 2 > 12-10-2023 > HC WPFW

Bij voorkeur is een testcase onafhankelijk van de andere testcases.
Ook gebruik je *mocking* om alle onderdelen die je niet wil testen ook daadwerkelijk niet test.

# Async programmeren (D-1) Weging: 15 %
## Je begrijpt waarom, en onder welke omstandigheden, async programmeren belangrijk is. Je kunt async programmeren toepassen in C#.
### Waarom async?
Dan kan je applicatie responsive blijven zelfs als het bezig is met een taak op de achtergrond. Ook kan het tijdens wachttijden andere dingen doen.

### Wanneer async?
Als je veel tijd bezig bent met wachten op I/O of als je met UI's te maken hebt.

### Hoe async?
```cs
public class Program
{
    public async Task<int> add(int a, int b)
    {
        return a + b;
    }

    public async Task Main(string[] args)
    {
        int sum = await add(1, 1);
    }
}
```
Het keyword `await` zegt dat het programma moet wachten op de uitvoer. Als je `await` weghaalt in het bovenstaande voorbeeld, dan krijg je een `Task<int>` terug, die je later kan `await`-en.

# API (C-1) Weging: 15 %
## Je kent JSON, je weet waar Postman voor wordt gebruikt, je weet welke functie services in het ASP.NET Core framework hebben.
### JSON (JavaScript Object Notation)
Een gestandaardiseerd gegevensformaat dat wordt gebruikt om gegevens op een gestructureerde en leesbare manier op te slaan en uit te wisselen. JSON is niet specifiek gebonden aan JavaScript en kan in verschillende programmeertalen worden gebruikt.

JSON-gegevens bestaan uit key-value pairs zoals te zien in dit voorbeeld:
```json
{
    "Naam": "Laurens",
    "Geboortedatum": {
        "Jaar": 2003,
        "Maand": "Mei",
        "Dag": 12
    },
    "Favoriete kleur": "Infrarood",
    "IsStudent": true
}
```
PS. vergeet niet om me te feliciteren. ;)

### Postman usecases
Bron: [ChatGPT-conversatie](https://chat.openai.com/share/762aca1b-0e09-4087-920a-78ac89b948ad)

- **API-testing en debugging:** met Postman kan je makkelijk requests doen, en dus makkelijk API's testen en debuggen.
- **Automatisch testen:** met Postman kan je automatisch testen.
- **API Documentatie:** Postman maakt het makkelijk om API's te documenteren. Je kan gedetaileerde documentatie voor je API's maken, inclusief voorbeeld requests en responses, deze kunnen met andere ontwikkelaars worden gedeeld.
- **API Monitoring:** Postman bied opties om capabiliteiten te monitoren en tests in te plannen die dan automatisch elke zoveel tijd worden uitgevoerd om de beschikbaarheid en prestaties van je API in de gaten te houden.
- **API Mocking:** Postman maakt het mogelijk mock-servers voor API's te maken. Dit kan handig zijn voor frontend ontwikkelaars die aan hun code moeten werken voordat de API klaar is.
- **Samenwerking:** Postmand maakt het mogelijk om heel veel dingen te delen. Dit maakt het makkelijker om samen aan dingen te werken.
- Etc. Zie bron.

### Welke functie services in ASP.NET Core hebben
MISSING

## je kent de middleware die standaard in dat framework wordt gebruikt (routing, model validation, model binding, etc.).
### Routing
Bron: Leerjaar 2 > 5-10-2023 > HC WPFW

Voorbeeldje van een controller (gedeeltelijk).
```cs
[Route("api/[controller]")]
  [ApiController]
  public class BooksController : ControllerBase
  {
    ...
    [HttpGet]
    public IActionResult GetAll() {  // GET api/Books
      ...
    }
    [HttpHead("{id}")]               // HEAD api/Books/1
    ...
    [HttpGet("{id}")]                // GET api/Books/1
    ...
    [HttpPut("{id}")]                // PUT api/Books/1
    ...
    [HttpPost]                       // POST api/Books
    ...
    [HttpDelete("{id}")]             // DELETE api/Books/1
    ...
    [Route("api/post")]              // POST api/post LET OP, dit hoeft niet een POST te zijn, maar is wel logisch.
    ...
    [Route("api/another")]
    ...
  }
```
### Model validation
Bron: [Microsoft - Learn](https://learn.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-7.0)

MISSING

### Model binding
Bron: Leerjaar 2 > 5-10-2023 > HC WPFW

Dat je een class 1-op-1 mapt met de endpoints.
`GET /books/{id}` matcht met de volgende class
```cs
class Book {
  int id;
  string name;
}
```
Model binding kan vanuit meerdere hoeken komen:
```cs
[FromQuery]
[FromRoute]
[FromForm]
[FromBody]
[FromHeader]
```
De data uit de request wordt een object (model) in de code.

## Je kunt de REST principes toepassen.
MISSING

# Specflow (D-2) Weging: 7 %
## Je begrijpt waarom BDD bestaat en waar je op moet letten bij het toepassen ervan. Je kan tests schrijven in specflow in feature-formaat met een bijbehorende step definitie.
### Waarom bestaat BDD?
Bron: [Wikipedia](https://en.wikipedia.org/wiki/Behavior-driven_development)

Behavior-driven developement bestaat omdat het de communicatie van eisen makkelijker maakt. Je geeft namelijk met concrete voorbeelden aan hoe bepaalde dingen moeten werken zodat ze een gedeeld begrip hebben voor wat de eis nu eigenlijk is.

### Waar moet je op letten bij het toepassen van BDD?
Bron: [LearningLoop](https://learningloop.io/glossary/behavior-driven-development#:~:text=Hint%20The%20risks%20associated%20with,complexity%20in%20the%20development%20process.)

- **Uitdaging bij het vaststellen van duidelijke doelen.** Behavior-Driven Development (BDD) vereist dat de ontwikkelaars en stakeholders het eens zijn over het gewenste gedrag van de software alvorens het begin van het ontwikkelen van de software. Dit kan moeilijk zijn omdat de stakeholders soms verschillende ideëen hebben over wat de software moet doen.
- **Uitdaging van het schrijven van tests.** BDD vereist dat de tests in een specifiek formaat geschreven zijn (zie voorbeeld hieronder). Dit kan ingewikkeld en rijdrovend zijn. Daarbovenop moeten er voor alle gedragingen tests geschreven worden.
- **Uitdagingen bij het debuggen.** BDD tests zijn op een bepaalde manier geschreven die het misschien moeilijk maken om te debuggen. En als de tests niet goed geschreven zijn, dan kan het moeilijk zijn om de bron van het probleem te ontdekken.

### Voorbeeld van tests in specflow (feature format)
Bron: Leerjaar 2 > 12-10-2023 > HC WPFW
```
Feature: BMI
BMI berekenen
@tag5
Scenario: BMI berekenen
  Given De webserver is geopend.
  And Ik geef het geslacht "man" aan.
  And Ik voer de leeftijd 57 in.
  And Ik voer het gewicht 75 in.
  And Ik voer de lengte 175 in.
  When Ik druk op de knop Bereken resultaat.
  Then laat de waarde 23 op het scherm zien.
```

### Bijbehorende step definitie
Bron: [ChatGPT-conversatie](https://chat.openai.com/share/91344c86-9a10-464c-9dd6-559d21d8c8a4)
```cs
[Binding]
public class BMISteps
{
    private double bmiResult;

    [Given("De webserver is geopend.")]
    public void GivenDeWebserverIsGeopend()
    {
        // Implementeer hier de code om de webserver te openen.
    }

    [Given("Ik geef het geslacht \"(.*)\" aan.")]
    public void GivenIkGeefHetGeslachtAan(string geslacht)
    {
        // Implementeer hier de code om het geslacht in te stellen.
    }

    [Given("Ik voer de leeftijd (.*) in.")]
    public void GivenIkVoerDeLeeftijdIn(int leeftijd)
    {
        // Implementeer hier de code om de leeftijd in te voeren.
    }

    [Given("Ik voer het gewicht (.*) in.")]
    public void GivenIkVoerHetGewichtIn(int gewicht)
    {
        // Implementeer hier de code om het gewicht in te voeren.
    }

    [Given("Ik voer de lengte (.*) in.")]
    public void GivenIkVoerDeLengteIn(int lengte)
    {
        // Implementeer hier de code om de lengte in te voeren.
    }

    [When("Ik druk op de knop Bereken resultaat.")]
    public void WhenIkDrukOpDeKnopBerekenResultaat()
    {
        // Implementeer hier de code om op de knop te drukken en het BMI te berekenen.
        // Het resulterende BMI zou in de variabele bmiResult moeten worden opgeslagen.
    }

    [Then("Laat de waarde (.*) op het scherm zien.")]
    public void ThenLaatDeWaardeOpHetSchermZien(double waarde)
    {
        // Implementeer hier de code om het resultaat op het scherm te controleren.
        Assert.AreEqual(waarde, bmiResult, 0.01); // Hier gebruiken we een marge van 0.01 voor de nauwkeurigheid van de dubbele waarde.
    }
}
```