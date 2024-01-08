# Voorwoord
Dit is een voorbereidende "les" binnen The Disabled Defenders (TDD). Deze les was niet voor iedereen toegankelijk en was ook niet ver van tevoren aangekondigd. De informatie is gefiltert op basis van wat we binnen TDD hebben besproken dat er wel of niet in mocht blijven.

# Disclaimer
Ga uiteraard nooit blind uit van de informatie die ik verstrek, maar in dit geval is de stof in kwestie door een student gegeven, en niet door een docent. Deze informatie is foutgevoeliger dan normaal.

# UI en UX Laws
## Zichtbaarheid van de status van het system
Ik denk dat dit betekent dat je bent ingelogd en op welke stap je bent bij een bepaald proces.
## Match tussen systeem en werkelijkheid
Het systeem moet begrijpbaar zijn voor de gebruiker, dus met dezelfde termen spreken als de gebruiker. Eenvoudig taalgebruik, geen taalgebruik wat alleen ICT'ers snappen.
## Vrijheid en controle voor de gebruiker
Altijd een nooduitgang (undo-knop) bieden.
## Consistentie en standaarden
Wat hetzelfde betekent moet er hetzelfde uitzien. Standaarden binnnen UI opvolgen.
## Voorkomen van fouten
Dingen die snel tot fouten leiden moet je voorkomen, dus ipv een rode knop en een blauwe knop waarvan de rode een delete knop is, maak je de delete knop minder prominent. Als er iets is wat de gebruiker misschien niet wil doen (zoals onomkeerbare dingen) minder zichtbaar maken (zoals alleen de tekst zichtbaar maken, en niet de rest van de knop). De minder gevaarlijke knop maak je groot en duidelijk (dus met een duidelijke knop, en niet alleen een tekst).
## Beter herkennen dan herinneren
Dus beter een lettertype-selectie maken die de naam van het lettertype schrijft in het lettertype in kwestie.
## Flexibel en efficient in gebruik
Zorg dat de applicatie efficient te gebruiken is, ook voor onervaren gebruikers.
## Estehtisch en minimalistisch ontwerp
Zorg dat alles alleen de informatie bevat die relevant is voor de gebruiker. Dus geen afleidende kleuren, en geen informatie die niet relevant is voor de gebruiker.
## Help gebruikers bij fouten
Dus geef duidelijk aan wat er niet goed is.
## Hulpfunctie en documentatie
Zorg dat er extra hulp op de site beschikbaar is (zoals een chat).

# Laws
## Hicks Law
Hoe meer dingen je kan kiezen, hoe meer tijd het kost om het te doen.
## Jacobs Law
Probeer het design vergelijkbaar te maken met andere sites, zodat het bekend voorkomt voor de gebruiker.
## Miller's Law
Probeer stuff op te splitsen op een manier dat de gebruiker niet teveel tegelijk hoeft te onthouden of verwerken. `(440) 867-5309` en niet `4408675309`.
## Peak-End Rule
Een ervaring is grotendeels gebaseerd op het beste moment, en het eindresultaat.
### Hoe pas je dit toe?
Als de header prachtig is, maar de onderzoekspagina niet. Dan onthoud je die header.
## Von Restorff Effect
Wat het meest afwijkt uit een lijst vergelijkbare opties, die blijft het beste bij.
## Prinicpal of Closure
Als we naar een complexe groep visuele dingen kijken, dan zoeken we vaak naar een enkel herkenbaar patroon en dan vult ons brein in wat we op de missende plekken verwachten.
### Voorbeeld experiment
In de playstore zie je bovenin een groot blok met een app erin. Rechts van het grote blok, zie je een klein stukje van een item ernaast, dus heb je in de gaten dat je daarheen kan scrollen.

# React
- **Node** om javascript zonder browser te draaien.
- **NPM** is de Node package manager.
- Package.json beschrijft scripts en meer.

    - Dependencies
    - Dev dependencies
    - En meer.

