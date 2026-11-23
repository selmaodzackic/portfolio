# Portfolio – plan

Statisk sajt i ren HTML och CSS byggd från Figma-filen
[portfolio](https://www.figma.com/design/xuukCGo7CJZ9VfT70u0AId/portfolio), sidan "ready design".

## Version 2: ny design (1440)

Designen gjordes om i november 2026: vit bakgrund, Switzer och Gambarino, en meny som fälls ut och en startsida.
Den gamla svarta designen (1920 och 375) finns kvar i git-historiken (till och med commit `cdb41b4`).

### Vilka Figma-frames som gäller

| Sida | Fil | Frame (1440) |
|---|---|---|
| Startsida | `index.html` | `Landing Page` (118:191) |
| Meny öppen | alla sidor | `Menu pressed` (128:67), komponent `Navigation bar` (128:101) |
| Visual Archive | `works.html` | `Works` (131:286) |
| About | `about.html` | `About` (128:131) |
| Contact | `contact.html` | `Contact` (131:318) |

Mobil (375) ritas om i Figma först. Framesen `Frame 2`, `Frame 3`, `Frame 13` och `Frame 14` hör till den gamla designen.

### Designvariabler (från Figma)

- Färger: bakgrund `#ffffff`, text `#000000`, nedtryckt menyval `#626262`, grå sektion `#d9d9d9`,
  bakgrund bakom öppen meny 62 % svart.
- Switzer (sans): menyrad Bold 20, brödtext Bold 24, kontakt Regular 16, spärrning 4 %.
- Gambarino (serif): namn 120, sidrubriker 140, menyval 100, etiketter 16, spärrning 3 %.
- Radhöjd "normal" överallt, som i Figmas textlager.
- Marginal 40.

### Beslut

- **Bara HTML och CSS, inget JavaScript.** Menyn är en `popover` som öppnas med "Menu".
  Esc, klick utanför eller "Menu" igen stänger den. Pricken visar aktuell sida.
- **Skalning:** alla mått är Figma-pixlar gånger `--u` (1/1440 av fönsterbredden). Exakt vid 1440,
  proportionerligt större vid 1920 och mindre under 1440 tills mobildesignen finns.
- **Verken i Visual Archive går inte att klicka på** än. Ett öppet läge designas senare.
- **Menyraden:** "Live Happily!" länkar till startsidan och "Visual Archive 01" till Visual Archive.
- **Typsnitt:** woff2 från Fontshare (ITF Free Font License) i `fonts/`.
- **Startsidans bild:** exporterad från Figma med strukturen (crayon-effekten) inbakad, 2× för skarpa skärmar.
- **Placeholders:** grå rutor och lorem ipsum tills riktigt innehåll finns.

### Filstruktur

```
portfolio/
├── index.html        Startsida
├── works.html        Visual Archive
├── about.html
├── contact.html
├── css/style.css     variabler, reset, menyrad, meny, sidor
├── fonts/            Switzer (400, 600, 700), Gambarino (400)
└── img/              landing.jpg, dot.svg, arrow-down.svg
```

### Steg

- [x] Typsnitt och bilder från Fontshare och Figma.
- [x] Grund, menyrad och meny (popover).
- [x] Startsida.
- [x] Visual Archive.
- [x] About: vit introduktion med pil ner till den grå sektionen.
- [x] Contact.
- [ ] Mobil, när den nya 375-designen finns i Figma.
- [ ] Öppet läge för verken i Visual Archive.
- [ ] Riktiga bilder och texter, LinkedIn-länk.

### Avgjort

- Menyraden ligger överst (y 0) på alla sidor. I `Landing Page` och `Menu pressed` ligger allt 4 px lägre,
  vilket inte följts så att menyraden står still mellan sidorna.
- `Works`-framen saknar menyrad i Figma. Den läggs ändå på alla sidor eftersom menyn bara nås därifrån.
- Avstånden mellan verken i Visual Archive är olika (88, 75, 77) och följer Figma.

### Kontroll

- Alla fyra sidor och menyn uppmätta mot Figma vid 1440: placering och storlek stämmer inom 0,5 px.
- Ingen horisontell scroll vid 1440 och 1920.
- Tangentbord: skip-länk, menyrad, "Menu" öppnar menyn, Tab går in i menyn, Esc stänger.
- Kontrast svart på vitt 21:1. Fokusmarkering 2 px svart.

## Version 1: svart design (1920/375), ersatt

Steg 0–6 gjordes klart i november 2026 (commits `a92dfe7` till `cdb41b4`).
