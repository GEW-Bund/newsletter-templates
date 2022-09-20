# Newsletter-Templates der GEW
Hier findest du Newsletter-Vorlagen ("Templates") für den Versand von E-Mails mit [Cleverreach](https://www.cleverreach.de).

## bootstrap
Die Templates werden mithilfe von bootstrap in HTML geschrieben. Das ruby-package [bootstrap-email](https://github.com/bootstrap-email/bootstrap-email) kann sie dann umwandeln. Herauskommen eigenständige Templates, die ohne externe Ressourcen in jedem E-Mail-Client funktionieren.

## Templates herunterladen und nutzen
Die umgewandelten, fertigen Templates sind als **compiled.zip** archiviert und können direkt heruntergeladen werden. Darin enthalten sind Templates, die direkt in Cleverreach importiert werden können.

## Was ist Was?
**Cleverreach-Call-to-Action-bootstrap_2022** – Einfache E-Mail mit Call-to-Action-Box und Button als Link.

**Cleverreach-EINFACH-bootstrap_2022** – Einfacher Newsletter mit weniger Bausteinen, dafür einfacher zu bedienen. Das Tutorial auf https://doku.gew.de/cleverreach basiert auf dieser Vorlage.

**Cleverreach-KOMPLEX-bootstrap_2022** – Komplexer Newsletter mit mehr Elementen und mehr Flexibilität, aber auch mehr Komplexität im Umgang in Cleverreach.

**Cleverreach-Shop-bootstrap_2022** – Einfacher Newsletter für Shop-Artikel.

**Cleverreach-Tariftelegramm-bootstrap_2022** – Basis für den Versand der Tariftelegramme.

**Cleverreach-VOLLSTAEDIG-bootstrap_2022** – Vollständiges Template mit allen Elementen, das nicht für den direkten Versand geeignet ist.

## Templates umwandeln
HTML-Templates mit bootstrap als eingebundene, externe Ressource liegen im Hauptverzeichnis. Im Unterordner **compiled** liegen jeweils aktuell umgewandelte, fertige Templates, die mit [bootstrap-email](https://github.com/bootstrap-email/bootstrap-email) umgewandelt wurden.

Um eigene, neue Vorlagen umzuwandeln ist folgender Befehl notwendig
`bootstrap-email [IN.html] > [OUT.html]`
