---
layout: post
title:  "Eingabeformular für ELER Maßnahmen"
date:   2021-02-25 18:00:00 +0100
categories: jomash
image: eingabeformular-fuer-eler-massnahmen.jpg
video: eingabeformular-fuer-eler-massnahmen.webm
---

Wie wäre es, wenn ein Multiple Choice Formular eine Auswahl lediglich dann vorschlägt, wenn die Auswahl aus sinnvoll ist? Die Eingabe ginge gewiss schneller vonstatten, da die Anzahl der sinnvollen Optionen geringer ist. Doch was wäre, wenn die gewünschte Auswahl nicht verfügbar ist und der Benutzer kann sich nicht erklären warum? Eine Information darüber, welche Voraussetzung die gewünschte Option erfüllen muss und warum sie es nicht tut, wäre notwendig.

Das Thünen-Institut für Ländliche Räume stellte die Entwicklung eines solchen Formulars in Auftrag. Es dient der Erfassung von Fördermaßnahmen des “Europäischen Landwirtschaftsfonds für die Entwicklung des ländlichen Raums” kurz ELER. Die Eingabefelder und die dazugehörigen Auswahloptionen sind zahlreich. 

Um zu gewährleisten, dass eine Auswahl nur dann vorgeschlagen wird, wenn die Auswahl der bisherigen Felder damit kompatibel ist, kann wie folgt realisiert werden:


{% highlight dart %}
static final wald = Zielflaeche("Wald/Forst",
    condition: (choices) =>
        (
            choices.contains(Foerderklasse.erschwernisAusgleich) ||
            choices.contains(Foerderklasse.agrarumweltUndKlimaMassnahme)
        ) &&
        (
            !choices.contains(Kategorie.FoerderungBestimmterRassenUndKulturen)
        )
);
{% endhighlight %}

Für das Eingabefeld “Zielfläche” kann die Option “Wald/Forst” nur dann gewählt werden, wenn die Funktion “contition” als wahr ausgewertet wird. Wenn zuvor die bei der Förderklasse z.B. der Erschwernisausgleich oder die Agrarumwelt- und Klimamaßnahme und außerdem als Kategorie die Förderung bestimmter Rassen und Kulturen ausgewählt wurde, dann sind die Bedingungen erfüllt und die Option ist auswählbar.

Doch diese Implementierung macht es unmöglich, dem Benutzer einen Hinweis zu geben, warum die Auswahl nicht zur Verfügung steht. condition ist eine Funktion und somit ist es nicht möglich, die notwendige Kombination von Optionen mit den aktuell tatsächlich eingegebenen Optionen zu vergleichen. Zu diesem Zweck muss die Bedingung als Datenstruktur gespeichert sein. Die Datenstruktur muss die logischen Operatoren UND, ODER und NICHT unterstützen, um die Bedingungen abzubilden. Gleichzeitig sollte die Notation einfach lesbar sein, damit die Bedingungen auch mühelos angepasst werden können.

Zu diesem Zweck entwickelte ich meine erste Fluent API, zu deutsch “sprechende Schnittstelle”. Die gleiche Bedingung sieht darin folgendermaßen aus:


{% highlight dart %}
static final wald = Zielflaeche("Wald/Forst",
    condition: 
    isIn({
        Foerderklasse.erschwernisAusgleich,
        Foerderklasse.agrarumweltUndKlimaMassnahme
    })
    .and(
        isNotIn({
                    Kategorie.FoerderungBestimmterRassenUndKulturen
                })
        )
);
{% endhighlight %}

Die Bedingung lässt sich nun mit der aktuellen Auswahl vergleichen und ein Mengendiagramm gibt Aufschluss darüber, wie die Bedingung aussieht. Ein roter Kreis um die falsche Option zeigt den Fehler der aktuellen Auswahl an.