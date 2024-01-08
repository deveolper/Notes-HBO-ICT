**Documentversie: 1-nov-2023 20:35**

**Author: Laurens Frensen (22106189)**

Zoals gebruikelijk heb ik de eisen weer van de [matrijs](https://brightspace.hhs.nl/d2l/le/lessons/56633/units/567017).

Deze keer is dit document heel gehaast opgesteld en maakt daarom gebruik van minder bronnen dan gebruikelijk. Dit zal ik later oplossen (wanneer de stof in de les wordt behandeld), maar voor nu is er in ieder geval informatie om te leren.

Op het eerste gezicht lijkt het erop dat dit tentamen voornamelijk kennen en begrijpen betreft en minder toepassen dan het vorige tentamen.

# HTML (D-1), weging: 17 %
```
De student begrijpt hoe hij HTML, CSS, JavaScript in kan zetten voor de realisatie van een responsive website, waarin rekening wordt gehouden de accessibility.
```

Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/155cc6a1-7d18-4bf6-a4a6-b7818988fd76)

Deze eis voor het tentamen houdt in dat de student moet begrijpen hoe HTML, CSS en JavaScript worden gebruikt om een responsieve website te creëren met aandacht voor toegankelijkheid. Laten we deze componenten in meer detail uitleggen:

1. **HTML (HyperText Markup Language)**: HTML is de basis van een webpagina. De student moet weten hoe HTML wordt gebruikt om de structuur en inhoud van de website te definiëren. Hier zijn enkele belangrijke punten:

   - Gebruik semantische HTML-elementen (zoals `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, enz.) om de structuur van de pagina duidelijk te maken.
   - Zorg voor juiste HTML-tags en attributen voor afbeeldingen, links en formulierelementen om toegankelijkheid te waarborgen.

    Hier volgt een voorbeeld met alle behandelde elementen (TODO: incompleet):
    ```html
    <!DOCTYPE html>
    <html>
        <head>
        </head>
        <body>
        </body>
    </html>
    ```

2. **CSS (Cascading Style Sheets)**: CSS wordt gebruikt om de visuele presentatie van de website te beheren. Voor een responsieve website zijn de volgende aspecten van belang:

   - Implementeer CSS-mediaqueries om de opmaak van de website aan te passen aan verschillende schermformaten (bijvoorbeeld desktop, tablet en mobiel).
   - Maak gebruik van flexbox, grid en andere CSS-layouttechnieken om de inhoud van de pagina op een aantrekkelijke manier weer te geven op verschillende schermgroottes.

    Hier volgt een voorbeeld met alle behandelde dingen van CSS (TODO: incompleet):
    ```css
    ```

3. **JavaScript**: JavaScript voegt interactiviteit toe aan de website. Voor toegankelijkheid moet de student rekening houden met:

   - Het implementeren van toetsenbordnavigatie, zodat alle interactieve elementen met behulp van het toetsenbord kunnen worden bediend.
   - Toegankelijkheidsfuncties, zoals ARIA-landmarks (Accessible Rich Internet Applications) gebruiken om de website begrijpelijk te maken voor hulpmiddelen voor mensen met een handicap.

    Hier volgt een voorbeeld met alle behandelde dingen van JavaScript:
    ```js
    // TODO: voeg code toe
    ```

4. **Toegankelijkheid**: Het tentamen benadrukt ook het belang van toegankelijkheid. Dit houdt in dat de student rekening moet houden met gebruikers met verschillende handicaps, zoals visuele, auditieve of motorische beperkingen. Dit omvat:

   - Zorgen voor alternatieve tekst voor afbeeldingen.
   - Ondersteuning bieden voor schermlezers.
   - Zorgen voor voldoende contrast tussen tekst en achtergrond.
   - Toetsenbordnavigatie en focusindicatie optimaliseren.

Al met al moet de student begrijpen hoe deze technologieën samenwerken om een website te bouwen die zowel visueel aantrekkelijk als toegankelijk is voor een breed publiek, inclusief mensen met beperkingen. Het is van essentieel belang om de inhoud en functies van de website voor alle gebruikers toegankelijk te maken, ongeacht het apparaat dat ze gebruiken of hun individuele behoeften.

# React (D-1), weging: 17 %
```
De student begrijpt op welke manier React wordt gebruikt om een single page application te maken met dynamische content, m.b.v. een API. 
```

Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/b4d262ff-b8cc-411d-8406-86719f4392bb)

Dit tentamen vereist dat de student begrijpt hoe React wordt gebruikt om een single page application (SPA) te maken met dynamische content, met gebruik van een API. Hier is een gedetailleerde uitleg:

1. **React**: React is een JavaScript-bibliotheek voor het bouwen van gebruikersinterfaces. Het is erg populair voor het ontwikkelen van webapplicaties vanwege zijn componentgebaseerde architectuur. Studenten moeten bekend zijn met React en weten hoe ze het moeten gebruiken.

2. **Single Page Application (SPA)**: Een SPA is een type webapplicatie waarbij alle benodigde HTML, JavaScript en CSS in één enkele pagina worden geladen. In plaats van volledige pagina's opnieuw te laden, wordt de inhoud dynamisch bijgewerkt terwijl de gebruiker door de applicatie navigeert. Studenten moeten begrijpen wat een SPA is en waarom het nuttig kan zijn.

3. **Dynamische content**: Dynamische content verwijst naar inhoud op een webpagina die op basis van gebruikersinteractie of gegevens van een externe bron kan veranderen. In het geval van een SPA kan dit betrekking hebben op het bijwerken van de weergegeven informatie zonder de hele pagina opnieuw te laden. Studenten moeten begrijpen hoe ze dynamische content kunnen implementeren in een React-gebaseerde SPA.

4. **API (Application Programming Interface)**: Een API is een reeks regels en protocollen waarmee verschillende softwaretoepassingen met elkaar kunnen communiceren. Voor dit tentamen zou de API waarschijnlijk verwijzen naar een externe bron van gegevens, zoals een server, die de SPA gebruikt om gegevens op te halen of te versturen. Studenten moeten weten hoe ze met API's moeten werken, gegevens kunnen ophalen en deze in hun React-applicatie kunnen integreren.

Concreet zouden studenten in staat moeten zijn om een React-applicatie te maken die een enkele pagina is, waarvan de inhoud dynamisch kan worden gewijzigd op basis van gegevens die worden opgehaald via een API. Dit kan inhouden dat ze React-componenten maken die gegevens weergeven en bijwerken op basis van gebruikersinteractie en de gegevens van de API.

Ik hoop dat dit je helpt begrijpen wat er van je wordt verwacht voor het tentamen. Als je meer specifieke vragen hebt over bepaalde aspecten van deze eis, laat het me dan weten.

## React Voorbeeld
TODO: produceer voorbeeld.
```
```

# Meer React (C-1), weging: 17 %
```
De student begrijpt op welke manier state wordt toegevoegd aan componenten en hoe onderlinge afhankelijkheden tussen componenten tot uitdrukking komen.
```

Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/2851818b-efe4-435d-95ee-578da97eee28)

Natuurlijk, ik kan uitleggen wat deze eis voor het tentamen inhoudt. De eis heeft betrekking op het begrip van het beheer van de "state" in componenten en hoe deze componenten onderling afhankelijk kunnen zijn in een softwaretoepassing, waarschijnlijk gerelateerd aan webontwikkeling of frontend-ontwikkeling. Hier is een gedetailleerde uitleg:

1. **State in Componenten**: In moderne softwareontwikkeling, vooral bij het werken met bibliotheken zoals React in JavaScript, hebben componenten een centrale rol. Een "state" in dit verband verwijst naar de gegevens en toestand die door een specifieke component wordt bijgehouden. Dit kan variëren van eenvoudige waarden zoals tekst tot meer complexe gegevens zoals lijsten, formulierinvoer, enz.

2. **Hoe State Wordt Toegevoegd aan Componenten**: Om de state toe te voegen aan een component, moet je overwegen hoe deze gegevens worden gebruikt binnen de component en hoe ze kunnen veranderen. In React, bijvoorbeeld, kun je de `useState` hook gebruiken om de state aan een functionele component toe te voegen. Je definieert een stuk geheugen in de component om de state op te slaan en kunt het bijwerken met behulp van specifieke functies.

3. **Onderlinge Afhankelijkheden Tussen Componenten**: In een complexe toepassing werken verschillende componenten samen. De onderlinge afhankelijkheden verwijzen naar situaties waarin de staat van de ene component van invloed kan zijn op de staat of het gedrag van andere componenten. Bijvoorbeeld, als je een invoerveld hebt in een formuliercomponent, kan de waarde van dat veld van invloed zijn op de weergave van andere componenten.

4. **Het Begrijpen van Onderlinge Afhankelijkheden**: Het is essentieel om te begrijpen hoe de staat tussen componenten wordt gedeeld en gecoördineerd. Dit kan worden bereikt door geavanceerde technieken zoals "lifting state up," waarbij de gedeelde staat wordt beheerd door een gemeenschappelijke oudercomponent, of door het gebruik van context-API's en bibliotheken zoals Redux voor geavanceerdere beheer van de staat.

5. **Toepassing in de Praktijk**: Om deze concepten in de praktijk toe te passen, moet je weten hoe je state kunt toevoegen aan specifieke componenten, hoe je deze state kunt bijwerken en hoe je onderlinge afhankelijkheden kunt beheren om een naadloze gebruikerservaring te bieden.

Het begrijpen van deze concepten is van vitaal belang bij het ontwikkelen van moderne web- en softwaretoepassingen, vooral in het kader van frontend-ontwikkeling. Het stelt ontwikkelaars in staat om dynamische en interactieve interfaces te creëren en gegevens effectief te beheren in een componentgebaseerde architectuur.

# Architectuur (C-1), weging: 17 %
```
De student begrijpt wat voor problemen worden opgelost met architectuurpatronen. De student begrijpt MVC, Microservices, Monoliths, Clean Architecture en Layers. De student kan de voor en nadelen van deze architectuurpatronen tegen elkaar afwegen m.b.t. verschillende toepassingen.
```

Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/105876f0-2b0b-489f-85f7-905b029bc3a5)

Het tentamen-eis waar je naar verwijst, vraagt om begrip van verschillende architectuurpatronen en de capaciteit om de voor- en nadelen van deze patronen in verschillende toepassingsgebieden tegen elkaar af te wegen. Laten we dit in meer detail bespreken:

1. **Architectuurpatronen**: Deze verwijzen naar gestandaardiseerde manieren om de structuur en organisatie van een softwaretoepassing te ontwerpen. Ze bieden richtlijnen voor het organiseren van code en functionaliteit. Enkele veelvoorkomende architectuurpatronen zijn:

   - **MVC (Model-View-Controller)**: Dit is een patroon dat vaak wordt gebruikt in webtoepassingen. Het verdeelt de applicatie in drie belangrijke componenten: Model (gegevens), View (gebruikersinterface) en Controller (logica voor de interactie tussen Model en View).

   - **Microservices**: Dit patroon betreft het opsplitsen van een applicatie in kleinere, onafhankelijke services die elk een specifieke taak uitvoeren. Dit maakt schaalbaarheid en onderhoud eenvoudiger, maar introduceert complexiteit in de coördinatie tussen services.

   - **Monoliths**: In tegenstelling tot microservices is een monolithische applicatie een enkele, grote codebase waarin alle functionaliteit is opgenomen. Het kan eenvoudiger zijn om te ontwikkelen, maar kan moeilijker te schalen en onderhouden zijn.

      Monoliths bevatten alle functionaliteit in een enkele server en database. Om te schalen moet je een nieuwe server en een nieuwe database toevoegen. Dit is best een grote investering. Bij microservices kan je schalen door gewoon de services die overbelast worden te schalen, en niet de volledige applicatie.

   - **Clean Architecture**: Dit is een benadering voor het organiseren van code om de afhankelijkheden om te keren, zodat de kernlogica van de applicatie onafhankelijk is van de buitenwereld. Het bevordert een geïsoleerde, testbare code.

   - **Layers**: Dit is een patroon waarin de code wordt opgesplitst in verschillende lagen, zoals de presentatielaag, applicatielaag en datalaag. Elke laag heeft een specifieke rol en verantwoordelijkheid.

     Voor de afhankelijkheden heb je eigenlijk gewoon een soort laag (laten we die voor het gemak even laag 0 noemen), die laag bevat alle modules (classes) die nergens van afhankelijk zijn. De volgende laag (laten we die laag 1 noemen) die is alleen afhankelijk van modules op laag 0. De modules van laag 2 zijn alleen afhankelijk van modules in laag 0 of laag 1, enz

2. **Voor- en nadelen afwegen**:

   - Het begrijpen van de voordelen van elk patroon is belangrijk. Bijvoorbeeld, microservices kunnen schaalbaarheid bieden, terwijl monoliths eenvoudiger te implementeren kunnen zijn.

   - Het begrijpen van de nadelen is net zo cruciaal. Bijvoorbeeld, microservices kunnen complexe communicatie en coördinatie vereisen, terwijl monoliths minder schaalbaar kunnen zijn.

   - Het is essentieel om te begrijpen wanneer elk patroon het meest geschikt is. Dit kan afhangen van de aard van de toepassing, de vereisten en de teamvaardigheden.

   - Het vermogen om de juiste architectuur te kiezen op basis van specifieke gebruiksscenario's en vereisten is cruciaal voor een succesvol softwareontwikkelingsproces.

Kortom, het tentamen vraagt om een diepgaand begrip van deze architectuurpatronen, hun voor- en nadelen en het vermogen om te redeneren welk patroon geschikt is voor verschillende situaties. Je moet in staat zijn om deze concepten in de praktijk toe te passen en te kunnen uitleggen waarom je een bepaald patroon zou kiezen voor een gegeven toepassing.

# Testing en deployment (D-2 en C-8), weging: 16 %
```
De student ziet het belang van end to end testing, en begrijpt op welke manier test tools hierbij kunnen helpen. De student kan de deployment van een applicatie inrichten op een veilige en efficiente manier.
```

Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/18d9d5fb-d874-4586-8daa-0e6fc090120e)

Deze eisen voor het tentamen verwijzen naar twee belangrijke concepten binnen softwareontwikkeling en IT: end-to-end testing en deployment van applicaties. Laten we deze concepten gedetailleerder uitleggen:

1. End-to-End Testing:
   - End-to-end testing is een fase in software testing waarbij het doel is om de functionaliteit van een applicatie te testen vanuit het perspectief van de eindgebruiker. Het simuleert echte gebruikersinteracties en kijkt of de applicatie correct werkt in een realistische omgeving.

   - Belang: End-to-end testing is van cruciaal belang om ervoor te zorgen dat een applicatie goed functioneert en aan de verwachtingen van de gebruikers voldoet voordat deze wordt uitgerold. Het helpt om mogelijke problemen op te sporen, zoals functionele fouten, prestatieproblemen of gebruikersinterfaceproblemen, voordat de applicatie in productie gaat.

   - Tools: Er zijn verschillende testtools beschikbaar voor end-to-end testing, zoals Selenium, Cypress, en Puppeteer. Deze tools stellen ontwikkelaars en QA-teams in staat om geautomatiseerde testscripts te maken die de interactie van gebruikers met de applicatie nabootsen.

2. Deployment van een Applicatie:
   - Deployment verwijst naar het proces van het vrijgeven en beschikbaar maken van een softwaretoepassing voor gebruik in een productieomgeving. Een veilige en efficiënte inzet is essentieel om ervoor te zorgen dat de applicatie correct en zonder onderbrekingen werkt.

   - Veiligheid: Bij de deployment moet ervoor worden gezorgd dat de applicatie veilig is en dat er geen beveiligingsproblemen zijn. Dit omvat het beschermen van gevoelige gegevens, het beperken van toegang tot de applicatie en het regelmatig bijwerken van beveiligingspatches.

   - Efficiëntie: Efficiënte deployment houdt in dat de applicatie snel en zonder onnodige vertragingen wordt uitgerold. Dit omvat het optimaliseren van de code, het gebruik van schaalbare infrastructuur en het minimaliseren van downtime tijdens de implementatie.

   - CI/CD (Continuous Integration/Continuous Deployment): Het gebruik van CI/CD-pijplijnen (Continuous Integration/Continuous Deployment) kan helpen bij het automatiseren van het deploymentproces. Dit stelt ontwikkelaars in staat om regelmatig nieuwe code in te zetten en automatisch te testen voordat deze naar productie gaat.

Kortom, de eisen voor het tentamen verwachten van de student dat ze begrijpen waarom end-to-end testing belangrijk is en hoe testtools kunnen helpen om dit proces te vergemakkelijken. Daarnaast moeten ze in staat zijn om een veilige en efficiënte deployment van een applicatie te begrijpen en in te richten. Het omvat zowel het testen van de applicatie als het implementeren ervan in een productieomgeving.

# UI en UX (C-6), weging: 16 %
```
De student kent de UI wetten en UX wetten die gebruikt kunnen worden bij het ontwerp van een frontend, herkent op welke manier een gegeven frontend wel of niet voldoet aan deze wetten, en kan deze wetten gebruiken om advies te geven over de gebruikersvriendelijkheid van een frontend.
```

Bron: [ChatGPT-Conversatie](https://chat.openai.com/share/e68adca0-97d8-423b-909f-9cec0f4937f9)

Dit tentamen-eis gaat over het begrip van UI (User Interface) en UX (User Experience) wetten in het ontwerp van een frontend (de visuele en interactieve kant van een softwaretoepassing, zoals een website of mobiele app). Laten we dit in meer detail uitleggen:

1. **UI-wetten en UX-wetten**: UI-wetten verwijzen naar de principes en regels die worden gebruikt bij het ontwerpen van de gebruikersinterface van een applicatie. Deze regels bepalen hoe elementen op het scherm worden georganiseerd, hoe interacties werken en hoe de gebruikersinterface eruitziet. UX-wetten verwijzen naar de principes die de algehele ervaring van de gebruiker beïnvloeden, inclusief factoren als gebruiksvriendelijkheid, toegankelijkheid, prestaties en algemene tevredenheid.

2. **Herkennen of een frontend voldoet aan deze wetten**: Om te beoordelen of een frontend aan deze wetten voldoet, moet een student in staat zijn om de frontend kritisch te bekijken en te analyseren. Dit kan inhouden dat ze controleren of de lay-out van de interface goed is gestructureerd, of de navigatie intuïtief is, of de kleuren en visuele elementen effectief worden gebruikt, enzovoort.

3. **Advies geven over de gebruikersvriendelijkheid**: Als een student deze wetten begrijpt en kan toepassen, kunnen ze advies geven over de gebruikersvriendelijkheid van een frontend. Dit betekent dat ze problemen kunnen identificeren en suggesties kunnen doen om de interface en ervaring te verbeteren. Bijvoorbeeld, als de tekst te klein is, kunnen ze aanbevelen om lettergroottes aan te passen voor betere leesbaarheid.

Het tentamen zal hoogstwaarschijnlijk verschillende aspecten van UI- en UX-ontwerp behandelen, zoals consistentie in het ontwerp, duidelijke navigatie, gebruiksvriendelijke interacties, enzovoort. De student moet deze wetten begrijpen en in staat zijn om ze toe te passen om te beoordelen hoe goed een frontend presteert en hoe deze kan worden verbeterd.

Mogelijk wordt de student ook gevraagd om concrete voorbeelden te geven van goede en slechte UI- en UX-ontwerppraktijken en om deze te relateren aan de wetten die ze hebben geleerd. Het begrijpen van deze principes is cruciaal voor het creëren van effectieve en gebruiksvriendelijke softwaretoepassingen.

