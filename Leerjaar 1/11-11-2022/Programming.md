# Aantekeningen
```java
System.out.printf(String format, arguments...)
```
Print een string op basis van het format en de waardes.

`arguments...` kan worden vervangen voor elk willekeurig aantal argumenten.

Deze functie kan ik het beste uitleggen door middel van een paar voorbeelden:

## Code
```java
System.out.printf("Getal: %d kan op scherm worden gezet", 1234);
```
## Output
```
Getal: 1234 kan op scherm worden gezet
```
## Uitleg
In de string "Getal: %d kan op scherm worden gezet" wordt %d vervangen voor 1234. Wat de string "Getal: 1234 kan op scherm worden gezet" creëert. Deze wordt op scherm gezet.
## Code
```java
System.out.printf("Getal: %8d kan op scherm worden gezet", 1234);
```
## Output
```
Getal:     1234 kan op scherm worden gezet
```
## Uitleg
In de string "Getal: %8d kan op scherm worden gezet" wordt %8d vervangen voor 8 tekens (vandaar de 8). De d geeft aan dat het om een getal gaat. 1234 is maar 4 tekens lang. Dus worden er spaties vóór gezet tot de lengte 8 tekens betreft. "    1234" wordt dus op de plaats van %8d gezet. "Getal:     1234 kan op scherm worden gezet" wordt dus op scherm gezet.
## Code
```java
System.out.printf("Nu een kommagetal %.2f tonen", 123.456789);
```
## Output
```
Nu een kommagetal 123.46 tonen
```
## Uitleg
`%.2f` zegt dat het kommagetal op 2 decimalen moet worden afgerond. Dus `123.456789` word afgerond op 2 decimalen. Om af te ronden op 2 decimalen kijk je alleen naar de eerste 3 decimalen. Dus we ronden 123.456 af op 2 decimalen. Als het laatste getal 5 of hoger is, wat het geval is `(6 >= 5)`. Dan ronden we af omhoog. `123.46` is dus het resultaat van de afronding. En dat is dus wat in de string wordt toegevoegd.
## Code
```java
System.out.printf("Tekst %s", "dit is een tekst");
```
## Output
```
Tekst dit is een tekst
```
## Uitleg
In de format-string wordt %s vervangen voor letterlijke tekst.
## Code
```java
System.out.printf("Wat als we %10s gebruiken?", "tekst");
```
## Output
```
Wat als we      tekst gebruiken?
```
## Uitleg
%10s geeft aan dat het een string betreft van 10 tekens lang. "tekst" is maar 5 tekens lang, dus voegen we spaties toe aan de linker kant tot de lengte 10 betreft.
## Code
```java
System.out.printf("Wat als we %-10s links willen uitlijnen?", "tekst");
```
## Output
```
Wat als we tekst links      willen uitlijnen?
```
## Uitleg
%-10s geeft aan dat de tekst precies 10 karakters lang is, en het minteken geeft aan dat het links-uitgelijnt moet zijn.
## Code
```java
System.out.printf("Kommagetal: %8.2f", 12345.6789);
```
## Output
```
Kommagetal: 12345.68
```
## Uitleg
De 8 geeft aan dat de totale lengte 8 tekens betreft (incl. komma). De .2f geeft aan dat het maximaal 2 getallen achter de komma mogen zijn. De eerste 8 tekens van het getal zijn 12345.67. Maar omdat er na de 7 een 8 komt en 8 groter dan of gelijk is aan 5 moet het naar boven worden afgerond. Dus wordt de 7 een 8. En dus komt 12345.68 op scherm te staan.
## Code
```java
System.out.printf("Getal %5.3f", 1234.56789);
```
## Output
```
Getal 1234.568
```
## Uitleg
Wacht? Wat? De totale lengte zou 5 moeten zijn toch? Niet 8? De 5 voegt alleen spaties toe indien het getal te kort is. Het kapt het getal niet af. 1234.56789 wordt dus afgerond op 3 decimalen en wordt dus 1234.568, wat op scherm wordt getoont.