- React hook

    - Use-state: Je houd een staat bij. Eigenlijk een variabele die je behoud zo lang als de applicatie draait.
    - Use-effect: Een soort event handler volgens mij.

# Meer React
De browser krijgt bundle.css en bundle.js worden opgehaald. Je kan ook de website kan ook de server benaderen via een controller (via API), die gebruikt models en haalt data uit de database.

In React hebben we arrow functions:
```js
const myArrowFunction = () => {
    Console.Log("Hi");
    return 5;
}
```

Het is verleidelijk dit een lambda expressie te noemen omdat dat in andere talen wel de term is (en het identiek werkt aan lambda expressies). Maar de naam is in JavaScript een arrow-functie.

## UseEffect
In principe een event listener, maar het kan ook een functie zijn die maar 1 keer wordt uitgevoerd (zoals wanneer de pagina geladen is).

Als een state wordt aangepast, dan kan je ook een use-effect uitvoeren. Dit is eigenlijk een soort van een event listener.

## UseState
Een UseState wordt gebruikt om de staat van de applicatie bij te houden.

# Architectuur
## MVC
### Model
De data.
### View
De UI. Aka. Wat je kan zien.
### Controller
API-logica (of de logica die de view met de model verbind).

## Layers
Dat bepaalde modules (in laag 1) alleen afhankelijk zijn van modules in laag 1. Dat modules in laag 2 alleen afhankelijk zijn van laag 1 en 2, etc.

## Microservices
Verschillende delen zijn heel erg van elkaar gescheiden, wat de schalbaarheid te goeden doet.

Dus verschillende functies draaien op beschillende servers met mogelijk zelfs verschillende databases. Deze zijn zo goed van elkaar gescheiden dat je enkele services kan opschalen zonder de rest op te hoeven schalen.

## Monoliths
Een enkele codebase (en enkele server, en enkele database) met alle functionaliteiten.

# Q & A
## Hoe verschillen de verschillende frameworks van elkaar?
| Functie | Vue.js | React | Angular |
|---|---|---|---|
| **Type** | UI-bibliotheek | Framework | Framework |
| **Populariteit** | Steeds populairder | Zeer populair | Populair |
| **Leercurve** | Gemiddeld | Gemiddeld | Steil |
| **Component-gebaseerd** | Ja | Ja | Ja |
| **Virtual DOM** | Nee | Ja | Nee |
| **TypeScript** | Nee | Nee | Ja |
| **Enterprise-geschikt** | Nee | Ja | Ja |

# Afkortingen
## DOM
Document Object Model

[Slides](https://brightspace.hhs.nl//content/enforced/56633-H-SE-S3WPFW-23_2023_VT/HC19.pdf?ou=56633)

[Ninja](https://www.youtube.com/watch?v=j942wKiXFu8&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d)

# Belangrijke links
[Ninja - Functions as props](https://www.youtube.com/watch?v=CWEOYFzgOJs&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=13)

[Ninja - useEffect hook](https://www.youtube.com/watch?v=gv9ugDJ1ynU&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=14)

[Ninja - useEffect dependencies](https://www.youtube.com/watch?v=jQc_bTFZ5_I&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=15)

[Ninja - custom hook](https://www.youtube.com/watch?v=Jl4q2cccwf0&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=20)

[W3Schools - useCallback](https://www.w3schools.com/react/react_usecallback.asp)

[BrightSpace - Slides](https://brightspace.hhs.nl//content/enforced/56633-H-SE-S3WPFW-23_2023_VT/HC201.pdf?ou=56633)

[BrightSpace - Meer Slides](https://brightspace.hhs.nl//content/enforced/56633-H-SE-S3WPFW-23_2023_VT/HC22.pdf?ou=56633)

# Extra informatie
Will's aambeien zijn niet meer weg te krijgen, en dat is prima. Zij mogen er zijn en worden geaccepteerd door de community.
