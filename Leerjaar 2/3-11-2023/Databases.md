# Databases
## Logisch ontwerp
Vorig jaar bij databases hebben we het over relationeel implementatiemodel gehad wat voortkwam uit het relationeel representatiemodel.

Voor elk van de tabellen in je releationele representatiemodel moet je een `CREATE TABLE` uitvoeren om deze aan te maken.

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

## Manipulation
### CREATE
```sql
CREATE DATABASE naam;
CREATE TABLE tabelnaam (
    -- Zie eerder deel van de aantekeningen voor meer details over create table  
);
```

### SELECT
```sql
-- Zie eerdere aantekeningen van databases voor meer informatie hierover.
```

### UPDATE
```sql
UPDATE tabelnaam
SET kolom = waarde
WHERE conditie;
```
Dit zet de `kolom` gelijk aan de waarde voor alle rijen in `tabelnaam` die voldoen aan de `conditie`.

```sql
UPDATE tabel
SET kolom = (SELECT waarde FROM anderetabel WHERE conditie)
WHERE nogeenconditie;
```

Je kan bijna altijd een subselect gebruiken. Als je de update op alle rijen wil toepassen, dan gebruik je geen `WHERE`.

Eerst wordt er een nieuwe tabel gemaakt zoals bij `DELETE` die bijhoud wat er moet worden verwijderd. En een tabel zoals bij `INSERT` die bijhoud wat er moet worden ingevoegd. Deze informatie is nuttig bij `triggers`.

### DELETE
```sql
DELETE FROM tabelnaam
WHERE conditie;
```
Verwijderd alle regels uit `tabelnaam` die aan `conditie` voldoen.
Als je alle rijen wil verwijderen, dan gebruik je geen `WHERE`.

Eerst wordt er een tabel gemaakt waarin alle data wordt opgebouwd die moet blijven, daarna wordt deze toegevoegd in de database.

### INSERT
**Soft-coded / SELECT-statement**
```sql
INSERT INTO tabelnaam SELECT * FROM anderetabel;
INSERT INTO tabelnaam (kolomnaam1, kolomnaam2) SELECT * FROM anderetabel;
```
De data die er in moet wordt opgehaald.

Eerst wordt er een nieuwe tabel gemaakt met alle rijen die moeten worden ingevoegd, daarna (wanneer deze klaar is) wordt die eindelijk ingevoegd.

**Hard-coded**
```sql
INSERT INTO tabelnaam (kolomnaam1) VALUES ('value1');
INSERT INTO tabelnaam (kolomnaam2) VALUES ('value2');
INSERT INTO tabelnaam (kolomnaam1, kolomnaam2) VALUES ('value1', 'value2');
```
De namen van de kolommen zijn hard-coded in het `INSERT`-statement.

### Constraints
Extra regels die je aan de database oplegt die de invoerbare informatie limiteert, dit is om foutieve informatie tegen te houden.

**Attribuutniveau**

Je hoeft maar naar 1 attribuut te kijken om te weten of het aan de constraint voldoet.

**Tupelniveau**

Je moet naar meerdere attributen kijken die in dezelfde rij zitten.

**Tabelniveau**

Je moet naar meerdere rijen in de tabel kijken.

**Databaseniveau**

Je moet naar meerdere tabellen kijken om deze constraint te checken. Een voorbeeld hiervan is een vreemde sleutel.

**Datawarehouseniveau**

Pas relevant in semester 4, als je naar meerdere databases moet kijken.

Advies: lees de slides terug omdat daar belangrijke informatie in staat.

Van attribuutniveau tot databaseniveau komen bijna gegarandeerd op de toets.

# DECLARE
```sql
DECLARE @variabele INT;  -- int variabele;

@variabele = SELECT num FROM person WHERE username = 'Henk';    -- variabele = Henk.num;
```
Dit maakt een variabele aan van het type `INT`.

# IF
```sql
IF (<boolean>) BEGIN
    <statements>
END
```
`BEGIN` is eigenlijk de open-accolade van SQL, en `END` is de sluit-accolade van SQL.

# RAISE ERROR
```sql
RAISERROR ("Verkeerde data", 16, 1);
```
16 is in dit geval de ernst van de fout en 1 is de status van de fout.

Ook dit statement kan je combineren met een `SELECT`.

# Wat niet op de slides staat
In SQL kan je ook een print-statement gebruiken.

```sql
PRINT("Hello, World!");
```

# Trigger
Een procedure die in gang wordt gezet bij een aanpassing in de database. Er zijn 3 soorten.

## Update trigger
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

## Insert trigger
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

## Delete trigger
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

## Trigger voor meerder events
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

# Stored Procedures
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

# Indexen
Performance optimalisatie. Kost wel meer opslag.

## Clustered index
Als je index is geoptimaliseerd voor zoeken op primaire sleutels.
Deze veranderd de data door deze te sorteren.

```sql
CREATE CLUSTERED INDEX id
ON tabelnaam(kolom1, kolom2);
```

Versnelt select op `kolom1` en `kolom2`.

## Non-clustered index
Als je index is geoptimaliseerd voor zoeken op een andere kolom.
Deze veranderd niet de originele data.

```sql
CREATE NONCLUSTERED INDEX naam
ON tabelnaam(kolom1, kolom2);
```

# Security
## Authenticatie
Wie de fuck bent u? *Anders dan de definitie van SIE, die luid 'hoe de fuck bewijst u henk te zijn?'*

## Authorisatie
Mag u deze fucking actie ondernemen?

## Rechten toekennen
```sql
GRANT SELECT, INSERT, UPDATE, DELETE ON tabel TO Henk;
```

## Rechten ontnemen
```sql
REVOKE SELECT ON tabel FROM Henk;
```

# Q & A
## Hoe identificeer je en constraint?
Als er een extra alinea staat onder alle ander relaties (de vreemde sleutels).
## Moet je speciale notaties gebruiken voor constraints?
Nee, je hoeft niet de constaints op een bepaalde manier te noteren. Je moet wel bij je RRM (Relationeel RepresentatieModel) constraints moeten wel overeenkomen met je RIM (Relationeel ImplementatieModel).
## Zijn er ook anders constraint-expressies dan CHECK?
Nee, CHECK met een boolean is de manier.
## Kunnen die deleted en inserted uit meerdere rijen bestaan?
Ja, maar voor deze week mag je er vanuit gaan dat het altijd maar 1 rij is.
## Zijn de checks ook een soort van triggers?
Ja, zo zou je dat kunnen zien.
## Doen EXEC en EXECUTE hetzelfde?
Ja.
