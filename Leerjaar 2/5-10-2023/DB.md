# Specialisatie, klassendiagrammen, etc.
Specialisaties en unaire associaties moeten we kennen. Dit zit in een klassendiagram.
Een entiteit is iets wat bestaat. Hele vage beschrijving, maar als je kan beargumenteren dat het bestaat, dan is het een entiteit.
- Een mens
- Een database
- Een wolk
- Een gedachte

Een relationeel representatiemodel (RRM) moeten we ook kennen (zie oudere aantekeningen).

Associatie zit alleen in een UML, niet in een RRM.
Relatie zit in RRM, niet in UML.

Een Associatie heeft altijd multipliciteiten.
Rolnaam is alleen verplicht bij een unaire associatie (associatie op de class zelf).

# Klassediagram opstellen uit een tekst cheatsheet
- Zelfstandige naamwoorden zijn vaak entiteiten of attributen
- Bepaal of een zn een klasse of attribuut of irrelevant is
- Werkwoorden zijn vaak associaties, stel vast welke werkwoorden associaties zijn en welke irrelevant zijn
- Teken het klassediagram

# Oefenopdracht
Zelfstandige naamwoorden: student(naam, studentnummer, geboortedatum, SLB'er), ~~Gegeven~~, docent(naam, faculteit), ~~periode~~, cijfer, blokken, toetsdatum, ~~systeem~~, ~~gemiddelde~~

Student(naam, studentnummer, geboortedatum, SLB'er)
Docent(naam, faculteit)
Toets(toetsdatum, blok, cijfer)

Werkwoorden: ~~dienen~~, ~~ingevoerd~~, ~~worden~~, ~~inschrijven~~, krijgt toegewezen, ~~moet~~, ~~zijn~~, ~~werkt~~, ~~moeten~~, ~~ingevoerd~~, ~~worden~~, ~~rekent uit~~

Student *krijgt toegewezen* Docent
Student *krijgt cijfer* Toets

# Specialisatie / generalisatie
OOP talen kunnen makelijk specialisaties en generalisaties implementeren. In klassendiagrammen kan het ook makkelijk, maar in SQL is het best moeilijk, maar dat zien we volgende week.
Als je van de Mens class naar de Student class gaat, dan zie je specialisatie. Student is een specialisatie van Mens. Als je van Student naar Mens gaat, dan zie je generalisatie.

# Datatypen
Deze moet je **niet** aangeven in een database-klassendiagram.

# Multipliciteiten
Alleen deze 4 symbolen (en combinaties) gebruik je voor de multipliciteiten {0, 1, .., *}.

# Een associatie bestaat uit maximaal 3 verschillende onderdelen
## Multipliciteit
Verplicht
## Associatie-beschrijving
Verplicht tenzij je een associatie-klasse hebt, dan is die **niet** toegestaan.
De associatie-beschrijving moet grammaticaal correcte zin van.
De docent is wel bereid om zelf uit te zoeken welke kant die op moet lezen.
## Rolnamen
Deze zijn verplicht bij unaire associatie, maar niet bij niet-unaire associaties. Het mag wel.
