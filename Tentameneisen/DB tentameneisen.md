**Documentversie: 19-nov-2023 19:23**

**Author: Laurens Frensen (22106189)**

Zoals gebruikelijk heb ik de eisen uit de [toetsmatrijs](https://brightspace.hhs.nl/content/enforced/56629-H-SE-S3DB-1-21_2023_VT/2022_Toetsmatrijs%20Database%20Design,%20Creation%20&%20Querying%20H-SE-S3DB1.pdf?_&d2lSessionVal=HPZJgrZ8drwWTG4RLuiWgVzDK&_&d2lSessionVal=1l7lCejcc959JfvwGzu7gei40&_&d2lSessionVal=F28iS5pjAXh0FDW6UtW68v2ia&_&d2lSessionVal=T2uQzlePfqkicsYPNALrDGTJx) gehaald.

Deze keer staan de tentameneisen van beide deeltoetsen in 1 matrix, dus som ik deze ook gezamelijk op.

Uit de matrix was het mij in veel gevallen niet duidelijk tot op welk niveau we een bepaalde eis moeten kennen, ik hoop dat Jelle daar binnenkort meer licht op kan schijnen.

# Niveaus
Niveau 1: Kennen

Niveau 2: Begrijpen

Niveau 3: Toepassen

# Student gebruikt tijdens een digitale toets SQL Server om (middels complexe query’s) een database te bevragen (weging: 50 %)

Niveau: 2, maar in de matrix staan 100 punten voor niveau 3.

MISSING, volgens mij is deze eis alleen voor deeltoets 1. Bovendien is dit best wel een uitgebreid punt. Het lijkt erop dat je hiervoor alle SQL moet kennen die door SQL Server wordt ondersteund.

# Student implementeert RIM met Triggers, Procedures, Constraints en maakt keuzes voor Security maatregelen en indexen (weging: 12.5 %)

Niveau: 2, maar in de matrix staan 25 punten voor niveau 3.

## RIM
Bron: Notes > 3-11-2023 > Databases

RIM = Relationeel ImplementatieModel.

Eigenlijk is het gewoon de SQL die je tabellen aanmaakt.

```sql
CREATE TABLE tabelnaam (
    kolomnaam1 INT,         -- Getal van arbitraire afmetingen
    kolomnaam2 CHAR(10),    -- String van precies 10 tekens
    kolomnaam3 VARCHAR(10), -- String van maximaal 10 tekens
    PRIMARY KEY(kolomnaam1) -- De onderstreepte kolom in je RRM, GEEN KOMMA HIER ACHTER ZETTEN, anders kost het veel debugging tijd. Soms werkt het wel, maar soms ook niet.
);

CREATE TABLE nogeentabel (
    kolomnaam1 INT,         -- Getal van arbitraire afmetingen
    kolomnaam2 CHAR(10),    -- String van precies 10 tekens
    kolomnaam3 VARCHAR(10), -- String van maximaal 10 tekens
    PRIMARY KEY(kolomnaam1),
    CHECK(kolomnaam2 IN ('1234567890', '0987654321'))   -- Attribuut-constraint
);

CREATE TABLE weereentabel (
    kolom1 INT,
    kolom2 INT NOT NULL,    -- Kan op een rare plek in je RRM staan
    kolom3 INT,

    PRIMARY KEY (kolom1),
    FOREIGN KEY (kolom2) REFERENCES nogeentabel(kolomnaam1) ON UPDATE NO ACTION ON DELETE SET NULL,
    FOREIGN KEY (kolom3) REFERENCES nogeentabel(kolomnaam1) ON UPDATE NO ACTION ON DELETE CASCADE
);
```

- `NO ACTION`

    Je krijgt een `error` als deze constaint faalt.

- `CASCADE`

    - `ON DELETE`

        Deze record wordt gewoon verwijderd. Deze is best gevaarlijk, want dit kan een hoop extra rijen verwijderen in een keer.

    - `ON UPDATE`

        Deze record wordt meegewijzigd.

- `SET NULL`

    Als het referenced item aanpast of verwijderd, wordt deze waarde `NULL`.


### Triggers
Bron: Notes > 3-11-2023 > Databases

Een procedure die in gang wordt gezet bij een aanpassing in de database. Er zijn 3 soorten.

**Update trigger**
```sql
CREATE TRIGGER triggernaam
ON tabelnaam
BEFORE UPDATE
FOR EACH ROW
BEGIN
    -- Code die voor een update wordt uitvoerd
END;

CREATE TRIGGER triggernaam
ON tabelnaam
AFTER UPDATE
FOR EACH ROW
BEGIN
    -- Code die na een update wordt uitvoerd
END;
```

**Insert trigger**
```sql
CREATE TRIGGER triggernaam
ON tabelnaam
BEFORE INSERT
FOR EACH ROW
BEGIN
    SELECT * FROM inserted;
    -- `inserted` is de magische tabel die tijdelijk wordt aangemaakt voordat de insert gedaan wordt.
    -- Code die voor een insert wordt uitvoerd
END;

CREATE TRIGGER triggernaam
AFTER INSERT
ON tabelnaam
FOR EACH ROW
BEGIN
    -- Code die na een insert wordt uitvoerd
END;
```

**Delete trigger**
```sql
CREATE TRIGGER triggernaam
ON tabelnaam
BEFORE DELETE
FOR EACH ROW
BEGIN
    SELECT * FROM deleted;
    -- `deleted` is de magische tabel die tijdelijk wordt aangemaakt voordat de delete gedaan wordt.
    -- Code die voor een delete wordt uitvoerd
END;

CREATE TRIGGER triggernaam
AFTER DELETE
ON tabelnaam
FOR EACH ROW
BEGIN
    -- `deleted` is de magische tabel die tijdelijk heeft bijgehouden wat er verwijderd is.
    -- Code die na een insert wordt uitvoerd
END;
```

**Trigger voor meerder events**
```sql
CREATE TRIGGER triggernaam
ON tabelnaam
BEFORE INSERT, UPDATE, DELETE
FOR EACH ROW
BEGIN
    -- Code die voor een insert, update of delete wordt uitvoerd
END;

CREATE TRIGGER triggernaam
AFTER INSERT, UPDATE
ON tabelnaam
AS
BEGIN
    -- Code die na een insert of update wordt uitvoerd, andere syntaxis
    IF (conditie) BEGIN
        RAISERROR("Oops", 16, 1);   -- Geef een error
        ROLLBACK TRANSACTION;   -- Maak de transactie ongedaan, zo een trigger zorgt voor een impliciete BEGIN TRANSACTION voor de actie en een COMMIT aan het einde, dus je kan ook een ROLLBACK TRANSACTION gebruiken.
        RETURN;     -- Einde van de trigger
    END;
END;

CREATE TRIGGER triggernaam
ON tabelnaam
INSTEAD OF INSERT
AS
BEGIN
    -- Bij een insert wordt dit gedaan in plaats van de insert, je moet je insert handmatig doen.
END;

CREATE TRIGGER triggernaam
ON tabelnaam
INSTEAD OF UPDATE, INSERT
AS
BEGIN
    -- Code
END;
```

### Procedures
**Stored Procedures**
Opgeslagen procedures, een functie of methode in een database.

```sql
CREATE PROCEDURE func
@woonplaats char(15)
AS
BEGIN
INSERT INTO lid (woonplaats) VALUES (@woonplaats);
END;

CREATE PROCEDURE getter
-- missing

EXEC func @woonplaats = 'Den Haag';
EXECUTE func @woonplaats = 'Rijswijk';

EXECUTE getter @woonplaats =;
```

### Constraints
Bron: Leerjaar 2 > 12-10-2023 > Databases

>Locomotief(<ins>lcode</ins>, aanschafprijs, aanschafdatum, aantalpk, soort)
>
>Wagon(<ins>wcode</ins>, aanschafprijs, aanschafdatum, aantal_zitplaatsen)
>
>Wagon_Rit(<ins>*wcode*</ins>, <ins>*ritnummer*</ins>)
>
>>wcode is vreemde sleutel naar wagon(wcode), not null
>>
>>ritnummer is vreemde sleutel naar rit(ritnummer), not null
>
>Personeel(<ins>pcode</ins>, naam, adres, type, datum_laatste_keuring, *koppel_met*)
>>koppel_met is vreemde sleutel naar Personeel(pcode)
>>
>>Constraint type in {Machinist, Conducteur}
>>
>>Als type = Machinist, datum_laatste_keuring is not null, koppel_met is null
>>
>>Als type = Conducteur, datum_laatste_keuring is null, koppel_met is not null
>
>Rit(<ins>ritnummer</ins>, datum, vertrektijd, aankomsttijd, *machinst*, *locomotief*)
>>locomotief is vreemde sleutel naar locomotief(lcode), not null
>>
>>machinist is vreemde sleutel naar personeel(pcode), not null
>>
>>Constraint pcode = machinist(mnr)

# Student tekent tijdens een schriftelijke toets een UML class diagram (als ontwerp van een database) op basis van een scenario (weging: 12 %)

Niveau: 2, maar in de matrix staan 24 punten voor niveau 3.

Dit is moeilijk in markdown uit te leggen, eigenlijk heb je echt afbeeldingen nodig.

# Student past tijdens een schriftelijke toets de normalisatiestappen toe om een ongestructureerd gegevensbestand in 3NF te zetten (weging: 12 %)

Niveau: 2, maar in de matrix staan 24 punten voor niveau 3.

Bron: Leerjaar 2 > 26-10-2023 > DB

## Normalisatie tot 0NF
1. Onderstreep de unieke sleutel
2. Verwijder afgeleide gegevens
3. Verwijder constante waardes
4. Markeer repeating-groups door deze tussen accolades te zetten

Accolades zie je alleen in 0NF.

### Voorbeeld

Klant (<ins>klantnr</ins>, klantnaam, {<ins>ordernr</ins>, datum}, {<ins>artikelnr</ins>, omschrijving, prijs, aantal})

## Normalisatie tot 1NF
1. Normaliseer tot 0NF
2. Verplaats repeating-groups naar een nieuwe tabel
3. Zorg dat er geen multi-value attributen meer in zitten

### Voorbeeld

Klant (<ins>klantnr, *ordernr*</ins>, klantnaam)

Order (<ins>ordernr</ins>, datum)

Artikel (<ins>artikelnr</ins>, omschrijving, prijs, aantal)

## Normalisatie tot 2NF
1. Normaliseer tot 1NF
2. Maak alle attributen functioneel afhankelijk van de volledige sleutel

    1. Bepaal de functionele afhankelijkheden van primaire sleutel (kijk hierbij wat afhankelijk is van welk deel van de sleutel en wat afhankelijk is van de volledige sleutel)
    2. Pak iets waar een hoop functioneel afhankelijk van is als primaire sleutel en voeg alle data die daar functioneel afhankelijk van is in een aparte tabel.

### Voorbeeld
Klant (<ins>klantnr, ordernr</ins>, klantnaam)

Order (<ins>ordernr</ins>, datum)

Order_Artikel(<ins>*ordernr*, *artikelnr*</ins>, aantal)

Artikel (<ins>artikelnr</ins>, omschrijving, prijs)

## Normalisatie tot 3NF
1. Normalisser tot 2NF
2. Verplaats alle attributen die volledig afhankelijk zijn van een niet-sleutel attribuut naar een eigen tabel (en maak een relatie tussen de tabellen)

### Voorbeeld
Klant (<ins>klantnr</ins>, klantnaam)

Klant_Order (<ins>*klantnr*, *ordernr*</ins>)

Order (<ins>ordernr</ins>, datum)

Order_Artikel(<ins>*ordernr*, *artikelnr*</ins>, aantal)

Artikel (<ins>artikelnr</ins>, omschrijving, prijs)

# Student stelt tijdens een schriftelijke toets het rationele model van een database samen op basis van een UML class diagram (weging: 7,5 %)

Niveau: 2, maar in de matrix staan 15 punten voor niveau 3.

Bron: Leerjaar 2 > 26-10-2023 > DB

Ik ga er even vanuit dat ze met "relationele model" een relationeel *representatie*model (RRM) bedoelen en niet een relationeel *implementatie*model.

## Voorbeeld van een RRM
Uitgever (<ins>uitgevernr</ins>, uitgever_naam, uitgever_adres, uitgever_plaats)

Boek (<ins>ISBN</ins>, titel, *uitgevernr*)

# Student verduidelijkt tijdens schriftelijke toets keuzes t.b.v. Transactiemanagement op basis van een scenario (weging: 6 %)

Niveau: 2, 12 punten voor niveau 2.

Bron: Leerjaar 2 > 10-11-2023 > Databases

## Transactiemanagement
```sql
START TRANSACTION;

-- meer SQL hiero.

COMMIT;
```

### Transactie
```sql
UPDATE Rekeninghouder
SET saldo = saldo + 10000
WHERE naam = "H. Bavinck";

UPDATE Rekeninghouder
SET saldo = saldo - 10000;
WHERE naam = "H.G. Sol";
```

Stel, het systeem crasht tussen de tweede de twee queries. Dan komt er 10000 uit de droge lucht. Dit is waar transactions voor dienen.

```sql
BEGIN TRANSACTION; -- START TRANSACTION kan ook

UPDATE Rekeninghouder
SET saldo = saldo + 10000
WHERE naam = "H. Bavinck";

UPDATE Rekeninghouder
SET saldo = saldo - 10000;
WHERE naam = "H.G. Sol";

COMMIT;
```

Deze statements worden nu allemaal wel, of allemaal niet worden uitgevoerd. Als het systeem nu crasht tussen de twee queries, dan wordt er niks gedaan.

### Commit
- Keyword wat het einde van de transactie aanduid.
- Maakt de transactie definitief.
- Maakt de wijzigingen voor anderen zichtbaar.
- Heft locks op.
- Als van uno-redo logging gebruikt wordt gemaakt: start nog niet het schrijven naar de fysieke database (dat is pas na een checkpoint).
- Schrijft een commit-record naar de transaction log.
- Schrijft de log naar de disk.

### Rollback
Maak de transactie ongedaan. Het kan zijn dat je tijdens de transactie erachter komt dat de data niet meer integer is, dan kan je rollback gebruiken om alle veranderingen ongedaan te maken.

```sql
ROLLBACK;
```

### Kwaliteitseisen (ACID)
- Atomic

Alles wordt uitgevoerd, of alles wordt niet uitgevoerd.

- Consistent

Na afloop voldoet de database weer aan alle integriteitsconstraints.

- Isolated

Andere transacties hebben er geen invloed op.

- Durable

Eenmaal uitgevoerd blijft het van kracht en wordt niet ongedaan gemaakt.

### Auto Commit Transactie
Na elke SQL-instructie wordt een commit uitgevoerd.

### Implicit Transactie
Na elke transactie ben je verplicht alle acties in een transactie te doen.

### Explicit Transactie
Maakt het mogelijk meerdere SQL-instrcuties met `BEGIN TRANSACTION`, `COMMIT` en `ROLLBACK` in 1 transactie te stoppen.

Je kan deze soorten transacties aan en uit zetten, kijk de slides terug als je daar meer over wil weten (geen toetsstof).

`@@error` (global variabele, dubbele @ is global, enkele @ is een local) is gelijk aan 0 als er *geen* error optreed.

`RETURN` we stappen uit de transactie.

Deze code checkt of er een error heeft plaatsgevonden, als dat zo is maakt die de transactie ongedaan.
```sql
IF @@error <> 0
BEGIN
    ROLLBACK;
    RETURN;
END
COMMIT;
```

Contraint-violation afvangen: `TRIGGER`, niet met `@@error`. `@@error` checkt alleen systeem-errors, geen contraint-violations.