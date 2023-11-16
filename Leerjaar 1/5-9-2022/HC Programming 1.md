Kadir Kuru mail: k.kuru@hhs.nl

Werkcollege vrijdag Stepik 1.1 t/m 2.3
gedaan / geïnstalleerd.

Brightspace = Blackboard

# Slide 1
Titel: IN- & UITVOER EN VARIABELEN

Blackboard opdrachten uitgewerkt en voorkennis uit filmpjes.

# Slide 2
Titel: Karel J. van der Lelij

# Slide 3
Titel: Wat verwachten wij van jou?

## Verwerking en voorbereiding
- Filmpjes.

## Instructiecollege
### Verwerking en voorbereiding
- Documenten lezen.

## Werkcollege / Practicum
- Verwerking en voorbereiding.

# Slide 4
Titel: Richtlijnen online gedrag

# Slide 5
Titel: Online etiquette tijdens HC Programming 2

Gedraag je professioneel, zoals in een fysiek lokaal

Chat functioneel, geen onnodige berichten.

Taalgebruik netjes, zowel chat als mic.

Instructies, geef er gehoor aan.

Mic, mute tenzij de docent zegt m aan te zetten.

Webcam, uit tenzij de docent vraagt aan te zetten.

Privacy, Geen recording of screenshots zonder
toestemming. Geen gebruik voor ongepaste of
privédoeleinden.

# Slide 6
Titel: Wat mag je van mij verwachten?

- De docent zal er alles aan doen om je van ? naar ! te helpen.
- De docenten respecteert je, geef aan als je je ergens aan stoord.
- De docent zoekt actief naar jouw vragen.
- De docent zoekt naar mijn mening en probeert het onderwijs te verbeteren.

# Slide 7
Titel: Waar vind ik de info voor programming 1?

## Op brightspace
- Huisje
- Programming 1 HBO-ICT
- Content

Hier staat de info.

# Slide 8-17
Herhalingen.

# Slide 18
- Wooclap wordt gebruikt om te bepalen of de student het begrijpt.

# Slide 19
- Verwerk zelf de leerstof.

# Slide 20
## Week 1
Opstartweek

## Week 2
- Hoorcollege
	- Introductie
	- Main
	- Uitvoer
	- Variabelen
		- Declareren
		- Toekennen
	- Invoer
- Prakticum
	- Werken aan oefenopgaven

## Week 3
- Hoorcollege
	- Rekenen
	- String manipulatie
- Prakticum
	- Oefenopgaven

## Week 4
- Hoorcollege
	- IF
	- Logic operators
- Prakticum
	- Oefenopgaven

## Week 5
- Multiple choice test

## Week 6
### HC
- Methoden
	- Aanroepen
	- Parameters
### Prakticum
- Oefenopgaven

## Week 7
### HC
- While.
### Prakticum
- Oefenopgaven.

## Week 8
### HC
- Methoden
	- Return-type
### Prakticum
- Oefenopgaven

## Week 9
- Skilltest


# Slide 21
Titel: Wat is programmeren?

- Je communiceert met een computer om die te laten doen wat je wil
- Daar gebruik je een programmeertaal voor
- Zo een taal moet je leren
- Leren doe je vooral als je het zelf doet
	- Voorbeeld kijken
	- Meedoen met het voorbeeld
	- Nog een keer doen zonder voorbeeld
	- Vergelijkbare opdracht doen

# Slide 22
- Voorlopig maken we CLI apps

```java
System.out.println("Tekst");
System.out.println(88);
System.out.print(88);
System.out.println("Klaar");
```

Output
```
Tekst
88
88Klaar
```

# Slide 23
## Declaraties
```java
int getal;
String tekst;
getal = 88;
tekst = "Tekst";
System.out.println(getal);
System.out.println(tekst);
```

Single-quotes in JS voor chars. Deze werken hetzelfde als een C++ char.

# Slide 24
```java
import java.util.Scanner; // voor input-tekst

Scanner toetsenbord;
toetsenbord = new Scanner(System.in);

String tekst = toetsenbord.nextLine();
System.out.println(tekst);
```
