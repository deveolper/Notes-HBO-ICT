# Week 6 business process management

Modeleren van een bedrijfsproces is wat we gaan doen vandaag en
de komende 3 weken.

BPMN = Business Process Modelling and Notation

# Toets in week 9
Omvangt het maken van een BPMN

Vandaag: voorbeelden bekijken en of maken.

Doelen: BPMN kennen, relatie tussen processen en informatie
in de vorm van data-objecten en data-stores uitleggen.

## Week 6
- Event (start / end)
- Activity (task)
- Gateway (exclusifve / inclusive / parallel)
- Sequence flow

## Week 7
- Swimlanes
- Pool/lane
- Sequence flow

## Week 8
- Data object
- Data store
- Data association

# BPMN
Standaard taal om processente visualiseren. Vrijwel compleet universeel.

BPMN is een ISO-standaard.

BPMN is belangrijk voor het visualiseren van processen en verbeter-voorstellen.

# OMG
Object Management Group - beheerder standaarden BPMN.

# Gateways
Alle gateways (behalve parallel) worden voorafgegaan door een activiteit.

# Flow-objects
- Start Event (thin circle)
- End Event (thick circle)
- Activity (rounded square)
	- Werkwoord + zelfstandig naamwoord
- Exclusive Gateway (ruit with cross or without cross)
	- Er wordt 1 pad gekozen wat we doen
	- Of 2 paden worden gecombineerd.
	- Sluitende gateway is niet verplicht maar wel aanbevolen.
	- Exclusive gateways can have more than 2 paths.
- Inclusive Gateway (ruit with circle)
	- Er kunnen 1 of meerdere gekozen worden die parallel worden uitgevoerd.
- Parallel Gateway (ruit with plus)
	- Alles wordt uitgevoerd, moet gemerged worden met een parallele gateway.
Connecting objects:
	- Sequence flow (arrow)

# Event
Cirkel. Er is altijd een start-event en een end-event

# Token
Rondje wat aangeeft waar het proces op dat moment is.

# Q & A
## Oefening Pizzeria 1, haalt de pizza uit de oven na het erin plaatsen. Moet daartussen niet een wachttijd? En moet de oven niet nog worden geopend?
Eigenlijk wel, maar nu nog out of scope.
## Kan je meerdere end-events hebben?
Ja.
## Klopt het dat incl. gateways redundant zijn aan de andere 2 gateways?
Nee, maar volgens mij hebben ze mijn vraag niet begrepen.
