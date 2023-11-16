Let op! Bij deze aantekeningen zijn niet alle stukken code volledig uitgetypt (voornamelijk in de HTML wordt de `<html>` en `</html>` niet meegenomen).

# CSS
Als je fouten maakt, wordt dat vaak door de browser opgelost.
Met CSS is de content hetzelfde, maar de weergave is compleet anders. Geen style is ook een style.
HTML wordt grotendeels hetzelfde getoond op elke browser, maar er kunnen kleine verschillen zijn. Om dit te omzijlen moet je CSS aan de site toevoegen.

```css
h1 {
  color: blue;
  font-size: 12px;
}
```
`h1` selecteert alle `h1`-tags in de html

`.h1` selecteert alle tags met `class="h1"`

`#h1` selecteert alle tags met `id="h1"`

Er zijn 3 manieren om CSS toe te voegen:

- Inline

  ```html
  <p style="color: red;">Paragraaf</p>
  ```

- Internal

  ```html
  <head>
    <style>
      p {
        color: red;
      }
    </style>
  </head>
  ```

- External

  ```html
  <head>
    <link rel="stylesheet" href="styles.css">
  </head>
  ```

styles.css
```css
p {
  color: red; /* Alle p-tags worden rood */
}

#id {
  color: green; /* Alles met id=id wordt groen */
}

.class {
  color: blue;  /* Alles met class=class wordt blauw */
  font-size: 20px;  /* Alles met class=class heeft tekst van 20 pixels */
}
```

Inline is het meest specifiek. Als er meerdere styles gedefinieerd zijn voor een bepaald element, dan geldt de meest specifieke.

Een hashtag selecteert een ID, een punt een class en niks een element.

Als er CSS dubbel is (dus een stylesheet, inline en in een styles sectie in de html aanwezig zijn) dan neemt de meest specifieke prioriteit (inline eerst, sectie in de HTML en tot slot het externe stylesheet).

Het tweede deel van de opdracht is met CSS. Het is de opmaak van het web.

# Size eenheden
- `px`

  Aantal pixels.

- `rem`

  Een andere eenheid.

- `em`

  Weer een andere eenheid.

# Een aantal behandelde attributen
- `border-color`

  De kleur van de border.

- `color`

  De kleur van het attribuut of tekst.

- `font-family`

  Welk lettertype je gebruikt.

- `font-size`

  Het formaat van de tekst.

- `font-weight`

  Dikte van de letters.

- `background-image`

  De achtergrondafbeelding. Kan ook `url(linkje naar de afbeelding)` zijn.

- `repeat-x`

  Herhaal de kleur of afbeelding over de x-as.

- `repeat-y`

  Herhaal de kleur of afbeelding over de y-as.

# Div en span
Deze hebben andere default-gedragingen wat betreft `display: inline` en `display: block`

# CSS Standaard Box Model
- `margin`

  De ruimte om dit element heen.

  - `margin-left`

    Ruimte aan de linkerkant van het element.

  - `margin-right`

    Ruimte aan de rechterkant van het element.

  - `margin-top`

    Ruimte aan de bovenkant van het element.

    Vereist `display: block`.

  - `margin-bottom`

    Ruimte aan de onderkant van het element.

    Vereist `display: block`.

- `border`

  De dikte van de rand van het element.

- `padding`

  De ruimte tussen de rand en de content.

- `content`

  De content van het element.

- `flexbox`

  Makkelijke manier om de ruimte eerlijk te verdelen tussen de elementen.

# Adviezen van de docent
- Ga aan de slag met [SoloLearn](https://www.sololearn.com/) om een beetje CSS te leren.
- Leer ook de `flexbox`, die zit niet in [SoloLearn](https://www.sololearn.com/).

# Q & A
## Wat is het verschil tussen een class en een ID?
Je kan een HTML-element hebben met zowel een ID als een class-attribuut. Een element kan meerdere classes hebben, maar kan slechts één ID hebben. Een ID is alleen om het HTML-element uniek te maken, een ID komt in principe maar 1 keer voor.

## Wanneer gaan we met JavaScript aan de slag?
Volgende week.
