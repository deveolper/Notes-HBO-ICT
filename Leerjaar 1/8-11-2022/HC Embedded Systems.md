# HC Embedded Systems
Eerste les Embedded Systems. Differentiatie van dit vak: NSE

Eerste slide was gewoon weer een samenvatting van de "regels" tijdens het
hoorcollege. Daarna ging hij zichzelf voorstellen. Dit is niet relevant voor
het tentamen.

Bij embedded systems knoop je alles aan elkaar. Dit is dus een software-hardware
combinatie.

## Wat is NSE
- Het programmeren van hardware.

Voor NSE moet je een low-level taal beheersen (bvb. C / C++)
Ook rekenen in verschillende talstelsels is belangrijk.

## Hoorcolleges, niet genoeg tijd om de practica op te sommen.
- Week 10: Stalstelsels + intro GPIO pinnen
- Week 11: Negatieve getallen
- Week 12: Poorten en logica
- Week 13: Deeltoets
- Week 14: Vervolg bitwise operators
- Week 15: GPIO functies
- Week 16: Inter-IC communicatie
- Week 17: Deeltoets

Uitgangspunt voor het HC: student heeft zich voorbereid.

Ga met de microbit klooien.

## Talstelsels
- Decimale: Normale talstelsel
- Binaire: Computer talstelsel
- Hexadecimale: Prettige representatie van binaire

1234 (decimal) is
```
1 * 10 ^ 3 +
2 * 10 ^ 2 +
3 * 10 ^ 1 +
4 * 10 ^ 0
```

1234 (hexadecimaal) is
```
1 * 16 ^ 3 +
2 * 16 ^ 2 +
3 * 16 ^ 1 +
4 * 16 ^ 0
```

Talstelsels kan je het beste leren door het gewoon te gebruiken.

### Decimal
- Prefix: Geen
- Suffix: Geen

### Binair
- Prefix: % of 0b
- Suffix: subscript "2", een kleine, lage 2.

### Hexadecimaal
- Prefix: 0x
- Suffix: subscript "16", kleine, lage 16.

%d = decimal format-string

%x = hex format-string

Prakticum is gebaseerd op de microbit.

Hierna was een aantal dingen die geen toetsstof waren. Die heb ik niet genoteerd.

GPIO = General Purpose Input Output

```ino
pinMode(pinnr, OUTPUT);	// Stelt de pin in als output.
digitalWrite(pinnr, HIGH); // Stuurt een 1 naar de pin.
```

Een pin kan ook een input zijn
```ino
pinMode(pinnr, INPUT);
bool waarde = digitalRead(pinnr);	// true als pinnr hoog is.
```

GND / Ground / Aarde = Negatieve pool

Als embedded systems engineer maak je NIET de hardware. Maar wel de code.

INPUT, INPUT_PULLUP, INPUT_PULLDOWN voor input-pinmode.
Alleen INPUT, is voor Arduino gedefinieerd. De anderen vereisen een microbit.

Voor analogRead is geen pinmode nodig. Dat doet Arduino zelf.

# Q & A
## Zijn deeltoetsen meerkeuze, open of allebei?
Meerkeuze (1 uur, incl. vragen over het practicum).
## Hoeveel wiskunde zit in NSE?
Vooral logica.
## Mogen we een rekenmachine gebruiken bij de toets?
Nee, geen rekenmachine toegestaan.
## Moet je op de toets de prefix schrijven? Of mag je ook de suffix gebruiken?
Binair mag met % op papier. 0b mag alleen in code.
## Gebruiken we Arduino IDE voor de microbit?
Ja.
