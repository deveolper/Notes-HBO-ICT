# Cheatsheet
## Problemen
### Het lukt niet om iets aan te passen
Als de applicatie draait, dan weigert Visual Studio hier iets van aan te passen.

## Routes toevoegen
React routes moet je niet vergeten om de controller importeren. Anders krijg je een error.

## Project ophalen vanuit git en opstarten
Alle onderstaande commands dienen uitgevoerd te worden in een git bash, niet in de normale CMD. De normale CMD werkt mogelijk wel, maar dat heb ik niet getest.

### Clone de repository
```bash
git clone https://github.com/williamvdm/tdd.git
```

### Ga naar de map
```bash
cd tdd
```

### Locale master up-to-date maken met remote master
```bash
git pull
```

### Branch up-to-date maken met master
```bash
git pull origin master
```

# Commands
## Google auth package installeren
```bash
npm install react-oauth/google
npm install @react-oauth/google@latest
```

# Structuur van de applicatie
## Program.cs
Dit is het entry point van de backend. `Program::Main()` is het eerste wat gebeurd in de applicatie.

## WeatherForecast.cs
Voor de weersvoorspellingen. De API afhandeling vind hier plaats.
