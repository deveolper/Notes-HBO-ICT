# API's = Application Programming Interface
Soms wordt hiermee een web API bedoeld.
API verbind het programming interface met de user interface.
## Voorbeelden
### Win32 API
### Fluent API
### Android API
### [Web API](https://www.apilist.fun/)
- Spotify
- Weerlive.nl
Etc.
## Use-cases
### Meerdere user-interfaces voor 1 back-end.
Als je meerdere UI's wil voor 1 back-end, dan kan je de back-end via een API aanroepen.
### Single Page Application (SPA)
Er wordt maar 1 keer HTML + CSS + JS verstuurd.
De rest van de HTTP-requests worden via JS gedaan: AJAX.
**AJAX call voorbeelden**
- Like knop
- Comments
- Autocompletion voor zoektermen
## ASP.NET Core
Een web framework. **.NET 6 is anders dan .NET 5**
- ASP.NET is een oude versie
```bash
dotnet new webapi
dotnet new webapi --framework dotnet7.0
```
Als je de conventies volgt hoef je heel weinig te configureren.
## Thread-safe
Concurrent uitvoeren is mogelijk zonder problemen.
## Services
## Middelware
### Routing
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
### Model binding
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
### Content negotiatoin
## REST API
Zowel de request als de response kunnen headers hebben. Status codes horen bij de response, de media types zitten in de header en gaan alleen van server naar client.
### Client Server
- Server is unaware of client
### Stateless
# HTTP Verbs
## GET
Opvragen van data.
## POST
Resource created or form submitted.
## PUT
Verander en valideer bestaand item.
## DELETE
Verwijderen van items.
## PATCH
## HEAD
Check of er een resource is.
## OPTIONS
Welk van de HTTP-verbs zijn geïmplementeerd.
# Endpoints / URL
Voorbeeld: 127.0.0.1:1576/myapi/books
127.0.0.1 is de host.
1576 is de poort.
De volledige URL is de endpoint.
# JSON
JavaScript Object Notation
**Voorbeeld**
```json
{
  "key": [1, 2, 3, 4, 5],
  "nog een key": {
    "hi": "een waarde",
    "test": "hallo"
  }
}
```

Ga experimenteren met PostMan en met ASP.NET etc. Kijk of je stuff werkend kan krijgen en alles begrijpt.