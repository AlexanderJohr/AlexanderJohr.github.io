---
layout: post
title:  "Biogasanlagen Finder"
date:   2016-06-26 18:00:00 +0100
categories: jomash
image: biogasanlagen-finder.jpg
video: biogasanlagen-finder.webm
alt_video: biogasanlagen-finder.mp4
---

Kreisförmig und einfarbig, das sind die Kriterien, nach denen sich der Großteil von Biogasanlagen auf Kartenausschnitten identifizieren lässt. Und genau diese Kriterien sind es auch, die ein eigens entwickelter Bildverarbeitungs-Algorithmus nutzt, um die Erkennung solcher Biogasanlagen zu automatisieren.

Der Rahmen des Projektes war die Berufsfeldorientierung Bildverarbeitung bei [Prof. Jürgen Singer Ph.D](https://www.hs-harz.de/jsinger/zur-person). Ich führte das Projekt zusammen mit meiner Teamkollegin Caroline Rühling durch. Gemeinsam erdachten wir folgenden Algorithmus: zunächst wird der Kartenausschnitt von Google Maps angefordert und anschließend in seiner Sättigung erhöht. Die verstärkten Farbkontraste erleichtern im folgenden Schritt die Kantenerkennung. Nun wird mit einem stetig zunehmendem Radius um jedes Pixel des Kantenbildes ein Kreis mit der gleichen Helligkeit des Ursprungspixels gezeichnet. Überlappen sich Kreise, so werden die Helligkeits-Intensitäten addiert. Das führt dazu, dass die Intensität vereinzelter Pixel im Vergleich zum restlichen Bild sehr hoch ist. Das liegt daran, dass wenn mit dem korrekten Radius eines Kreises um jedes Pixel der Kreiskante ein neuer Kreis gezogen wird, so überlappen sich all diese Kreise im Zentrum des Ursprungskreises. Die Pixel mit der höchsten Intensität werden somit zu Kandidaten für Biogasanlagen gekennzeichnet. Im abschließenden Schritt wird überprüft, ob die Fläche einfarbig ist. Somit können beispielsweise Kläranlagen herausgefiltert werden, da sie zwar ebenfalls kreisförmig, aber nicht einfarbig sind.