# Applicatielaag

We gaan het hebben over de protocollen (afspraken) die tussen de applicatie en het netwerk zitten.

## Protocollen op Applicatielaag
- TELNET, SSH
- HTTP(S)
- FTP (SFTP, FTPS)
- Email (SMTP etc.)

Veel protocollen gebruiken het client-server model.

Veel meer TCP op de applicatielaag dan UDP wegens betrouwbaarheid.

Veel applicatielaag-protocollen zijn tekst-georiënteerd. Dus veel Ascii tekst in
requests en responses.

## TELNET
- Maakt werken vanaf een remote terminal mogelijk (de CLI).
- Volledig tekst-georiënteerd.
- "Luistert" op poort 23.
- Verouderd (geen encryptie, geen authenticatie).

## SSH
- Secure Shell
- "Luistert" op poort 22
- Doet precies hetzelfde als TELNET, maar dan beveiligd:
	- Encryptie
	- Authenticatie van verbinding
	- Wijzigingen worden gedetecteerd

## HTTP
- Hyper Text Transfer Protocol
- Pagina's bestaan uit meerdere objecten
- Servers luisteren naar meerder poorten
- HTTP is vervangen door HTTPS (secure)

# Hoe het request eruit ziet
- HEADER
	```
	<methode: get|post|put|head|delete> <URL> <versie><cr><lf>
	<naam headerveld> <waarde><cr><lf>
	<naam headerveld> <waarde><cr><lf>
	...
	<naam headerveld> <waarde><cr><lf>
	<cr><lf>
	<data / payload / body>

	<cr> = Carriage return
	<lf> = Linefeed
	```

	De header bevat de host, het soort request, wat voor browser, natuurlijke taal etc.
- URL
	```
	protocol://host(:port)/dir/file?argnaam=waarde&anderarg=anderewaarde
	```

	Voorbeeld:
	```
	https://1.2.3.4:80/map/bestand.html?query=value+of+argument&safesearch=yes
	```
	
	**LET OP:** deze host opzoeken kan een bluescreen triggeren!

	file://C:/Windows/System32/wininit.exe

	Maar ook dat is een host.

# Response
```
<versie> <status> <statusbericht> <cr> <lf>
<naam headerveld> <waarde> <cr> <lf>
...
<cr><lf>
<data / payload / body>
```

## Status
- 200 OK
- 301 Moved Permanently
- 302 Moved Temporarly
- 404 Not Found
- 500 Internal Server Error

Er zijn er meer, deze kun je online vinden.

Nummer is strict gedefinieerd en het bericht kan veranderen.

## HTTP versies
- HTTP 1.0

	Apparte verbinding per object. Zeer traag.

- HTTP 1.1

	1 verbinding mag meerdere objecten opvragen. Sneller (slechts 1 TCP verbindin openen). In praktijk vaak toch meerdere verbindingen.

- HTTP 2.0

	Parallele verbindingen en ongevraagd doorsturen van objecten (voor de request)

- HTTP 3.0

	HTTP over UDP ipv TCP

	Sneller, maar foutgevoeliger.

## Cookies
- Om de webserver op de hoogte te stellen van wat de client heeft gedaan.
- Een cookie geef je mee met de request, zodat de server de bezoekers uit elkaar kan houden.
- In de HTTP-header worden cookies meegestuurd.
- Cookies bestaan uit keys en values. bvb: session-id: 12345
- Browser bewaart het cookie. De volgende keer dat je de site bezoekt wordt het cookie meegestuurd zodat de server je herkent.
- De cookies hebben unieke waardes.

### Session cookies
Verdwijnen na het sluiten van een tabblad.

### Persistent cookies
Blijven bewaard.

Cookies worden vaak ook gebruikt voor advertentie-doeleinden.
Vanwegen privacy moet je cookies accepteren.

## HTTPS
- Gebruikt poort 443
- Beveiligd

### TLS
- Een tussenlaag met cryptografische bescherming.
- Maakt vervalsen en afluisteren is moeilijker.
- Ook de afzender wordt gecontroleerd.
- Moderne versie: TLS
- Oude versie: SSL
- TLS zit in HTTPS

## File transfer
- Het managen van bestanden.
- Dit is het lezen, schrijven en deleten van bestanden en het bladeren door mappen.

### FTP
- File Transfer Protocol
- Niet veilig en geen authenticatie.

### SFTP / FTPS
- Secure File Transfer Protocol
- File Transfer Protocol Secure
- SFTP: SSH FTP
- FTPS: TLS FTP

Beide secure varianten gebruiken encryptie en authenticatie HTTP en HTTPS kunnen ook files transferen.

## Email
### SMTP
- Verzenden van mail.

### POP of IMAP
- Ontvangen van mail
- EWS: Verzenden en ontvangen van Microsoft mail.

Waarom is dat zo?
	Je weet niet zeker of de ontvanger online is.
	Dus moet je de mail zenden naar de server.
	De ontvanger moet ook kunnen ontvangen als de zender offline is.

	SMTP wordt gebruikt om van client naar server of van server naar server
	bij het zenden.

	IMAP wordt gebruikt om mail op te halen.

	Veilige email gaat over TLS/SSL voor de beveiliging.

## DNS
- Domain name system
- Applicatieprotocol
- Werkt meestal op UDP
- Beschreven in RFC 920 en latere standaarden
- DNS info is NIET centraal opgeslagen.
- Eindsystemen vragen aan de lokale nameservers. De lokale nameservers gaan dan onderzoek doen wat het IP adres is.
- De root-servers die weten niet waar het is, maar die geeft een betere indicatie waar er moet worden gezocht.
- Deze server doet een betere gok. En zo gaat het door tot er een exact IP-adres is gevonden.
- DNS heeft ook DNSSEC = veilige versie van DNS. Geen encryptie, wel integriteit.
- ICANN is de baas voor het domeinnaam-beheer.

Applicaties waarbij je met peers communiceert, kan een peer-to-peer systeem worden
gebruikt.

P2P-filesharing is vaak sneller dan van de server downloaden.
Bij de server moet de snelheid worden verdeeld over de clients. Bij P2P moet je meer
stukken downloaden en dus ook traager als er meer clients zijn.

P2P kunnen ook een DDOS uitvoeren door computers te infecteren.
Ook illegale content worden gedeeld.
Lastig offline te halen.

# Q & A
## Komen bij de poortnummers bij de applicatielaag kijken?
Ja.
## Welke HTTP statuscodes moeten we onthouden?
200 en 404.
## Wat is het verschil tussen GET en POST?
Met GET vraag je informatie op. Met POST stuur je informatie naar de server.
## Wat is een RFC?
Een standaard.
## Wat is het verschil tussen SSL en TLS?
SSL is de verourderde versie van TLS.
## Wat is er veroudered aan SSL? Het wordt namelijk nog steeds gebruikt.
SSL wordt eigenlijk niet meer gebruikt, maar TLS wordt vaak SSL genoemd.
## Sla je de DNS over als je rechtstreeks een IP-adres opzoekt?
Ja.
## Hoe kan ik een botnet opzetten?
Gaan we niet op in.
