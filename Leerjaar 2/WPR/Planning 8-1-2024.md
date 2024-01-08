# Deze week
Laatste week van de implementatie. Na het project gaan we de applicatie aan stichting accessibility laten zien. Op de 15e gaan we langs bij stichting accessibility, daar krijgen we mogelijk een extra punt voor.

# Assessment
Er komt een assessment, maar de tussentijdse beoordelingen wegen ook mee. Het assessment is dus niet allesbepalend voor ons cijfer. 15 januari.

# Deze ochtend
Bekijk elkaars producten en help elkaar.

## Tot 11:00
Vakantie en planning bespreken en product klaarzetten.

# Stuff waar andere groepjes tegenaanlopen en of waar ze mee kunnen helpen
## Authentication
Daar lopen meerdere groepjes tegenaan, maar Noah's groep heeft het en is bereid te helpen. Het groepje van Joren heeft de backend van de authenticatie al werkend en gaan vandaag de rest daarvan doen.

## Invoervalidatie
Het groepje van Noah is door de mand gevallen met onvoldoende invoervalidatie. Dat zullen wij ook mee moeten nemen in ons ontwikkelproces.

## Accessibility
Het groepje van Noah heeft daar nog minimaal mee gewerkt, maar wel een klein beetje. Ze hebben wel dingen getest met onder andere screenreaders. We kunnen hun terecht voor eventuele hulp.

## Chat
Het groepje van Jorrit kan hulp gebruiken bij de chat. De chat is geen prioriteit. Chat is nice to have, maar is niet noodzakelijk. Je krijgt geen 5 aftrekpunten als je het niet hebt.
Laurens kan eventueel helpen met een ChatGPT-clone erachter te zetten, maar alleen als daar tijd voor is.

## Azure
Het groepje van Calvin kan waarschijnlijk helpen met Azure, ze hebben een cloud-native application.

# Activiteit
Bowlen (door de docent georganiseerd en door school betaald). 18 Januari in de middag, niet verplicht.

# Kees deelt **iets**
## Firefox Developer Edition
Firefox developer edition geeft de optie om de tabbing volgorde tonen. Dat is mogelijk handig.
## React webtools
React webtools is ook aan te raden om te installeren.

# Feedback met Joren
## DTO
Klein deel van een Model, alles wat naar de client gaat staat in de DTO. Voor beveiliging wil je een DTO met zo min mogelijk info gebruiken. Een DTO gebruik je ook om minder informatie mee te hoeven geven (zoals alleen de identificeerende informatie). Dingen zoals de relaties eruit yeeten bij een DTO. De relaties moeten niet required zijn, anders zijn ze vereist bij het aanmaken van het bedrijf. Ook is het een goed idee de endpoints in het swagger UI te testen en ook met `curl` in de command-line.
### Automapper
Googlen. Gaat van een DTO naar een model en van een model naar een DTO zolang de naam hetzelfde is. Het kan ook handmatig.
## Database
Handige [informatie voor de database](https://www.youtube.com/watch?v=_8nLSsK5NDo&list=PL82C6-O4XrHdiS10BLh23x71ve9mQCln0).
### Koppelen
We moeten een database koppelen. Zo snel mogelijk regelen en seeden met dummy-data.
### Samenvoegen
Alle contexten in 1 context yeeten.
## Overig
### Primary keys
Alle modellen een ID wat niet op zichtzelf data is.
