---
layout: post
title:  "Eingabeformular für ELER Maßnahmen"
date:   2021-02-25 18:00:00 +0100
categories: jomash
image: eingabeformular-fuer-eler-massnahmen.jpg
video: eingabeformular-fuer-eler-massnahmen.webm
---

JoMash ist eine Erweiterung von Qlik Sense®. Mit Benutzerfreundliche Navigation führt
einen ohne Programmierkenntnisse durch die Funktionen, die per Drag and Drop für ein
übersichtliches Seitenlayout sorgt.

{% highlight dart %}
static final wald = Zielflaeche("Wald/Forst",
    condition: 
    isIn({
        Foerderklasse.erschwernisAusgleich,
        Foerderklasse.agrarumweltUndKlimaMassnahmeNurVertragsnaturschutz,
        Foerderklasse.agrarumweltUndKlimaMassnahmeOhneVertragsnaturschutz
    })
    .and(
        isNotIn({
                    Kategorie.AnbauZwischenfruchtUntersaat,
                    Kategorie.FoerderungBestimmterRassenUndKulturen
                })
        )
);
{% endhighlight %}




Dabei ist das Kundenspezifisches Corporate- und das
responsive Design nur eine der vielen Möglichkeiten die JoMash zu bieten hat.
JoMash ermöglicht die Erstellung von Qlik Sense Mashups ohne jegliche Programmierkenntnisse.
Objekte können per Drag and Drop Funktion eingefügt werden und bieten zahlreiche
Konfigurationen an. So können Objekte ein- und ausgeblendet werden, in ihrer Höhe und
Breite angepasst werden oder mit einem Exportdialog ausgestattet werden. Zudem können
Objekte aus unterschiedlichen Qlik Sense Applikationen eingebettet werden.
Die Navigation enthält mehreren Ebenen und ist genau wie das Seitenlayout mit wenigen
Klicks erstellt.
Eine intelligente Suche ermöglicht das Suchen über mehrere Qlik Sense Applikationen.
Zudem lassen sich die Felder eingrenzen, um die Suchgeschwindigkeit zu erhöhen.
Über iframes ist die Integration externer Inhalte, wie z.B. Wetterinformationen, Börsencharts
etc. möglich.