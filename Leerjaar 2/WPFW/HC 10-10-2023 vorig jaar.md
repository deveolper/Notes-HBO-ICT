De volgende aantekeningen zijn dubbel maar gemaakt van een hoorcollege wat door Pascal gegeven is, mogelijk accuratere data dus :)

Klik [hier](https://web.microsoftstream.com/video/ba4bcd4d-0f8e-4230-bef3-c67b8497d8bb) voor het hoorcollege waar deze aantekeningen op gebaseerd zijn.

# API
Stel je zou een "is_admin" boolean in de request stoppen, dan zou een hacker deze kunnen manipuleren.

## REST API's
REST geeft ons handvatten om een API te maken.
- Alternatief: GraphQL
REST = REpresentational State Transfer.
REST is een architectural style, **geen protocol of standaard.**
Houd je netjes aan de HTTP-verbs:
### GET
Verzoek om data op te halen, cachable.
### PUT
Verzoek om data aan te passen.
### POST
Verzoek om nieuwe data te maken.
### DELETE
Verzoek om data te verwijderen.
### Stateless
De REST API heeft geen states, dus dezelfde request doet hetzelfde, ongeacht hoe vaak je het aanroept. Een state moet bij de client worden bijgehouden, niet bij de server.

### Rest architectural constraints
Splits de verantwoordelijkheden van de server en de client.
Zorg voor een uniform interface. Zorg dat alle end-points een vergelijkbaar interface gebruiken.
- Alle resources hebben een URI
- Manipulaties doe je met *representaties* (URI is voor dereferentie, niet voor de informatie).
- Alle nodige informatie moet in de request zitten.
- HATEOAS, maak linkjes volgbaar voor geautomatiseerde systemen, zodat alle resources ontdekbaar zijn.
Statelessness: geen states
Cacheability: het moet duidelijk zijn wat gecached kan worden
Layeredness: hierover komt een andere keer meer.
Code on demand, server kan javascript naar de client sturen om het gedrag van de client aan te kunnen passen.

## API Design
### API first
Hoe maak ik het zo nuttig mogelijk voor ontwikkelaars?
### Hoe regelen we authenticatie?
Niet ;)
### Hoe implementeren we sorteren/filteren/pagineren?
In de get-parameters is een veel voorkomende implementatie. `/studenten?sort=name&class=3b&page=2`
Errors in JSON? Kan.
Probeer niet te lange URL's te gebruiken. Dat is niet leesbaar.
## Authenticatie + Identificatie + Claims/roles
## OpenAPI / Swagger