We gaan het hebben over classes en objecten.

Volgende week wat herhaling met wat nieuwe dingen gemixt.

File I/O en het gebruik van objecten wordt behandeld.

```java
File bestand = new File("path/to/file.txt");
Scanner bestandLeer = new Scanner(bestand);
String regel = bestandLezer.nextLine();
```

De class is de definitie, een object is iets wat die definitie
volgt.

```java
public class Student { // Student is een class
  // Implementatie voor deze aantekening niet relevant
}

Student Anita = new Student(); // Anita is een object
Student Dominik = new Student(); // Dominik is een object
Student Laurens = new Student(); // Laurens is een object
Student Noah = new Student(); // Noah is een object
Student Tim = new Student(); // Tim is een object
Student William = new Student(); // William is een object
```

Bij het uitvoeren van een methode in een non-static methode, dan
is die ook non-static.

# Q & A
## Bij de eerste vraag in WooClap is het bestand nooit afgesloten toch? En de regel die is gelezen is niet in gebruikt genomen in de code. Wat was het punt van het lezen van dat bestand dan eigenlijk?
Waarschijnlijk niet relevant voor dit HC
## Wat als je dit doet? \<code> Krijg je dan een fout of wordt het bestand aangemaakt?
```java
File bestand = new File("file/does/not/exist.txt");
```
Dan krijg je een fout.
