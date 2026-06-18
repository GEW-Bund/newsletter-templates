# Newsletter-Templates der GEW

Hier findest du Newsletter-Vorlagen ("Templates") für den Versand von E-Mails mit [Cleverreach](https://www.cleverreach.de).

## bootstrap

Die Templates wurden mithilfe von Bootstrap in HTML geschrieben. Das Ruby-Package [bootstrap-email](https://github.com/bootstrap-email/bootstrap-email) (v1.5.1) wandelt sie in eigenständige Templates um, die ohne externe Ressourcen in jedem E-Mail-Client funktionieren.

## Templates herunterladen und nutzen

Die umgewandelten, fertigen Templates sind als **compiled.zip** archiviert und können direkt heruntergeladen werden. Darin enthalten sind Templates, die direkt in Cleverreach importiert werden können.

## Was ist Was?

**Cleverreach-CALLTOACTION-2025** — Einfache E-Mail mit Call-to-Action-Box, Titelbild und Button.

**Cleverreach-EINFACH-2025** — Einfacher Newsletter mit News, Pressemitteilungen und Call-to-Action. Das Tutorial auf https://doku.gew.de/cleverreach basiert auf dieser Vorlage.

**Cleverreach-KOMPLEX-2025** — Komplexer Newsletter mit mehr Elementen und Flexibilität, aber auch höherer Komplexität in Cleverreach.

**Cleverreach-SHOP-2025** — Kompakte Vorlage für Shop-Artikel.

**Cleverreach-TARIFTELEGRAMM-2025** — Basis für den Versand der Tariftelegramme mit lila Farb-Schema.

**Cleverreach-VOLLSTAENDIG-2025** — Vollständiges Template mit allen Elementen (Referenz). Nicht für den direkten Versand geeignet.

**Cleverreach-EINFACH-AJuM-2025** — AJuM-Newsletter mit 2-Spalten-News-Layout und AJuM-Logo.

**Cleverreach-CALLTOACTION-Mitglied-2025** — Template für den Mitglied-werden-Prozess, ohne Bilder, mit Antrag-CTA und Gute-Gründe-Block.

## Templates umwandeln

Die bearbeitbaren Bootstrap-HTML-Quellen liegen im Ordner **sources/**. Im Ordner **compiled/** liegen die fertig kompilierten Templates.

Zum Kompilieren im `sources/`-Verzeichnis:

```bash
for file in *bootstrap*.html; do
  bootstrap-email "$file" > "../compiled/${file/-bootstrap/}"
done
```

**WICHTIG:** Die Datei `bootstrap-email.scss` im `sources/`-Ordner muss beim Kompilieren vorhanden sein. Sie enthält die globalen Farb- und Font-Definitionen.

## Alte Templates

Veraltete Templates (2022/2023) befinden sich im Ordner **legacy/** und werden nicht mehr aktiv genutzt.
