Opdracht staat op Brightspace.

Morgen is een gastcollege.

Casus: KLM, per klas werken we aan de casus. Dit is om te ervaren hoe het in de praktijk werkt.

Ook wordt er binnenkort een gastcollege over git conflicten gegeven.

20 juni presenteren we ons product aan 42, de docenten en onze medestudenten. Zondag ervoor moet het ingeleverd zijn.

# Code Smells
Er staat een cheatsheet op BrightSpace. Deze is nu compleet. Deze kunnen we raadplegen tijdens het maken van de opdrachten.

## Large Class (13.2.1.3)
- Symptoom: Class met meer dan 1 verantwoordelijkheid
- Oplossing: Extract class

## Long Parameter List (13.2.1.3)
- Symptoom: Methode neemt veel argumenten mee
- Oplossing: Verplaats waardes naar binnen de functie
- Oplossing: Gebruik een data-class
- Oplossing: Preserve whole object (geef het hele object mee, in plaats van dat je de waardes uit een object leest en die los meegeeft)

## Primitive Obsession (14.1.1.3)
- Symptoom: Veel variabelen gebruikt die eigenlijk samen een class zouden moeten zijn
- Oplossing: Verplaats de variabelen naar een data-class

## Switch-Statement (14.1.1.3)
- Symptoom: Veel switch-cases en if-else waar je eigenlijk een nieuwe class moet maken
- Oplossing: Splits de methode (gebruik polymorphism)

## Duplicate code (14.2.1.3)
- Symptoom: Meerdere code-blokken zijn hetzelfde (zelfs al is het alleen maar een variabele)
- Oplossingen:
  - Pull Up Field: Verplaats naar super-class
  - Pull Up Constructor Body: Verplaats vergelijkbare constructor naar super-class
  - Substitute algorithm: Vervang vergelijkbare code voor een slimmer algoritme
  - Consolidate Conditional Expression: Verplaats de voorwaarde naar een methode
  - Consolidate dupplicate conditional fragments: verplaats dubbele code in if-else naar buiten de if-else

## Long method (15.1.1.3)
- Symptoom: Methode is lang
- Oplossingen:
  - Vervang deel van de code voor methode aanroep
  - Vervang een query met een tijdelijke variabele
  - Neem het hele object mee
  - Verplaats ingewikkelde code naar een eigen class
  - Vervang code in if-else met methode aanroep
  - Lange conditional naar een methode verplaatsen

## Temporary field opgeruimd
- Een waarde die je alleen maar gebruikt voor 1 methode
- Oplossing:
  - Replace method with method object (extract class)

## Shotgun Surgery
- Een wijziging in 1 class vereist een hoop wijzigingen in andere classes.
- Koppeling tussen de classes is te hoog, je hebt de classes te ver uit elkaar getrokken.
### Oplossingen
- Move method: verplaats de methode naar waar die het meest wordt aangeroepen
- Move field: verplaats variabele naar waar die het meest wordt aangeroepen
- Inline class: maak extract class ongedaan

# Extra begrippen
## Koppeling
De classes zijn te afhankelijk van elkaar
## Cohesie
De classes hangen goed samen
## Extract subclass
Maak een subclass waar je de afwijkingen van de originele class implementeert
## Extract superclass
Maak een superclass waar de dubbele code naartoe gaat

Vanaag moeten we de conceptversie van de code (code smells eruit) inleveren. Zondag de definitieve versie.