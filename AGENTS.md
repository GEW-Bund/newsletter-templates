# AGENTS.md — Newsletter-Templates für CleverReach

Dieses Repository enthält die GEW-Newsletter-Templates für den Import in [CleverReach](https://www.cleverreach.de).
Die Templates werden mit [bootstrap-email](https://github.com/bootstrap-email/bootstrap-email) v1.5.1 kompiliert.

## Repo-Struktur

```
├── sources/          # Bootstrap-Quelldateien (uncompiled, zum Bearbeiten)
│   └── bootstrap-email.scss  # Globale SCSS-Overrides (Farben, Fonts)
├── compiled/         # Kompilierte Outputs (direkt in CleverReach importierbar)
├── legacy/           # Archivierte alte Templates (2022/2023)
├── AGENTS.md         # Diese Datei
├── README.md         # Allgemeine Doku
├── compiled.zip      # Archiv aller kompilierten Templates
└── .gitignore        # .sass-cache/, *.bak
```

## Bootstrap-Email Kompilierung

```bash
cd sources/
for file in *bootstrap*.html; do
  bootstrap-email "$file" > "../compiled/${file/-bootstrap/}"
done
```

**Wichtig:** `bootstrap-email.scss` muss im Arbeitsverzeichnis liegen.

## Kritische Regeln (beim Bearbeiten/Erstellen von Templates)

### Kein `<title>`-Tag
CleverReach setzt den `<title>` beim Versand automatisch (aus dem Betreff). Ein `<title>` im Template darf **nicht** vorhanden sein.

### Keine CSS Custom Properties
`var(--gew-red)` funktioniert nicht → immer direkte Hex-Werte (`#e3001f`).

### Button-Styling: Inline Styles
CSS-Klassen für Buttons werden überschrieben. Immer inline styles verwenden:
```html
<a href="url" style="display: inline-block; padding: 12px 32px; background-color: #e3001f; color: #ffffff; ...">Text</a>
```

### Zentrierung: Table-Trick
`text-align: center` in divs wird ignoriert. Inhalte in Tables packen:
```html
<div class="card-body" style="text-align: center;">
  <table style="margin: 0 auto;">
    <tr><td style="text-align: center;">Inhalt</td></tr>
  </table>
</div>
```

### CleverReach Image-Alignment
Der `align=` Parameter überschreibt CSS:
```html
<!--#image align="left" #--><img ... /><!--#/image#-->    <!-- linksbündig -->
<!--#image align="center" #--><img ... /><!--#/image#-->  <!-- zentriert -->
```

### CleverReach-Syntax (muss erhalten bleiben)
```html
<!--#loop#--> ... <!--#/loop#-->
<!--#loopitem name="Element Name"#--> ... <!--#/loopitem#-->
<!--#html mode="default/textonly" inline="true"#--> ... <!--#/html#-->
<!--#image align="center" #--> ... <!--#/image#-->
<!--#onlineversion#--> ... <!--#/onlineversion#-->
<!--#unsubscribe#--> ... <!--#/unsubscribe#-->
<!--#spacer size="50px"#-->
```

## GEW-Design-Standards

### Farben
- **GEW-Rot:** `#e3001f` (Links, H3, Buttons, HR-Linien)
- **GEW-Lila:** `#482289` / `#6f42c1` (TARIFTELEGRAMM)
- **Call-to-Action-Hintergrund:** `#fce5e5` (helles Rosa) / `#f3e8ff` (TARIFTELEGRAMM)
- **News-Cards:** `#f1f3f4` (neutrales Grau)

### Typografie
- **Font:** `Calibri, "Segoe UI", Arial, sans-serif`
- **H1:** Light (300), `#343a40`
- **H2:** Bold (700), `#343a40` (außer TARIFTELEGRAMM: `#e3001f`)
- **H3:** Bold (700), `#e3001f` (außer TARIFTELEGRAMM: `#6f42c1`)
- **Text:** Normal (400), `#343a40`

### Cards
- **Border-radius:** 16px
- **Standard-Card:** Weiß mit `1px solid #f1f3f4`
- **News-Cards (card-news):** `background-color: #f1f3f4`
- **Call-to-Action (bg-gray):** `#fce5e5` (Standard) oder `#f3e8ff` (Tariftelegramm)

### Logo-Platzierung
- Im Footer-Bereich, zwischen Social Media und Impressum
- Max-width: 250px, zentriert mit Table-Trick
- Padding: 2rem

### Social Media Icons
- Instagram, Facebook, Bluesky, YouTube (kein Twitter/X mehr)
- Bluesky-URL: `https://bsky.app/profile/gew.de`
- Icon-Größe: 48px (Klasse `w-12`)

## Template-Typen und ihre Besonderheiten

| Template | Zweck | Farb-Schema | Besonderheiten |
|----------|-------|-------------|----------------|
| CALLTOACTION | Einfache Kampagnen-Mail | GEW-Rot | Spotlight-Card, Titelbild mit Button |
| EINFACH | Standard-Newsletter | GEW-Rot | News mit Bild, Pressemitteilungen |
| KOMPLEX | Erweiterter Newsletter | GEW-Rot | Mehr Elemente, 2-Spalten-Layout |
| SHOP | Shop-Artikel | GEW-Rot | Kompakte Cards, Preisangabe |
| TARIFTELEGRAMM | Tarif-Infos | Lila (`#6f42c1`/`#f3e8ff`) | Spezieller Tarifkopf, PDF-Link |
| VOLLSTAENDIG | Alle Elemente (Referenz) | GEW-Rot | Tarifkopf, Shop, CTA mit Bild, 2-Spalten |
| EINFACH-AJuM | AJuM-Newsletter | GEW-Rot | AJuM-Logo, 2-Spalten-News |
| CALLTOACTION-Mitglied | Mitglied-werden-Prozess | GEW-Rot | Keine Bilder, Antrag-CTA, Gute-Gründe |

## Workflow für neue Templates

1. Bootstrap-HTML mit direkten Hex-Farben erstellen (keine `var()`)
2. Inline Styles für Buttons verwenden
3. Table-Zentrierung für Footer und Social Media
4. CleverReach `image align` korrekt setzen (nicht auf CSS verlassen)
5. Mit `bootstrap-email` kompilieren (aus dem `sources/` Verzeichnis)
6. Nach Bedarf in `compiled/` manuell nachbessern (z.B. SCSS-Variablen-Reste)
