Nog een keer ARRAYS.

Nu kopieren we een array (for real), niet de pointer naar de array.
Ook gaan we het hebben over string-vergelijking hebben.

Na de vakantie hebben we een open-vragen toets. Sterkte @everyone!

Vandaag komt een video van 1 uur beschikbaar waarin een samenvatting van ALLE stof gegeven wordt.

Verschil in lengte-berekening tussen string en array:
```java
String tekst = "test";
int[] items = {1, 2, 3};
int aantal_tekens = tekst.length();	// Method call, result = 4
int aantal_items = items.length;	// Attribute access, result = 3
System.out.println(tekst.substring(0, 2));	// Print: "te"
String tekst1 = "12345";
String tekst2 = "13425";
int vergelijking = tekst1.compareTo(tekst2);
System.out.println(vergelijking);	// Resultaat: -1
int [] kopie = andere_array;	// kopie verwijst naar dezelfde array, NIET een copy.

/*
 * Deze code hieronder maakt wel een kopie
 */
int [] kopie = new int[array.length];
for (int i = 0; i < array.length; i++) {
	kopie[i] = array[i];
}
```

Wat moet je weten voor te toets:
```java
tekst.length()	// Telt het aantal tekens in een string
```
Strings kan je vergelijken met `compareTo` en `compareToIgnoreCase`
substring kan je gebruiken om een deel van de string te krijgen, deze methode kan bij counting matches worden gebruikt
Je moet copying an array, minimum value in array, en maximum value in array herkennen en zelf programmeren
En alles wat we eerder hebben behandeld uiteraard!
Zie Brightspace voor meer informatie over het tentamen.

Vragen? Stel ze! Ik ben bereikbaar (waarschijnlijk)!
Vakantie? Toch stellen! Ik houd Discord nog steeds in de gaten!
Nacht? Gewoon stellen! Ik antwoord wel wanneer ik wakker ben!