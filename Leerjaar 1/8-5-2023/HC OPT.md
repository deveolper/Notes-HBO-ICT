# Modified Decision/Condition Coverage
Voor elke variabele zorg je ervoor dat als die ene variabele wijzigd, de uitkomst wijzigd.

# Randwaarden
Je test de waardes die op de grens liggen.

# Pairwise Testing
Reduceert het aantal testcases zonder de kwaliteit te compromiteren. Voor elke collectie van 2 condities wordt elke combinatie een keer getest.

# Equivilantie Classes Testen
Beweringen die waar of onwaar kunnen zijn die kan je met al die testtechnieken testen. Niet alle beweringen zijn booleans.

## Voorbeeld
Onder de 18: minderjarig, korting

18 - 65: volwassen, volle prijs

65+: gepensioneerd, gratis

19 jaar en 45 jaar zijn eigenlijk gelijkwaardig, je kan pairwise testing gebruiken om het aantal cases te reduceren terwijl je de kwaliteit waarborgt.

Je geeft dus een range van waardes of een collectie waardes. Deze klasse moet EXACT de definitie zijn waarvoor de conditie geldt.

# Fysieke testcase
Testcase met exacte waardes. Dus niet de equivilantie classes, maar de concrete waardes die het zouden kunnen zijn. Deze zou je rechtstreeks in code kunnen implementeren.

## Voorbeeld
- Henk is 19 jaar, en mag dus alcohol kopen
- Piet is 17 jaar, en mag dus geen alcohol kopen

# Logische testcase
Testcase waarin gespecifieerd wordt wat belangrijk is aan de test.

## Voorbeeld
- Iemand wie minstens 18 jaar is, mag alcohol kopen.
- Iemand wie minderjarig is, mag geen alcohol kopen.

# Deadlines
Zie brightspace.
