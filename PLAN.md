# Portfolio – plan

Statisk sajt i ren HTML och CSS byggd från Figma-filen
[portfolio](https://www.figma.com/design/xuukCGo7CJZ9VfT70u0AId/portfolio), sidan "ready design".
Sajten ska följa designen exakt i 1920 px (desktop) och 375 px (mobil) och skala mjukt däremellan.

## Vilka Figma-frames som gäller

| Sida | Desktop (1920) | Mobil (375) |
|---|---|---|
| Works – lista | `menu 2` (24:95) | `Frame 2` (93:91) |
| Works – öppet case | `menu 3` (93:145) | `Frame 14` (102:215) |
| About | `menu 4` (38:2) | `Frame 3` (93:105) |
| Contact | `menu 5` (78:424) | `Frame 13` (98:192) |

Startsidan (`start 1`, `start 2`) ingår inte än.

## Designvariabler (från Figma)

- Färger: bakgrund `#000000`, text `#ffffff`
- Typsnitt: Neue Haas Grotesk Display Pro
  - Meny: 65 Medium, 24 px, radhöjd 100 %, spärrning 4
  - Rubrik: 95 Black, 128 px, radhöjd 100 %, spärrning 3
  - Brödtext: 55 Roman, 24 px, radhöjd 100 %
- Grid: 12 kolumner, marginal 40 px, mellanrum 24 px
- Mobil: marginal 20 px

## Beslut

- **Bara HTML och CSS, inget JavaScript.** Ett case öppnas med HTML:s inbyggda
  `popover`. Bakgrunden och de andra verken blir suddiga med CSS (`filter: blur()` via `:has(:popover-open)`),
  medan menyn och rubriken förblir skarpa, som i `Frame 14`. Esc, pilen och klick utanför stänger caset.
  Man stannar kvar på Works-sidan.
- **`index.html` är Works** tills startsidan finns.
- **Platshållare:** grå rutor och lorem ipsum tills riktigt innehåll finns.
- **Responsivitet:** exakta Figma-mått vid 1920 och 375. Däremellan skalar storlekar med `clamp()`, och
  layouten växlar mellan mobil och desktop vid en brytpunkt (cirka 768 px). En egen 1440-design läggs till senare.
- **Hover/fokus på menyn:** diskret understrykning plus synlig fokusmarkering för tangentbord (finns inte i Figma).

## Filstruktur

```
portfolio/
├── index.html        Works (lista + case som popovers)
├── about.html
├── contact.html
├── css/
│   └── style.css     variabler, reset, header, sidor, brytpunkter
├── fonts/            Neue Haas Grotesk Display Pro (55, 65, 95)
└── img/              pilikon (exporterad från Figma)
```

## Steg

Varje steg avslutas med en commit, och du granskar innan vi går vidare.

- [x] **0. Plan och repo:** `git init`, `PLAN.md`, `.gitignore`.
- [x] **1. Grund och header:** filstruktur, `@font-face`, CSS-variabler, reset. Den gemensamma headern
      (meny, linje och sidrubrik) på alla tre sidor, desktop och mobil, med aktiv länk markerad.
- [x] **2. Works – lista:** fyra platshållare i sicksack (höger/vänster), 530×358 på desktop och 156×101 på mobil,
      med avstånd enligt Figma.
- [x] **3. Works – öppet case:** popover per verk med pil tillbaka, bild och text. Suddig bakgrund.
      Desktop enligt `menu 3`, mobil enligt `Frame 14`. Tangentbord och skärmläsare ska fungera.
- [ ] **4. About:** text i två stycken och en bild. Desktop: text till vänster och bild till höger. Mobil: bild ovanför text.
- [ ] **5. Contact:** två textstycken.
- [ ] **6. Responsivitet och kontroll:** testa mellanbredder, jämför varje sida med Figma vid 1920 och 375,
      kontrollera kontrast, fokus, `prefers-reduced-motion` och validera HTML.
- [ ] **Senare:** 1440-design, startsida, riktiga bilder och texter.

## Öppna punkter

- **Typsnitt:** `fonts/` är tom. CSS:en hittar Neue Haas Grotesk Display Pro om det är installerat lokalt, och annars används
  Helvetica Neue (Roman/Medium/Bold) som reserv. Webbfonter (woff2) behövs innan sajten publiceras.
  Mappen `portfolio:font/` (Macens HelveticaNeue.ttc) ignoreras av git.

## Avgjort

- Alla mobilsidor följer `Frame 2`: meny 16 px, rubrik 39 px med 20 px marginal. Aktiv länk i 95 Black på mobil, som i Figma.
  Desktop har ingen markering av aktiv länk, eftersom Figma inte har någon.
