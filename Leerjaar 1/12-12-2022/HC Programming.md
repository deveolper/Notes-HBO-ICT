We gaan het wederom over arrays hebben (en een beetje over objecten).

Volgende week gaan we het hebben over complexere array algoritmen.
De week er na is een OPEN VRAGEN TENTAMEN.

Eerst een herhaling van de array.

```java
int [] trein  = new int [5];	// Maakt array van 5 integers

for (int wagon = 0; wagin < trein.length; wagon++) {
	trein[wagon] = 10 * (wagon + 1);
}

// trein is nu {10, 20, 30, 40, 50};
// De lengte is 5
// De hoogste index is 4
// De laagste index is 0
// Op index 3 staat de waarde 40
```

Bij een functie-aanroep wordt een array als parameter niet gekopiëerd.
Hierin is een array dus speciaal.

Een instantie van een zelf-gemaakte class wordt ook niet gekopiëerd.

Geen tentamenstof: van een file inlezen
```java
import java.io.File;
import java.io.IOException;

public class Main {
	public static void main(String[] args) throws IOException {
		File file = new File("resources\\in.txt");
		Scanner in = new Scanner(file);
		System.out.println(in.nextLine());
	}
}
```

Je moet ook de common-array algoritmes (de veelvoorkomende array-algoritmes) moet je kunnen herkennen:
- find first match
- average
- counting matches
- Finding the First match
- Finding the Last match

Je moet ook begrijpen hoe arrays, objecten en strings worden opgeslagen in het
geheugen.

# Q & A
## Gegevens die je mee geeft aan een methode worden toch sws gekopieerd?
Arrays zijn de uitzondering.
## Als je een array aanmaakt, zet je dan tussen de blokhaken een 10, voor 10 items? Of een 9 voor 10 items genummerd 0 t/m 9?
Een 10, voor 10 items genummerd 0 t/m 9.
## Wat doet die value: values?
`for (double item : items) {...};` gaat langs elementen uit de array items.
## Wat is een common array algoritme?
Een veelvoorkomend algoritme wat je gebruikt op arrays.
## Kan je een array nog langer maken?
Nee, dan moet je de array kopieren naar een langere array.
## Wat doet een try en een catch?
Die handelt fouten af.
```java
public class Main {
	public static void main(String[] args) {
		try {
			throw new Exception("Oops");
		} catch (Exception e) {
			System.out.println("An exception occured!");
			System.out.println("Fuckit, let's continue");
		}
		System.out.println("Exception succesfully ignored!");
	}
}
```
## Kan je `return a, b;` doen in Java?
Nee, kan wel in een array of met dynamic typing.
